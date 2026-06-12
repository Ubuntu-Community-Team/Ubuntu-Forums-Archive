---
title: "weird wubi error"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by jetpackweasel on 2011-04-29
ok so i partitioned my hard drive for 30Gb using windows 7 built in partitioning tool. i then opened wubi, and downloaded and installed ubuntu 11.04 on to that partition, using all 30Gb of it. Wubi then downloaded and installed ubuntu. except when i came back to my computer about an hour later to see of it was done, i got this error. i will give a screen shot in the form of a link to a photo sharing web site, and i will also paste the log file it said for me to look at. please, any help would be appreciated. i am a n00b to ubuntu so please go easy on me. thanks :)
screen shot of error (ignore insomnia window): [http://img24.imageshack.us/i/wubierrormessage.png/](http://img24.imageshack.us/i/wubierrormessage.png/) or [http://img24.imageshack.us/img24/6143/wubierrormessage.png](http://img24.imageshack.us/img24/6143/wubierrormessage.png)


log file begins here:



04-28 18:44 INFO   root: === wubi 11.04 rev211 ===
04-28 18:44 DEBUG  root: Logfile is c:\users\steve\appdata\local\temp\wubi-11.04-rev211.log
04-28 18:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\steve\\Desktop\\wubi.exe"']
04-28 18:44 DEBUG  CommonBackend: data_dir=C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\data
04-28 18:44 DEBUG  WindowsBackend: 7z=C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\bin\7z.exe
04-28 18:44 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-28 18:44 DEBUG  CommonBackend: Fetching basic info...
04-28 18:44 DEBUG  CommonBackend: original_exe=C:\Users\steve\Desktop\wubi.exe
04-28 18:44 DEBUG  CommonBackend: platform=win32
04-28 18:44 DEBUG  CommonBackend: osname=nt
04-28 18:44 DEBUG  CommonBackend: language=en_CA
04-28 18:44 DEBUG  CommonBackend: encoding=cp1252
04-28 18:44 DEBUG  WindowsBackend: arch=amd64
04-28 18:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\data\isolist.ini
04-28 18:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-28 18:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-28 18:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-28 18:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-28 18:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-28 18:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-28 18:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-28 18:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-28 18:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-28 18:44 DEBUG  WindowsBackend: Fetching host info...
04-28 18:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-28 18:44 DEBUG  WindowsBackend: windows version=vista
04-28 18:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-28 18:44 DEBUG  WindowsBackend: windows_sp=None
04-28 18:44 DEBUG  WindowsBackend: windows_build=7600
04-28 18:44 DEBUG  WindowsBackend: gmt=-8
04-28 18:44 DEBUG  WindowsBackend: country=CA
04-28 18:44 DEBUG  WindowsBackend: timezone=America/Vancouver
04-28 18:44 DEBUG  WindowsBackend: windows_username=steve
04-28 18:44 DEBUG  WindowsBackend: user_full_name=steve
04-28 18:44 DEBUG  WindowsBackend: user_directory=C:\Users\steve
04-28 18:44 DEBUG  WindowsBackend: windows_language_code=1033
04-28 18:44 DEBUG  WindowsBackend: windows_language=English
04-28 18:44 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
04-28 18:44 DEBUG  WindowsBackend: bootloader=vista
04-28 18:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 225918.765625 mb free ntfs)
04-28 18:44 DEBUG  WindowsBackend: drive=Drive(C: hd 225918.765625 mb free ntfs)
04-28 18:44 DEBUG  WindowsBackend: drive=Drive(D: hd 2535.83203125 mb free ntfs)
04-28 18:44 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-28 18:44 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-28 18:44 DEBUG  WindowsBackend: uninstaller_path=None
04-28 18:44 DEBUG  WindowsBackend: previous_target_dir=None
04-28 18:44 DEBUG  WindowsBackend: previous_distro_name=None
04-28 18:44 DEBUG  WindowsBackend: keyboard_id=67702793
04-28 18:44 DEBUG  WindowsBackend: keyboard_layout=us
04-28 18:44 DEBUG  WindowsBackend: keyboard_variant=
04-28 18:44 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
04-28 18:44 DEBUG  CommonBackend: locale=en_CA.UTF-8
04-28 18:44 DEBUG  WindowsBackend: total_memory_mb=2974.91796875
04-28 18:44 DEBUG  CommonBackend: Searching ISOs on USB devices
04-28 18:44 DEBUG  CommonBackend: Searching for local CDs
04-28 18:44 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp is a valid Ubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp is a valid Ubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp is a valid Ubuntu Netbook CD
04-28 18:44 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp is a valid Kubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp is a valid Kubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp is a valid Xubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp is a valid Xubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp is a valid Mythbuntu CD
04-28 18:44 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp is a valid Mythbuntu CD
04-28 18:44 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-28 18:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 18:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 18:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-28 18:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 18:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 18:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
04-28 18:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 18:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 18:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:44 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 18:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:44 INFO   root: Running the installer...
04-28 18:44 DEBUG  WindowsFrontend: __init__...
04-28 18:44 DEBUG  WindowsFrontend: on_init...
04-28 18:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\translations, languages=['en_CA', 'en']
04-28 18:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\translations, languages=['en_CA', 'en']
04-28 18:45 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=25000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=redundant409
04-28 18:45 INFO   root: Received settings
04-28 18:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\translations, languages=['en_US', 'en']
04-28 18:45 DEBUG  TaskList: # Running tasklist...
04-28 18:45 DEBUG  TaskList: ## Running select_target_dir...
04-28 18:45 INFO   WindowsBackend: Installing into C:\ubuntu
04-28 18:45 DEBUG  TaskList: ## Finished select_target_dir
04-28 18:45 DEBUG  TaskList: ## Running create_dir_structure...
04-28 18:45 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-28 18:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-28 18:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-28 18:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-28 18:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-28 18:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-28 18:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-28 18:45 DEBUG  TaskList: ## Finished create_dir_structure
04-28 18:45 DEBUG  TaskList: ## Running uncompress_target_dir...
04-28 18:45 DEBUG  TaskList: ## Finished uncompress_target_dir
04-28 18:45 DEBUG  TaskList: ## Running create_uninstaller...
04-28 18:45 DEBUG  WindowsBackend: Copying uninstaller C:\Users\steve\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-28 18:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-28 18:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-28 18:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-28 18:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-28 18:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
04-28 18:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-28 18:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-28 18:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-28 18:45 DEBUG  TaskList: ## Finished create_uninstaller
04-28 18:45 DEBUG  TaskList: ## Running copy_installation_files...
04-28 18:45 DEBUG  WindowsBackend: Copying C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-28 18:45 DEBUG  WindowsBackend: Copying C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\winboot -> C:\ubuntu\winboot
04-28 18:45 DEBUG  WindowsBackend: Copying C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-28 18:45 DEBUG  TaskList: ## Finished copy_installation_files
04-28 18:45 DEBUG  TaskList: ## Running get_iso...
04-28 18:45 DEBUG  CommonBackend: Searching for local CD
04-28 18:45 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp is a valid Ubuntu CD
04-28 18:45 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl85F3.tmp\casper\filesystem.squashfs
04-28 18:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 18:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 18:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:45 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 18:45 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:45 DEBUG  CommonBackend: Searching for local ISO
04-28 18:45 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-28 18:45 DEBUG  TaskList: New task get_metalink
04-28 18:45 DEBUG  TaskList: ### Running get_metalink...
04-28 18:45 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
04-28 18:45 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
04-28 18:45 DEBUG  downloader: download finished (read 28363 bytes)
04-28 18:45 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
04-28 18:45 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
04-28 18:45 DEBUG  downloader: download finished (read 874 bytes)
04-28 18:45 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-28 18:45 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-28 18:45 DEBUG  downloader: download finished (read 198 bytes)
04-28 18:45 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-28 18:45 INFO   saplog: Checking block bindings..
04-28 18:45 INFO   saplog: Key verified successfully.
04-28 18:45 DEBUG  CommonBackend: metalink md5sums:
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

04-28 18:45 DEBUG  TaskList: ### Finished get_metalink
04-28 18:45 DEBUG  TaskList: New task download
04-28 18:45 DEBUG  TaskList: ### Running download...
04-28 18:45 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
04-28 18:51 INFO   WindowsFrontend: Operation cancelled
04-28 18:51 DEBUG  WindowsFrontend: frontend.quit
04-28 18:51 DEBUG  WindowsFrontend: frontend.on_quit
04-28 18:51 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
04-28 18:51 DEBUG  TaskList: # Cancelling tasklist
04-28 18:51 DEBUG  TaskList: ### Finished download
04-28 18:51 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
04-28 18:51 DEBUG  root: application.on_quit
04-28 18:51 DEBUG  root: Forceful exit
04-28 18:51 INFO   root: sys.exit
04-28 18:52 INFO   root: === wubi 11.04 rev211 ===
04-28 18:52 DEBUG  root: Logfile is c:\users\steve\appdata\local\temp\wubi-11.04-rev211.log
04-28 18:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\steve\\Desktop\\wubi.exe"']
04-28 18:52 DEBUG  CommonBackend: data_dir=C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\data
04-28 18:52 DEBUG  WindowsBackend: 7z=C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\bin\7z.exe
04-28 18:52 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-28 18:52 DEBUG  CommonBackend: Fetching basic info...
04-28 18:52 DEBUG  CommonBackend: original_exe=C:\Users\steve\Desktop\wubi.exe
04-28 18:52 DEBUG  CommonBackend: platform=win32
04-28 18:52 DEBUG  CommonBackend: osname=nt
04-28 18:52 DEBUG  CommonBackend: language=en_CA
04-28 18:52 DEBUG  CommonBackend: encoding=cp1252
04-28 18:52 DEBUG  WindowsBackend: arch=amd64
04-28 18:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\data\isolist.ini
04-28 18:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-28 18:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-28 18:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-28 18:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-28 18:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-28 18:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-28 18:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-28 18:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-28 18:52 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-28 18:52 DEBUG  WindowsBackend: Fetching host info...
04-28 18:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-28 18:52 DEBUG  WindowsBackend: windows version=vista
04-28 18:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-28 18:52 DEBUG  WindowsBackend: windows_sp=None
04-28 18:52 DEBUG  WindowsBackend: windows_build=7600
04-28 18:52 DEBUG  WindowsBackend: gmt=-8
04-28 18:52 DEBUG  WindowsBackend: country=CA
04-28 18:52 DEBUG  WindowsBackend: timezone=America/Vancouver
04-28 18:52 DEBUG  WindowsBackend: windows_username=steve
04-28 18:52 DEBUG  WindowsBackend: user_full_name=steve
04-28 18:52 DEBUG  WindowsBackend: user_directory=C:\Users\steve
04-28 18:52 DEBUG  WindowsBackend: windows_language_code=1033
04-28 18:52 DEBUG  WindowsBackend: windows_language=English
04-28 18:52 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
04-28 18:52 DEBUG  WindowsBackend: bootloader=vista
04-28 18:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 225923.359375 mb free ntfs)
04-28 18:52 DEBUG  WindowsBackend: drive=Drive(C: hd 225923.359375 mb free ntfs)
04-28 18:52 DEBUG  WindowsBackend: drive=Drive(D: hd 2535.83203125 mb free ntfs)
04-28 18:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-28 18:52 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-28 18:52 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-28 18:52 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-28 18:52 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-28 18:52 DEBUG  WindowsBackend: keyboard_id=67702793
04-28 18:52 DEBUG  WindowsBackend: keyboard_layout=us
04-28 18:52 DEBUG  WindowsBackend: keyboard_variant=
04-28 18:52 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
04-28 18:52 DEBUG  CommonBackend: locale=en_CA.UTF-8
04-28 18:52 DEBUG  WindowsBackend: total_memory_mb=2974.91796875
04-28 18:52 DEBUG  CommonBackend: Searching ISOs on USB devices
04-28 18:52 DEBUG  CommonBackend: Searching for local CDs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Ubuntu Netbook CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 INFO   root: Already installed, running the uninstaller...
04-28 18:52 INFO   root: Running the uninstaller...
04-28 18:52 INFO   CommonBackend: This is the uninstaller running
04-28 18:52 DEBUG  WindowsFrontend: __init__...
04-28 18:52 DEBUG  WindowsFrontend: on_init...
04-28 18:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\translations, languages=['en_CA', 'en']
04-28 18:52 INFO   root: Received settings
04-28 18:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\translations, languages=['en_CA', 'en']
04-28 18:52 DEBUG  TaskList: # Running tasklist...
04-28 18:52 DEBUG  TaskList: ## Running Backup ISO...
04-28 18:52 DEBUG  TaskList: ## Finished Backup ISO
04-28 18:52 DEBUG  TaskList: ## Running Remove bootloader entry...
04-28 18:52 DEBUG  WindowsBackend: Could not find bcd id
04-28 18:52 DEBUG  WindowsBackend: undo_bootini C:
04-28 18:52 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 225923.359375 mb free ntfs)
04-28 18:52 DEBUG  WindowsBackend: undo_bootini D:
04-28 18:52 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2535.83203125 mb free ntfs)
04-28 18:52 DEBUG  WindowsBackend: undo_bootini Q:
04-28 18:52 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
04-28 18:52 DEBUG  TaskList: ## Finished Remove bootloader entry
04-28 18:52 DEBUG  TaskList: ## Running Remove target dir...
04-28 18:52 DEBUG  CommonBackend: Deleting C:\ubuntu
04-28 18:52 DEBUG  TaskList: ## Finished Remove target dir
04-28 18:52 DEBUG  TaskList: ## Running Remove registry key...
04-28 18:52 DEBUG  TaskList: ## Finished Remove registry key
04-28 18:52 DEBUG  TaskList: # Finished tasklist
04-28 18:52 INFO   root: Almost finished uninstalling
04-28 18:52 INFO   root: Finished uninstallation
04-28 18:52 DEBUG  CommonBackend: Fetching basic info...
04-28 18:52 DEBUG  CommonBackend: original_exe=C:\Users\steve\Desktop\wubi.exe
04-28 18:52 DEBUG  CommonBackend: platform=win32
04-28 18:52 DEBUG  CommonBackend: osname=nt
04-28 18:52 DEBUG  WindowsBackend: arch=amd64
04-28 18:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\data\isolist.ini
04-28 18:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-28 18:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-28 18:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-28 18:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-28 18:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-28 18:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-28 18:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-28 18:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-28 18:52 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-28 18:52 DEBUG  WindowsBackend: Fetching host info...
04-28 18:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-28 18:52 DEBUG  WindowsBackend: windows version=vista
04-28 18:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-28 18:52 DEBUG  WindowsBackend: windows_sp=None
04-28 18:52 DEBUG  WindowsBackend: windows_build=7600
04-28 18:52 DEBUG  WindowsBackend: gmt=-8
04-28 18:52 DEBUG  WindowsBackend: country=CA
04-28 18:52 DEBUG  WindowsBackend: timezone=America/Vancouver
04-28 18:52 DEBUG  WindowsBackend: windows_username=steve
04-28 18:52 DEBUG  WindowsBackend: user_full_name=steve
04-28 18:52 DEBUG  WindowsBackend: user_directory=C:\Users\steve
04-28 18:52 DEBUG  WindowsBackend: windows_language_code=1033
04-28 18:52 DEBUG  WindowsBackend: windows_language=English
04-28 18:52 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
04-28 18:52 DEBUG  WindowsBackend: bootloader=vista
04-28 18:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 225941.898438 mb free ntfs)
04-28 18:52 DEBUG  WindowsBackend: drive=Drive(C: hd 225941.898438 mb free ntfs)
04-28 18:52 DEBUG  WindowsBackend: drive=Drive(D: hd 2535.83203125 mb free ntfs)
04-28 18:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-28 18:52 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-28 18:52 DEBUG  WindowsBackend: uninstaller_path=None
04-28 18:52 DEBUG  WindowsBackend: previous_target_dir=None
04-28 18:52 DEBUG  WindowsBackend: previous_distro_name=None
04-28 18:52 DEBUG  WindowsBackend: keyboard_id=67702793
04-28 18:52 DEBUG  WindowsBackend: keyboard_layout=us
04-28 18:52 DEBUG  WindowsBackend: keyboard_variant=
04-28 18:52 DEBUG  WindowsBackend: total_memory_mb=2974.91796875
04-28 18:52 DEBUG  CommonBackend: Searching ISOs on USB devices
04-28 18:52 DEBUG  CommonBackend: Searching for local CDs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Ubuntu Netbook CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 18:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 18:52 INFO   root: Running the installer...
04-28 18:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\translations, languages=['en_CA', 'en']
04-28 18:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pyl70BF.tmp\translations, languages=['en_CA', 'en']
04-28 18:55 DEBUG  WindowsFrontend: frontend.on_quit
04-28 18:55 DEBUG  root: application.on_quit
04-28 18:55 INFO   root: sys.exit
04-28 19:12 INFO   root: === wubi 11.04 rev211 ===
04-28 19:12 DEBUG  root: Logfile is c:\users\steve\appdata\local\temp\wubi-11.04-rev211.log
04-28 19:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\steve\\Desktop\\wubi.exe"']
04-28 19:12 DEBUG  CommonBackend: data_dir=C:\Users\steve\AppData\Local\Temp\pylBE81.tmp\data
04-28 19:12 DEBUG  WindowsBackend: 7z=C:\Users\steve\AppData\Local\Temp\pylBE81.tmp\bin\7z.exe
04-28 19:12 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-28 19:12 DEBUG  CommonBackend: Fetching basic info...
04-28 19:12 DEBUG  CommonBackend: original_exe=C:\Users\steve\Desktop\wubi.exe
04-28 19:12 DEBUG  CommonBackend: platform=win32
04-28 19:12 DEBUG  CommonBackend: osname=nt
04-28 19:12 DEBUG  CommonBackend: language=en_CA
04-28 19:12 DEBUG  CommonBackend: encoding=cp1252
04-28 19:12 DEBUG  WindowsBackend: arch=amd64
04-28 19:12 DEBUG  CommonBackend: Parsing isolist=C:\Users\steve\AppData\Local\Temp\pylBE81.tmp\data\isolist.ini
04-28 19:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-28 19:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-28 19:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-28 19:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-28 19:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-28 19:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-28 19:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-28 19:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-28 19:12 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-28 19:12 DEBUG  WindowsBackend: Fetching host info...
04-28 19:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-28 19:12 DEBUG  WindowsBackend: windows version=vista
04-28 19:12 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-28 19:12 DEBUG  WindowsBackend: windows_sp=None
04-28 19:12 DEBUG  WindowsBackend: windows_build=7600
04-28 19:12 DEBUG  WindowsBackend: gmt=-8
04-28 19:12 DEBUG  WindowsBackend: country=CA
04-28 19:12 DEBUG  WindowsBackend: timezone=America/Vancouver
04-28 19:12 DEBUG  WindowsBackend: windows_username=steve
04-28 19:12 DEBUG  WindowsBackend: user_full_name=steve
04-28 19:12 DEBUG  WindowsBackend: user_directory=C:\Users\steve
04-28 19:12 DEBUG  WindowsBackend: windows_language_code=1033
04-28 19:12 DEBUG  WindowsBackend: windows_language=English
04-28 19:12 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
04-28 19:12 DEBUG  WindowsBackend: bootloader=vista
04-28 19:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 200287.148438 mb free ntfs)
04-28 19:12 DEBUG  WindowsBackend: drive=Drive(C: hd 200287.148438 mb free ntfs)
04-28 19:12 DEBUG  WindowsBackend: drive=Drive(D: hd 2535.83203125 mb free ntfs)
04-28 19:12 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-28 19:12 DEBUG  WindowsBackend: drive=Drive(F: hd 25506.7070313 mb free ntfs)
04-28 19:12 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-28 19:12 DEBUG  WindowsBackend: uninstaller_path=None
04-28 19:12 DEBUG  WindowsBackend: previous_target_dir=None
04-28 19:12 DEBUG  WindowsBackend: previous_distro_name=None
04-28 19:12 DEBUG  WindowsBackend: keyboard_id=67702793
04-28 19:12 DEBUG  WindowsBackend: keyboard_layout=us
04-28 19:12 DEBUG  WindowsBackend: keyboard_variant=
04-28 19:12 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
04-28 19:12 DEBUG  CommonBackend: locale=en_CA.UTF-8
04-28 19:12 DEBUG  WindowsBackend: total_memory_mb=2974.91796875
04-28 19:12 DEBUG  CommonBackend: Searching ISOs on USB devices
04-28 19:12 DEBUG  CommonBackend: Searching for local CDs
04-28 19:12 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylBE81.tmp is a valid Ubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylBE81.tmp\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylBE81.tmp is a valid Ubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylBE81.tmp\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylBE81.tmp is a valid Ubuntu Netbook CD
04-28 19:12 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylBE81.tmp\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylBE81.tmp is a valid Kubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylBE81.tmp\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylBE81.tmp is a valid Kubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylBE81.tmp\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylBE81.tmp is a valid Xubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylBE81.tmp\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylBE81.tmp is a valid Xubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylBE81.tmp\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylBE81.tmp is a valid Mythbuntu CD
04-28 19:12 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylBE81.tmp\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylBE81.tmp is a valid Mythbuntu CD
04-28 19:12 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylBE81.tmp\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-28 19:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 19:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 19:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-28 19:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 19:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 19:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-28 19:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-28 19:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-28 19:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
04-28 19:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 19:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 19:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:12 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 19:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:12 INFO   root: Running the installer...
04-28 19:12 DEBUG  WindowsFrontend: __init__...
04-28 19:12 DEBUG  WindowsFrontend: on_init...
04-28 19:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pylBE81.tmp\translations, languages=['en_CA', 'en']
04-28 19:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pylBE81.tmp\translations, languages=['en_CA', 'en']
04-28 19:12 INFO   WindowsFrontend: Operation cancelled
04-28 19:12 DEBUG  WindowsFrontend: frontend.quit
04-28 19:12 DEBUG  WindowsFrontend: frontend.on_quit
04-28 19:12 DEBUG  root: application.on_quit
04-28 19:12 INFO   root: sys.exit
04-28 19:24 INFO   root: === wubi 11.04 rev211 ===
04-28 19:24 DEBUG  root: Logfile is c:\users\steve\appdata\local\temp\wubi-11.04-rev211.log
04-28 19:24 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\steve\\Desktop\\wubi.exe"']
04-28 19:24 DEBUG  CommonBackend: data_dir=C:\Users\steve\AppData\Local\Temp\pylB78.tmp\data
04-28 19:24 DEBUG  WindowsBackend: 7z=C:\Users\steve\AppData\Local\Temp\pylB78.tmp\bin\7z.exe
04-28 19:24 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-28 19:24 DEBUG  CommonBackend: Fetching basic info...
04-28 19:24 DEBUG  CommonBackend: original_exe=C:\Users\steve\Desktop\wubi.exe
04-28 19:24 DEBUG  CommonBackend: platform=win32
04-28 19:24 DEBUG  CommonBackend: osname=nt
04-28 19:24 DEBUG  CommonBackend: language=en_CA
04-28 19:24 DEBUG  CommonBackend: encoding=cp1252
04-28 19:24 DEBUG  WindowsBackend: arch=amd64
04-28 19:24 DEBUG  CommonBackend: Parsing isolist=C:\Users\steve\AppData\Local\Temp\pylB78.tmp\data\isolist.ini
04-28 19:24 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-28 19:24 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-28 19:24 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-28 19:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-28 19:24 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-28 19:24 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-28 19:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-28 19:24 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-28 19:24 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-28 19:24 DEBUG  WindowsBackend: Fetching host info...
04-28 19:24 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-28 19:24 DEBUG  WindowsBackend: windows version=vista
04-28 19:24 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-28 19:24 DEBUG  WindowsBackend: windows_sp=None
04-28 19:24 DEBUG  WindowsBackend: windows_build=7600
04-28 19:24 DEBUG  WindowsBackend: gmt=-8
04-28 19:24 DEBUG  WindowsBackend: country=CA
04-28 19:24 DEBUG  WindowsBackend: timezone=America/Vancouver
04-28 19:24 DEBUG  WindowsBackend: windows_username=steve
04-28 19:24 DEBUG  WindowsBackend: user_full_name=steve
04-28 19:24 DEBUG  WindowsBackend: user_directory=C:\Users\steve
04-28 19:24 DEBUG  WindowsBackend: windows_language_code=1033
04-28 19:24 DEBUG  WindowsBackend: windows_language=English
04-28 19:24 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
04-28 19:24 DEBUG  WindowsBackend: bootloader=vista
04-28 19:24 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195165.199219 mb free ntfs)
04-28 19:24 DEBUG  WindowsBackend: drive=Drive(C: hd 195165.199219 mb free ntfs)
04-28 19:24 DEBUG  WindowsBackend: drive=Drive(D: hd 2535.83203125 mb free ntfs)
04-28 19:24 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-28 19:24 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-28 19:24 DEBUG  WindowsBackend: drive=Drive(X: hd 30627.5507813 mb free ntfs)
04-28 19:24 DEBUG  WindowsBackend: uninstaller_path=None
04-28 19:24 DEBUG  WindowsBackend: previous_target_dir=None
04-28 19:24 DEBUG  WindowsBackend: previous_distro_name=None
04-28 19:24 DEBUG  WindowsBackend: keyboard_id=67702793
04-28 19:24 DEBUG  WindowsBackend: keyboard_layout=us
04-28 19:24 DEBUG  WindowsBackend: keyboard_variant=
04-28 19:24 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
04-28 19:24 DEBUG  CommonBackend: locale=en_CA.UTF-8
04-28 19:24 DEBUG  WindowsBackend: total_memory_mb=2974.91796875
04-28 19:24 DEBUG  CommonBackend: Searching ISOs on USB devices
04-28 19:24 DEBUG  CommonBackend: Searching for local CDs
04-28 19:24 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylB78.tmp is a valid Ubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylB78.tmp\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylB78.tmp is a valid Ubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylB78.tmp\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylB78.tmp is a valid Ubuntu Netbook CD
04-28 19:24 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylB78.tmp\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylB78.tmp is a valid Kubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylB78.tmp\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylB78.tmp is a valid Kubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylB78.tmp\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylB78.tmp is a valid Xubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylB78.tmp\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylB78.tmp is a valid Xubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylB78.tmp\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylB78.tmp is a valid Mythbuntu CD
04-28 19:24 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylB78.tmp\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylB78.tmp is a valid Mythbuntu CD
04-28 19:24 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylB78.tmp\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-28 19:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 19:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 19:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-28 19:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 19:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 19:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
04-28 19:24 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 19:24 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 19:24 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu Netbook CD
04-28 19:24 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether X:\ is a valid Kubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether X:\ is a valid Kubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether X:\ is a valid Xubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether X:\ is a valid Xubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether X:\ is a valid Mythbuntu CD
04-28 19:24 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether X:\ is a valid Mythbuntu CD
04-28 19:24 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:24 INFO   root: Running the installer...
04-28 19:24 DEBUG  WindowsFrontend: __init__...
04-28 19:24 DEBUG  WindowsFrontend: on_init...
04-28 19:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pylB78.tmp\translations, languages=['en_CA', 'en']
04-28 19:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pylB78.tmp\translations, languages=['en_CA', 'en']
04-28 19:24 DEBUG  WinuiInstallationPage: target_drive=X:, installation_size=29000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=redundant409
04-28 19:24 INFO   root: Received settings
04-28 19:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pylB78.tmp\translations, languages=['en_US', 'en']
04-28 19:24 DEBUG  TaskList: # Running tasklist...
04-28 19:24 DEBUG  TaskList: ## Running select_target_dir...
04-28 19:24 INFO   WindowsBackend: Installing into X:\ubuntu
04-28 19:24 DEBUG  TaskList: ## Finished select_target_dir
04-28 19:24 DEBUG  TaskList: ## Running create_dir_structure...
04-28 19:24 DEBUG  CommonBackend: Creating dir X:\ubuntu
04-28 19:24 DEBUG  CommonBackend: Creating dir X:\ubuntu\disks
04-28 19:24 DEBUG  CommonBackend: Creating dir X:\ubuntu\install
04-28 19:24 DEBUG  CommonBackend: Creating dir X:\ubuntu\install\boot
04-28 19:24 DEBUG  CommonBackend: Creating dir X:\ubuntu\disks\boot
04-28 19:24 DEBUG  CommonBackend: Creating dir X:\ubuntu\disks\boot\grub
04-28 19:24 DEBUG  CommonBackend: Creating dir X:\ubuntu\install\boot\grub
04-28 19:24 DEBUG  TaskList: ## Finished create_dir_structure
04-28 19:24 DEBUG  TaskList: ## Running uncompress_target_dir...
04-28 19:24 DEBUG  TaskList: ## Finished uncompress_target_dir
04-28 19:24 DEBUG  TaskList: ## Running create_uninstaller...
04-28 19:24 DEBUG  WindowsBackend: Copying uninstaller C:\Users\steve\Desktop\wubi.exe -> X:\ubuntu\uninstall-wubi.exe
04-28 19:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString X:\ubuntu\uninstall-wubi.exe
04-28 19:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir X:\ubuntu
04-28 19:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-28 19:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon X:\ubuntu\Ubuntu.ico
04-28 19:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
04-28 19:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-28 19:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-28 19:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-28 19:24 DEBUG  TaskList: ## Finished create_uninstaller
04-28 19:24 DEBUG  TaskList: ## Running copy_installation_files...
04-28 19:24 DEBUG  WindowsBackend: Copying C:\Users\steve\AppData\Local\Temp\pylB78.tmp\data\custom-installation -> X:\ubuntu\install\custom-installation
04-28 19:24 DEBUG  WindowsBackend: Copying C:\Users\steve\AppData\Local\Temp\pylB78.tmp\winboot -> X:\ubuntu\winboot
04-28 19:24 DEBUG  WindowsBackend: Copying C:\Users\steve\AppData\Local\Temp\pylB78.tmp\data\images\Ubuntu.ico -> X:\ubuntu\Ubuntu.ico
04-28 19:24 DEBUG  TaskList: ## Finished copy_installation_files
04-28 19:24 DEBUG  TaskList: ## Running get_iso...
04-28 19:24 DEBUG  CommonBackend: Searching for local CD
04-28 19:24 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pylB78.tmp is a valid Ubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pylB78.tmp\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:24 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
04-28 19:24 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:24 DEBUG  CommonBackend: Searching for local ISO
04-28 19:24 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-28 19:24 DEBUG  TaskList: New task get_metalink
04-28 19:24 DEBUG  TaskList: ### Running get_metalink...
04-28 19:24 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > X:\ubuntu\install
04-28 19:24 DEBUG  downloader: Download start filename=X:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
04-28 19:24 DEBUG  downloader: download finished (read 28363 bytes)
04-28 19:24 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > X:\ubuntu\install
04-28 19:24 DEBUG  downloader: Download start filename=X:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
04-28 19:24 DEBUG  downloader: download finished (read 874 bytes)
04-28 19:24 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > X:\ubuntu\install
04-28 19:24 DEBUG  downloader: Download start filename=X:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-28 19:24 DEBUG  downloader: download finished (read 198 bytes)
04-28 19:24 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-28 19:24 INFO   saplog: Checking block bindings..
04-28 19:24 INFO   saplog: Key verified successfully.
04-28 19:24 DEBUG  CommonBackend: metalink md5sums:
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

04-28 19:24 DEBUG  TaskList: ### Finished get_metalink
04-28 19:24 DEBUG  TaskList: New task download
04-28 19:24 DEBUG  TaskList: ### Running download...
04-28 19:24 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > X:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
04-28 19:25 INFO   WindowsFrontend: Operation cancelled
04-28 19:25 DEBUG  WindowsFrontend: frontend.quit
04-28 19:25 DEBUG  WindowsFrontend: frontend.on_quit
04-28 19:25 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
04-28 19:25 DEBUG  TaskList: # Cancelling tasklist
04-28 19:25 DEBUG  TaskList: ### Finished download
04-28 19:26 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
04-28 19:26 DEBUG  root: application.on_quit
04-28 19:26 DEBUG  root: Forceful exit
04-28 19:26 INFO   root: sys.exit
04-28 19:26 INFO   root: === wubi 11.04 rev211 ===
04-28 19:26 DEBUG  root: Logfile is c:\users\steve\appdata\local\temp\wubi-11.04-rev211.log
04-28 19:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\steve\\Desktop\\wubi.exe"']
04-28 19:26 DEBUG  CommonBackend: data_dir=C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\data
04-28 19:26 DEBUG  WindowsBackend: 7z=C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\bin\7z.exe
04-28 19:26 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-28 19:26 DEBUG  CommonBackend: Fetching basic info...
04-28 19:26 DEBUG  CommonBackend: original_exe=C:\Users\steve\Desktop\wubi.exe
04-28 19:26 DEBUG  CommonBackend: platform=win32
04-28 19:26 DEBUG  CommonBackend: osname=nt
04-28 19:26 DEBUG  CommonBackend: language=en_CA
04-28 19:26 DEBUG  CommonBackend: encoding=cp1252
04-28 19:26 DEBUG  WindowsBackend: arch=amd64
04-28 19:26 DEBUG  CommonBackend: Parsing isolist=C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\data\isolist.ini
04-28 19:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-28 19:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-28 19:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-28 19:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-28 19:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-28 19:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-28 19:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-28 19:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-28 19:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-28 19:26 DEBUG  WindowsBackend: Fetching host info...
04-28 19:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-28 19:26 DEBUG  WindowsBackend: windows version=vista
04-28 19:26 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-28 19:26 DEBUG  WindowsBackend: windows_sp=None
04-28 19:26 DEBUG  WindowsBackend: windows_build=7600
04-28 19:26 DEBUG  WindowsBackend: gmt=-8
04-28 19:26 DEBUG  WindowsBackend: country=CA
04-28 19:26 DEBUG  WindowsBackend: timezone=America/Vancouver
04-28 19:26 DEBUG  WindowsBackend: windows_username=steve
04-28 19:26 DEBUG  WindowsBackend: user_full_name=steve
04-28 19:26 DEBUG  WindowsBackend: user_directory=C:\Users\steve
04-28 19:26 DEBUG  WindowsBackend: windows_language_code=1033
04-28 19:26 DEBUG  WindowsBackend: windows_language=English
04-28 19:26 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
04-28 19:26 DEBUG  WindowsBackend: bootloader=vista
04-28 19:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195164.164063 mb free ntfs)
04-28 19:26 DEBUG  WindowsBackend: drive=Drive(C: hd 195164.164063 mb free ntfs)
04-28 19:26 DEBUG  WindowsBackend: drive=Drive(D: hd 2535.83203125 mb free ntfs)
04-28 19:26 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-28 19:26 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-28 19:26 DEBUG  WindowsBackend: drive=Drive(X: hd 30615.8671875 mb free ntfs)
04-28 19:26 DEBUG  WindowsBackend: uninstaller_path=X:\ubuntu\uninstall-wubi.exe
04-28 19:26 DEBUG  WindowsBackend: previous_target_dir=X:\ubuntu
04-28 19:26 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-28 19:26 DEBUG  WindowsBackend: keyboard_id=67702793
04-28 19:26 DEBUG  WindowsBackend: keyboard_layout=us
04-28 19:26 DEBUG  WindowsBackend: keyboard_variant=
04-28 19:26 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
04-28 19:26 DEBUG  CommonBackend: locale=en_CA.UTF-8
04-28 19:26 DEBUG  WindowsBackend: total_memory_mb=2974.91796875
04-28 19:26 DEBUG  CommonBackend: Searching ISOs on USB devices
04-28 19:26 DEBUG  CommonBackend: Searching for local CDs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Ubuntu Netbook CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu Netbook CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 INFO   root: Already installed, running the uninstaller...
04-28 19:26 INFO   root: Running the uninstaller...
04-28 19:26 INFO   CommonBackend: This is the uninstaller running
04-28 19:26 DEBUG  WindowsFrontend: __init__...
04-28 19:26 DEBUG  WindowsFrontend: on_init...
04-28 19:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\translations, languages=['en_CA', 'en']
04-28 19:26 INFO   root: Received settings
04-28 19:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\translations, languages=['en_CA', 'en']
04-28 19:26 DEBUG  TaskList: # Running tasklist...
04-28 19:26 DEBUG  TaskList: ## Running Backup ISO...
04-28 19:26 DEBUG  TaskList: ## Finished Backup ISO
04-28 19:26 DEBUG  TaskList: ## Running Remove bootloader entry...
04-28 19:26 DEBUG  WindowsBackend: Could not find bcd id
04-28 19:26 DEBUG  WindowsBackend: undo_bootini C:
04-28 19:26 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 195164.164063 mb free ntfs)
04-28 19:26 DEBUG  WindowsBackend: undo_bootini D:
04-28 19:26 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2535.83203125 mb free ntfs)
04-28 19:26 DEBUG  WindowsBackend: undo_bootini Q:
04-28 19:26 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
04-28 19:26 DEBUG  WindowsBackend: undo_bootini X:
04-28 19:26 DEBUG  WindowsBackend: undo_configsys Drive(X: hd 30615.8671875 mb free ntfs)
04-28 19:26 DEBUG  TaskList: ## Finished Remove bootloader entry
04-28 19:26 DEBUG  TaskList: ## Running Remove target dir...
04-28 19:26 DEBUG  CommonBackend: Deleting X:\ubuntu
04-28 19:26 DEBUG  TaskList: ## Finished Remove target dir
04-28 19:26 DEBUG  TaskList: ## Running Remove registry key...
04-28 19:26 DEBUG  TaskList: ## Finished Remove registry key
04-28 19:26 DEBUG  TaskList: # Finished tasklist
04-28 19:26 INFO   root: Almost finished uninstalling
04-28 19:26 INFO   root: Finished uninstallation
04-28 19:26 DEBUG  CommonBackend: Fetching basic info...
04-28 19:26 DEBUG  CommonBackend: original_exe=C:\Users\steve\Desktop\wubi.exe
04-28 19:26 DEBUG  CommonBackend: platform=win32
04-28 19:26 DEBUG  CommonBackend: osname=nt
04-28 19:26 DEBUG  WindowsBackend: arch=amd64
04-28 19:26 DEBUG  CommonBackend: Parsing isolist=C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\data\isolist.ini
04-28 19:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-28 19:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-28 19:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-28 19:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-28 19:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-28 19:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-28 19:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-28 19:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-28 19:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-28 19:26 DEBUG  WindowsBackend: Fetching host info...
04-28 19:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-28 19:26 DEBUG  WindowsBackend: windows version=vista
04-28 19:26 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-28 19:26 DEBUG  WindowsBackend: windows_sp=None
04-28 19:26 DEBUG  WindowsBackend: windows_build=7600
04-28 19:26 DEBUG  WindowsBackend: gmt=-8
04-28 19:26 DEBUG  WindowsBackend: country=CA
04-28 19:26 DEBUG  WindowsBackend: timezone=America/Vancouver
04-28 19:26 DEBUG  WindowsBackend: windows_username=steve
04-28 19:26 DEBUG  WindowsBackend: user_full_name=steve
04-28 19:26 DEBUG  WindowsBackend: user_directory=C:\Users\steve
04-28 19:26 DEBUG  WindowsBackend: windows_language_code=1033
04-28 19:26 DEBUG  WindowsBackend: windows_language=English
04-28 19:26 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
04-28 19:26 DEBUG  WindowsBackend: bootloader=vista
04-28 19:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 195164.152344 mb free ntfs)
04-28 19:26 DEBUG  WindowsBackend: drive=Drive(C: hd 195164.152344 mb free ntfs)
04-28 19:26 DEBUG  WindowsBackend: drive=Drive(D: hd 2535.83203125 mb free ntfs)
04-28 19:26 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-28 19:26 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-28 19:26 DEBUG  WindowsBackend: drive=Drive(X: hd 30627.546875 mb free ntfs)
04-28 19:26 DEBUG  WindowsBackend: uninstaller_path=None
04-28 19:26 DEBUG  WindowsBackend: previous_target_dir=None
04-28 19:26 DEBUG  WindowsBackend: previous_distro_name=None
04-28 19:26 DEBUG  WindowsBackend: keyboard_id=67702793
04-28 19:26 DEBUG  WindowsBackend: keyboard_layout=us
04-28 19:26 DEBUG  WindowsBackend: keyboard_variant=
04-28 19:26 DEBUG  WindowsBackend: total_memory_mb=2974.91796875
04-28 19:26 DEBUG  CommonBackend: Searching ISOs on USB devices
04-28 19:26 DEBUG  CommonBackend: Searching for local CDs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Ubuntu Netbook CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu Netbook CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Kubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Xubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Mythbuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 INFO   root: Running the installer...
04-28 19:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\translations, languages=['en_CA', 'en']
04-28 19:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\translations, languages=['en_CA', 'en']
04-28 19:26 DEBUG  WinuiInstallationPage: target_drive=X:, installation_size=29000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=redundant409
04-28 19:26 INFO   root: Received settings
04-28 19:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\translations, languages=['en_US', 'en']
04-28 19:26 DEBUG  TaskList: # Running tasklist...
04-28 19:26 DEBUG  TaskList: ## Running select_target_dir...
04-28 19:26 INFO   WindowsBackend: Installing into X:\ubuntu
04-28 19:26 DEBUG  TaskList: ## Finished select_target_dir
04-28 19:26 DEBUG  TaskList: ## Running create_dir_structure...
04-28 19:26 DEBUG  CommonBackend: Creating dir X:\ubuntu
04-28 19:26 DEBUG  CommonBackend: Creating dir X:\ubuntu\disks
04-28 19:26 DEBUG  CommonBackend: Creating dir X:\ubuntu\install
04-28 19:26 DEBUG  CommonBackend: Creating dir X:\ubuntu\install\boot
04-28 19:26 DEBUG  CommonBackend: Creating dir X:\ubuntu\disks\boot
04-28 19:26 DEBUG  CommonBackend: Creating dir X:\ubuntu\disks\boot\grub
04-28 19:26 DEBUG  CommonBackend: Creating dir X:\ubuntu\install\boot\grub
04-28 19:26 DEBUG  TaskList: ## Finished create_dir_structure
04-28 19:26 DEBUG  TaskList: ## Running uncompress_target_dir...
04-28 19:26 DEBUG  TaskList: ## Finished uncompress_target_dir
04-28 19:26 DEBUG  TaskList: ## Running create_uninstaller...
04-28 19:26 DEBUG  WindowsBackend: Copying uninstaller C:\Users\steve\Desktop\wubi.exe -> X:\ubuntu\uninstall-wubi.exe
04-28 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString X:\ubuntu\uninstall-wubi.exe
04-28 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir X:\ubuntu
04-28 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-28 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon X:\ubuntu\Ubuntu.ico
04-28 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
04-28 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-28 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-28 19:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-28 19:26 DEBUG  TaskList: ## Finished create_uninstaller
04-28 19:26 DEBUG  TaskList: ## Running copy_installation_files...
04-28 19:26 DEBUG  WindowsBackend: Copying C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\data\custom-installation -> X:\ubuntu\install\custom-installation
04-28 19:26 DEBUG  WindowsBackend: Copying C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\winboot -> X:\ubuntu\winboot
04-28 19:26 DEBUG  WindowsBackend: Copying C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\data\images\Ubuntu.ico -> X:\ubuntu\Ubuntu.ico
04-28 19:26 DEBUG  TaskList: ## Finished copy_installation_files
04-28 19:26 DEBUG  TaskList: ## Running get_iso...
04-28 19:26 DEBUG  CommonBackend: Searching for local CD
04-28 19:26 DEBUG  Distro:   checking whether C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain C:\Users\steve\AppData\Local\Temp\pyl9D3B.tmp\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-28 19:26 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
04-28 19:26 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
04-28 19:26 DEBUG  CommonBackend: Searching for local ISO
04-28 19:26 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-28 19:26 DEBUG  TaskList: New task get_metalink
04-28 19:26 DEBUG  TaskList: ### Running get_metalink...
04-28 19:26 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > X:\ubuntu\install
04-28 19:26 DEBUG  downloader: Download start filename=X:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
04-28 19:26 DEBUG  downloader: download finished (read 28363 bytes)
04-28 19:26 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > X:\ubuntu\install
04-28 19:26 DEBUG  downloader: Download start filename=X:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
04-28 19:26 DEBUG  downloader: download finished (read 874 bytes)
04-28 19:26 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > X:\ubuntu\install
04-28 19:26 DEBUG  downloader: Download start filename=X:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-28 19:26 DEBUG  downloader: download finished (read 198 bytes)
04-28 19:26 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-28 19:26 INFO   saplog: Checking block bindings..
04-28 19:26 INFO   saplog: Key verified successfully.
04-28 19:26 DEBUG  CommonBackend: metalink md5sums:
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

04-28 19:26 DEBUG  TaskList: ### Finished get_metalink
04-28 19:26 DEBUG  TaskList: New task download
04-28 19:26 DEBUG  TaskList: ### Running download...
04-28 19:26 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > X:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
04-28 21:01 DEBUG  TaskList: ### Finished download
04-28 21:01 DEBUG  TaskList: New task check_iso
04-28 21:01 DEBUG  TaskList: ### Running check_iso...
04-28 21:01 DEBUG  CommonBackend: Checking X:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
04-28 21:01 DEBUG  Distro:   checking Ubuntu ISO X:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
04-28 21:01 DEBUG  WindowsBackend:   extracting .disk\info from X:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
04-28 21:01 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
04-28 21:01 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
04-28 21:01 INFO   Distro: Found a valid iso for Ubuntu: X:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
04-28 21:01 DEBUG  TaskList: New task get_file_md5
04-28 21:01 DEBUG  TaskList: #### Running get_file_md5...
04-28 21:01 DEBUG  TaskList: #### Finished get_file_md5
04-28 21:01 DEBUG  TaskList: ### Finished check_iso
04-28 21:01 DEBUG  TaskList: ## Finished get_iso
04-28 21:01 DEBUG  TaskList: ## Running extract_kernel...
04-28 21:01 DEBUG  CommonBackend: Extracting files from ISO X:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
04-28 21:01 DEBUG  WindowsBackend:   extracting md5sum.txt from X:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
04-28 21:01 DEBUG  WindowsBackend:   extracting casper\vmlinuz from X:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
04-28 21:01 DEBUG  WindowsBackend:   extracting casper\initrd.lz from X:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
04-28 21:01 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
04-28 21:01 DEBUG  CommonBackend:   checking X:\ubuntu\install\boot\vmlinuz
04-28 21:01 DEBUG  CommonBackend:   X:\ubuntu\install\boot\vmlinuz md5 = 45a7bee6779b8cd75634a70fd7a566dd == 45a7bee6779b8cd75634a70fd7a566dd
04-28 21:01 DEBUG  CommonBackend:   checking X:\ubuntu\install\boot\initrd.lz
04-28 21:01 DEBUG  CommonBackend:   X:\ubuntu\install\boot\initrd.lz md5 = 4aa66b9da42e1a3f667ab0c8009cc801 == 4aa66b9da42e1a3f667ab0c8009cc801
04-28 21:01 DEBUG  TaskList: ## Finished extract_kernel
04-28 21:01 DEBUG  TaskList: ## Running choose_disk_sizes...
04-28 21:01 DEBUG  WindowsBackend: total size=29000
  root=28744
  swap=256
  home=0
  usr=0
04-28 21:01 DEBUG  TaskList: ## Finished choose_disk_sizes
04-28 21:01 DEBUG  TaskList: ## Running create_preseed...
04-28 21:01 DEBUG  TaskList: ## Finished create_preseed
04-28 21:01 DEBUG  TaskList: ## Running modify_bootloader...
04-28 21:01 DEBUG  TaskList: New task modify_bcd
04-28 21:01 DEBUG  TaskList: ### Running modify_bcd...
04-28 21:01 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 195164.152344 mb free ntfs)
04-28 21:01 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {0d67b86d-a9e1-11df-b661-f65ab86d47fa} device partition=X:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 648, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {0d67b86d-a9e1-11df-b661-f65ab86d47fa} device partition=X:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
04-28 21:01 DEBUG  TaskList: # Cancelling tasklist
04-28 21:01 DEBUG  TaskList: New task modify_bcd
04-28 21:01 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {0d67b86d-a9e1-11df-b661-f65ab86d47fa} device partition=X:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 648, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {0d67b86d-a9e1-11df-b661-f65ab86d47fa} device partition=X:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
04-28 21:01 DEBUG  TaskList: New task modify_bcd
04-28 21:01 DEBUG  TaskList: New task modify_bcd
04-28 21:01 DEBUG  TaskList: ## Finished modify_bootloader
04-28 21:01 DEBUG  TaskList: # Finished tasklist

please help :)

---

### Post by bcbc on 2011-04-29
Likely X: is a dynamic drive (these are only good when booted in windows).

PS. Wubi doesn't require a separate partition (there's no benefit to it).

---

