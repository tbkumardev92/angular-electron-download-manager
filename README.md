# electron-download-manager

> Manage downloadItems for Angular from [Electron](http://electron.atom.io)'s BrowserWindows without user interaction, allowing single file download and bulk downloading asynchronously


## Why?

- Register global listener that attaches to all newly created BrowserWindow instances
- Automatically download the file to a given folder, without user prompt
- Callback when download has completed (or failed)
- Bulk download: pass a bunch of links and all will get downloaded, with a callback once they're all done.


## Install

```
$ add "electron-download-manager":"require('electron-download-manager')" to module.exports in webpack.config
```


## Usage


const electron = require('electron').remote;
const app = electron.app;
const DownloadManager = require("electron-download-manager");

function(File){

    DownloadManager.register({downloadFolder: app.getPath("downloads") + "/my-app"});
    DownloadManager.download({
      url: File
    }, function(error, url){
      if(error){
        console.log("ERROR: " + url);
        return;
      }

      console.log("DONE: " + url);
    });
}
## Questions
Feel free to open Issues to ask questions about using this module, PRs are very welcome and encouraged.

## License

MIT © Daniel Nieto, loosely based on code from [Sindre Sorhus](https://sindresorhus.com)
