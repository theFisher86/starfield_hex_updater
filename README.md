# Starfield Hex Updater

Install/build instructions can be found [HERE](https://github.com/gazzamc/starfield_hex_updater/tree/main/docs), you have the option of a powershell Auto Installer script or you can do the process manually.

Compatible/Incompatible mods can be found [Here](https://github.com/gazzamc/starfield_hex_updater/blob/main/docs/compatibility/README.md).

## Requirements
I've tried to keep it as simple as possible, I've used only built-in imports. Using the below version of python, I'm sure any version above python 3.x would work, but if you have any trouble use the one I mentioned.

Be vigilant of the hex table name `hex_table_{game_version}_{commit_id}.json`, it consists of important data, so if you're having issues after running the update be sure you're trying to update with the correct hex table.

> Python 3.11 

## Notes

### Patcher
* As of `v0.1.3` the script can patch without providing the path, if placed in the root of the SFSE repo folder.

* As of `v0.2.0`, the script can now verify the files patched via md5 checksums

### CLI

* Added support for Powershell 7

* As of `v1.5.6`, the powershell CLI can now install a standalone python version, this can be helpful if you're having issues detecting your install.

* As of `v1.5.10`, when setting the newGamePath, the permissions will be checked to ensure there's less issues when moving the Starfield executable.

### Misc

* Added a script to auto generate the hex table using the Address Libraries

## Usage
        hex_updater.py -m <mode> <options>

        Modes:
            generate: Creates a hex table for updating hex values
            update: Updates hex values using a hex dictionary
            patch: Patches out the error message preventing program from running
            md5: Will generate a md5 checksum for the files to verify patch was successful

        <Options>
            -h, --help
            -m, --mode: Selects the mode to use
            -v, --version: script version number
            -s, --silent: hides output of commands
                generate:
                    -p, --path: Path of the old hex values, will be used as a reference (use full path)
                    -n, --path2: Path of the new hex values, will become the value of the old key (use full path)
                    -g, --starfield: Starfield game version, will be used in the filename
                    -c, --commit: Truncated commit ID of SFSE, will be used in the filename
                update:
                    -p, --path: Path to the folder of files to be updated, files will be backed up by default (use full path)
                    -d, --dictfile: dictionary to be used for updating hex values (use full path)
                    -b, --backup: Option to backup files
                patch:
                    -p, --path: Path to the folder of files to be patched, files will be backed up by default (use full path)
                    -b, --backup: Option to backup files
                md5:
                    -p, --path: Path to the folder containing the files
                    -f, --filename: Filename of the file generated
                    --verify: Verify patch/update via md5 hash
