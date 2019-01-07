# nxshot
Automatically organize and timestamp your Nintendo Switch captures
![image](https://user-images.githubusercontent.com/17756301/33006063-0c36d2ce-cdb0-11e7-8875-1044eab6527a.png)

## Requirements

* ``pip install pycryptodome``

* ``pip install BeautifulSoup4``

* (Optional) Key at offset 0x71000704D0 from the capsrv NSO loaded up in IDA as ``key.txt`` on the same folder as nxshot for automatic updating. Hash: ``24e0dc62a15c11d38b622162ea2b4383``

## Usage

``nxshot.py FILEPATH [-h] [-l] [-s] [-o outputfolder]``

Positional arguments:

>FILEPATH:    "Nintendo/Album" folder from your SD card.

Optional arguments:
```
-h, --help                    Show the help message and exit
-l, --local                   Treat FILEPATH as a single folder of captures, instead of "Nintendo/Album/" 
                              structure 
-s, --strip-regions           Don't include game region in the folder's name
-o, --output outputfolder     Path where "Organized/" captures should be copied to.
```
![image](https://user-images.githubusercontent.com/17756301/33006113-3f204800-cdb0-11e7-99f4-94790c01916d.png)

By default, organized and tagged files are copied to ``../Nintendo/Album/Organized`` in a folder with the game's name.

If some of your screenshots end up being copied to ``../Nintendo/Album/Organized/Unknown``, please open an issue with the game id from the screenshot filename so that I can update the gameid list.

## Examples


### Organize from SD to external folder

By default, organized captures are copied to the source `Nintendo/Album`, in a new `Organized/` folder. If you are using a path directly from your SD card, you might not have the sufficient free space, or simply might not want that. You can manually select the output folder with `--output` parameter:

`python nxshot.py G:\Nintendo\Album -o D:\MyPictures`

### Folders with game name only

The `gameids.json` list contain games with their respective regions, and are included in the game folder's name. If you prefer a more clean directory name, you can use the `--strip-regions` parameter.

`python nxshot.py G:\Nintendo\Album --strip-regions`

### Reorganize your Unknown/ folder

So, you organized your captures and are still left with an `Unknown/` folder. After editing the `gameids.json` list file, you can opt to organize that folder individually, instead of repeating the whole process again or manually creating folders yourself. Just use the parameter `--local` to individually organize any folder that contains the Nintendo Switch capture media:

`python nxshot.py D:\MyPictures\Unknown --local -o D:\MyPictures`

This will put your past `Unknown` captures into their proper place in `D:\MyPictures\Organized` (as long as you add them to the gameid list properly)

## Current gameid list

To see what games are currently automatically recognized, take a look at the [gameids.json](gameids.json) file.

The list is automatically updated from [SwitchBrew](http://switchbrew.org/index.php?title=Title_list/Games)
          
## Help

If you have any questions, feel free to send me a tweet [**@Some1CP**](https://twitter.com/Some1CP).
