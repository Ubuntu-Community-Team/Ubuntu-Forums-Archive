---
title: "Wubi slow install"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by Blackbm on 2011-06-02
Complete novice here, So go easy on me :)
I'm trying to install ubuntu by way of Wubi to run with my windows 7 on an Acer Aspire 5542.
But the Wubi.exe gets to 1/3 dowloaded and then just stays there. It says I have 30 thousand hrs to wait, and is steadily going up :( lol. Surely there's a fault here somewhere.

Any help would be appreciated.....

---

### Post by Blackbm on 2011-06-02
Downloaded the iso image and created the boot disc. I booted the disc and it seems the file has a corrupt kernel image file now :(

I give up. I thought it would be easy to get away from Windows, But it looks like I'm stuck with it :(

---

### Post by mörgæs on 2011-06-02
Hi, welcome to the fora.

When you have downloaded the ISO, you can check it with the MD5 test to see if it is damaged.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If your internet connection is slow, can't you download at some other place? 

There are also internet services which sell Ubuntu CD's at a low price.

---

### Post by Blackbm on 2011-06-03
Finally got it downloaded to a disc. But I ran into this error while booting from the disc...

Initramfs Mount: Mounting 1dev/loop0 on //filesystem failed: input/output error
Can not mount 1dev/loop0 c/cdrom/casper/filesystem.squashfs //filesystem.squashfs

Any ideas what to do now?
Here is the log file from temp folder in case it might shed some light on the problem..

```
05-29 18:14 INFO   root: === wubi 11.04 rev211 ===
05-29 18:14 DEBUG  root: Logfile is c:\users\little~1\appdata\local\temp\wubi-11.04-rev211.log
05-29 18:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Little Bastard\\Downloads\\wubi.exe"']
05-29 18:14 DEBUG  CommonBackend: data_dir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\data
05-29 18:14 DEBUG  WindowsBackend: 7z=C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\bin\7z.exe
05-29 18:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-29 18:14 DEBUG  CommonBackend: Fetching basic info...
05-29 18:14 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi.exe
05-29 18:14 DEBUG  CommonBackend: platform=win32
05-29 18:14 DEBUG  CommonBackend: osname=nt
05-29 18:14 DEBUG  CommonBackend: language=en_IE
05-29 18:14 DEBUG  CommonBackend: encoding=cp1252
05-29 18:14 DEBUG  WindowsBackend: arch=amd64
05-29 18:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\data\isolist.ini
05-29 18:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 18:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 18:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 18:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 18:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 18:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 18:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 18:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 18:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 18:14 DEBUG  WindowsBackend: Fetching host info...
05-29 18:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 18:14 DEBUG  WindowsBackend: windows version=vista
05-29 18:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 18:14 DEBUG  WindowsBackend: windows_sp=None
05-29 18:14 DEBUG  WindowsBackend: windows_build=7601
05-29 18:14 DEBUG  WindowsBackend: gmt=0
05-29 18:14 DEBUG  WindowsBackend: country=IE
05-29 18:14 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 18:14 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 18:14 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 18:14 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 18:14 DEBUG  WindowsBackend: windows_language_code=1033
05-29 18:14 DEBUG  WindowsBackend: windows_language=English
05-29 18:14 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 18:14 DEBUG  WindowsBackend: bootloader=vista
05-29 18:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195714.296875 mb free ntfs)
05-29 18:14 DEBUG  WindowsBackend: drive=Drive(C: hd 195714.296875 mb free ntfs)
05-29 18:14 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 18:14 DEBUG  WindowsBackend: uninstaller_path=None
05-29 18:14 DEBUG  WindowsBackend: previous_target_dir=None
05-29 18:14 DEBUG  WindowsBackend: previous_distro_name=None
05-29 18:14 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 18:14 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 18:14 DEBUG  WindowsBackend: keyboard_variant=
05-29 18:14 DEBUG  CommonBackend: python locale=('en_IE', 'cp1252')
05-29 18:14 DEBUG  CommonBackend: locale=en_IE.UTF-8
05-29 18:14 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 18:14 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 18:14 DEBUG  CommonBackend: Searching for local CDs
05-29 18:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp is a valid Ubuntu CD
05-29 18:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp is a valid Ubuntu CD
05-29 18:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp is a valid Ubuntu Netbook CD
05-29 18:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp is a valid Kubuntu CD
05-29 18:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp is a valid Kubuntu CD
05-29 18:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp is a valid Xubuntu CD
05-29 18:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp is a valid Xubuntu CD
05-29 18:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp is a valid Mythbuntu CD
05-29 18:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp is a valid Mythbuntu CD
05-29 18:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 18:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:14 INFO   root: Running the installer...
05-29 18:14 DEBUG  WindowsFrontend: __init__...
05-29 18:14 DEBUG  WindowsFrontend: on_init...
05-29 18:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\translations, languages=['en_IE', 'en']
05-29 18:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\translations, languages=['en_IE', 'en']
05-29 18:15 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=littlebastard
05-29 18:15 INFO   root: Received settings
05-29 18:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\translations, languages=['en_US', 'en']
05-29 18:15 DEBUG  TaskList: # Running tasklist...
05-29 18:15 DEBUG  TaskList: ## Running select_target_dir...
05-29 18:15 INFO   WindowsBackend: Installing into C:\ubuntu
05-29 18:15 DEBUG  TaskList: ## Finished select_target_dir
05-29 18:15 DEBUG  TaskList: ## Running create_dir_structure...
05-29 18:15 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-29 18:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-29 18:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-29 18:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-29 18:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-29 18:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-29 18:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-29 18:15 DEBUG  TaskList: ## Finished create_dir_structure
05-29 18:15 DEBUG  TaskList: ## Running uncompress_target_dir...
05-29 18:15 DEBUG  TaskList: ## Finished uncompress_target_dir
05-29 18:15 DEBUG  TaskList: ## Running create_uninstaller...
05-29 18:15 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Little Bastard\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-29 18:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-29 18:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-29 18:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-29 18:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-29 18:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-29 18:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-29 18:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-29 18:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-29 18:15 DEBUG  TaskList: ## Finished create_uninstaller
05-29 18:15 DEBUG  TaskList: ## Running copy_installation_files...
05-29 18:15 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-29 18:15 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\winboot -> C:\ubuntu\winboot
05-29 18:15 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-29 18:15 DEBUG  TaskList: ## Finished copy_installation_files
05-29 18:15 DEBUG  TaskList: ## Running get_iso...
05-29 18:15 DEBUG  CommonBackend: Searching for local CD
05-29 18:15 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp is a valid Ubuntu CD
05-29 18:15 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl6651.tmp\casper\filesystem.squashfs
05-29 18:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:15 DEBUG  CommonBackend: Searching for local ISO
05-29 18:15 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-29 18:15 DEBUG  TaskList: New task get_metalink
05-29 18:15 DEBUG  TaskList: ### Running get_metalink...
05-29 18:15 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink > C:\ubuntu\install
05-29 18:15 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-29 18:15 DEBUG  downloader: download finished (read 28363 bytes)
05-29 18:15 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink > C:\ubuntu\install
05-29 18:15 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-29 18:15 DEBUG  downloader: download finished (read 874 bytes)
05-29 18:15 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
05-29 18:15 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-29 18:15 DEBUG  downloader: download finished (read 198 bytes)
05-29 18:15 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-29 18:15 INFO   saplog: Checking block bindings..
05-29 18:15 INFO   saplog: Key verified successfully.
05-29 18:15 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

05-29 18:15 DEBUG  TaskList: ### Finished get_metalink
05-29 18:15 DEBUG  TaskList: New task download
05-29 18:15 DEBUG  TaskList: ### Running download...
05-29 18:15 DEBUG  btdownloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-29 18:19 INFO   WindowsFrontend: Operation cancelled
05-29 18:19 DEBUG  WindowsFrontend: frontend.quit
05-29 18:19 DEBUG  WindowsFrontend: frontend.on_quit
05-29 18:19 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-29 18:19 DEBUG  TaskList: # Cancelling tasklist
05-29 18:19 DEBUG  TaskList: ### Finished download
05-29 18:19 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-29 18:19 DEBUG  root: application.on_quit
05-29 18:19 DEBUG  root: Forceful exit
05-29 18:19 INFO   root: sys.exit
05-29 18:19 INFO   root: === wubi 11.04 rev211 ===
05-29 18:19 DEBUG  root: Logfile is c:\users\little~1\appdata\local\temp\wubi-11.04-rev211.log
05-29 18:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Little Bastard\\Downloads\\wubi.exe"']
05-29 18:19 DEBUG  CommonBackend: data_dir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\data
05-29 18:19 DEBUG  WindowsBackend: 7z=C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\bin\7z.exe
05-29 18:19 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-29 18:19 DEBUG  CommonBackend: Fetching basic info...
05-29 18:19 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi.exe
05-29 18:19 DEBUG  CommonBackend: platform=win32
05-29 18:19 DEBUG  CommonBackend: osname=nt
05-29 18:19 DEBUG  CommonBackend: language=en_IE
05-29 18:19 DEBUG  CommonBackend: encoding=cp1252
05-29 18:19 DEBUG  WindowsBackend: arch=amd64
05-29 18:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\data\isolist.ini
05-29 18:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 18:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 18:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 18:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 18:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 18:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 18:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 18:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 18:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 18:19 DEBUG  WindowsBackend: Fetching host info...
05-29 18:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 18:19 DEBUG  WindowsBackend: windows version=vista
05-29 18:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 18:19 DEBUG  WindowsBackend: windows_sp=None
05-29 18:19 DEBUG  WindowsBackend: windows_build=7601
05-29 18:19 DEBUG  WindowsBackend: gmt=0
05-29 18:19 DEBUG  WindowsBackend: country=IE
05-29 18:19 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 18:19 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 18:19 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 18:19 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 18:19 DEBUG  WindowsBackend: windows_language_code=1033
05-29 18:19 DEBUG  WindowsBackend: windows_language=English
05-29 18:19 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 18:19 DEBUG  WindowsBackend: bootloader=vista
05-29 18:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195715.054688 mb free ntfs)
05-29 18:19 DEBUG  WindowsBackend: drive=Drive(C: hd 195715.054688 mb free ntfs)
05-29 18:19 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 18:19 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-29 18:19 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-29 18:19 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-29 18:19 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 18:19 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 18:19 DEBUG  WindowsBackend: keyboard_variant=
05-29 18:19 DEBUG  CommonBackend: python locale=('en_IE', 'cp1252')
05-29 18:19 DEBUG  CommonBackend: locale=en_IE.UTF-8
05-29 18:19 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 18:19 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 18:19 DEBUG  CommonBackend: Searching for local CDs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Ubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Ubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Ubuntu Netbook CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Kubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Kubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Xubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Xubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Mythbuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Mythbuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 INFO   root: Already installed, running the uninstaller...
05-29 18:19 INFO   root: Running the uninstaller...
05-29 18:19 INFO   CommonBackend: This is the uninstaller running
05-29 18:19 DEBUG  WindowsFrontend: __init__...
05-29 18:19 DEBUG  WindowsFrontend: on_init...
05-29 18:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\translations, languages=['en_IE', 'en']
05-29 18:19 INFO   root: Received settings
05-29 18:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\translations, languages=['en_IE', 'en']
05-29 18:19 DEBUG  TaskList: # Running tasklist...
05-29 18:19 DEBUG  TaskList: ## Running Backup ISO...
05-29 18:19 DEBUG  TaskList: ## Finished Backup ISO
05-29 18:19 DEBUG  TaskList: ## Running Remove bootloader entry...
05-29 18:19 DEBUG  WindowsBackend: Could not find bcd id
05-29 18:19 DEBUG  WindowsBackend: undo_bootini C:
05-29 18:19 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 195715.054688 mb free ntfs)
05-29 18:19 DEBUG  TaskList: ## Finished Remove bootloader entry
05-29 18:19 DEBUG  TaskList: ## Running Remove target dir...
05-29 18:19 DEBUG  CommonBackend: Deleting C:\ubuntu
05-29 18:19 DEBUG  TaskList: ## Finished Remove target dir
05-29 18:19 DEBUG  TaskList: ## Running Remove registry key...
05-29 18:19 DEBUG  TaskList: ## Finished Remove registry key
05-29 18:19 DEBUG  TaskList: # Finished tasklist
05-29 18:19 INFO   root: Almost finished uninstalling
05-29 18:19 INFO   root: Finished uninstallation
05-29 18:19 DEBUG  CommonBackend: Fetching basic info...
05-29 18:19 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi.exe
05-29 18:19 DEBUG  CommonBackend: platform=win32
05-29 18:19 DEBUG  CommonBackend: osname=nt
05-29 18:19 DEBUG  WindowsBackend: arch=amd64
05-29 18:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\data\isolist.ini
05-29 18:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 18:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 18:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 18:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 18:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 18:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 18:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 18:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 18:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 18:19 DEBUG  WindowsBackend: Fetching host info...
05-29 18:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 18:19 DEBUG  WindowsBackend: windows version=vista
05-29 18:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 18:19 DEBUG  WindowsBackend: windows_sp=None
05-29 18:19 DEBUG  WindowsBackend: windows_build=7601
05-29 18:19 DEBUG  WindowsBackend: gmt=0
05-29 18:19 DEBUG  WindowsBackend: country=IE
05-29 18:19 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 18:19 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 18:19 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 18:19 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 18:19 DEBUG  WindowsBackend: windows_language_code=1033
05-29 18:19 DEBUG  WindowsBackend: windows_language=English
05-29 18:19 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 18:19 DEBUG  WindowsBackend: bootloader=vista
05-29 18:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195716.722656 mb free ntfs)
05-29 18:19 DEBUG  WindowsBackend: drive=Drive(C: hd 195716.722656 mb free ntfs)
05-29 18:19 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 18:19 DEBUG  WindowsBackend: uninstaller_path=None
05-29 18:19 DEBUG  WindowsBackend: previous_target_dir=None
05-29 18:19 DEBUG  WindowsBackend: previous_distro_name=None
05-29 18:19 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 18:19 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 18:19 DEBUG  WindowsBackend: keyboard_variant=
05-29 18:19 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 18:19 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 18:19 DEBUG  CommonBackend: Searching for local CDs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Ubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Ubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Ubuntu Netbook CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Kubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Kubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Xubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Xubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Mythbuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Mythbuntu CD
05-29 18:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:19 INFO   root: Running the installer...
05-29 18:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\translations, languages=['en_IE', 'en']
05-29 18:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\translations, languages=['en_IE', 'en']
05-29 18:20 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=littlebastard
05-29 18:20 INFO   root: Received settings
05-29 18:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\translations, languages=['en_US', 'en']
05-29 18:20 DEBUG  TaskList: # Running tasklist...
05-29 18:20 DEBUG  TaskList: ## Running select_target_dir...
05-29 18:20 INFO   WindowsBackend: Installing into C:\ubuntu
05-29 18:20 DEBUG  TaskList: ## Finished select_target_dir
05-29 18:20 DEBUG  TaskList: ## Running create_dir_structure...
05-29 18:20 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-29 18:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-29 18:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-29 18:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-29 18:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-29 18:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-29 18:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-29 18:20 DEBUG  TaskList: ## Finished create_dir_structure
05-29 18:20 DEBUG  TaskList: ## Running uncompress_target_dir...
05-29 18:20 DEBUG  TaskList: ## Finished uncompress_target_dir
05-29 18:20 DEBUG  TaskList: ## Running create_uninstaller...
05-29 18:20 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Little Bastard\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-29 18:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-29 18:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-29 18:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-29 18:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-29 18:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-29 18:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-29 18:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-29 18:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-29 18:20 DEBUG  TaskList: ## Finished create_uninstaller
05-29 18:20 DEBUG  TaskList: ## Running copy_installation_files...
05-29 18:20 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-29 18:20 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\winboot -> C:\ubuntu\winboot
05-29 18:20 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-29 18:20 DEBUG  TaskList: ## Finished copy_installation_files
05-29 18:20 DEBUG  TaskList: ## Running get_iso...
05-29 18:20 DEBUG  CommonBackend: Searching for local CD
05-29 18:20 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp is a valid Ubuntu CD
05-29 18:20 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl51A8.tmp\casper\filesystem.squashfs
05-29 18:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:20 DEBUG  CommonBackend: Searching for local ISO
05-29 18:20 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-29 18:20 DEBUG  TaskList: New task get_metalink
05-29 18:20 DEBUG  TaskList: ### Running get_metalink...
05-29 18:20 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink > C:\ubuntu\install
05-29 18:20 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-29 18:20 DEBUG  downloader: download finished (read 28363 bytes)
05-29 18:20 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink > C:\ubuntu\install
05-29 18:20 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-29 18:20 DEBUG  downloader: download finished (read 874 bytes)
05-29 18:20 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
05-29 18:20 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-29 18:20 DEBUG  downloader: download finished (read 198 bytes)
05-29 18:20 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-29 18:20 INFO   saplog: Checking block bindings..
05-29 18:20 INFO   saplog: Key verified successfully.
05-29 18:20 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

05-29 18:20 DEBUG  TaskList: ### Finished get_metalink
05-29 18:20 DEBUG  TaskList: New task download
05-29 18:20 DEBUG  TaskList: ### Running download...
05-29 18:20 DEBUG  btdownloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-29 18:27 INFO   WindowsFrontend: Operation cancelled
05-29 18:27 DEBUG  WindowsFrontend: frontend.quit
05-29 18:27 DEBUG  WindowsFrontend: frontend.on_quit
05-29 18:27 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-29 18:27 DEBUG  TaskList: # Cancelling tasklist
05-29 18:27 DEBUG  TaskList: ### Finished download
05-29 18:27 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-29 18:27 DEBUG  root: application.on_quit
05-29 18:27 DEBUG  root: Forceful exit
05-29 18:27 INFO   root: sys.exit
05-29 18:28 INFO   root: === wubi 11.04 rev211 ===
05-29 18:28 DEBUG  root: Logfile is c:\users\little~1\appdata\local\temp\wubi-11.04-rev211.log
05-29 18:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Little Bastard\\Downloads\\wubi.exe"']
05-29 18:28 DEBUG  CommonBackend: data_dir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\data
05-29 18:28 DEBUG  WindowsBackend: 7z=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\bin\7z.exe
05-29 18:28 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-29 18:28 DEBUG  CommonBackend: Fetching basic info...
05-29 18:28 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi.exe
05-29 18:28 DEBUG  CommonBackend: platform=win32
05-29 18:28 DEBUG  CommonBackend: osname=nt
05-29 18:28 DEBUG  CommonBackend: language=en_IE
05-29 18:28 DEBUG  CommonBackend: encoding=cp1252
05-29 18:28 DEBUG  WindowsBackend: arch=amd64
05-29 18:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\data\isolist.ini
05-29 18:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 18:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 18:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 18:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 18:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 18:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 18:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 18:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 18:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 18:28 DEBUG  WindowsBackend: Fetching host info...
05-29 18:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 18:28 DEBUG  WindowsBackend: windows version=vista
05-29 18:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 18:28 DEBUG  WindowsBackend: windows_sp=None
05-29 18:28 DEBUG  WindowsBackend: windows_build=7601
05-29 18:28 DEBUG  WindowsBackend: gmt=0
05-29 18:28 DEBUG  WindowsBackend: country=IE
05-29 18:28 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 18:28 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 18:28 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 18:28 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 18:28 DEBUG  WindowsBackend: windows_language_code=1033
05-29 18:28 DEBUG  WindowsBackend: windows_language=English
05-29 18:28 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 18:28 DEBUG  WindowsBackend: bootloader=vista
05-29 18:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195712.171875 mb free ntfs)
05-29 18:28 DEBUG  WindowsBackend: drive=Drive(C: hd 195712.171875 mb free ntfs)
05-29 18:28 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 18:28 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-29 18:28 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-29 18:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-29 18:28 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 18:28 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 18:28 DEBUG  WindowsBackend: keyboard_variant=
05-29 18:28 DEBUG  CommonBackend: python locale=('en_IE', 'cp1252')
05-29 18:28 DEBUG  CommonBackend: locale=en_IE.UTF-8
05-29 18:28 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 18:28 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 18:28 DEBUG  CommonBackend: Searching for local CDs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Ubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Ubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Ubuntu Netbook CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Kubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Kubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Xubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Xubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Mythbuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Mythbuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 INFO   root: Already installed, running the uninstaller...
05-29 18:28 INFO   root: Running the uninstaller...
05-29 18:28 INFO   CommonBackend: This is the uninstaller running
05-29 18:28 DEBUG  WindowsFrontend: __init__...
05-29 18:28 DEBUG  WindowsFrontend: on_init...
05-29 18:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\translations, languages=['en_IE', 'en']
05-29 18:28 INFO   root: Received settings
05-29 18:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\translations, languages=['en_IE', 'en']
05-29 18:28 DEBUG  TaskList: # Running tasklist...
05-29 18:28 DEBUG  TaskList: ## Running Backup ISO...
05-29 18:28 DEBUG  TaskList: ## Finished Backup ISO
05-29 18:28 DEBUG  TaskList: ## Running Remove bootloader entry...
05-29 18:28 DEBUG  WindowsBackend: Could not find bcd id
05-29 18:28 DEBUG  WindowsBackend: undo_bootini C:
05-29 18:28 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 195712.171875 mb free ntfs)
05-29 18:28 DEBUG  TaskList: ## Finished Remove bootloader entry
05-29 18:28 DEBUG  TaskList: ## Running Remove target dir...
05-29 18:28 DEBUG  CommonBackend: Deleting C:\ubuntu
05-29 18:28 DEBUG  TaskList: ## Finished Remove target dir
05-29 18:28 DEBUG  TaskList: ## Running Remove registry key...
05-29 18:28 DEBUG  TaskList: ## Finished Remove registry key
05-29 18:28 DEBUG  TaskList: # Finished tasklist
05-29 18:28 INFO   root: Almost finished uninstalling
05-29 18:28 INFO   root: Finished uninstallation
05-29 18:28 DEBUG  CommonBackend: Fetching basic info...
05-29 18:28 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi.exe
05-29 18:28 DEBUG  CommonBackend: platform=win32
05-29 18:28 DEBUG  CommonBackend: osname=nt
05-29 18:28 DEBUG  WindowsBackend: arch=amd64
05-29 18:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\data\isolist.ini
05-29 18:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 18:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 18:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 18:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 18:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 18:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 18:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 18:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 18:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 18:28 DEBUG  WindowsBackend: Fetching host info...
05-29 18:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 18:28 DEBUG  WindowsBackend: windows version=vista
05-29 18:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 18:28 DEBUG  WindowsBackend: windows_sp=None
05-29 18:28 DEBUG  WindowsBackend: windows_build=7601
05-29 18:28 DEBUG  WindowsBackend: gmt=0
05-29 18:28 DEBUG  WindowsBackend: country=IE
05-29 18:28 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 18:28 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 18:28 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 18:28 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 18:28 DEBUG  WindowsBackend: windows_language_code=1033
05-29 18:28 DEBUG  WindowsBackend: windows_language=English
05-29 18:28 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 18:28 DEBUG  WindowsBackend: bootloader=vista
05-29 18:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195713.335938 mb free ntfs)
05-29 18:28 DEBUG  WindowsBackend: drive=Drive(C: hd 195713.335938 mb free ntfs)
05-29 18:28 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 18:28 DEBUG  WindowsBackend: uninstaller_path=None
05-29 18:28 DEBUG  WindowsBackend: previous_target_dir=None
05-29 18:28 DEBUG  WindowsBackend: previous_distro_name=None
05-29 18:28 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 18:28 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 18:28 DEBUG  WindowsBackend: keyboard_variant=
05-29 18:28 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 18:28 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 18:28 DEBUG  CommonBackend: Searching for local CDs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Ubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Ubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Ubuntu Netbook CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Kubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Kubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Xubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Xubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Mythbuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Mythbuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 INFO   root: Running the installer...
05-29 18:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\translations, languages=['en_IE', 'en']
05-29 18:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\translations, languages=['en_IE', 'en']
05-29 18:28 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=littlebastard
05-29 18:28 INFO   root: Received settings
05-29 18:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\translations, languages=['en_US', 'en']
05-29 18:28 DEBUG  TaskList: # Running tasklist...
05-29 18:28 DEBUG  TaskList: ## Running select_target_dir...
05-29 18:28 INFO   WindowsBackend: Installing into C:\ubuntu
05-29 18:28 DEBUG  TaskList: ## Finished select_target_dir
05-29 18:28 DEBUG  TaskList: ## Running create_dir_structure...
05-29 18:28 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-29 18:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-29 18:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-29 18:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-29 18:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-29 18:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-29 18:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-29 18:28 DEBUG  TaskList: ## Finished create_dir_structure
05-29 18:28 DEBUG  TaskList: ## Running uncompress_target_dir...
05-29 18:28 DEBUG  TaskList: ## Finished uncompress_target_dir
05-29 18:28 DEBUG  TaskList: ## Running create_uninstaller...
05-29 18:28 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Little Bastard\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-29 18:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-29 18:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-29 18:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-29 18:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-29 18:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-29 18:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-29 18:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-29 18:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-29 18:28 DEBUG  TaskList: ## Finished create_uninstaller
05-29 18:28 DEBUG  TaskList: ## Running copy_installation_files...
05-29 18:28 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-29 18:28 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\winboot -> C:\ubuntu\winboot
05-29 18:28 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-29 18:28 DEBUG  TaskList: ## Finished copy_installation_files
05-29 18:28 DEBUG  TaskList: ## Running get_iso...
05-29 18:28 DEBUG  CommonBackend: Searching for local CD
05-29 18:28 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp is a valid Ubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2414.tmp\casper\filesystem.squashfs
05-29 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:28 DEBUG  CommonBackend: Searching for local ISO
05-29 18:28 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-29 18:28 DEBUG  TaskList: New task get_metalink
05-29 18:28 DEBUG  TaskList: ### Running get_metalink...
05-29 18:28 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink > C:\ubuntu\install
05-29 18:28 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-29 18:28 DEBUG  downloader: download finished (read 28363 bytes)
05-29 18:28 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink > C:\ubuntu\install
05-29 18:28 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-29 18:28 DEBUG  downloader: download finished (read 874 bytes)
05-29 18:28 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
05-29 18:28 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-29 18:28 DEBUG  downloader: download finished (read 198 bytes)
05-29 18:28 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-29 18:28 INFO   saplog: Checking block bindings..
05-29 18:28 INFO   saplog: Key verified successfully.
05-29 18:28 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

05-29 18:28 DEBUG  TaskList: ### Finished get_metalink
05-29 18:28 DEBUG  TaskList: New task download
05-29 18:28 DEBUG  TaskList: ### Running download...
05-29 18:28 DEBUG  btdownloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-29 18:31 INFO   WindowsFrontend: Operation cancelled
05-29 18:31 DEBUG  WindowsFrontend: frontend.quit
05-29 18:31 DEBUG  WindowsFrontend: frontend.on_quit
05-29 18:31 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-29 18:31 DEBUG  TaskList: # Cancelling tasklist
05-29 18:31 DEBUG  TaskList: ### Finished download
05-29 18:31 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-29 18:31 DEBUG  root: application.on_quit
05-29 18:31 DEBUG  root: Forceful exit
05-29 18:31 INFO   root: sys.exit
05-29 18:31 INFO   root: === wubi 11.04 rev211 ===
05-29 18:31 DEBUG  root: Logfile is c:\users\little~1\appdata\local\temp\wubi-11.04-rev211.log
05-29 18:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Little Bastard\\Downloads\\wubi.exe"']
05-29 18:31 DEBUG  CommonBackend: data_dir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\data
05-29 18:31 DEBUG  WindowsBackend: 7z=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\bin\7z.exe
05-29 18:31 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-29 18:31 DEBUG  CommonBackend: Fetching basic info...
05-29 18:31 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi.exe
05-29 18:31 DEBUG  CommonBackend: platform=win32
05-29 18:31 DEBUG  CommonBackend: osname=nt
05-29 18:31 DEBUG  CommonBackend: language=en_IE
05-29 18:31 DEBUG  CommonBackend: encoding=cp1252
05-29 18:31 DEBUG  WindowsBackend: arch=amd64
05-29 18:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\data\isolist.ini
05-29 18:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 18:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 18:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 18:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 18:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 18:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 18:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 18:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 18:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 18:31 DEBUG  WindowsBackend: Fetching host info...
05-29 18:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 18:31 DEBUG  WindowsBackend: windows version=vista
05-29 18:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 18:31 DEBUG  WindowsBackend: windows_sp=None
05-29 18:31 DEBUG  WindowsBackend: windows_build=7601
05-29 18:31 DEBUG  WindowsBackend: gmt=0
05-29 18:31 DEBUG  WindowsBackend: country=IE
05-29 18:31 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 18:31 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 18:31 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 18:31 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 18:31 DEBUG  WindowsBackend: windows_language_code=1033
05-29 18:31 DEBUG  WindowsBackend: windows_language=English
05-29 18:31 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 18:31 DEBUG  WindowsBackend: bootloader=vista
05-29 18:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195710.992188 mb free ntfs)
05-29 18:31 DEBUG  WindowsBackend: drive=Drive(C: hd 195710.992188 mb free ntfs)
05-29 18:31 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 18:31 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-29 18:31 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-29 18:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-29 18:31 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 18:31 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 18:31 DEBUG  WindowsBackend: keyboard_variant=
05-29 18:31 DEBUG  CommonBackend: python locale=('en_IE', 'cp1252')
05-29 18:31 DEBUG  CommonBackend: locale=en_IE.UTF-8
05-29 18:31 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 18:31 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 18:31 DEBUG  CommonBackend: Searching for local CDs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Ubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Ubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Ubuntu Netbook CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Kubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Kubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Xubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Xubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Mythbuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Mythbuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 INFO   root: Already installed, running the uninstaller...
05-29 18:31 INFO   root: Running the uninstaller...
05-29 18:31 INFO   CommonBackend: This is the uninstaller running
05-29 18:31 DEBUG  WindowsFrontend: __init__...
05-29 18:31 DEBUG  WindowsFrontend: on_init...
05-29 18:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\translations, languages=['en_IE', 'en']
05-29 18:31 INFO   root: Received settings
05-29 18:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\translations, languages=['en_IE', 'en']
05-29 18:31 DEBUG  TaskList: # Running tasklist...
05-29 18:31 DEBUG  TaskList: ## Running Backup ISO...
05-29 18:31 DEBUG  TaskList: ## Finished Backup ISO
05-29 18:31 DEBUG  TaskList: ## Running Remove bootloader entry...
05-29 18:31 DEBUG  WindowsBackend: Could not find bcd id
05-29 18:31 DEBUG  WindowsBackend: undo_bootini C:
05-29 18:31 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 195710.992188 mb free ntfs)
05-29 18:31 DEBUG  TaskList: ## Finished Remove bootloader entry
05-29 18:31 DEBUG  TaskList: ## Running Remove target dir...
05-29 18:31 DEBUG  CommonBackend: Deleting C:\ubuntu
05-29 18:31 DEBUG  TaskList: ## Finished Remove target dir
05-29 18:31 DEBUG  TaskList: ## Running Remove registry key...
05-29 18:31 DEBUG  TaskList: ## Finished Remove registry key
05-29 18:31 DEBUG  TaskList: # Finished tasklist
05-29 18:31 INFO   root: Almost finished uninstalling
05-29 18:31 INFO   root: Finished uninstallation
05-29 18:31 DEBUG  CommonBackend: Fetching basic info...
05-29 18:31 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi.exe
05-29 18:31 DEBUG  CommonBackend: platform=win32
05-29 18:31 DEBUG  CommonBackend: osname=nt
05-29 18:31 DEBUG  WindowsBackend: arch=amd64
05-29 18:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\data\isolist.ini
05-29 18:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 18:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 18:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 18:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 18:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 18:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 18:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 18:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 18:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 18:31 DEBUG  WindowsBackend: Fetching host info...
05-29 18:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 18:31 DEBUG  WindowsBackend: windows version=vista
05-29 18:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 18:31 DEBUG  WindowsBackend: windows_sp=None
05-29 18:31 DEBUG  WindowsBackend: windows_build=7601
05-29 18:31 DEBUG  WindowsBackend: gmt=0
05-29 18:31 DEBUG  WindowsBackend: country=IE
05-29 18:31 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 18:31 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 18:31 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 18:31 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 18:31 DEBUG  WindowsBackend: windows_language_code=1033
05-29 18:31 DEBUG  WindowsBackend: windows_language=English
05-29 18:31 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 18:31 DEBUG  WindowsBackend: bootloader=vista
05-29 18:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195712.164063 mb free ntfs)
05-29 18:31 DEBUG  WindowsBackend: drive=Drive(C: hd 195712.164063 mb free ntfs)
05-29 18:31 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 18:31 DEBUG  WindowsBackend: uninstaller_path=None
05-29 18:31 DEBUG  WindowsBackend: previous_target_dir=None
05-29 18:31 DEBUG  WindowsBackend: previous_distro_name=None
05-29 18:31 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 18:31 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 18:31 DEBUG  WindowsBackend: keyboard_variant=
05-29 18:31 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 18:31 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 18:31 DEBUG  CommonBackend: Searching for local CDs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Ubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Ubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Ubuntu Netbook CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Kubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Kubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Xubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Xubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Mythbuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Mythbuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 INFO   root: Running the installer...
05-29 18:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\translations, languages=['en_IE', 'en']
05-29 18:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\translations, languages=['en_IE', 'en']
05-29 18:31 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=littlebastard
05-29 18:31 INFO   root: Received settings
05-29 18:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\translations, languages=['en_US', 'en']
05-29 18:31 DEBUG  TaskList: # Running tasklist...
05-29 18:31 DEBUG  TaskList: ## Running select_target_dir...
05-29 18:31 INFO   WindowsBackend: Installing into C:\ubuntu
05-29 18:31 DEBUG  TaskList: ## Finished select_target_dir
05-29 18:31 DEBUG  TaskList: ## Running create_dir_structure...
05-29 18:31 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-29 18:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-29 18:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-29 18:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-29 18:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-29 18:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-29 18:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-29 18:31 DEBUG  TaskList: ## Finished create_dir_structure
05-29 18:31 DEBUG  TaskList: ## Running uncompress_target_dir...
05-29 18:31 DEBUG  TaskList: ## Finished uncompress_target_dir
05-29 18:31 DEBUG  TaskList: ## Running create_uninstaller...
05-29 18:31 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Little Bastard\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-29 18:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-29 18:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-29 18:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-29 18:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-29 18:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-29 18:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-29 18:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-29 18:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-29 18:31 DEBUG  TaskList: ## Finished create_uninstaller
05-29 18:31 DEBUG  TaskList: ## Running copy_installation_files...
05-29 18:31 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-29 18:31 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\winboot -> C:\ubuntu\winboot
05-29 18:31 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-29 18:31 DEBUG  TaskList: ## Finished copy_installation_files
05-29 18:31 DEBUG  TaskList: ## Running get_iso...
05-29 18:31 DEBUG  CommonBackend: Searching for local CD
05-29 18:31 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp is a valid Ubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl2DB4.tmp\casper\filesystem.squashfs
05-29 18:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:31 DEBUG  CommonBackend: Searching for local ISO
05-29 18:31 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-29 18:31 DEBUG  TaskList: New task get_metalink
05-29 18:31 DEBUG  TaskList: ### Running get_metalink...
05-29 18:31 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink > C:\ubuntu\install
05-29 18:31 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-29 18:31 DEBUG  downloader: download finished (read 28363 bytes)
05-29 18:31 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink > C:\ubuntu\install
05-29 18:31 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-29 18:31 DEBUG  downloader: download finished (read 874 bytes)
05-29 18:31 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
05-29 18:31 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-29 18:31 DEBUG  downloader: download finished (read 198 bytes)
05-29 18:31 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-29 18:31 INFO   saplog: Checking block bindings..
05-29 18:31 INFO   saplog: Key verified successfully.
05-29 18:31 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

05-29 18:31 DEBUG  TaskList: ### Finished get_metalink
05-29 18:31 DEBUG  TaskList: New task download
05-29 18:31 DEBUG  TaskList: ### Running download...
05-29 18:31 DEBUG  btdownloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-29 18:33 INFO   WindowsFrontend: Operation cancelled
05-29 18:33 DEBUG  WindowsFrontend: frontend.quit
05-29 18:33 DEBUG  WindowsFrontend: frontend.on_quit
05-29 18:33 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-29 18:33 DEBUG  TaskList: # Cancelling tasklist
05-29 18:33 DEBUG  TaskList: ### Finished download
05-29 18:33 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-29 18:33 DEBUG  root: application.on_quit
05-29 18:33 DEBUG  root: Forceful exit
05-29 18:33 INFO   root: sys.exit
05-29 18:33 INFO   root: === wubi 11.04 rev211 ===
05-29 18:33 DEBUG  root: Logfile is c:\users\little~1\appdata\local\temp\wubi-11.04-rev211.log
05-29 18:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Little Bastard\\Downloads\\wubi.exe"']
05-29 18:33 DEBUG  CommonBackend: data_dir=C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\data
05-29 18:33 DEBUG  WindowsBackend: 7z=C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\bin\7z.exe
05-29 18:33 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-29 18:33 DEBUG  CommonBackend: Fetching basic info...
05-29 18:33 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi.exe
05-29 18:33 DEBUG  CommonBackend: platform=win32
05-29 18:33 DEBUG  CommonBackend: osname=nt
05-29 18:33 DEBUG  CommonBackend: language=en_IE
05-29 18:33 DEBUG  CommonBackend: encoding=cp1252
05-29 18:33 DEBUG  WindowsBackend: arch=amd64
05-29 18:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\data\isolist.ini
05-29 18:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 18:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 18:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 18:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 18:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 18:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 18:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 18:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 18:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 18:33 DEBUG  WindowsBackend: Fetching host info...
05-29 18:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 18:33 DEBUG  WindowsBackend: windows version=vista
05-29 18:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 18:33 DEBUG  WindowsBackend: windows_sp=None
05-29 18:33 DEBUG  WindowsBackend: windows_build=7601
05-29 18:33 DEBUG  WindowsBackend: gmt=0
05-29 18:33 DEBUG  WindowsBackend: country=IE
05-29 18:33 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 18:33 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 18:33 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 18:33 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 18:33 DEBUG  WindowsBackend: windows_language_code=1033
05-29 18:33 DEBUG  WindowsBackend: windows_language=English
05-29 18:33 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 18:33 DEBUG  WindowsBackend: bootloader=vista
05-29 18:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195706.988281 mb free ntfs)
05-29 18:33 DEBUG  WindowsBackend: drive=Drive(C: hd 195706.988281 mb free ntfs)
05-29 18:33 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 18:33 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-29 18:33 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-29 18:33 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-29 18:33 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 18:33 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 18:33 DEBUG  WindowsBackend: keyboard_variant=
05-29 18:33 DEBUG  CommonBackend: python locale=('en_IE', 'cp1252')
05-29 18:33 DEBUG  CommonBackend: locale=en_IE.UTF-8
05-29 18:33 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 18:33 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 18:33 DEBUG  CommonBackend: Searching for local CDs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Ubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Ubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Ubuntu Netbook CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Kubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Kubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Xubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Xubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Mythbuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Mythbuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 INFO   root: Already installed, running the uninstaller...
05-29 18:33 INFO   root: Running the uninstaller...
05-29 18:33 INFO   CommonBackend: This is the uninstaller running
05-29 18:33 DEBUG  WindowsFrontend: __init__...
05-29 18:33 DEBUG  WindowsFrontend: on_init...
05-29 18:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\translations, languages=['en_IE', 'en']
05-29 18:33 INFO   root: Received settings
05-29 18:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\translations, languages=['en_IE', 'en']
05-29 18:33 DEBUG  TaskList: # Running tasklist...
05-29 18:33 DEBUG  TaskList: ## Running Backup ISO...
05-29 18:33 DEBUG  TaskList: ## Finished Backup ISO
05-29 18:33 DEBUG  TaskList: ## Running Remove bootloader entry...
05-29 18:33 DEBUG  WindowsBackend: Could not find bcd id
05-29 18:33 DEBUG  WindowsBackend: undo_bootini C:
05-29 18:33 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 195706.988281 mb free ntfs)
05-29 18:33 DEBUG  TaskList: ## Finished Remove bootloader entry
05-29 18:33 DEBUG  TaskList: ## Running Remove target dir...
05-29 18:33 DEBUG  CommonBackend: Deleting C:\ubuntu
05-29 18:33 DEBUG  TaskList: ## Finished Remove target dir
05-29 18:33 DEBUG  TaskList: ## Running Remove registry key...
05-29 18:33 DEBUG  TaskList: ## Finished Remove registry key
05-29 18:33 DEBUG  TaskList: # Finished tasklist
05-29 18:33 INFO   root: Almost finished uninstalling
05-29 18:33 INFO   root: Finished uninstallation
05-29 18:33 DEBUG  CommonBackend: Fetching basic info...
05-29 18:33 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi.exe
05-29 18:33 DEBUG  CommonBackend: platform=win32
05-29 18:33 DEBUG  CommonBackend: osname=nt
05-29 18:33 DEBUG  WindowsBackend: arch=amd64
05-29 18:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\data\isolist.ini
05-29 18:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 18:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 18:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 18:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 18:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 18:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 18:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 18:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 18:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 18:33 DEBUG  WindowsBackend: Fetching host info...
05-29 18:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 18:33 DEBUG  WindowsBackend: windows version=vista
05-29 18:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 18:33 DEBUG  WindowsBackend: windows_sp=None
05-29 18:33 DEBUG  WindowsBackend: windows_build=7601
05-29 18:33 DEBUG  WindowsBackend: gmt=0
05-29 18:33 DEBUG  WindowsBackend: country=IE
05-29 18:33 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 18:33 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 18:33 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 18:33 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 18:33 DEBUG  WindowsBackend: windows_language_code=1033
05-29 18:33 DEBUG  WindowsBackend: windows_language=English
05-29 18:33 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 18:33 DEBUG  WindowsBackend: bootloader=vista
05-29 18:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195708.65625 mb free ntfs)
05-29 18:33 DEBUG  WindowsBackend: drive=Drive(C: hd 195708.65625 mb free ntfs)
05-29 18:33 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 18:33 DEBUG  WindowsBackend: uninstaller_path=None
05-29 18:33 DEBUG  WindowsBackend: previous_target_dir=None
05-29 18:33 DEBUG  WindowsBackend: previous_distro_name=None
05-29 18:33 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 18:33 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 18:33 DEBUG  WindowsBackend: keyboard_variant=
05-29 18:33 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 18:33 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 18:33 DEBUG  CommonBackend: Searching for local CDs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Ubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Ubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Ubuntu Netbook CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Kubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Kubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Xubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Xubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Mythbuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Mythbuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 INFO   root: Running the installer...
05-29 18:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\translations, languages=['en_IE', 'en']
05-29 18:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\translations, languages=['en_IE', 'en']
05-29 18:33 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=littlebastard
05-29 18:33 INFO   root: Received settings
05-29 18:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\translations, languages=['en_US', 'en']
05-29 18:33 DEBUG  TaskList: # Running tasklist...
05-29 18:33 DEBUG  TaskList: ## Running select_target_dir...
05-29 18:33 INFO   WindowsBackend: Installing into C:\ubuntu
05-29 18:33 DEBUG  TaskList: ## Finished select_target_dir
05-29 18:33 DEBUG  TaskList: ## Running create_dir_structure...
05-29 18:33 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-29 18:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-29 18:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-29 18:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-29 18:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-29 18:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-29 18:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-29 18:33 DEBUG  TaskList: ## Finished create_dir_structure
05-29 18:33 DEBUG  TaskList: ## Running uncompress_target_dir...
05-29 18:33 DEBUG  TaskList: ## Finished uncompress_target_dir
05-29 18:33 DEBUG  TaskList: ## Running create_uninstaller...
05-29 18:33 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Little Bastard\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-29 18:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-29 18:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-29 18:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-29 18:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-29 18:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-29 18:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-29 18:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-29 18:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-29 18:33 DEBUG  TaskList: ## Finished create_uninstaller
05-29 18:33 DEBUG  TaskList: ## Running copy_installation_files...
05-29 18:33 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-29 18:33 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\winboot -> C:\ubuntu\winboot
05-29 18:33 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-29 18:33 DEBUG  TaskList: ## Finished copy_installation_files
05-29 18:33 DEBUG  TaskList: ## Running get_iso...
05-29 18:33 DEBUG  CommonBackend: Searching for local CD
05-29 18:33 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp is a valid Ubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
05-29 18:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:33 DEBUG  CommonBackend: Searching for local ISO
05-29 18:33 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-29 18:33 DEBUG  TaskList: New task get_metalink
05-29 18:33 DEBUG  TaskList: ### Running get_metalink...
05-29 18:33 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink > C:\ubuntu\install
05-29 18:33 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-29 18:33 DEBUG  downloader: download finished (read 28363 bytes)
05-29 18:33 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink > C:\ubuntu\install
05-29 18:33 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-29 18:33 DEBUG  downloader: download finished (read 874 bytes)
05-29 18:33 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
05-29 18:33 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-29 18:33 DEBUG  downloader: download finished (read 198 bytes)
05-29 18:33 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-29 18:33 INFO   saplog: Checking block bindings..
05-29 18:33 INFO   saplog: Key verified successfully.
05-29 18:33 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

05-29 18:33 DEBUG  TaskList: ### Finished get_metalink
05-29 18:33 DEBUG  TaskList: New task download
05-29 18:33 DEBUG  TaskList: ### Running download...
05-29 18:33 DEBUG  btdownloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-29 18:55 DEBUG  WindowsFrontend: frontend.on_quit
05-29 18:55 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-29 18:55 DEBUG  TaskList: # Cancelling tasklist
05-29 18:55 DEBUG  TaskList: ### Finished download
05-29 18:55 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-29 18:55 DEBUG  root: application.on_quit
05-29 18:55 DEBUG  root: Forceful exit
05-29 18:55 INFO   root: sys.exit
05-29 18:56 INFO   root: === wubi 11.04 rev211 ===
05-29 18:56 DEBUG  root: Logfile is c:\users\little~1\appdata\local\temp\wubi-11.04-rev211.log
05-29 18:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Little Bastard\\Downloads\\wubi.exe"']
05-29 18:56 DEBUG  CommonBackend: data_dir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\data
05-29 18:56 DEBUG  WindowsBackend: 7z=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\bin\7z.exe
05-29 18:56 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-29 18:56 DEBUG  CommonBackend: Fetching basic info...
05-29 18:56 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi.exe
05-29 18:56 DEBUG  CommonBackend: platform=win32
05-29 18:56 DEBUG  CommonBackend: osname=nt
05-29 18:56 DEBUG  CommonBackend: language=en_IE
05-29 18:56 DEBUG  CommonBackend: encoding=cp1252
05-29 18:56 DEBUG  WindowsBackend: arch=amd64
05-29 18:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\data\isolist.ini
05-29 18:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 18:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 18:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 18:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 18:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 18:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 18:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 18:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 18:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 18:56 DEBUG  WindowsBackend: Fetching host info...
05-29 18:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 18:56 DEBUG  WindowsBackend: windows version=vista
05-29 18:56 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 18:56 DEBUG  WindowsBackend: windows_sp=None
05-29 18:56 DEBUG  WindowsBackend: windows_build=7601
05-29 18:56 DEBUG  WindowsBackend: gmt=0
05-29 18:56 DEBUG  WindowsBackend: country=IE
05-29 18:56 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 18:56 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 18:56 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 18:56 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 18:56 DEBUG  WindowsBackend: windows_language_code=1033
05-29 18:56 DEBUG  WindowsBackend: windows_language=English
05-29 18:56 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 18:56 DEBUG  WindowsBackend: bootloader=vista
05-29 18:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195695.09375 mb free ntfs)
05-29 18:56 DEBUG  WindowsBackend: drive=Drive(C: hd 195695.09375 mb free ntfs)
05-29 18:56 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 18:56 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-29 18:56 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-29 18:56 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-29 18:56 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 18:56 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 18:56 DEBUG  WindowsBackend: keyboard_variant=
05-29 18:56 DEBUG  CommonBackend: python locale=('en_IE', 'cp1252')
05-29 18:56 DEBUG  CommonBackend: locale=en_IE.UTF-8
05-29 18:56 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 18:56 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 18:56 DEBUG  CommonBackend: Searching for local CDs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Ubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Ubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Ubuntu Netbook CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Kubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Kubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Xubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Xubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Mythbuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Mythbuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 INFO   root: Already installed, running the uninstaller...
05-29 18:56 INFO   root: Running the uninstaller...
05-29 18:56 INFO   CommonBackend: This is the uninstaller running
05-29 18:56 DEBUG  WindowsFrontend: __init__...
05-29 18:56 DEBUG  WindowsFrontend: on_init...
05-29 18:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\translations, languages=['en_IE', 'en']
05-29 18:56 INFO   root: Received settings
05-29 18:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\translations, languages=['en_IE', 'en']
05-29 18:56 DEBUG  TaskList: # Running tasklist...
05-29 18:56 DEBUG  TaskList: ## Running Backup ISO...
05-29 18:56 DEBUG  TaskList: ## Finished Backup ISO
05-29 18:56 DEBUG  TaskList: ## Running Remove bootloader entry...
05-29 18:56 DEBUG  WindowsBackend: Could not find bcd id
05-29 18:56 DEBUG  WindowsBackend: undo_bootini C:
05-29 18:56 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 195695.09375 mb free ntfs)
05-29 18:56 DEBUG  TaskList: ## Finished Remove bootloader entry
05-29 18:56 DEBUG  TaskList: ## Running Remove target dir...
05-29 18:56 DEBUG  CommonBackend: Deleting C:\ubuntu
05-29 18:56 DEBUG  TaskList: ## Finished Remove target dir
05-29 18:56 DEBUG  TaskList: ## Running Remove registry key...
05-29 18:56 DEBUG  TaskList: ## Finished Remove registry key
05-29 18:56 DEBUG  TaskList: # Finished tasklist
05-29 18:56 INFO   root: Almost finished uninstalling
05-29 18:56 INFO   root: Finished uninstallation
05-29 18:56 DEBUG  CommonBackend: Fetching basic info...
05-29 18:56 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi.exe
05-29 18:56 DEBUG  CommonBackend: platform=win32
05-29 18:56 DEBUG  CommonBackend: osname=nt
05-29 18:56 DEBUG  WindowsBackend: arch=amd64
05-29 18:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\data\isolist.ini
05-29 18:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 18:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 18:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 18:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 18:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 18:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 18:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 18:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 18:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 18:56 DEBUG  WindowsBackend: Fetching host info...
05-29 18:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 18:56 DEBUG  WindowsBackend: windows version=vista
05-29 18:56 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 18:56 DEBUG  WindowsBackend: windows_sp=None
05-29 18:56 DEBUG  WindowsBackend: windows_build=7601
05-29 18:56 DEBUG  WindowsBackend: gmt=0
05-29 18:56 DEBUG  WindowsBackend: country=IE
05-29 18:56 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 18:56 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 18:56 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 18:56 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 18:56 DEBUG  WindowsBackend: windows_language_code=1033
05-29 18:56 DEBUG  WindowsBackend: windows_language=English
05-29 18:56 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 18:56 DEBUG  WindowsBackend: bootloader=vista
05-29 18:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195696.761719 mb free ntfs)
05-29 18:56 DEBUG  WindowsBackend: drive=Drive(C: hd 195696.761719 mb free ntfs)
05-29 18:56 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 18:56 DEBUG  WindowsBackend: uninstaller_path=None
05-29 18:56 DEBUG  WindowsBackend: previous_target_dir=None
05-29 18:56 DEBUG  WindowsBackend: previous_distro_name=None
05-29 18:56 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 18:56 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 18:56 DEBUG  WindowsBackend: keyboard_variant=
05-29 18:56 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 18:56 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 18:56 DEBUG  CommonBackend: Searching for local CDs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Ubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Ubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Ubuntu Netbook CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Kubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Kubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Xubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Xubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Mythbuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp is a valid Mythbuntu CD
05-29 18:56 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:56 INFO   root: Running the installer...
05-29 18:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\translations, languages=['en_IE', 'en']
05-29 18:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9128.tmp\translations, languages=['en_IE', 'en']
05-29 18:56 INFO   WindowsFrontend: Operation cancelled
05-29 18:56 DEBUG  WindowsFrontend: frontend.quit
05-29 18:56 DEBUG  WindowsFrontend: frontend.on_quit
05-29 18:56 DEBUG  root: application.on_quit
05-29 18:56 INFO   root: sys.exit
05-29 18:57 INFO   root: === wubi 11.04 rev211 ===
05-29 18:57 DEBUG  root: Logfile is c:\users\little~1\appdata\local\temp\wubi-11.04-rev211.log
05-29 18:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Little Bastard\\Downloads\\wubi(3).exe"']
05-29 18:57 DEBUG  CommonBackend: data_dir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\data
05-29 18:57 DEBUG  WindowsBackend: 7z=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\bin\7z.exe
05-29 18:57 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-29 18:57 DEBUG  CommonBackend: Fetching basic info...
05-29 18:57 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi(3).exe
05-29 18:57 DEBUG  CommonBackend: platform=win32
05-29 18:57 DEBUG  CommonBackend: osname=nt
05-29 18:57 DEBUG  CommonBackend: language=en_IE
05-29 18:57 DEBUG  CommonBackend: encoding=cp1252
05-29 18:57 DEBUG  WindowsBackend: arch=amd64
05-29 18:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\data\isolist.ini
05-29 18:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 18:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 18:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 18:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 18:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 18:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 18:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 18:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 18:57 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 18:57 DEBUG  WindowsBackend: Fetching host info...
05-29 18:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 18:57 DEBUG  WindowsBackend: windows version=vista
05-29 18:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 18:57 DEBUG  WindowsBackend: windows_sp=None
05-29 18:57 DEBUG  WindowsBackend: windows_build=7601
05-29 18:57 DEBUG  WindowsBackend: gmt=0
05-29 18:57 DEBUG  WindowsBackend: country=IE
05-29 18:57 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 18:57 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 18:57 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 18:57 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 18:57 DEBUG  WindowsBackend: windows_language_code=1033
05-29 18:57 DEBUG  WindowsBackend: windows_language=English
05-29 18:57 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 18:57 DEBUG  WindowsBackend: bootloader=vista
05-29 18:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195695.242188 mb free ntfs)
05-29 18:57 DEBUG  WindowsBackend: drive=Drive(C: hd 195695.242188 mb free ntfs)
05-29 18:57 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 18:57 DEBUG  WindowsBackend: uninstaller_path=None
05-29 18:57 DEBUG  WindowsBackend: previous_target_dir=None
05-29 18:57 DEBUG  WindowsBackend: previous_distro_name=None
05-29 18:57 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 18:57 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 18:57 DEBUG  WindowsBackend: keyboard_variant=
05-29 18:57 DEBUG  CommonBackend: python locale=('en_IE', 'cp1252')
05-29 18:57 DEBUG  CommonBackend: locale=en_IE.UTF-8
05-29 18:57 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 18:57 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 18:57 DEBUG  CommonBackend: Searching for local CDs
05-29 18:57 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp is a valid Ubuntu CD
05-29 18:57 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp is a valid Ubuntu CD
05-29 18:57 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp is a valid Ubuntu Netbook CD
05-29 18:57 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp is a valid Kubuntu CD
05-29 18:57 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp is a valid Kubuntu CD
05-29 18:57 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp is a valid Xubuntu CD
05-29 18:57 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp is a valid Xubuntu CD
05-29 18:57 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp is a valid Mythbuntu CD
05-29 18:57 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp is a valid Mythbuntu CD
05-29 18:57 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 18:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 18:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 18:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 18:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:57 INFO   root: Running the installer...
05-29 18:57 DEBUG  WindowsFrontend: __init__...
05-29 18:57 DEBUG  WindowsFrontend: on_init...
05-29 18:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\translations, languages=['en_IE', 'en']
05-29 18:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\translations, languages=['en_IE', 'en']
05-29 18:57 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=littlebastard
05-29 18:57 INFO   root: Received settings
05-29 18:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\translations, languages=['en_GB', 'en']
05-29 18:57 DEBUG  TaskList: # Running tasklist...
05-29 18:57 DEBUG  TaskList: ## Running select_target_dir...
05-29 18:57 INFO   WindowsBackend: Installing into C:\ubuntu
05-29 18:57 DEBUG  TaskList: ## Finished select_target_dir
05-29 18:57 DEBUG  TaskList: ## Running create_dir_structure...
05-29 18:57 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-29 18:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-29 18:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-29 18:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-29 18:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-29 18:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-29 18:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-29 18:57 DEBUG  TaskList: ## Finished create_dir_structure
05-29 18:57 DEBUG  TaskList: ## Running uncompress_target_dir...
05-29 18:57 DEBUG  TaskList: ## Finished uncompress_target_dir
05-29 18:57 DEBUG  TaskList: ## Running create_uninstaller...
05-29 18:57 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Little Bastard\Downloads\wubi(3).exe -> C:\ubuntu\uninstall-wubi.exe
05-29 18:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-29 18:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-29 18:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-29 18:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-29 18:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-29 18:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-29 18:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-29 18:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-29 18:57 DEBUG  TaskList: ## Finished create_uninstaller
05-29 18:57 DEBUG  TaskList: ## Running copy_installation_files...
05-29 18:57 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-29 18:57 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\winboot -> C:\ubuntu\winboot
05-29 18:57 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-29 18:57 DEBUG  TaskList: ## Finished copy_installation_files
05-29 18:57 DEBUG  TaskList: ## Running get_iso...
05-29 18:57 DEBUG  CommonBackend: Searching for local CD
05-29 18:57 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp is a valid Ubuntu CD
05-29 18:57 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9FF7.tmp\casper\filesystem.squashfs
05-29 18:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 18:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 18:57 DEBUG  CommonBackend: Searching for local ISO
05-29 18:57 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-29 18:57 DEBUG  TaskList: New task get_metalink
05-29 18:57 DEBUG  TaskList: ### Running get_metalink...
05-29 18:57 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink > C:\ubuntu\install
05-29 18:57 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-29 18:57 DEBUG  downloader: download finished (read 28363 bytes)
05-29 18:57 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink > C:\ubuntu\install
05-29 18:57 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-29 18:57 DEBUG  downloader: download finished (read 874 bytes)
05-29 18:57 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
05-29 18:57 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-29 18:57 DEBUG  downloader: download finished (read 198 bytes)
05-29 18:57 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-29 18:57 INFO   saplog: Checking block bindings..
05-29 18:57 INFO   saplog: Key verified successfully.
05-29 18:57 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

05-29 18:57 DEBUG  TaskList: ### Finished get_metalink
05-29 18:57 DEBUG  TaskList: New task download
05-29 18:57 DEBUG  TaskList: ### Running download...
05-29 18:57 DEBUG  btdownloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-29 19:14 INFO   WindowsFrontend: Operation cancelled
05-29 19:14 DEBUG  WindowsFrontend: frontend.quit
05-29 19:14 DEBUG  WindowsFrontend: frontend.on_quit
05-29 19:14 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-29 19:14 DEBUG  TaskList: # Cancelling tasklist
05-29 19:14 DEBUG  TaskList: ### Finished download
05-29 19:14 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-29 19:14 DEBUG  root: application.on_quit
05-29 19:14 DEBUG  root: Forceful exit
05-29 19:14 INFO   root: sys.exit
05-29 19:14 INFO   root: === wubi 11.04 rev211 ===
05-29 19:14 DEBUG  root: Logfile is c:\users\little~1\appdata\local\temp\wubi-11.04-rev211.log
05-29 19:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Little Bastard\\Downloads\\wubi(3).exe"']
05-29 19:14 DEBUG  CommonBackend: data_dir=C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\data
05-29 19:14 DEBUG  WindowsBackend: 7z=C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\bin\7z.exe
05-29 19:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-29 19:14 DEBUG  CommonBackend: Fetching basic info...
05-29 19:14 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi(3).exe
05-29 19:14 DEBUG  CommonBackend: platform=win32
05-29 19:14 DEBUG  CommonBackend: osname=nt
05-29 19:14 DEBUG  CommonBackend: language=en_IE
05-29 19:14 DEBUG  CommonBackend: encoding=cp1252
05-29 19:14 DEBUG  WindowsBackend: arch=amd64
05-29 19:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\data\isolist.ini
05-29 19:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 19:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 19:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 19:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 19:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 19:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 19:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 19:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 19:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 19:14 DEBUG  WindowsBackend: Fetching host info...
05-29 19:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 19:14 DEBUG  WindowsBackend: windows version=vista
05-29 19:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 19:14 DEBUG  WindowsBackend: windows_sp=None
05-29 19:14 DEBUG  WindowsBackend: windows_build=7601
05-29 19:14 DEBUG  WindowsBackend: gmt=0
05-29 19:14 DEBUG  WindowsBackend: country=IE
05-29 19:14 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 19:14 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 19:14 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 19:14 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 19:14 DEBUG  WindowsBackend: windows_language_code=1033
05-29 19:14 DEBUG  WindowsBackend: windows_language=English
05-29 19:14 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 19:14 DEBUG  WindowsBackend: bootloader=vista
05-29 19:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195690.757813 mb free ntfs)
05-29 19:14 DEBUG  WindowsBackend: drive=Drive(C: hd 195690.757813 mb free ntfs)
05-29 19:14 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 19:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-29 19:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-29 19:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-29 19:14 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 19:14 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 19:14 DEBUG  WindowsBackend: keyboard_variant=
05-29 19:14 DEBUG  CommonBackend: python locale=('en_IE', 'cp1252')
05-29 19:14 DEBUG  CommonBackend: locale=en_IE.UTF-8
05-29 19:14 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 19:14 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 19:14 DEBUG  CommonBackend: Searching for local CDs
05-29 19:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Ubuntu CD
05-29 19:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Ubuntu CD
05-29 19:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Ubuntu Netbook CD
05-29 19:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Kubuntu CD
05-29 19:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Kubuntu CD
05-29 19:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Xubuntu CD
05-29 19:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Xubuntu CD
05-29 19:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Mythbuntu CD
05-29 19:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Mythbuntu CD
05-29 19:14 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:14 INFO   root: Already installed, running the uninstaller...
05-29 19:14 INFO   root: Running the uninstaller...
05-29 19:14 INFO   CommonBackend: This is the uninstaller running
05-29 19:14 DEBUG  WindowsFrontend: __init__...
05-29 19:14 DEBUG  WindowsFrontend: on_init...
05-29 19:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\translations, languages=['en_IE', 'en']
05-29 19:14 INFO   root: Received settings
05-29 19:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\translations, languages=['en_IE', 'en']
05-29 19:14 DEBUG  TaskList: # Running tasklist...
05-29 19:14 DEBUG  TaskList: ## Running Backup ISO...
05-29 19:14 DEBUG  TaskList: ## Finished Backup ISO
05-29 19:14 DEBUG  TaskList: ## Running Remove bootloader entry...
05-29 19:14 DEBUG  WindowsBackend: Could not find bcd id
05-29 19:14 DEBUG  WindowsBackend: undo_bootini C:
05-29 19:14 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 195690.757813 mb free ntfs)
05-29 19:14 DEBUG  TaskList: ## Finished Remove bootloader entry
05-29 19:14 DEBUG  TaskList: ## Running Remove target dir...
05-29 19:14 DEBUG  CommonBackend: Deleting C:\ubuntu
05-29 19:15 DEBUG  TaskList: ## Finished Remove target dir
05-29 19:15 DEBUG  TaskList: ## Running Remove registry key...
05-29 19:15 DEBUG  TaskList: ## Finished Remove registry key
05-29 19:15 DEBUG  TaskList: # Finished tasklist
05-29 19:15 INFO   root: Almost finished uninstalling
05-29 19:15 INFO   root: Finished uninstallation
05-29 19:15 DEBUG  CommonBackend: Fetching basic info...
05-29 19:15 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi(3).exe
05-29 19:15 DEBUG  CommonBackend: platform=win32
05-29 19:15 DEBUG  CommonBackend: osname=nt
05-29 19:15 DEBUG  WindowsBackend: arch=amd64
05-29 19:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\data\isolist.ini
05-29 19:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 19:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 19:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 19:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 19:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 19:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 19:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 19:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 19:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 19:15 DEBUG  WindowsBackend: Fetching host info...
05-29 19:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 19:15 DEBUG  WindowsBackend: windows version=vista
05-29 19:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 19:15 DEBUG  WindowsBackend: windows_sp=None
05-29 19:15 DEBUG  WindowsBackend: windows_build=7601
05-29 19:15 DEBUG  WindowsBackend: gmt=0
05-29 19:15 DEBUG  WindowsBackend: country=IE
05-29 19:15 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 19:15 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 19:15 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 19:15 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 19:15 DEBUG  WindowsBackend: windows_language_code=1033
05-29 19:15 DEBUG  WindowsBackend: windows_language=English
05-29 19:15 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 19:15 DEBUG  WindowsBackend: bootloader=vista
05-29 19:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195692.421875 mb free ntfs)
05-29 19:15 DEBUG  WindowsBackend: drive=Drive(C: hd 195692.421875 mb free ntfs)
05-29 19:15 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 19:15 DEBUG  WindowsBackend: uninstaller_path=None
05-29 19:15 DEBUG  WindowsBackend: previous_target_dir=None
05-29 19:15 DEBUG  WindowsBackend: previous_distro_name=None
05-29 19:15 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 19:15 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 19:15 DEBUG  WindowsBackend: keyboard_variant=
05-29 19:15 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 19:15 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 19:15 DEBUG  CommonBackend: Searching for local CDs
05-29 19:15 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Ubuntu CD
05-29 19:15 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Ubuntu CD
05-29 19:15 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Ubuntu Netbook CD
05-29 19:15 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Kubuntu CD
05-29 19:15 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Kubuntu CD
05-29 19:15 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Xubuntu CD
05-29 19:15 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Xubuntu CD
05-29 19:15 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Mythbuntu CD
05-29 19:15 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Mythbuntu CD
05-29 19:15 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:15 INFO   root: Running the installer...
05-29 19:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\translations, languages=['en_IE', 'en']
05-29 19:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\translations, languages=['en_IE', 'en']
05-29 19:15 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_US, locale=en_US.UTF-8, username=littlebastard
05-29 19:15 INFO   root: Received settings
05-29 19:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\translations, languages=['en_US', 'en']
05-29 19:15 DEBUG  TaskList: # Running tasklist...
05-29 19:15 DEBUG  TaskList: ## Running select_target_dir...
05-29 19:15 INFO   WindowsBackend: Installing into C:\ubuntu
05-29 19:15 DEBUG  TaskList: ## Finished select_target_dir
05-29 19:15 DEBUG  TaskList: ## Running create_dir_structure...
05-29 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-29 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-29 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-29 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-29 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-29 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-29 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-29 19:15 DEBUG  TaskList: ## Finished create_dir_structure
05-29 19:15 DEBUG  TaskList: ## Running uncompress_target_dir...
05-29 19:15 DEBUG  TaskList: ## Finished uncompress_target_dir
05-29 19:15 DEBUG  TaskList: ## Running create_uninstaller...
05-29 19:15 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Little Bastard\Downloads\wubi(3).exe -> C:\ubuntu\uninstall-wubi.exe
05-29 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-29 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-29 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
05-29 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
05-29 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-29 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
05-29 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-29 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-29 19:15 DEBUG  TaskList: ## Finished create_uninstaller
05-29 19:15 DEBUG  TaskList: ## Running copy_installation_files...
05-29 19:15 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-29 19:15 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\winboot -> C:\ubuntu\winboot
05-29 19:15 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
05-29 19:15 DEBUG  TaskList: ## Finished copy_installation_files
05-29 19:15 DEBUG  TaskList: ## Running get_iso...
05-29 19:15 DEBUG  CommonBackend: Searching for local CD
05-29 19:15 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp is a valid Ubuntu Netbook CD
05-29 19:15 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylD6DF.tmp\casper\filesystem.squashfs
05-29 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:15 DEBUG  CommonBackend: Searching for local ISO
05-29 19:15 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-29 19:15 DEBUG  TaskList: New task get_metalink
05-29 19:15 DEBUG  TaskList: ### Running get_metalink...
05-29 19:15 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink > C:\ubuntu\install
05-29 19:15 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
05-29 19:15 DEBUG  downloader: downloading http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink > C:\ubuntu\install
05-29 19:15 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
05-29 19:15 DEBUG  TaskList: ### Finished get_metalink
05-29 19:15 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-29 19:15 DEBUG  TaskList: # Cancelling tasklist
05-29 19:15 DEBUG  TaskList: # Finished tasklist
05-29 19:15 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-29 19:16 INFO   root: === wubi 11.04 rev211 ===
05-29 19:16 DEBUG  root: Logfile is c:\users\little~1\appdata\local\temp\wubi-11.04-rev211.log
05-29 19:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Little Bastard\\Downloads\\wubi(3).exe"']
05-29 19:16 DEBUG  CommonBackend: data_dir=C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\data
05-29 19:16 DEBUG  WindowsBackend: 7z=C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\bin\7z.exe
05-29 19:16 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-29 19:16 DEBUG  CommonBackend: Fetching basic info...
05-29 19:16 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi(3).exe
05-29 19:16 DEBUG  CommonBackend: platform=win32
05-29 19:16 DEBUG  CommonBackend: osname=nt
05-29 19:16 DEBUG  CommonBackend: language=en_IE
05-29 19:16 DEBUG  CommonBackend: encoding=cp1252
05-29 19:16 DEBUG  WindowsBackend: arch=amd64
05-29 19:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\data\isolist.ini
05-29 19:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 19:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 19:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 19:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 19:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 19:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 19:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 19:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 19:16 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 19:16 DEBUG  WindowsBackend: Fetching host info...
05-29 19:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 19:16 DEBUG  WindowsBackend: windows version=vista
05-29 19:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 19:16 DEBUG  WindowsBackend: windows_sp=None
05-29 19:16 DEBUG  WindowsBackend: windows_build=7601
05-29 19:16 DEBUG  WindowsBackend: gmt=0
05-29 19:16 DEBUG  WindowsBackend: country=IE
05-29 19:16 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 19:16 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 19:16 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 19:16 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 19:16 DEBUG  WindowsBackend: windows_language_code=1033
05-29 19:16 DEBUG  WindowsBackend: windows_language=English
05-29 19:16 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 19:16 DEBUG  WindowsBackend: bootloader=vista
05-29 19:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195690.265625 mb free ntfs)
05-29 19:16 DEBUG  WindowsBackend: drive=Drive(C: hd 195690.265625 mb free ntfs)
05-29 19:16 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 19:16 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-29 19:16 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-29 19:16 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
05-29 19:16 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 19:16 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 19:16 DEBUG  WindowsBackend: keyboard_variant=
05-29 19:16 DEBUG  CommonBackend: python locale=('en_IE', 'cp1252')
05-29 19:16 DEBUG  CommonBackend: locale=en_IE.UTF-8
05-29 19:16 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 19:16 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 19:16 DEBUG  CommonBackend: Searching for local CDs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Ubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Ubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Ubuntu Netbook CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Kubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Kubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Xubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Xubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Mythbuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Mythbuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 INFO   root: Already installed, running the uninstaller...
05-29 19:16 INFO   root: Running the uninstaller...
05-29 19:16 INFO   CommonBackend: This is the uninstaller running
05-29 19:16 DEBUG  WindowsFrontend: __init__...
05-29 19:16 DEBUG  WindowsFrontend: on_init...
05-29 19:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\translations, languages=['en_IE', 'en']
05-29 19:16 INFO   root: Received settings
05-29 19:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\translations, languages=['en_IE', 'en']
05-29 19:16 DEBUG  TaskList: # Running tasklist...
05-29 19:16 DEBUG  TaskList: ## Running Backup ISO...
05-29 19:16 DEBUG  TaskList: ## Finished Backup ISO
05-29 19:16 DEBUG  TaskList: ## Running Remove bootloader entry...
05-29 19:16 DEBUG  WindowsBackend: Could not find bcd id
05-29 19:16 DEBUG  WindowsBackend: undo_bootini C:
05-29 19:16 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 195690.265625 mb free ntfs)
05-29 19:16 DEBUG  TaskList: ## Finished Remove bootloader entry
05-29 19:16 DEBUG  TaskList: ## Running Remove target dir...
05-29 19:16 DEBUG  CommonBackend: Deleting C:\ubuntu
05-29 19:16 DEBUG  TaskList: ## Finished Remove target dir
05-29 19:16 DEBUG  TaskList: ## Running Remove registry key...
05-29 19:16 DEBUG  TaskList: ## Finished Remove registry key
05-29 19:16 DEBUG  TaskList: # Finished tasklist
05-29 19:16 INFO   root: Almost finished uninstalling
05-29 19:16 INFO   root: Finished uninstallation
05-29 19:16 DEBUG  CommonBackend: Fetching basic info...
05-29 19:16 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi(3).exe
05-29 19:16 DEBUG  CommonBackend: platform=win32
05-29 19:16 DEBUG  CommonBackend: osname=nt
05-29 19:16 DEBUG  WindowsBackend: arch=amd64
05-29 19:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\data\isolist.ini
05-29 19:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 19:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 19:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 19:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 19:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 19:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 19:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 19:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 19:16 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 19:16 DEBUG  WindowsBackend: Fetching host info...
05-29 19:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 19:16 DEBUG  WindowsBackend: windows version=vista
05-29 19:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 19:16 DEBUG  WindowsBackend: windows_sp=None
05-29 19:16 DEBUG  WindowsBackend: windows_build=7601
05-29 19:16 DEBUG  WindowsBackend: gmt=0
05-29 19:16 DEBUG  WindowsBackend: country=IE
05-29 19:16 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 19:16 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 19:16 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 19:16 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 19:16 DEBUG  WindowsBackend: windows_language_code=1033
05-29 19:16 DEBUG  WindowsBackend: windows_language=English
05-29 19:16 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 19:16 DEBUG  WindowsBackend: bootloader=vista
05-29 19:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195691.902344 mb free ntfs)
05-29 19:16 DEBUG  WindowsBackend: drive=Drive(C: hd 195691.902344 mb free ntfs)
05-29 19:16 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 19:16 DEBUG  WindowsBackend: uninstaller_path=None
05-29 19:16 DEBUG  WindowsBackend: previous_target_dir=None
05-29 19:16 DEBUG  WindowsBackend: previous_distro_name=None
05-29 19:16 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 19:16 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 19:16 DEBUG  WindowsBackend: keyboard_variant=
05-29 19:16 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 19:16 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 19:16 DEBUG  CommonBackend: Searching for local CDs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Ubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Ubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Ubuntu Netbook CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Kubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Kubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Xubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Xubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Mythbuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Mythbuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 INFO   root: Running the installer...
05-29 19:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\translations, languages=['en_IE', 'en']
05-29 19:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\translations, languages=['en_IE', 'en']
05-29 19:16 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=littlebastard
05-29 19:16 INFO   root: Received settings
05-29 19:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\translations, languages=['en_US', 'en']
05-29 19:16 DEBUG  TaskList: # Running tasklist...
05-29 19:16 DEBUG  TaskList: ## Running select_target_dir...
05-29 19:16 INFO   WindowsBackend: Installing into C:\ubuntu
05-29 19:16 DEBUG  TaskList: ## Finished select_target_dir
05-29 19:16 DEBUG  TaskList: ## Running create_dir_structure...
05-29 19:16 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-29 19:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-29 19:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-29 19:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-29 19:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-29 19:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-29 19:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-29 19:16 DEBUG  TaskList: ## Finished create_dir_structure
05-29 19:16 DEBUG  TaskList: ## Running uncompress_target_dir...
05-29 19:16 DEBUG  TaskList: ## Finished uncompress_target_dir
05-29 19:16 DEBUG  TaskList: ## Running create_uninstaller...
05-29 19:16 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Little Bastard\Downloads\wubi(3).exe -> C:\ubuntu\uninstall-wubi.exe
05-29 19:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-29 19:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-29 19:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-29 19:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-29 19:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-29 19:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-29 19:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-29 19:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-29 19:16 DEBUG  TaskList: ## Finished create_uninstaller
05-29 19:16 DEBUG  TaskList: ## Running copy_installation_files...
05-29 19:16 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-29 19:16 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\winboot -> C:\ubuntu\winboot
05-29 19:16 DEBUG  WindowsBackend: Copying C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-29 19:16 DEBUG  TaskList: ## Finished copy_installation_files
05-29 19:16 DEBUG  TaskList: ## Running get_iso...
05-29 19:16 DEBUG  CommonBackend: Searching for local CD
05-29 19:16 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp is a valid Ubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pylE57F.tmp\casper\filesystem.squashfs
05-29 19:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 19:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:16 DEBUG  CommonBackend: Searching for local ISO
05-29 19:16 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-29 19:16 DEBUG  TaskList: New task get_metalink
05-29 19:16 DEBUG  TaskList: ### Running get_metalink...
05-29 19:16 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink > C:\ubuntu\install
05-29 19:16 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-29 19:16 DEBUG  downloader: download finished (read 28363 bytes)
05-29 19:16 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink > C:\ubuntu\install
05-29 19:16 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-29 19:16 DEBUG  downloader: download finished (read 874 bytes)
05-29 19:16 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
05-29 19:16 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-29 19:16 DEBUG  downloader: download finished (read 198 bytes)
05-29 19:16 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-29 19:16 INFO   saplog: Checking block bindings..
05-29 19:16 INFO   saplog: Key verified successfully.
05-29 19:16 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

05-29 19:16 DEBUG  TaskList: ### Finished get_metalink
05-29 19:16 DEBUG  TaskList: New task download
05-29 19:16 DEBUG  TaskList: ### Running download...
05-29 19:16 DEBUG  btdownloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-29 19:18 INFO   WindowsFrontend: Operation cancelled
05-29 19:18 DEBUG  WindowsFrontend: frontend.quit
05-29 19:18 DEBUG  WindowsFrontend: frontend.on_quit
05-29 19:18 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-29 19:18 DEBUG  TaskList: # Cancelling tasklist
05-29 19:18 DEBUG  TaskList: ### Finished download
05-29 19:18 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-29 19:18 DEBUG  root: application.on_quit
05-29 19:18 DEBUG  root: Forceful exit
05-29 19:18 INFO   root: sys.exit
05-29 19:19 INFO   root: === wubi 11.04 rev211 ===
05-29 19:19 DEBUG  root: Logfile is c:\users\little~1\appdata\local\temp\wubi-11.04-rev211.log
05-29 19:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Little Bastard\\Downloads\\wubi(3).exe"']
05-29 19:19 DEBUG  CommonBackend: data_dir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\data
05-29 19:19 DEBUG  WindowsBackend: 7z=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\bin\7z.exe
05-29 19:19 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-29 19:19 DEBUG  CommonBackend: Fetching basic info...
05-29 19:19 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi(3).exe
05-29 19:19 DEBUG  CommonBackend: platform=win32
05-29 19:19 DEBUG  CommonBackend: osname=nt
05-29 19:19 DEBUG  CommonBackend: language=en_IE
05-29 19:19 DEBUG  CommonBackend: encoding=cp1252
05-29 19:19 DEBUG  WindowsBackend: arch=amd64
05-29 19:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\data\isolist.ini
05-29 19:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 19:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 19:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 19:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 19:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 19:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 19:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 19:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 19:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 19:19 DEBUG  WindowsBackend: Fetching host info...
05-29 19:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 19:19 DEBUG  WindowsBackend: windows version=vista
05-29 19:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 19:19 DEBUG  WindowsBackend: windows_sp=None
05-29 19:19 DEBUG  WindowsBackend: windows_build=7601
05-29 19:19 DEBUG  WindowsBackend: gmt=0
05-29 19:19 DEBUG  WindowsBackend: country=IE
05-29 19:19 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 19:19 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 19:19 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 19:19 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 19:19 DEBUG  WindowsBackend: windows_language_code=1033
05-29 19:19 DEBUG  WindowsBackend: windows_language=English
05-29 19:19 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 19:19 DEBUG  WindowsBackend: bootloader=vista
05-29 19:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195689.261719 mb free ntfs)
05-29 19:19 DEBUG  WindowsBackend: drive=Drive(C: hd 195689.261719 mb free ntfs)
05-29 19:19 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 19:19 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-29 19:19 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-29 19:19 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-29 19:19 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 19:19 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 19:19 DEBUG  WindowsBackend: keyboard_variant=
05-29 19:19 DEBUG  CommonBackend: python locale=('en_IE', 'cp1252')
05-29 19:19 DEBUG  CommonBackend: locale=en_IE.UTF-8
05-29 19:19 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 19:19 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 19:19 DEBUG  CommonBackend: Searching for local CDs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Ubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Ubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Ubuntu Netbook CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Kubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Kubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Xubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Xubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Mythbuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Mythbuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 INFO   root: Already installed, running the uninstaller...
05-29 19:19 INFO   root: Running the uninstaller...
05-29 19:19 INFO   CommonBackend: This is the uninstaller running
05-29 19:19 DEBUG  WindowsFrontend: __init__...
05-29 19:19 DEBUG  WindowsFrontend: on_init...
05-29 19:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\translations, languages=['en_IE', 'en']
05-29 19:19 INFO   root: Received settings
05-29 19:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\translations, languages=['en_IE', 'en']
05-29 19:19 DEBUG  TaskList: # Running tasklist...
05-29 19:19 DEBUG  TaskList: ## Running Backup ISO...
05-29 19:19 DEBUG  TaskList: ## Finished Backup ISO
05-29 19:19 DEBUG  TaskList: ## Running Remove bootloader entry...
05-29 19:19 DEBUG  WindowsBackend: Could not find bcd id
05-29 19:19 DEBUG  WindowsBackend: undo_bootini C:
05-29 19:19 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 195689.261719 mb free ntfs)
05-29 19:19 DEBUG  TaskList: ## Finished Remove bootloader entry
05-29 19:19 DEBUG  TaskList: ## Running Remove target dir...
05-29 19:19 DEBUG  CommonBackend: Deleting C:\ubuntu
05-29 19:19 DEBUG  TaskList: ## Finished Remove target dir
05-29 19:19 DEBUG  TaskList: ## Running Remove registry key...
05-29 19:19 DEBUG  TaskList: ## Finished Remove registry key
05-29 19:19 DEBUG  TaskList: # Finished tasklist
05-29 19:19 INFO   root: Almost finished uninstalling
05-29 19:19 INFO   root: Finished uninstallation
05-29 19:19 DEBUG  CommonBackend: Fetching basic info...
05-29 19:19 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi(3).exe
05-29 19:19 DEBUG  CommonBackend: platform=win32
05-29 19:19 DEBUG  CommonBackend: osname=nt
05-29 19:19 DEBUG  WindowsBackend: arch=amd64
05-29 19:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\data\isolist.ini
05-29 19:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-29 19:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-29 19:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-29 19:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-29 19:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-29 19:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-29 19:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-29 19:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-29 19:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-29 19:19 DEBUG  WindowsBackend: Fetching host info...
05-29 19:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-29 19:19 DEBUG  WindowsBackend: windows version=vista
05-29 19:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-29 19:19 DEBUG  WindowsBackend: windows_sp=None
05-29 19:19 DEBUG  WindowsBackend: windows_build=7601
05-29 19:19 DEBUG  WindowsBackend: gmt=0
05-29 19:19 DEBUG  WindowsBackend: country=IE
05-29 19:19 DEBUG  WindowsBackend: timezone=Europe/Dublin
05-29 19:19 DEBUG  WindowsBackend: windows_username=Little Bastard
05-29 19:19 DEBUG  WindowsBackend: user_full_name=Little Bastard
05-29 19:19 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
05-29 19:19 DEBUG  WindowsBackend: windows_language_code=1033
05-29 19:19 DEBUG  WindowsBackend: windows_language=English
05-29 19:19 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) II Dual-Core M300
05-29 19:19 DEBUG  WindowsBackend: bootloader=vista
05-29 19:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195690.925781 mb free ntfs)
05-29 19:19 DEBUG  WindowsBackend: drive=Drive(C: hd 195690.925781 mb free ntfs)
05-29 19:19 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
05-29 19:19 DEBUG  WindowsBackend: uninstaller_path=None
05-29 19:19 DEBUG  WindowsBackend: previous_target_dir=None
05-29 19:19 DEBUG  WindowsBackend: previous_distro_name=None
05-29 19:19 DEBUG  WindowsBackend: keyboard_id=134813705
05-29 19:19 DEBUG  WindowsBackend: keyboard_layout=gb
05-29 19:19 DEBUG  WindowsBackend: keyboard_variant=
05-29 19:19 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-29 19:19 DEBUG  CommonBackend: Searching ISOs on USB devices
05-29 19:19 DEBUG  CommonBackend: Searching for local CDs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Ubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Ubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Ubuntu Netbook CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Kubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Kubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Xubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Xubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Mythbuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp is a valid Mythbuntu CD
05-29 19:19 DEBUG  Distro:     does not contain C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-29 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-29 19:19 INFO   root: Running the installer...
05-29 19:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\translations, languages=['en_IE', 'en']
05-29 19:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9618.tmp\translations, languages=['en_IE', 'en']
05-29 19:19 INFO   WindowsFrontend: Operation cancelled
05-29 19:19 DEBUG  WindowsFrontend: frontend.quit
05-29 19:19 DEBUG  WindowsFrontend: frontend.on_quit
05-29 19:19 DEBUG  root: application.on_quit
05-29 19:19 INFO   root: sys.exit
06-01 19:51 INFO   root: === wubi 11.04 rev211 ===
06-01 19:51 DEBUG  root: Logfile is c:\users\little~1\appdata\local\temp\wubi-11.04-rev211.log
06-01 19:51 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Little Bastard\\Downloads\\wubi.exe"']
06-01 19:51 DEBUG  CommonBackend: data_dir=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9031.tmp\data
06-01 19:51 DEBUG  WindowsBackend: 7z=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9031.tmp\bin\7z.exe
06-01 19:51 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-01 19:51 DEBUG  CommonBackend: Fetching basic info...
06-01 19:51 DEBUG  CommonBackend: original_exe=C:\Users\Little Bastard\Downloads\wubi.exe
06-01 19:51 DEBUG  CommonBackend: platform=win32
06-01 19:51 DEBUG  CommonBackend: osname=nt
06-01 19:51 DEBUG  CommonBackend: language=en_IE
06-01 19:51 DEBUG  CommonBackend: encoding=cp1252
06-01 19:51 DEBUG  WindowsBackend: arch=amd64
06-01 19:51 DEBUG  CommonBackend: Parsing isolist=C:\Users\LITTLE~1\AppData\Local\Temp\pyl9031.tmp\data\isolist.ini
06-01 19:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-01 19:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-01 19:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-01 19:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-01 19:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-01 19:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-01 19:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-01 19:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-01 19:51 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-01 19:51 DEBUG  WindowsBackend: Fetching host info...
06-01 19:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-01 19:51 DEBUG  WindowsBackend: windows version=vista
06-01 19:51 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
06-01 19:51 DEBUG  WindowsBackend: windows_sp=None
06-01 19:51 DEBUG  WindowsBackend: windows_build=7601
06-01 19:51 DEBUG  WindowsBackend: gmt=0
06-01 19:51 DEBUG  WindowsBackend: country=IE
06-01 19:51 DEBUG  WindowsBackend: timezone=Europe/Dublin
06-01 19:51 DEBUG  WindowsBackend: windows_username=Little Bastard
06-01 19:51 DEBUG  WindowsBackend: user_full_name=Little Bastard
06-01 19:51 DEBUG  WindowsBackend: user_directory=C:\Users\Little Bastard
06-01 19:51 DEBUG  WindowsBackend: windows_language_code=1033
06-01 19:51 DEBUG  WindowsBackend
```

---

### Post by Rubi1200 on 2011-06-03
Hi and welcome to the forums :-)

Two things to check:

check the integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

burn to CD at the lowest speed: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by mörgæs on 2011-06-03
This error appears mostly on CD's. Creating a bootable USB stick is worth trying.

---

### Post by Blackbm on 2011-06-05
Just checked with winmd5sum and the hash keys are different :(
Looks like I have to download it again.

---

### Post by Blackbm on 2011-06-05
Wahoo. I'm finally Ubuntu'd lol. Looks fantastic :) How stupid was I. All I had to do is put the wubi.exe in the same folder as the Iso file. I read it hundreds of time, But never looked at what I was reading. If that makes any sense lol
Now to get my on-board sound working :(

---

### Post by Rubi1200 on 2011-06-06
Excellent! Glad you got things working (almost) :)

---

