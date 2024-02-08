<h1 align="center">Windows 7 Survival Kit</h1>
<p align="center"><small>An Essential Toolkit to Surviving with Windows 7 post-EOL and ESU</small></p>
<hr>

## Preface
This toolkit was designed by me, toydotgame, an avid Windows 7 fan. Although I currently am an Arch Linux user, the OS I used before Arch was Windows 7. I think that the great OS that was 7 should be usable far into the future despite its sunsetting because there simply hasn't been a better Windows since.
Might I give a word of warning: **Windows 7 will only get less and less secure as time goes on**, and there isn't really much you can do about that. However, putting massive security vulnerabilities that may arise in the future aside, Windows 7 _can be_ secure if you use it with common sense and keep secure/good practices in mind.

I'm going to assume you know Windows well enough to know what an `.msc` executable is and how to use Run, etc.

## Introduction/Preparation
This guide assumes you have an installed and activated copy of Windows 7 Pro, Enterprise, or Ultimate, at a minimum SP1 RTM. The updates in this guide will get you to the EOL level of updates. Windows 7 _can_ be activated for free using [online KMS activation](https://massgrave.dev/online_kms.html), however this only grants you a 180-day license and I personally recommend you dig out an old OEM Windows license sticker on any old laptop or desktop you have. Labels for Vista and 7 can be used for valid product keys.

Please download a ZIP of this repository from the green _Code_ button above and extract it, or clone using Git.

## 1. Update Windows
Before running newer updates, run the [Simplix Update Pack](https://blog.simplix.info/update7/) first (can be found in the `Updates\` directory). It'll update your system to "SP1++" and the latest non-ESU updates. It may take multiple restarts and runs for this to complete. The update pack will notably not install the updates that add the full-screen "You should update to Windows 10" advertisements and similar Microsoft EOL garbage.

After that, you'll want to run [BypassESU](https://www.youtube.com/watch?v=gpBTB3ST4kk) to update your system to the extended security updates Microsoft put out after January of 2020 when Windows 7 was sunset.
1. Begin by installing the 5 update packages in the `Updates\`. It may take a few restarts to get them all installed.
2. Run `LiveOS-Setup.cmd` as administrator. Run the full installation (<kbd>1</kbd>). Reboot your system and check for updates from Windows Updates, your system may need to be restarted multiple times.

### Disabling the Windows Update Service
As it doesn't serve much use anymore, and can sometimes use 100% of your available RAM on lower end machines, it's worthwhile to disable the Windows Update service.
1. Run, `services.msc`
2. Look for the _Windows Update_ service. Set its startup type to _Disabled_ and press the _Stop_ button to stop the task.

## 2. Programs
In the `Extras\` folder, there are a few program installer executables that I've collected.
### Supported
The following applications will support Windows 7 for the forseeable future and therefore can alternatively be downloaded as their respective latest versions from the internet:
* 7-Zip
* Discord
	* Vencord (Includes OpenAsar)
* Search Everything
* JDK8 (SE)
* Waterfox (Note: G6 will be the final major release of Waterfox to support Windows 7, as it is based on Firefox ESR 115)
* GIMP
* ShareX (Note: Set up a Win+Shift+S shortcut if you are used to the Windows 10+ muscle memory)
* VLC
* Git
* ThrottleStop

### Unsupported
The following applications have specifically been picked for being the last available versions to support Windows 7:
* Audacity
* Firefox (v115 ESR)
* .NET Framework 4.8 Runtime
* OBS
* Obsidian
* VS Code
* iTunes

### Minecraft Launcher
For legal/EULA reasons (Microsoft hates redistribution of even non-paid software grr), I cannot distribute a copy of the classic launcher. However I _can_ say that if you go to [https://launcher.mojang.com/v1/objects/eabbff5ff8e21250e33670924a0c5e38f47c840b/launcher.jar](http://web.archive.org/web/20190929213435/https://launcher.mojang.com/v1/objects/eabbff5ff8e21250e33670924a0c5e38f47c840b/launcher.jar), you might find it.

To patch the launcher to work with Microsoft accounts rather than Mojang/Minecraft Premium accounts only, you can use a program called [MSA4Legacy written by NepNep21](https://github.com/NepNep21/MSA4Legacy).

#### Procedure: Requires the included JRE to be installed!
1. Move your downloaded `launcher.jar` to this directory.
2. In a terminal here, run `java -jar .\installer-1.1.0.jar`.
3. Follow the GUI's instructions and select the launcher JAR. Once finished, it will output `launcher-patched.jar`.
3a. You can now move that to your .minecraft or some other location such as a hidden folder on the desktop.
3b. Create a link on your desktop to run `java -jar C:\path\to\launcher-patched.jar`. Modify `%ProgramData%\Microsoft\Windows\Start Menu\Programs\Minecraft.lnk` (or whatever it's called) to run this Java command also, rather than the new launcher EXE.

PS: If you are installing Fabric also, make sure to unselect "Create profile" in the installer. It doesn't function right with the legacy launcher and you will be required to create a profile manually.

### Steam
Steam ended support for Windows 7 on January 1<sup>st</sup>, 2024. However, you can use an older build and force updates to stop to continue using Steam for a bit longer.
1. Start by installing Steam from the internet (or from `Extras\`).
2. Extract the Steam ZIP in `Extras\` and copy the `Steam\` folder to overwrite the Steam folder in Program Files.
3. Add/overwrite the following to `C:\Program Files (x86)\Steam\steam.cfg`:
	```
	BootStrapperInhibitAll=enable
	BootStrapperForceSelfUpdate=disable
	```

If you did it correctly, Steam should throw an error when you try to update from within the client.

<hr>

## 3. Untested Extras
### Extended Kernel
There isn't really a proper extended kernel mod for Windows 7 like Vista had, but [VxKex](https://github.com/vxiiduu/VxKex) claims Windows 8+ compatibility running on Windows 7, which is definitely worth the install.

### Modern Hardware Support/USB 3
If installing on a modern system, USB drivers are messed up with modern CPUs and chipsets. [This Reddit thread](https://www.reddit.com/r/windows7/comments/tlndaf/can_you_install_windows_7_on_a_b550f/) _might_ be a good launching pad to start reading from, but I myself haven't tested any part of it yet.
