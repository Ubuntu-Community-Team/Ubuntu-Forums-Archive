---
title: "Ubuntu Won't Install Through Wubi"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by sirloganthestud on 2010-03-02
Recently I have been trying to install Ubuntu on a desktop PC through Wubi because there is a problem with the CD drive.  At around the third quarter of the download, it comes up with an error message that reads:

"An error occurred:

Permission Denied

For more information, please see the log file.........." it gives me the name of a log file, so I located it and it came up with this (it's rather long):

02-26 17:02 INFO   root: === wubi 9.10ubuntu1 rev160 ===
02-26 17:02 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-9.10ubuntu1-rev160.log
02-26 17:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Owner\\My Documents\\Downloads\\wubi (1).exe"']
02-26 17:02 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\data
02-26 17:02 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\bin\7z.exe
02-26 17:02 DEBUG  CommonBackend: Fetching basic info...
02-26 17:02 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe
02-26 17:02 DEBUG  CommonBackend: platform=win32
02-26 17:02 DEBUG  CommonBackend: osname=nt
02-26 17:02 DEBUG  CommonBackend: language=en_US
02-26 17:02 DEBUG  CommonBackend: encoding=cp1252
02-26 17:02 DEBUG  WindowsBackend: arch=i386
02-26 17:02 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\data\isolist.ini
02-26 17:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-26 17:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-26 17:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-26 17:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-26 17:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-26 17:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-26 17:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-26 17:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-26 17:02 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-26 17:02 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-26 17:02 DEBUG  WindowsBackend: Fetching host info...
02-26 17:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-26 17:02 DEBUG  WindowsBackend: windows version=xp
02-26 17:02 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-26 17:02 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-26 17:02 DEBUG  WindowsBackend: windows_build=2600
02-26 17:02 DEBUG  WindowsBackend: gmt=-6
02-26 17:02 DEBUG  WindowsBackend: country=US
02-26 17:02 DEBUG  WindowsBackend: timezone=America/Chicago
02-26 17:02 DEBUG  WindowsBackend: windows_username=Owner
02-26 17:02 DEBUG  WindowsBackend: user_full_name=Owner
02-26 17:02 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
02-26 17:02 DEBUG  WindowsBackend: windows_language_code=1033
02-26 17:02 DEBUG  WindowsBackend: windows_language=English
02-26 17:02 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2400+
02-26 17:02 DEBUG  WindowsBackend: bootloader=xp
02-26 17:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 71119.71875 mb free ntfs)
02-26 17:02 DEBUG  WindowsBackend: drive=Drive(C: hd 71119.71875 mb free ntfs)
02-26 17:02 DEBUG  WindowsBackend: drive=Drive(D: hd 1028.88671875 mb free fat32)
02-26 17:02 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-26 17:02 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-26 17:02 DEBUG  WindowsBackend: uninstaller_path=None
02-26 17:02 DEBUG  WindowsBackend: previous_target_dir=None
02-26 17:02 DEBUG  WindowsBackend: previous_distro_name=None
02-26 17:02 DEBUG  WindowsBackend: keyboard_id=67699721
02-26 17:02 DEBUG  WindowsBackend: keyboard_layout=us
02-26 17:02 DEBUG  WindowsBackend: keyboard_variant=
02-26 17:02 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-26 17:02 DEBUG  CommonBackend: locale=en_US.UTF-8
02-26 17:02 DEBUG  WindowsBackend: total_memory_mb=479.484375
02-26 17:02 DEBUG  CommonBackend: Searching ISOs on USB devices
02-26 17:02 DEBUG  CommonBackend: Searching for local CDs
02-26 17:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Ubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Ubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Ubuntu Netbook Remix CD
02-26 17:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Kubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Kubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Kubuntu Netbook CD
02-26 17:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Xubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Xubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Mythbuntu CD
02-26 17:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Mythbuntu CD
02-26 17:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-26 17:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-26 17:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-26 17:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-26 17:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-26 17:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-26 17:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-26 17:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-26 17:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
02-26 17:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
02-26 17:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-26 17:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-26 17:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-26 17:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:02 INFO   root: Running the installer...
02-26 17:02 DEBUG  WindowsFrontend: __init__...
02-26 17:02 DEBUG  WindowsFrontend: on_init...
02-26 17:02 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\translations, languages=['en_US', 'en']
02-26 17:02 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\translations, languages=['en_US', 'en']
02-26 17:03 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=diningroom
02-26 17:03 INFO   root: Received settings
02-26 17:03 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\translations, languages=['en_US', 'en']
02-26 17:03 DEBUG  TaskList: # Running tasklist...
02-26 17:03 DEBUG  TaskList: ## Running select_target_dir...
02-26 17:03 INFO   WindowsBackend: Installing into C:\ubuntu
02-26 17:03 DEBUG  TaskList: ## Finished select_target_dir
02-26 17:03 DEBUG  TaskList: ## Running create_dir_structure...
02-26 17:03 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-26 17:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-26 17:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-26 17:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-26 17:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-26 17:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-26 17:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-26 17:03 DEBUG  TaskList: ## Finished create_dir_structure
02-26 17:03 DEBUG  TaskList: ## Running uncompress_target_dir...
02-26 17:03 DEBUG  TaskList: ## Finished uncompress_target_dir
02-26 17:03 DEBUG  TaskList: ## Running create_uninstaller...
02-26 17:03 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
02-26 17:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-26 17:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-26 17:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-26 17:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-26 17:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
02-26 17:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-26 17:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-26 17:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-26 17:03 DEBUG  TaskList: ## Finished create_uninstaller
02-26 17:03 DEBUG  TaskList: ## Running copy_installation_files...
02-26 17:03 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-26 17:03 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\winboot -> C:\ubuntu\winboot
02-26 17:03 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
02-26 17:03 DEBUG  TaskList: ## Finished copy_installation_files
02-26 17:03 DEBUG  TaskList: ## Running get_iso...
02-26 17:03 DEBUG  CommonBackend: Searching for local CD
02-26 17:03 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp is a valid Ubuntu CD
02-26 17:03 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4B.tmp\casper\filesystem.squashfs
02-26 17:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 17:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 17:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-26 17:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:03 DEBUG  CommonBackend: Searching for local ISO
02-26 17:03 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\Owner\My Documents\Downloads\xubuntu-9.10-beta-desktop-i386.iso
02-26 17:03 DEBUG  WindowsBackend:   extracting .disk\info from C:\Documents and Settings\Owner\My Documents\Downloads\xubuntu-9.10-beta-desktop-i386.iso
02-26 17:03 DEBUG  Distro:   parsing info from str=Xubuntu 9.10 "Karmic Koala" - Beta i386 (20090929.1)
02-26 17:03 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Beta', 'version': '9.10', 'build': '20090929.1', 'codename': 'Karmic Koala', 'arch': 'i386'}
02-26 17:03 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
02-26 17:03 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
02-26 17:03 DEBUG  TaskList: New task get_metalink
02-26 17:03 DEBUG  TaskList: ### Running get_metalink...
02-26 17:03 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink) > C:\ubuntu\install
02-26 17:03 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-i386.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink, basename=ubuntu-9.10-desktop-i386.metalink, length=26455, text=None
02-26 17:03 DEBUG  downloader: download finished (read 26455 bytes)
02-26 17:03 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > C:\ubuntu\install
02-26 17:03 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
02-26 17:03 DEBUG  downloader: download finished (read 562 bytes)
02-26 17:03 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
02-26 17:03 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
02-26 17:03 DEBUG  downloader: download finished (read 189 bytes)
02-26 17:03 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
02-26 17:03 INFO   saplog: Checking block bindings..
02-26 17:03 INFO   saplog: Key verified successfully.
02-26 17:03 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

02-26 17:03 DEBUG  TaskList: ### Finished get_metalink
02-26 17:03 DEBUG  TaskList: New task download
02-26 17:03 DEBUG  TaskList: ### Running download...
02-26 17:03 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent) > C:\ubuntu\install\ubuntu-9.10-desktop-i386.iso
02-26 17:04 INFO   WindowsFrontend: Operation cancelled
02-26 17:04 DEBUG  WindowsFrontend: frontend.quit
02-26 17:04 DEBUG  WindowsFrontend: frontend.on_quit
02-26 17:04 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
02-26 17:04 DEBUG  TaskList: # Cancelling tasklist
02-26 17:04 DEBUG  TaskList: ### Finished download
02-26 17:04 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
02-26 17:04 DEBUG  root: application.on_quit
02-26 17:04 DEBUG  root: Forceful exit
02-26 17:04 INFO   root: sys.exit
02-26 17:05 INFO   root: === wubi 9.10ubuntu1 rev160 ===
02-26 17:05 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-9.10ubuntu1-rev160.log
02-26 17:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Owner\\My Documents\\Downloads\\wubi (1).exe"']
02-26 17:05 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\data
02-26 17:05 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\bin\7z.exe
02-26 17:05 DEBUG  CommonBackend: Fetching basic info...
02-26 17:05 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe
02-26 17:05 DEBUG  CommonBackend: platform=win32
02-26 17:05 DEBUG  CommonBackend: osname=nt
02-26 17:05 DEBUG  CommonBackend: language=en_US
02-26 17:05 DEBUG  CommonBackend: encoding=cp1252
02-26 17:05 DEBUG  WindowsBackend: arch=i386
02-26 17:05 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\data\isolist.ini
02-26 17:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-26 17:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-26 17:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-26 17:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-26 17:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-26 17:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-26 17:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-26 17:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-26 17:05 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-26 17:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-26 17:05 DEBUG  WindowsBackend: Fetching host info...
02-26 17:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-26 17:05 DEBUG  WindowsBackend: windows version=xp
02-26 17:05 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-26 17:05 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-26 17:05 DEBUG  WindowsBackend: windows_build=2600
02-26 17:05 DEBUG  WindowsBackend: gmt=-6
02-26 17:05 DEBUG  WindowsBackend: country=US
02-26 17:05 DEBUG  WindowsBackend: timezone=America/Chicago
02-26 17:05 DEBUG  WindowsBackend: windows_username=Owner
02-26 17:05 DEBUG  WindowsBackend: user_full_name=Owner
02-26 17:05 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
02-26 17:05 DEBUG  WindowsBackend: windows_language_code=1033
02-26 17:05 DEBUG  WindowsBackend: windows_language=English
02-26 17:05 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2400+
02-26 17:05 DEBUG  WindowsBackend: bootloader=xp
02-26 17:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 71114.0117188 mb free ntfs)
02-26 17:05 DEBUG  WindowsBackend: drive=Drive(C: hd 71114.0117188 mb free ntfs)
02-26 17:05 DEBUG  WindowsBackend: drive=Drive(D: hd 1028.88671875 mb free fat32)
02-26 17:05 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-26 17:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-26 17:05 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-26 17:05 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-26 17:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-26 17:05 DEBUG  WindowsBackend: keyboard_id=67699721
02-26 17:05 DEBUG  WindowsBackend: keyboard_layout=us
02-26 17:05 DEBUG  WindowsBackend: keyboard_variant=
02-26 17:05 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-26 17:05 DEBUG  CommonBackend: locale=en_US.UTF-8
02-26 17:05 DEBUG  WindowsBackend: total_memory_mb=479.484375
02-26 17:05 DEBUG  CommonBackend: Searching ISOs on USB devices
02-26 17:05 DEBUG  CommonBackend: Searching for local CDs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Ubuntu Netbook Remix CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Kubuntu Netbook CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 INFO   root: Already installed, running the uninstaller...
02-26 17:05 INFO   root: Running the uninstaller...
02-26 17:05 INFO   CommonBackend: This is the uninstaller running
02-26 17:05 DEBUG  WindowsFrontend: __init__...
02-26 17:05 DEBUG  WindowsFrontend: on_init...
02-26 17:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\translations, languages=['en_US', 'en']
02-26 17:05 INFO   root: Received settings
02-26 17:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\translations, languages=['en_US', 'en']
02-26 17:05 DEBUG  TaskList: # Running tasklist...
02-26 17:05 DEBUG  TaskList: ## Running Backup ISO...
02-26 17:05 DEBUG  TaskList: ## Finished Backup ISO
02-26 17:05 DEBUG  TaskList: ## Running Remove bootloader entry...
02-26 17:05 ERROR  WindowsBackend: Cannot find bcdedit
02-26 17:05 DEBUG  WindowsBackend: undo_bootini C:
02-26 17:05 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 71114.0117188 mb free ntfs)
02-26 17:05 DEBUG  WindowsBackend: undo_bootini D:
02-26 17:05 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1028.88671875 mb free fat32)
02-26 17:05 DEBUG  TaskList: ## Finished Remove bootloader entry
02-26 17:05 DEBUG  TaskList: ## Running Remove target dir...
02-26 17:05 DEBUG  CommonBackend: Deleting C:\ubuntu
02-26 17:05 DEBUG  TaskList: ## Finished Remove target dir
02-26 17:05 DEBUG  TaskList: ## Running Remove registry key...
02-26 17:05 DEBUG  TaskList: ## Finished Remove registry key
02-26 17:05 DEBUG  TaskList: # Finished tasklist
02-26 17:05 INFO   root: Almost finished uninstalling
02-26 17:05 INFO   root: Finished uninstallation
02-26 17:05 DEBUG  CommonBackend: Fetching basic info...
02-26 17:05 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe
02-26 17:05 DEBUG  CommonBackend: platform=win32
02-26 17:05 DEBUG  CommonBackend: osname=nt
02-26 17:05 DEBUG  WindowsBackend: arch=i386
02-26 17:05 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\data\isolist.ini
02-26 17:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-26 17:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-26 17:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-26 17:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-26 17:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-26 17:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-26 17:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-26 17:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-26 17:05 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-26 17:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-26 17:05 DEBUG  WindowsBackend: Fetching host info...
02-26 17:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-26 17:05 DEBUG  WindowsBackend: windows version=xp
02-26 17:05 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-26 17:05 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-26 17:05 DEBUG  WindowsBackend: windows_build=2600
02-26 17:05 DEBUG  WindowsBackend: gmt=-6
02-26 17:05 DEBUG  WindowsBackend: country=US
02-26 17:05 DEBUG  WindowsBackend: timezone=America/Chicago
02-26 17:05 DEBUG  WindowsBackend: windows_username=Owner
02-26 17:05 DEBUG  WindowsBackend: user_full_name=Owner
02-26 17:05 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
02-26 17:05 DEBUG  WindowsBackend: windows_language_code=1033
02-26 17:05 DEBUG  WindowsBackend: windows_language=English
02-26 17:05 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2400+
02-26 17:05 DEBUG  WindowsBackend: bootloader=xp
02-26 17:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 71119.5507813 mb free ntfs)
02-26 17:05 DEBUG  WindowsBackend: drive=Drive(C: hd 71119.5507813 mb free ntfs)
02-26 17:05 DEBUG  WindowsBackend: drive=Drive(D: hd 1028.88671875 mb free fat32)
02-26 17:05 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-26 17:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-26 17:05 DEBUG  WindowsBackend: uninstaller_path=None
02-26 17:05 DEBUG  WindowsBackend: previous_target_dir=None
02-26 17:05 DEBUG  WindowsBackend: previous_distro_name=None
02-26 17:05 DEBUG  WindowsBackend: keyboard_id=67699721
02-26 17:05 DEBUG  WindowsBackend: keyboard_layout=us
02-26 17:05 DEBUG  WindowsBackend: keyboard_variant=
02-26 17:05 DEBUG  WindowsBackend: total_memory_mb=479.484375
02-26 17:05 DEBUG  CommonBackend: Searching ISOs on USB devices
02-26 17:05 DEBUG  CommonBackend: Searching for local CDs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Ubuntu Netbook Remix CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Kubuntu Netbook CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-26 17:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:05 INFO   root: Running the installer...
02-26 17:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\translations, languages=['en_US', 'en']
02-26 17:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\translations, languages=['en_US', 'en']
02-26 17:06 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=diningroom
02-26 17:06 INFO   root: Received settings
02-26 17:06 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\translations, languages=['en_US', 'en']
02-26 17:06 DEBUG  TaskList: # Running tasklist...
02-26 17:06 DEBUG  TaskList: ## Running select_target_dir...
02-26 17:06 INFO   WindowsBackend: Installing into C:\ubuntu
02-26 17:06 DEBUG  TaskList: ## Finished select_target_dir
02-26 17:06 DEBUG  TaskList: ## Running create_dir_structure...
02-26 17:06 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-26 17:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-26 17:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-26 17:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-26 17:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-26 17:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-26 17:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-26 17:06 DEBUG  TaskList: ## Finished create_dir_structure
02-26 17:06 DEBUG  TaskList: ## Running uncompress_target_dir...
02-26 17:06 DEBUG  TaskList: ## Finished uncompress_target_dir
02-26 17:06 DEBUG  TaskList: ## Running create_uninstaller...
02-26 17:06 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
02-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
02-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-26 17:06 DEBUG  TaskList: ## Finished create_uninstaller
02-26 17:06 DEBUG  TaskList: ## Running copy_installation_files...
02-26 17:06 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-26 17:06 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\winboot -> C:\ubuntu\winboot
02-26 17:06 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
02-26 17:06 DEBUG  TaskList: ## Finished copy_installation_files
02-26 17:06 DEBUG  TaskList: ## Running get_iso...
02-26 17:06 DEBUG  CommonBackend: Searching for local CD
02-26 17:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp is a valid Ubuntu CD
02-26 17:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl74.tmp\casper\filesystem.squashfs
02-26 17:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 17:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 17:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 17:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 17:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-26 17:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 17:06 DEBUG  CommonBackend: Searching for local ISO
02-26 17:06 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\Owner\My Documents\Downloads\xubuntu-9.10-beta-desktop-i386.iso
02-26 17:06 DEBUG  WindowsBackend:   extracting .disk\info from C:\Documents and Settings\Owner\My Documents\Downloads\xubuntu-9.10-beta-desktop-i386.iso
02-26 17:06 DEBUG  Distro:   parsing info from str=Xubuntu 9.10 "Karmic Koala" - Beta i386 (20090929.1)
02-26 17:06 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Beta', 'version': '9.10', 'build': '20090929.1', 'codename': 'Karmic Koala', 'arch': 'i386'}
02-26 17:06 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
02-26 17:06 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
02-26 17:06 DEBUG  TaskList: New task get_metalink
02-26 17:06 DEBUG  TaskList: ### Running get_metalink...
02-26 17:06 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink) > C:\ubuntu\install
02-26 17:06 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-i386.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink, basename=ubuntu-9.10-desktop-i386.metalink, length=26455, text=None
02-26 17:06 DEBUG  downloader: download finished (read 26455 bytes)
02-26 17:06 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > C:\ubuntu\install
02-26 17:06 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
02-26 17:06 DEBUG  downloader: download finished (read 562 bytes)
02-26 17:06 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
02-26 17:06 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
02-26 17:06 DEBUG  downloader: download finished (read 189 bytes)
02-26 17:06 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
02-26 17:06 INFO   saplog: Checking block bindings..
02-26 17:06 INFO   saplog: Key verified successfully.
02-26 17:06 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

02-26 17:06 DEBUG  TaskList: ### Finished get_metalink
02-26 17:06 DEBUG  TaskList: New task download
02-26 17:06 DEBUG  TaskList: ### Running download...
02-26 17:06 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent) > C:\ubuntu\install\ubuntu-9.10-desktop-i386.iso
02-26 18:36 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


02-26 18:36 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
02-26 18:36 DEBUG  TaskList: ### Finished download
02-26 18:36 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'
02-26 18:36 DEBUG  TaskList: # Cancelling tasklist
02-26 18:36 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'
02-26 18:36 DEBUG  TaskList: # Finished tasklist
02-26 18:43 INFO   root: === wubi 9.10ubuntu1 rev160 ===
02-26 18:43 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-9.10ubuntu1-rev160.log
02-26 18:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Owner\\My Documents\\Downloads\\wubi (1).exe"']
02-26 18:43 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\data
02-26 18:43 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\bin\7z.exe
02-26 18:43 DEBUG  CommonBackend: Fetching basic info...
02-26 18:43 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe
02-26 18:43 DEBUG  CommonBackend: platform=win32
02-26 18:43 DEBUG  CommonBackend: osname=nt
02-26 18:43 DEBUG  CommonBackend: language=en_US
02-26 18:43 DEBUG  CommonBackend: encoding=cp1252
02-26 18:43 DEBUG  WindowsBackend: arch=i386
02-26 18:43 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\data\isolist.ini
02-26 18:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-26 18:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-26 18:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-26 18:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-26 18:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-26 18:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-26 18:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-26 18:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-26 18:43 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-26 18:43 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-26 18:43 DEBUG  WindowsBackend: Fetching host info...
02-26 18:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-26 18:43 DEBUG  WindowsBackend: windows version=xp
02-26 18:43 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-26 18:43 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-26 18:43 DEBUG  WindowsBackend: windows_build=2600
02-26 18:43 DEBUG  WindowsBackend: gmt=-6
02-26 18:43 DEBUG  WindowsBackend: country=US
02-26 18:43 DEBUG  WindowsBackend: timezone=America/Chicago
02-26 18:43 DEBUG  WindowsBackend: windows_username=Owner
02-26 18:43 DEBUG  WindowsBackend: user_full_name=Owner
02-26 18:43 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
02-26 18:43 DEBUG  WindowsBackend: windows_language_code=1033
02-26 18:43 DEBUG  WindowsBackend: windows_language=English
02-26 18:43 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2400+
02-26 18:43 DEBUG  WindowsBackend: bootloader=xp
02-26 18:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 71567.0507813 mb free ntfs)
02-26 18:43 DEBUG  WindowsBackend: drive=Drive(C: hd 71567.0507813 mb free ntfs)
02-26 18:43 DEBUG  WindowsBackend: drive=Drive(D: hd 1028.94921875 mb free fat32)
02-26 18:43 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-26 18:43 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-26 18:43 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-26 18:43 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-26 18:43 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-26 18:43 DEBUG  WindowsBackend: keyboard_id=67699721
02-26 18:43 DEBUG  WindowsBackend: keyboard_layout=us
02-26 18:43 DEBUG  WindowsBackend: keyboard_variant=
02-26 18:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-26 18:43 DEBUG  CommonBackend: locale=en_US.UTF-8
02-26 18:43 DEBUG  WindowsBackend: total_memory_mb=479.484375
02-26 18:43 DEBUG  CommonBackend: Searching ISOs on USB devices
02-26 18:43 DEBUG  CommonBackend: Searching for local CDs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu Netbook Remix CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu Netbook CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 INFO   root: Already installed, running the uninstaller...
02-26 18:43 INFO   root: Running the uninstaller...
02-26 18:43 INFO   CommonBackend: This is the uninstaller running
02-26 18:43 DEBUG  WindowsFrontend: __init__...
02-26 18:43 DEBUG  WindowsFrontend: on_init...
02-26 18:43 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_US', 'en']
02-26 18:43 INFO   root: Received settings
02-26 18:43 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_US', 'en']
02-26 18:43 DEBUG  TaskList: # Running tasklist...
02-26 18:43 DEBUG  TaskList: ## Running Backup ISO...
02-26 18:43 DEBUG  TaskList: ## Finished Backup ISO
02-26 18:43 DEBUG  TaskList: ## Running Remove bootloader entry...
02-26 18:43 ERROR  WindowsBackend: Cannot find bcdedit
02-26 18:43 DEBUG  WindowsBackend: undo_bootini C:
02-26 18:43 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 71567.0507813 mb free ntfs)
02-26 18:43 DEBUG  WindowsBackend: undo_bootini D:
02-26 18:43 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1028.94921875 mb free fat32)
02-26 18:43 DEBUG  TaskList: ## Finished Remove bootloader entry
02-26 18:43 DEBUG  TaskList: ## Running Remove target dir...
02-26 18:43 DEBUG  CommonBackend: Deleting C:\ubuntu
02-26 18:43 DEBUG  TaskList: ## Finished Remove target dir
02-26 18:43 DEBUG  TaskList: ## Running Remove registry key...
02-26 18:43 DEBUG  TaskList: ## Finished Remove registry key
02-26 18:43 DEBUG  TaskList: # Finished tasklist
02-26 18:43 INFO   root: Almost finished uninstalling
02-26 18:43 INFO   root: Finished uninstallation
02-26 18:43 DEBUG  CommonBackend: Fetching basic info...
02-26 18:43 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe
02-26 18:43 DEBUG  CommonBackend: platform=win32
02-26 18:43 DEBUG  CommonBackend: osname=nt
02-26 18:43 DEBUG  WindowsBackend: arch=i386
02-26 18:43 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\data\isolist.ini
02-26 18:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-26 18:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-26 18:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-26 18:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-26 18:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-26 18:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-26 18:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-26 18:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-26 18:43 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-26 18:43 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-26 18:43 DEBUG  WindowsBackend: Fetching host info...
02-26 18:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-26 18:43 DEBUG  WindowsBackend: windows version=xp
02-26 18:43 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-26 18:43 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-26 18:43 DEBUG  WindowsBackend: windows_build=2600
02-26 18:43 DEBUG  WindowsBackend: gmt=-6
02-26 18:43 DEBUG  WindowsBackend: country=US
02-26 18:43 DEBUG  WindowsBackend: timezone=America/Chicago
02-26 18:43 DEBUG  WindowsBackend: windows_username=Owner
02-26 18:43 DEBUG  WindowsBackend: user_full_name=Owner
02-26 18:43 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
02-26 18:43 DEBUG  WindowsBackend: windows_language_code=1033
02-26 18:43 DEBUG  WindowsBackend: windows_language=English
02-26 18:43 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2400+
02-26 18:43 DEBUG  WindowsBackend: bootloader=xp
02-26 18:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72105.65625 mb free ntfs)
02-26 18:43 DEBUG  WindowsBackend: drive=Drive(C: hd 72105.65625 mb free ntfs)
02-26 18:43 DEBUG  WindowsBackend: drive=Drive(D: hd 1028.9296875 mb free fat32)
02-26 18:43 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-26 18:43 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-26 18:43 DEBUG  WindowsBackend: uninstaller_path=None
02-26 18:43 DEBUG  WindowsBackend: previous_target_dir=None
02-26 18:43 DEBUG  WindowsBackend: previous_distro_name=None
02-26 18:43 DEBUG  WindowsBackend: keyboard_id=67699721
02-26 18:43 DEBUG  WindowsBackend: keyboard_layout=us
02-26 18:43 DEBUG  WindowsBackend: keyboard_variant=
02-26 18:43 DEBUG  WindowsBackend: total_memory_mb=479.484375
02-26 18:43 DEBUG  CommonBackend: Searching ISOs on USB devices
02-26 18:43 DEBUG  CommonBackend: Searching for local CDs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu Netbook Remix CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu Netbook CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 INFO   root: Running the installer...
02-26 18:43 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_US', 'en']
02-26 18:43 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_US', 'en']
02-26 18:43 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=diningroom
02-26 18:43 INFO   root: Received settings
02-26 18:43 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_US', 'en']
02-26 18:43 DEBUG  TaskList: # Running tasklist...
02-26 18:43 DEBUG  TaskList: ## Running select_target_dir...
02-26 18:43 INFO   WindowsBackend: Installing into C:\ubuntu
02-26 18:43 DEBUG  TaskList: ## Finished select_target_dir
02-26 18:43 DEBUG  TaskList: ## Running create_dir_structure...
02-26 18:43 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-26 18:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-26 18:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-26 18:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-26 18:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-26 18:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-26 18:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-26 18:43 DEBUG  TaskList: ## Finished create_dir_structure
02-26 18:43 DEBUG  TaskList: ## Running uncompress_target_dir...
02-26 18:43 DEBUG  TaskList: ## Finished uncompress_target_dir
02-26 18:43 DEBUG  TaskList: ## Running create_uninstaller...
02-26 18:43 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
02-26 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-26 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-26 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-26 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-26 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
02-26 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-26 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-26 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-26 18:43 DEBUG  TaskList: ## Finished create_uninstaller
02-26 18:43 DEBUG  TaskList: ## Running copy_installation_files...
02-26 18:43 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-26 18:43 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\winboot -> C:\ubuntu\winboot
02-26 18:43 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
02-26 18:43 DEBUG  TaskList: ## Finished copy_installation_files
02-26 18:43 DEBUG  TaskList: ## Running get_iso...
02-26 18:43 DEBUG  CommonBackend: Searching for local CD
02-26 18:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 18:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-26 18:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-26 18:43 DEBUG  CommonBackend: Searching for local ISO
02-26 18:43 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\Owner\My Documents\Downloads\xubuntu-9.10-beta-desktop-i386.iso
02-26 18:43 DEBUG  WindowsBackend:   extracting .disk\info from C:\Documents and Settings\Owner\My Documents\Downloads\xubuntu-9.10-beta-desktop-i386.iso
02-26 18:43 DEBUG  Distro:   parsing info from str=Xubuntu 9.10 "Karmic Koala" - Beta i386 (20090929.1)
02-26 18:43 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Beta', 'version': '9.10', 'build': '20090929.1', 'codename': 'Karmic Koala', 'arch': 'i386'}
02-26 18:43 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
02-26 18:43 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
02-26 18:43 DEBUG  TaskList: New task get_metalink
02-26 18:43 DEBUG  TaskList: ### Running get_metalink...
02-26 18:43 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink) > C:\ubuntu\install
02-26 18:43 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-i386.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink, basename=ubuntu-9.10-desktop-i386.metalink, length=26455, text=None
02-26 18:43 DEBUG  downloader: download finished (read 26455 bytes)
02-26 18:43 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > C:\ubuntu\install
02-26 18:43 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
02-26 18:43 DEBUG  downloader: download finished (read 562 bytes)
02-26 18:43 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
02-26 18:43 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
02-26 18:43 DEBUG  downloader: download finished (read 189 bytes)
02-26 18:43 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
02-26 18:43 INFO   saplog: Checking block bindings..
02-26 18:43 INFO   saplog: Key verified successfully.
02-26 18:43 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

02-26 18:43 DEBUG  TaskList: ### Finished get_metalink
02-26 18:43 DEBUG  TaskList: New task download
02-26 18:43 DEBUG  TaskList: ### Running download...
02-26 18:43 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent) > C:\ubuntu\install\ubuntu-9.10-desktop-i386.iso
02-26 18:51 INFO   WindowsFrontend: Operation cancelled
02-26 18:51 DEBUG  WindowsFrontend: frontend.quit
02-26 18:51 DEBUG  WindowsFrontend: frontend.on_quit
02-26 18:51 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
02-26 18:51 DEBUG  TaskList: # Cancelling tasklist
02-26 18:51 DEBUG  TaskList: ### Finished download
02-26 18:51 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
02-26 18:51 DEBUG  root: application.on_quit
02-26 18:51 DEBUG  root: Forceful exit
02-26 18:51 INFO   root: sys.exit
03-01 20:36 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-01 20:36 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-01 20:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Owner\\My Documents\\Downloads\\wubi (1).exe"']
03-01 20:36 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\data
03-01 20:36 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\bin\7z.exe
03-01 20:36 DEBUG  CommonBackend: Fetching basic info...
03-01 20:36 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe
03-01 20:36 DEBUG  CommonBackend: platform=win32
03-01 20:36 DEBUG  CommonBackend: osname=nt
03-01 20:36 DEBUG  CommonBackend: language=en_US
03-01 20:36 DEBUG  CommonBackend: encoding=cp1252
03-01 20:36 DEBUG  WindowsBackend: arch=i386
03-01 20:36 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\data\isolist.ini
03-01 20:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 20:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 20:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 20:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 20:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 20:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 20:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 20:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 20:36 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 20:36 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 20:36 DEBUG  WindowsBackend: Fetching host info...
03-01 20:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 20:36 DEBUG  WindowsBackend: windows version=xp
03-01 20:36 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-01 20:36 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-01 20:36 DEBUG  WindowsBackend: windows_build=2600
03-01 20:36 DEBUG  WindowsBackend: gmt=-6
03-01 20:36 DEBUG  WindowsBackend: country=US
03-01 20:36 DEBUG  WindowsBackend: timezone=America/Chicago
03-01 20:36 DEBUG  WindowsBackend: windows_username=Owner
03-01 20:36 DEBUG  WindowsBackend: user_full_name=Owner
03-01 20:36 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
03-01 20:36 DEBUG  WindowsBackend: windows_language_code=1033
03-01 20:36 DEBUG  WindowsBackend: windows_language=English
03-01 20:36 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2400+
03-01 20:36 DEBUG  WindowsBackend: bootloader=xp
03-01 20:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72032.3046875 mb free ntfs)
03-01 20:36 DEBUG  WindowsBackend: drive=Drive(C: hd 72032.3046875 mb free ntfs)
03-01 20:36 DEBUG  WindowsBackend: drive=Drive(D: hd 1028.9375 mb free fat32)
03-01 20:36 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-01 20:36 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-01 20:36 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-01 20:36 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-01 20:36 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-01 20:36 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 20:36 DEBUG  WindowsBackend: keyboard_layout=us
03-01 20:36 DEBUG  WindowsBackend: keyboard_variant=
03-01 20:36 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-01 20:36 DEBUG  CommonBackend: locale=en_US.UTF-8
03-01 20:36 DEBUG  WindowsBackend: total_memory_mb=479.484375
03-01 20:36 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 20:36 DEBUG  CommonBackend: Searching for local CDs
03-01 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu Netbook Remix CD
03-01 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu Netbook CD
03-01 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
03-01 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
03-01 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-01 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-01 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-01 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-01 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-01 20:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-01 20:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 20:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 20:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 20:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:36 INFO   root: Already installed, running the uninstaller...
03-01 20:36 INFO   root: Running the uninstaller...
03-01 20:36 INFO   CommonBackend: This is the uninstaller running
03-01 20:36 DEBUG  WindowsFrontend: __init__...
03-01 20:36 DEBUG  WindowsFrontend: on_init...
03-01 20:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
03-01 20:37 INFO   root: Received settings
03-01 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
03-01 20:37 DEBUG  TaskList: # Running tasklist...
03-01 20:37 DEBUG  TaskList: ## Running Backup ISO...
03-01 20:37 DEBUG  TaskList: ## Finished Backup ISO
03-01 20:37 DEBUG  TaskList: ## Running Remove bootloader entry...
03-01 20:37 ERROR  WindowsBackend: Cannot find bcdedit
03-01 20:37 DEBUG  WindowsBackend: undo_bootini C:
03-01 20:37 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 72032.3046875 mb free ntfs)
03-01 20:37 DEBUG  WindowsBackend: undo_bootini D:
03-01 20:37 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1028.9375 mb free fat32)
03-01 20:37 DEBUG  TaskList: ## Finished Remove bootloader entry
03-01 20:37 DEBUG  TaskList: ## Running Remove target dir...
03-01 20:37 DEBUG  CommonBackend: Deleting C:\ubuntu
03-01 20:37 DEBUG  TaskList: ## Finished Remove target dir
03-01 20:37 DEBUG  TaskList: ## Running Remove registry key...
03-01 20:37 DEBUG  TaskList: ## Finished Remove registry key
03-01 20:37 DEBUG  TaskList: # Finished tasklist
03-01 20:37 INFO   root: Almost finished uninstalling
03-01 20:37 INFO   root: Finished uninstallation
03-01 20:37 DEBUG  CommonBackend: Fetching basic info...
03-01 20:37 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe
03-01 20:37 DEBUG  CommonBackend: platform=win32
03-01 20:37 DEBUG  CommonBackend: osname=nt
03-01 20:37 DEBUG  WindowsBackend: arch=i386
03-01 20:37 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\data\isolist.ini
03-01 20:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 20:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 20:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 20:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 20:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 20:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 20:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 20:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 20:37 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 20:37 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 20:37 DEBUG  WindowsBackend: Fetching host info...
03-01 20:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 20:37 DEBUG  WindowsBackend: windows version=xp
03-01 20:37 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-01 20:37 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-01 20:37 DEBUG  WindowsBackend: windows_build=2600
03-01 20:37 DEBUG  WindowsBackend: gmt=-6
03-01 20:37 DEBUG  WindowsBackend: country=US
03-01 20:37 DEBUG  WindowsBackend: timezone=America/Chicago
03-01 20:37 DEBUG  WindowsBackend: windows_username=Owner
03-01 20:37 DEBUG  WindowsBackend: user_full_name=Owner
03-01 20:37 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
03-01 20:37 DEBUG  WindowsBackend: windows_language_code=1033
03-01 20:37 DEBUG  WindowsBackend: windows_language=English
03-01 20:37 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2400+
03-01 20:37 DEBUG  WindowsBackend: bootloader=xp
03-01 20:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72072.8632813 mb free ntfs)
03-01 20:37 DEBUG  WindowsBackend: drive=Drive(C: hd 72072.8632813 mb free ntfs)
03-01 20:37 DEBUG  WindowsBackend: drive=Drive(D: hd 1028.9140625 mb free fat32)
03-01 20:37 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-01 20:37 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-01 20:37 DEBUG  WindowsBackend: uninstaller_path=None
03-01 20:37 DEBUG  WindowsBackend: previous_target_dir=None
03-01 20:37 DEBUG  WindowsBackend: previous_distro_name=None
03-01 20:37 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 20:37 DEBUG  WindowsBackend: keyboard_layout=us
03-01 20:37 DEBUG  WindowsBackend: keyboard_variant=
03-01 20:37 DEBUG  WindowsBackend: total_memory_mb=479.484375
03-01 20:37 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 20:37 DEBUG  CommonBackend: Searching for local CDs
03-01 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu Netbook Remix CD
03-01 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu Netbook CD
03-01 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
03-01 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
03-01 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-01 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-01 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-01 20:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-01 20:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 20:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 20:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-01 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-01 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:37 INFO   root: Running the installer...
03-01 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
03-01 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
03-01 20:37 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=diningroom
03-01 20:37 INFO   root: Received settings
03-01 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
03-01 20:37 DEBUG  TaskList: # Running tasklist...
03-01 20:37 DEBUG  TaskList: ## Running select_target_dir...
03-01 20:37 INFO   WindowsBackend: Installing into C:\ubuntu
03-01 20:37 DEBUG  TaskList: ## Finished select_target_dir
03-01 20:37 DEBUG  TaskList: ## Running create_dir_structure...
03-01 20:37 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-01 20:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-01 20:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-01 20:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-01 20:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-01 20:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-01 20:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-01 20:37 DEBUG  TaskList: ## Finished create_dir_structure
03-01 20:37 DEBUG  TaskList: ## Running uncompress_target_dir...
03-01 20:37 DEBUG  TaskList: ## Finished uncompress_target_dir
03-01 20:37 DEBUG  TaskList: ## Running create_uninstaller...
03-01 20:37 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
03-01 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-01 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-01 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-01 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-01 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-01 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-01 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-01 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-01 20:37 DEBUG  TaskList: ## Finished create_uninstaller
03-01 20:37 DEBUG  TaskList: ## Running copy_installation_files...
03-01 20:37 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-01 20:37 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\winboot -> C:\ubuntu\winboot
03-01 20:37 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-01 20:37 DEBUG  TaskList: ## Finished copy_installation_files
03-01 20:37 DEBUG  TaskList: ## Running get_iso...
03-01 20:37 DEBUG  CommonBackend: Searching for local CD
03-01 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:37 DEBUG  CommonBackend: Searching for local ISO
03-01 20:37 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\Owner\My Documents\Downloads\xubuntu-9.10-beta-desktop-i386.iso
03-01 20:37 DEBUG  WindowsBackend:   extracting .disk\info from C:\Documents and Settings\Owner\My Documents\Downloads\xubuntu-9.10-beta-desktop-i386.iso
03-01 20:37 DEBUG  Distro:   parsing info from str=Xubuntu 9.10 "Karmic Koala" - Beta i386 (20090929.1)
03-01 20:37 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Beta', 'version': '9.10', 'build': '20090929.1', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-01 20:37 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
03-01 20:37 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-01 20:37 DEBUG  TaskList: New task get_metalink
03-01 20:37 DEBUG  TaskList: ### Running get_metalink...
03-01 20:37 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink) > C:\ubuntu\install
03-01 20:37 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-i386.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink, basename=ubuntu-9.10-desktop-i386.metalink, length=26455, text=None
03-01 20:37 DEBUG  downloader: download finished (read 26455 bytes)
03-01 20:37 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > C:\ubuntu\install
03-01 20:37 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
03-01 20:37 DEBUG  downloader: download finished (read 562 bytes)
03-01 20:37 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
03-01 20:37 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
03-01 20:37 DEBUG  downloader: download finished (read 189 bytes)
03-01 20:37 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-01 20:37 INFO   saplog: Checking block bindings..
03-01 20:37 INFO   saplog: Key verified successfully.
03-01 20:37 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

03-01 20:37 DEBUG  TaskList: ### Finished get_metalink
03-01 20:37 DEBUG  TaskList: New task download
03-01 20:37 DEBUG  TaskList: ### Running download...
03-01 20:37 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent) > C:\ubuntu\install\ubuntu-9.10-desktop-i386.iso
03-01 20:56 INFO   WindowsFrontend: Operation cancelled
03-01 20:56 DEBUG  WindowsFrontend: frontend.quit
03-01 20:56 DEBUG  WindowsFrontend: frontend.on_quit
03-01 20:56 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
03-01 20:56 DEBUG  TaskList: # Cancelling tasklist
03-01 20:56 DEBUG  TaskList: ### Finished download
03-01 20:56 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
03-01 20:56 DEBUG  root: application.on_quit
03-01 20:56 DEBUG  root: Forceful exit
03-01 20:56 INFO   root: sys.exit
03-01 20:56 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-01 20:56 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-01 20:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Owner\\My Documents\\Downloads\\wubi (1).exe"']
03-01 20:56 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\data
03-01 20:56 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\bin\7z.exe
03-01 20:56 DEBUG  CommonBackend: Fetching basic info...
03-01 20:56 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe
03-01 20:56 DEBUG  CommonBackend: platform=win32
03-01 20:56 DEBUG  CommonBackend: osname=nt
03-01 20:56 DEBUG  CommonBackend: language=en_US
03-01 20:56 DEBUG  CommonBackend: encoding=cp1252
03-01 20:56 DEBUG  WindowsBackend: arch=i386
03-01 20:56 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\data\isolist.ini
03-01 20:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 20:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 20:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 20:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 20:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 20:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 20:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 20:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 20:56 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 20:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 20:56 DEBUG  WindowsBackend: Fetching host info...
03-01 20:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 20:56 DEBUG  WindowsBackend: windows version=xp
03-01 20:56 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-01 20:56 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-01 20:56 DEBUG  WindowsBackend: windows_build=2600
03-01 20:56 DEBUG  WindowsBackend: gmt=-6
03-01 20:56 DEBUG  WindowsBackend: country=US
03-01 20:56 DEBUG  WindowsBackend: timezone=America/Chicago
03-01 20:56 DEBUG  WindowsBackend: windows_username=Owner
03-01 20:56 DEBUG  WindowsBackend: user_full_name=Owner
03-01 20:56 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
03-01 20:56 DEBUG  WindowsBackend: windows_language_code=1033
03-01 20:56 DEBUG  WindowsBackend: windows_language=English
03-01 20:56 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2400+
03-01 20:56 DEBUG  WindowsBackend: bootloader=xp
03-01 20:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 71972.7265625 mb free ntfs)
03-01 20:56 DEBUG  WindowsBackend: drive=Drive(C: hd 71972.7265625 mb free ntfs)
03-01 20:56 DEBUG  WindowsBackend: drive=Drive(D: hd 1028.9140625 mb free fat32)
03-01 20:56 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-01 20:56 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-01 20:56 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-01 20:56 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-01 20:56 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-01 20:56 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 20:56 DEBUG  WindowsBackend: keyboard_layout=us
03-01 20:56 DEBUG  WindowsBackend: keyboard_variant=
03-01 20:56 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-01 20:56 DEBUG  CommonBackend: locale=en_US.UTF-8
03-01 20:56 DEBUG  WindowsBackend: total_memory_mb=479.484375
03-01 20:56 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 20:56 DEBUG  CommonBackend: Searching for local CDs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu Netbook Remix CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu Netbook CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 INFO   root: Already installed, running the uninstaller...
03-01 20:56 INFO   root: Running the uninstaller...
03-01 20:56 INFO   CommonBackend: This is the uninstaller running
03-01 20:56 DEBUG  WindowsFrontend: __init__...
03-01 20:56 DEBUG  WindowsFrontend: on_init...
03-01 20:56 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
03-01 20:56 INFO   root: Received settings
03-01 20:56 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
03-01 20:56 DEBUG  TaskList: # Running tasklist...
03-01 20:56 DEBUG  TaskList: ## Running Backup ISO...
03-01 20:56 DEBUG  TaskList: ## Finished Backup ISO
03-01 20:56 DEBUG  TaskList: ## Running Remove bootloader entry...
03-01 20:56 ERROR  WindowsBackend: Cannot find bcdedit
03-01 20:56 DEBUG  WindowsBackend: undo_bootini C:
03-01 20:56 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 71972.7265625 mb free ntfs)
03-01 20:56 DEBUG  WindowsBackend: undo_bootini D:
03-01 20:56 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1028.9140625 mb free fat32)
03-01 20:56 DEBUG  TaskList: ## Finished Remove bootloader entry
03-01 20:56 DEBUG  TaskList: ## Running Remove target dir...
03-01 20:56 DEBUG  CommonBackend: Deleting C:\ubuntu
03-01 20:56 DEBUG  TaskList: ## Finished Remove target dir
03-01 20:56 DEBUG  TaskList: ## Running Remove registry key...
03-01 20:56 DEBUG  TaskList: ## Finished Remove registry key
03-01 20:56 DEBUG  TaskList: # Finished tasklist
03-01 20:56 INFO   root: Almost finished uninstalling
03-01 20:56 INFO   root: Finished uninstallation
03-01 20:56 DEBUG  CommonBackend: Fetching basic info...
03-01 20:56 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe
03-01 20:56 DEBUG  CommonBackend: platform=win32
03-01 20:56 DEBUG  CommonBackend: osname=nt
03-01 20:56 DEBUG  WindowsBackend: arch=i386
03-01 20:56 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\data\isolist.ini
03-01 20:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 20:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 20:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 20:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 20:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 20:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 20:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 20:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 20:56 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 20:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 20:56 DEBUG  WindowsBackend: Fetching host info...
03-01 20:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 20:56 DEBUG  WindowsBackend: windows version=xp
03-01 20:56 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-01 20:56 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-01 20:56 DEBUG  WindowsBackend: windows_build=2600
03-01 20:56 DEBUG  WindowsBackend: gmt=-6
03-01 20:56 DEBUG  WindowsBackend: country=US
03-01 20:56 DEBUG  WindowsBackend: timezone=America/Chicago
03-01 20:56 DEBUG  WindowsBackend: windows_username=Owner
03-01 20:56 DEBUG  WindowsBackend: user_full_name=Owner
03-01 20:56 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
03-01 20:56 DEBUG  WindowsBackend: windows_language_code=1033
03-01 20:56 DEBUG  WindowsBackend: windows_language=English
03-01 20:56 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2400+
03-01 20:56 DEBUG  WindowsBackend: bootloader=xp
03-01 20:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72072.7617188 mb free ntfs)
03-01 20:56 DEBUG  WindowsBackend: drive=Drive(C: hd 72072.7617188 mb free ntfs)
03-01 20:56 DEBUG  WindowsBackend: drive=Drive(D: hd 1028.9140625 mb free fat32)
03-01 20:56 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-01 20:56 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-01 20:56 DEBUG  WindowsBackend: uninstaller_path=None
03-01 20:56 DEBUG  WindowsBackend: previous_target_dir=None
03-01 20:56 DEBUG  WindowsBackend: previous_distro_name=None
03-01 20:56 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 20:56 DEBUG  WindowsBackend: keyboard_layout=us
03-01 20:56 DEBUG  WindowsBackend: keyboard_variant=
03-01 20:56 DEBUG  WindowsBackend: total_memory_mb=479.484375
03-01 20:56 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 20:56 DEBUG  CommonBackend: Searching for local CDs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu Netbook Remix CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu Netbook CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 20:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 20:56 INFO   root: Running the installer...
03-01 20:56 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
03-01 20:56 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
03-01 21:16 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=diningroom
03-01 21:16 INFO   root: Received settings
03-01 21:16 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
03-01 21:16 DEBUG  TaskList: # Running tasklist...
03-01 21:16 DEBUG  TaskList: ## Running select_target_dir...
03-01 21:16 INFO   WindowsBackend: Installing into C:\ubuntu
03-01 21:16 DEBUG  TaskList: ## Finished select_target_dir
03-01 21:16 DEBUG  TaskList: ## Running create_dir_structure...
03-01 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-01 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-01 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-01 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-01 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-01 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-01 21:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-01 21:16 DEBUG  TaskList: ## Finished create_dir_structure
03-01 21:16 DEBUG  TaskList: ## Running uncompress_target_dir...
03-01 21:16 DEBUG  TaskList: ## Finished uncompress_target_dir
03-01 21:16 DEBUG  TaskList: ## Running create_uninstaller...
03-01 21:16 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
03-01 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-01 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-01 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-01 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-01 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-01 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-01 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-01 21:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-01 21:16 DEBUG  TaskList: ## Finished create_uninstaller
03-01 21:16 DEBUG  TaskList: ## Running copy_installation_files...
03-01 21:16 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-01 21:16 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\winboot -> C:\ubuntu\winboot
03-01 21:16 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-01 21:16 DEBUG  TaskList: ## Finished copy_installation_files
03-01 21:16 DEBUG  TaskList: ## Running get_iso...
03-01 21:16 DEBUG  CommonBackend: Searching for local CD
03-01 21:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
03-01 21:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
03-01 21:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 21:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 21:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 21:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:16 DEBUG  CommonBackend: Searching for local ISO
03-01 21:16 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\Owner\My Documents\Downloads\xubuntu-9.10-beta-desktop-i386.iso
03-01 21:16 DEBUG  WindowsBackend:   extracting .disk\info from C:\Documents and Settings\Owner\My Documents\Downloads\xubuntu-9.10-beta-desktop-i386.iso
03-01 21:16 DEBUG  Distro:   parsing info from str=Xubuntu 9.10 "Karmic Koala" - Beta i386 (20090929.1)
03-01 21:16 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Beta', 'version': '9.10', 'build': '20090929.1', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-01 21:16 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
03-01 21:16 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-01 21:16 DEBUG  TaskList: New task get_metalink
03-01 21:16 DEBUG  TaskList: ### Running get_metalink...
03-01 21:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink) > C:\ubuntu\install
03-01 21:16 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-i386.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink, basename=ubuntu-9.10-desktop-i386.metalink, length=26455, text=None
03-01 21:16 DEBUG  downloader: download finished (read 26455 bytes)
03-01 21:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > C:\ubuntu\install
03-01 21:16 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
03-01 21:16 DEBUG  downloader: download finished (read 562 bytes)
03-01 21:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
03-01 21:16 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
03-01 21:16 DEBUG  downloader: download finished (read 189 bytes)
03-01 21:16 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-01 21:16 INFO   saplog: Checking block bindings..
03-01 21:16 INFO   saplog: Key verified successfully.
03-01 21:16 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

03-01 21:16 DEBUG  TaskList: ### Finished get_metalink
03-01 21:16 DEBUG  TaskList: New task download
03-01 21:16 DEBUG  TaskList: ### Running download...
03-01 21:16 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent) > C:\ubuntu\install\ubuntu-9.10-desktop-i386.iso
03-01 21:16 INFO   WindowsFrontend: Operation cancelled
03-01 21:16 DEBUG  WindowsFrontend: frontend.quit
03-01 21:16 DEBUG  WindowsFrontend: frontend.on_quit
03-01 21:16 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
03-01 21:16 DEBUG  TaskList: # Cancelling tasklist
03-01 21:16 DEBUG  TaskList: ### Finished download
03-01 21:16 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
03-01 21:16 DEBUG  root: application.on_quit
03-01 21:16 DEBUG  root: Forceful exit
03-01 21:16 INFO   root: sys.exit
03-01 21:17 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-01 21:17 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-01 21:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Owner\\My Documents\\Downloads\\wubi (1).exe"']
03-01 21:17 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\data
03-01 21:17 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\bin\7z.exe
03-01 21:17 DEBUG  CommonBackend: Fetching basic info...
03-01 21:17 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe
03-01 21:17 DEBUG  CommonBackend: platform=win32
03-01 21:17 DEBUG  CommonBackend: osname=nt
03-01 21:17 DEBUG  CommonBackend: language=en_US
03-01 21:17 DEBUG  CommonBackend: encoding=cp1252
03-01 21:17 DEBUG  WindowsBackend: arch=i386
03-01 21:17 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\data\isolist.ini
03-01 21:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 21:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 21:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 21:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 21:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 21:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 21:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 21:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 21:17 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 21:17 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 21:17 DEBUG  WindowsBackend: Fetching host info...
03-01 21:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 21:17 DEBUG  WindowsBackend: windows version=xp
03-01 21:17 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-01 21:17 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-01 21:17 DEBUG  WindowsBackend: windows_build=2600
03-01 21:17 DEBUG  WindowsBackend: gmt=-6
03-01 21:17 DEBUG  WindowsBackend: country=US
03-01 21:17 DEBUG  WindowsBackend: timezone=America/Chicago
03-01 21:17 DEBUG  WindowsBackend: windows_username=Owner
03-01 21:17 DEBUG  WindowsBackend: user_full_name=Owner
03-01 21:17 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
03-01 21:17 DEBUG  WindowsBackend: windows_language_code=1033
03-01 21:17 DEBUG  WindowsBackend: windows_language=English
03-01 21:17 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2400+
03-01 21:17 DEBUG  WindowsBackend: bootloader=xp
03-01 21:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72039.2773438 mb free ntfs)
03-01 21:17 DEBUG  WindowsBackend: drive=Drive(C: hd 72039.2773438 mb free ntfs)
03-01 21:17 DEBUG  WindowsBackend: drive=Drive(D: hd 1028.921875 mb free fat32)
03-01 21:17 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-01 21:17 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-01 21:17 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-01 21:17 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-01 21:17 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-01 21:17 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 21:17 DEBUG  WindowsBackend: keyboard_layout=us
03-01 21:17 DEBUG  WindowsBackend: keyboard_variant=
03-01 21:17 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-01 21:17 DEBUG  CommonBackend: locale=en_US.UTF-8
03-01 21:17 DEBUG  WindowsBackend: total_memory_mb=479.484375
03-01 21:17 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 21:17 DEBUG  CommonBackend: Searching for local CDs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Ubuntu Netbook Remix CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Kubuntu Netbook CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 INFO   root: Already installed, running the uninstaller...
03-01 21:17 INFO   root: Running the uninstaller...
03-01 21:17 INFO   CommonBackend: This is the uninstaller running
03-01 21:17 DEBUG  WindowsFrontend: __init__...
03-01 21:17 DEBUG  WindowsFrontend: on_init...
03-01 21:17 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\translations, languages=['en_US', 'en']
03-01 21:17 INFO   root: Received settings
03-01 21:17 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\translations, languages=['en_US', 'en']
03-01 21:17 DEBUG  TaskList: # Running tasklist...
03-01 21:17 DEBUG  TaskList: ## Running Backup ISO...
03-01 21:17 DEBUG  TaskList: ## Finished Backup ISO
03-01 21:17 DEBUG  TaskList: ## Running Remove bootloader entry...
03-01 21:17 ERROR  WindowsBackend: Cannot find bcdedit
03-01 21:17 DEBUG  WindowsBackend: undo_bootini C:
03-01 21:17 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 72039.2773438 mb free ntfs)
03-01 21:17 DEBUG  WindowsBackend: undo_bootini D:
03-01 21:17 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1028.921875 mb free fat32)
03-01 21:17 DEBUG  TaskList: ## Finished Remove bootloader entry
03-01 21:17 DEBUG  TaskList: ## Running Remove target dir...
03-01 21:17 DEBUG  CommonBackend: Deleting C:\ubuntu
03-01 21:17 DEBUG  TaskList: ## Finished Remove target dir
03-01 21:17 DEBUG  TaskList: ## Running Remove registry key...
03-01 21:17 DEBUG  TaskList: ## Finished Remove registry key
03-01 21:17 DEBUG  TaskList: # Finished tasklist
03-01 21:17 INFO   root: Almost finished uninstalling
03-01 21:17 INFO   root: Finished uninstallation
03-01 21:17 DEBUG  CommonBackend: Fetching basic info...
03-01 21:17 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe
03-01 21:17 DEBUG  CommonBackend: platform=win32
03-01 21:17 DEBUG  CommonBackend: osname=nt
03-01 21:17 DEBUG  WindowsBackend: arch=i386
03-01 21:17 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\data\isolist.ini
03-01 21:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-01 21:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-01 21:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-01 21:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-01 21:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-01 21:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-01 21:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-01 21:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-01 21:17 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-01 21:17 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-01 21:17 DEBUG  WindowsBackend: Fetching host info...
03-01 21:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-01 21:17 DEBUG  WindowsBackend: windows version=xp
03-01 21:17 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-01 21:17 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-01 21:17 DEBUG  WindowsBackend: windows_build=2600
03-01 21:17 DEBUG  WindowsBackend: gmt=-6
03-01 21:17 DEBUG  WindowsBackend: country=US
03-01 21:17 DEBUG  WindowsBackend: timezone=America/Chicago
03-01 21:17 DEBUG  WindowsBackend: windows_username=Owner
03-01 21:17 DEBUG  WindowsBackend: user_full_name=Owner
03-01 21:17 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
03-01 21:17 DEBUG  WindowsBackend: windows_language_code=1033
03-01 21:17 DEBUG  WindowsBackend: windows_language=English
03-01 21:17 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2400+
03-01 21:17 DEBUG  WindowsBackend: bootloader=xp
03-01 21:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72041.765625 mb free ntfs)
03-01 21:17 DEBUG  WindowsBackend: drive=Drive(C: hd 72041.765625 mb free ntfs)
03-01 21:17 DEBUG  WindowsBackend: drive=Drive(D: hd 1028.8984375 mb free fat32)
03-01 21:17 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-01 21:17 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-01 21:17 DEBUG  WindowsBackend: uninstaller_path=None
03-01 21:17 DEBUG  WindowsBackend: previous_target_dir=None
03-01 21:17 DEBUG  WindowsBackend: previous_distro_name=None
03-01 21:17 DEBUG  WindowsBackend: keyboard_id=67699721
03-01 21:17 DEBUG  WindowsBackend: keyboard_layout=us
03-01 21:17 DEBUG  WindowsBackend: keyboard_variant=
03-01 21:17 DEBUG  WindowsBackend: total_memory_mb=479.484375
03-01 21:17 DEBUG  CommonBackend: Searching ISOs on USB devices
03-01 21:17 DEBUG  CommonBackend: Searching for local CDs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Ubuntu Netbook Remix CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Kubuntu Netbook CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-01 21:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:17 INFO   root: Running the installer...
03-01 21:17 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\translations, languages=['en_US', 'en']
03-01 21:17 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\translations, languages=['en_US', 'en']
03-01 21:35 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=diningroom
03-01 21:35 INFO   root: Received settings
03-01 21:35 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\translations, languages=['en_US', 'en']
03-01 21:35 DEBUG  TaskList: # Running tasklist...
03-01 21:35 DEBUG  TaskList: ## Running select_target_dir...
03-01 21:35 INFO   WindowsBackend: Installing into C:\ubuntu
03-01 21:35 DEBUG  TaskList: ## Finished select_target_dir
03-01 21:35 DEBUG  TaskList: ## Running create_dir_structure...
03-01 21:35 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-01 21:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-01 21:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-01 21:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-01 21:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-01 21:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-01 21:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-01 21:35 DEBUG  TaskList: ## Finished create_dir_structure
03-01 21:35 DEBUG  TaskList: ## Running uncompress_target_dir...
03-01 21:35 DEBUG  TaskList: ## Finished uncompress_target_dir
03-01 21:35 DEBUG  TaskList: ## Running create_uninstaller...
03-01 21:35 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
03-01 21:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-01 21:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-01 21:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-01 21:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-01 21:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-01 21:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-01 21:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-01 21:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-01 21:35 DEBUG  TaskList: ## Finished create_uninstaller
03-01 21:35 DEBUG  TaskList: ## Running copy_installation_files...
03-01 21:35 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-01 21:35 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\winboot -> C:\ubuntu\winboot
03-01 21:35 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-01 21:35 DEBUG  TaskList: ## Finished copy_installation_files
03-01 21:35 DEBUG  TaskList: ## Running get_iso...
03-01 21:35 DEBUG  CommonBackend: Searching for local CD
03-01 21:35 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp is a valid Ubuntu CD
03-01 21:35 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
03-01 21:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-01 21:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-01 21:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-01 21:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-01 21:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-01 21:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-01 21:35 DEBUG  CommonBackend: Searching for local ISO
03-01 21:35 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\Owner\My Documents\Downloads\xubuntu-9.10-beta-desktop-i386.iso
03-01 21:35 DEBUG  WindowsBackend:   extracting .disk\info from C:\Documents and Settings\Owner\My Documents\Downloads\xubuntu-9.10-beta-desktop-i386.iso
03-01 21:35 DEBUG  Distro:   parsing info from str=Xubuntu 9.10 "Karmic Koala" - Beta i386 (20090929.1)
03-01 21:35 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Beta', 'version': '9.10', 'build': '20090929.1', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-01 21:35 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
03-01 21:35 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-01 21:35 DEBUG  TaskList: New task get_metalink
03-01 21:35 DEBUG  TaskList: ### Running get_metalink...
03-01 21:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink) > C:\ubuntu\install
03-01 21:35 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-i386.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink, basename=ubuntu-9.10-desktop-i386.metalink, length=26455, text=None
03-01 21:36 DEBUG  downloader: download finished (read 26455 bytes)
03-01 21:36 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > C:\ubuntu\install
03-01 21:36 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
03-01 21:36 DEBUG  downloader: download finished (read 562 bytes)
03-01 21:36 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
03-01 21:36 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
03-01 21:36 DEBUG  downloader: download finished (read 189 bytes)
03-01 21:36 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-01 21:36 INFO   saplog: Checking block bindings..
03-01 21:36 INFO   saplog: Key verified successfully.
03-01 21:36 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

03-01 21:36 DEBUG  TaskList: ### Finished get_metalink
03-01 21:36 DEBUG  TaskList: New task download
03-01 21:36 DEBUG  TaskList: ### Running download...
03-01 21:36 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent) > C:\ubuntu\install\ubuntu-9.10-desktop-i386.iso
03-01 23:16 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


03-01 23:16 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
03-01 23:16 DEBUG  TaskList: ### Finished download
03-01 23:16 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'
03-01 23:16 DEBUG  TaskList: # Cancelling tasklist
03-01 23:16 DEBUG  TaskList: # Finished tasklist
03-01 23:16 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'
03-02 17:01 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-02 17:01 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-02 17:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Owner\\My Documents\\Downloads\\wubi (1).exe"']
03-02 17:01 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\data
03-02 17:01 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\bin\7z.exe
03-02 17:01 DEBUG  CommonBackend: Fetching basic info...
03-02 17:01 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe
03-02 17:01 DEBUG  CommonBackend: platform=win32
03-02 17:01 DEBUG  CommonBackend: osname=nt
03-02 17:01 DEBUG  CommonBackend: language=en_US
03-02 17:01 DEBUG  CommonBackend: encoding=cp1252
03-02 17:01 DEBUG  WindowsBackend: arch=i386
03-02 17:01 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\data\isolist.ini
03-02 17:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-02 17:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-02 17:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-02 17:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-02 17:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-02 17:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-02 17:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-02 17:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-02 17:01 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-02 17:01 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-02 17:01 DEBUG  WindowsBackend: Fetching host info...
03-02 17:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-02 17:01 DEBUG  WindowsBackend: windows version=xp
03-02 17:01 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-02 17:01 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-02 17:01 DEBUG  WindowsBackend: windows_build=2600
03-02 17:01 DEBUG  WindowsBackend: gmt=-6
03-02 17:01 DEBUG  WindowsBackend: country=US
03-02 17:01 DEBUG  WindowsBackend: timezone=America/Chicago
03-02 17:01 DEBUG  WindowsBackend: windows_username=Owner
03-02 17:01 DEBUG  WindowsBackend: user_full_name=Owner
03-02 17:01 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
03-02 17:01 DEBUG  WindowsBackend: windows_language_code=1033
03-02 17:01 DEBUG  WindowsBackend: windows_language=English
03-02 17:01 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2400+
03-02 17:01 DEBUG  WindowsBackend: bootloader=xp
03-02 17:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 71559.296875 mb free ntfs)
03-02 17:01 DEBUG  WindowsBackend: drive=Drive(C: hd 71559.296875 mb free ntfs)
03-02 17:01 DEBUG  WindowsBackend: drive=Drive(D: hd 1028.91015625 mb free fat32)
03-02 17:01 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-02 17:01 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-02 17:01 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-02 17:01 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-02 17:01 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-02 17:01 DEBUG  WindowsBackend: keyboard_id=67699721
03-02 17:01 DEBUG  WindowsBackend: keyboard_layout=us
03-02 17:01 DEBUG  WindowsBackend: keyboard_variant=
03-02 17:01 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-02 17:01 DEBUG  CommonBackend: locale=en_US.UTF-8
03-02 17:01 DEBUG  WindowsBackend: total_memory_mb=479.484375
03-02 17:01 DEBUG  CommonBackend: Searching ISOs on USB devices
03-02 17:01 DEBUG  CommonBackend: Searching for local CDs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu Netbook Remix CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu Netbook CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 INFO   root: Already installed, running the uninstaller...
03-02 17:01 INFO   root: Running the uninstaller...
03-02 17:01 INFO   CommonBackend: This is the uninstaller running
03-02 17:01 DEBUG  WindowsFrontend: __init__...
03-02 17:01 DEBUG  WindowsFrontend: on_init...
03-02 17:01 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
03-02 17:01 INFO   root: Received settings
03-02 17:01 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
03-02 17:01 DEBUG  TaskList: # Running tasklist...
03-02 17:01 DEBUG  TaskList: ## Running Backup ISO...
03-02 17:01 DEBUG  TaskList: ## Finished Backup ISO
03-02 17:01 DEBUG  TaskList: ## Running Remove bootloader entry...
03-02 17:01 ERROR  WindowsBackend: Cannot find bcdedit
03-02 17:01 DEBUG  WindowsBackend: undo_bootini C:
03-02 17:01 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 71559.296875 mb free ntfs)
03-02 17:01 DEBUG  WindowsBackend: undo_bootini D:
03-02 17:01 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1028.91015625 mb free fat32)
03-02 17:01 DEBUG  TaskList: ## Finished Remove bootloader entry
03-02 17:01 DEBUG  TaskList: ## Running Remove target dir...
03-02 17:01 DEBUG  CommonBackend: Deleting C:\ubuntu
03-02 17:01 DEBUG  TaskList: ## Finished Remove target dir
03-02 17:01 DEBUG  TaskList: ## Running Remove registry key...
03-02 17:01 DEBUG  TaskList: ## Finished Remove registry key
03-02 17:01 DEBUG  TaskList: # Finished tasklist
03-02 17:01 INFO   root: Almost finished uninstalling
03-02 17:01 INFO   root: Finished uninstallation
03-02 17:01 DEBUG  CommonBackend: Fetching basic info...
03-02 17:01 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe
03-02 17:01 DEBUG  CommonBackend: platform=win32
03-02 17:01 DEBUG  CommonBackend: osname=nt
03-02 17:01 DEBUG  WindowsBackend: arch=i386
03-02 17:01 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\data\isolist.ini
03-02 17:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-02 17:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-02 17:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-02 17:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-02 17:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-02 17:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-02 17:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-02 17:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-02 17:01 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-02 17:01 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-02 17:01 DEBUG  WindowsBackend: Fetching host info...
03-02 17:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-02 17:01 DEBUG  WindowsBackend: windows version=xp
03-02 17:01 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-02 17:01 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-02 17:01 DEBUG  WindowsBackend: windows_build=2600
03-02 17:01 DEBUG  WindowsBackend: gmt=-6
03-02 17:01 DEBUG  WindowsBackend: country=US
03-02 17:01 DEBUG  WindowsBackend: timezone=America/Chicago
03-02 17:01 DEBUG  WindowsBackend: windows_username=Owner
03-02 17:01 DEBUG  WindowsBackend: user_full_name=Owner
03-02 17:01 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
03-02 17:01 DEBUG  WindowsBackend: windows_language_code=1033
03-02 17:01 DEBUG  WindowsBackend: windows_language=English
03-02 17:01 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) XP 2400+
03-02 17:01 DEBUG  WindowsBackend: bootloader=xp
03-02 17:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72154.4101563 mb free ntfs)
03-02 17:01 DEBUG  WindowsBackend: drive=Drive(C: hd 72154.4101563 mb free ntfs)
03-02 17:01 DEBUG  WindowsBackend: drive=Drive(D: hd 1028.890625 mb free fat32)
03-02 17:01 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
03-02 17:01 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-02 17:01 DEBUG  WindowsBackend: uninstaller_path=None
03-02 17:01 DEBUG  WindowsBackend: previous_target_dir=None
03-02 17:01 DEBUG  WindowsBackend: previous_distro_name=None
03-02 17:01 DEBUG  WindowsBackend: keyboard_id=67699721
03-02 17:01 DEBUG  WindowsBackend: keyboard_layout=us
03-02 17:01 DEBUG  WindowsBackend: keyboard_variant=
03-02 17:01 DEBUG  WindowsBackend: total_memory_mb=479.484375
03-02 17:01 DEBUG  CommonBackend: Searching ISOs on USB devices
03-02 17:01 DEBUG  CommonBackend: Searching for local CDs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu Netbook Remix CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Kubuntu Netbook CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 INFO   root: Running the installer...
03-02 17:01 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
03-02 17:01 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
03-02 17:01 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=diningroom
03-02 17:01 INFO   root: Received settings
03-02 17:01 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\translations, languages=['en_US', 'en']
03-02 17:01 DEBUG  TaskList: # Running tasklist...
03-02 17:01 DEBUG  TaskList: ## Running select_target_dir...
03-02 17:01 INFO   WindowsBackend: Installing into C:\ubuntu
03-02 17:01 DEBUG  TaskList: ## Finished select_target_dir
03-02 17:01 DEBUG  TaskList: ## Running create_dir_structure...
03-02 17:01 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-02 17:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-02 17:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-02 17:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-02 17:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-02 17:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-02 17:01 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-02 17:01 DEBUG  TaskList: ## Finished create_dir_structure
03-02 17:01 DEBUG  TaskList: ## Running uncompress_target_dir...
03-02 17:01 DEBUG  TaskList: ## Finished uncompress_target_dir
03-02 17:01 DEBUG  TaskList: ## Running create_uninstaller...
03-02 17:01 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Owner\My Documents\Downloads\wubi (1).exe -> C:\ubuntu\uninstall-wubi.exe
03-02 17:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-02 17:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-02 17:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-02 17:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-02 17:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
03-02 17:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-02 17:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-02 17:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-02 17:01 DEBUG  TaskList: ## Finished create_uninstaller
03-02 17:01 DEBUG  TaskList: ## Running copy_installation_files...
03-02 17:01 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-02 17:01 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\winboot -> C:\ubuntu\winboot
03-02 17:01 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-02 17:01 DEBUG  TaskList: ## Finished copy_installation_files
03-02 17:01 DEBUG  TaskList: ## Running get_iso...
03-02 17:01 DEBUG  CommonBackend: Searching for local CD
03-02 17:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl15.tmp\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-02 17:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-02 17:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-02 17:01 DEBUG  CommonBackend: Searching for local ISO
03-02 17:01 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\Owner\My Documents\Downloads\xubuntu-9.10-beta-desktop-i386.iso
03-02 17:01 DEBUG  WindowsBackend:   extracting .disk\info from C:\Documents and Settings\Owner\My Documents\Downloads\xubuntu-9.10-beta-desktop-i386.iso
03-02 17:01 DEBUG  Distro:   parsing info from str=Xubuntu 9.10 "Karmic Koala" - Beta i386 (20090929.1)
03-02 17:01 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Beta', 'version': '9.10', 'build': '20090929.1', 'codename': 'Karmic Koala', 'arch': 'i386'}
03-02 17:01 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
03-02 17:01 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-02 17:01 DEBUG  TaskList: New task get_metalink
03-02 17:01 DEBUG  TaskList: ### Running get_metalink...
03-02 17:01 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink) > C:\ubuntu\install
03-02 17:01 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-i386.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.metalink, basename=ubuntu-9.10-desktop-i386.metalink, length=26455, text=None
03-02 17:01 DEBUG  downloader: download finished (read 26455 bytes)
03-02 17:01 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > C:\ubuntu\install
03-02 17:01 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
03-02 17:01 DEBUG  downloader: download finished (read 562 bytes)
03-02 17:01 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
03-02 17:01 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
03-02 17:01 DEBUG  downloader: download finished (read 189 bytes)
03-02 17:01 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-02 17:01 INFO   saplog: Checking block bindings..
03-02 17:01 INFO   saplog: Key verified successfully.
03-02 17:01 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

03-02 17:01 DEBUG  TaskList: ### Finished get_metalink
03-02 17:01 DEBUG  TaskList: New task download
03-02 17:01 DEBUG  TaskList: ### Running download...
03-02 17:01 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-i386.iso.torrent) > C:\ubuntu\install\ubuntu-9.10-desktop-i386.iso
03-02 18:31 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


03-02 18:31 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
03-02 18:31 DEBUG  TaskList: ### Finished download
03-02 18:31 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'
03-02 18:31 DEBUG  TaskList: # Cancelling tasklist
03-02 18:31 DEBUG  TaskList: # Finished tasklist
03-02 18:31 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-i386.iso'



Any help is appreciated!

---

### Post by Mark Phelps on 2010-03-03
When you run the Wubi installer, are you simply double-clicking the install file? Or are you right-clicking it and selecting "Run as Administrator"?

---

### Post by budlyapi on 2010-03-03
I'm having the same wubi / install issue onto an HP Mini (Netbook, W7 Basic, 1GB RAM, 120 MB HD).

Attached is the error message I get.

Thanx,

Budly

---

### Post by sirloganthestud on 2010-03-03
I'm using XP, so I right clicked the program and clicked the "Run as.." button.  I ran it under the administrator account and unchecked the box that says "Protect my computer and data from unauthorized program activity".  I then ran the program and the download went a lot farther, but it stopped with about 15 minutes left.  Any help?

---

### Post by docguy on 2010-03-25
Has anybody resolved this problem? I've got a Win 7 box that I'm trying to install Ubuntu on and I'm getting the same error, even when I Run as an Administrator (also from the command prompt, running command prompt as administrator).

I'd like to install Ubuntu, but I don't know how to beat this error.

---

### Post by fireball961 on 2010-04-07
yes me to! i also am having issues with this install in win7! if it helps iv got Dell Inspiron 1525! I have also Ran as administrator! Below is my Log file--------------

04-02 17:41 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-02 17:41 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
04-02 17:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-02 17:41 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\data
04-02 17:41 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\bin\7z.exe
04-02 17:41 DEBUG  CommonBackend: Fetching basic info...
04-02 17:41 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-02 17:41 DEBUG  CommonBackend: platform=win32
04-02 17:41 DEBUG  CommonBackend: osname=nt
04-02 17:41 DEBUG  CommonBackend: language=en_AU
04-02 17:41 DEBUG  CommonBackend: encoding=cp1252
04-02 17:41 DEBUG  WindowsBackend: arch=amd64
04-02 17:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\data\isolist.ini
04-02 17:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-02 17:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-02 17:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-02 17:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-02 17:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-02 17:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-02 17:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-02 17:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-02 17:41 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-02 17:41 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-02 17:41 DEBUG  WindowsBackend: Fetching host info...
04-02 17:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-02 17:41 DEBUG  WindowsBackend: windows version=vista
04-02 17:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-02 17:41 DEBUG  WindowsBackend: windows_sp=None
04-02 17:41 DEBUG  WindowsBackend: windows_build=7600
04-02 17:41 DEBUG  WindowsBackend: gmt=10
04-02 17:41 DEBUG  WindowsBackend: country=AU
04-02 17:41 DEBUG  WindowsBackend: timezone=Australia/Sydney
04-02 17:41 DEBUG  WindowsBackend: windows_username=Darren
04-02 17:41 DEBUG  WindowsBackend: user_full_name=Darren
04-02 17:41 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-02 17:41 DEBUG  WindowsBackend: windows_language_code=1033
04-02 17:41 DEBUG  WindowsBackend: windows_language=English
04-02 17:41 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
04-02 17:41 DEBUG  WindowsBackend: bootloader=vista
04-02 17:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5594.94921875 mb free ntfs)
04-02 17:41 DEBUG  WindowsBackend: drive=Drive(C: hd 5594.94921875 mb free ntfs)
04-02 17:41 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-02 17:41 DEBUG  WindowsBackend: drive=Drive(E: hd 107612.382813 mb free ntfs)
04-02 17:41 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-02 17:41 DEBUG  WindowsBackend: drive=Drive(H: removable 5425.34375 mb free fat32)
04-02 17:41 DEBUG  WindowsBackend: drive=Drive(I: removable 630.140625 mb free fat)
04-02 17:41 DEBUG  WindowsBackend: uninstaller_path=None
04-02 17:41 DEBUG  WindowsBackend: previous_target_dir=None
04-02 17:41 DEBUG  WindowsBackend: previous_distro_name=None
04-02 17:41 DEBUG  WindowsBackend: keyboard_id=-268366839
04-02 17:41 DEBUG  WindowsBackend: keyboard_layout=au
04-02 17:41 DEBUG  WindowsBackend: keyboard_variant=
04-02 17:41 DEBUG  CommonBackend: python locale=('en_AU', 'cp1252')
04-02 17:41 DEBUG  CommonBackend: locale=en_AU.UTF-8
04-02 17:41 DEBUG  WindowsBackend: total_memory_mb=2038.04296875
04-02 17:41 DEBUG  CommonBackend: Searching ISOs on USB devices
04-02 17:41 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-9.10-desktop-amd64.iso
04-02 17:41 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-9.10-desktop-amd64.iso
04-02 17:41 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
04-02 17:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
04-02 17:41 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-9.10-desktop-amd64.iso
04-02 17:41 DEBUG  CommonBackend: Searching for local CDs
04-02 17:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp is a valid Ubuntu CD
04-02 17:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\casper\filesystem.squashfs
04-02 17:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp is a valid Ubuntu CD
04-02 17:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\casper\filesystem.squashfs
04-02 17:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp is a valid Ubuntu Netbook Remix CD
04-02 17:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\casper\filesystem.squashfs
04-02 17:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp is a valid Kubuntu CD
04-02 17:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\casper\filesystem.squashfs
04-02 17:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp is a valid Kubuntu CD
04-02 17:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\casper\filesystem.squashfs
04-02 17:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp is a valid Kubuntu Netbook CD
04-02 17:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\casper\filesystem.squashfs
04-02 17:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp is a valid Xubuntu CD
04-02 17:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\casper\filesystem.squashfs
04-02 17:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp is a valid Xubuntu CD
04-02 17:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\casper\filesystem.squashfs
04-02 17:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp is a valid Mythbuntu CD
04-02 17:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\casper\filesystem.squashfs
04-02 17:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp is a valid Mythbuntu CD
04-02 17:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\casper\filesystem.squashfs
04-02 17:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-02 17:41 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
04-02 17:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
04-02 17:41 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-02 17:41 INFO   root: Running the CD menu...
04-02 17:41 DEBUG  WindowsFrontend: __init__...
04-02 17:41 DEBUG  WindowsFrontend: on_init...
04-02 17:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\translations, languages=['en_AU', 'en']
04-02 17:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\translations, languages=['en_AU', 'en']
04-02 17:41 INFO   root: CD menu finished
04-02 17:41 INFO   root: Running the installer...
04-02 17:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\translations, languages=['en_AU', 'en']
04-02 17:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylC86F.tmp\translations, languages=['en_AU', 'en']
04-02 17:42 INFO   WindowsFrontend: Operation cancelled
04-02 17:42 DEBUG  WindowsFrontend: frontend.quit
04-02 17:42 DEBUG  WindowsFrontend: frontend.on_quit
04-02 17:42 DEBUG  root: application.on_quit
04-02 17:42 INFO   root: sys.exit
04-08 09:39 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-08 09:39 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
04-08 09:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-08 09:39 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\data
04-08 09:39 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\bin\7z.exe
04-08 09:39 DEBUG  CommonBackend: Fetching basic info...
04-08 09:39 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-08 09:39 DEBUG  CommonBackend: platform=win32
04-08 09:39 DEBUG  CommonBackend: osname=nt
04-08 09:39 DEBUG  CommonBackend: language=en_AU
04-08 09:39 DEBUG  CommonBackend: encoding=cp1252
04-08 09:39 DEBUG  WindowsBackend: arch=amd64
04-08 09:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\data\isolist.ini
04-08 09:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-08 09:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-08 09:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-08 09:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-08 09:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-08 09:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-08 09:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-08 09:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-08 09:39 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-08 09:39 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-08 09:39 DEBUG  WindowsBackend: Fetching host info...
04-08 09:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-08 09:39 DEBUG  WindowsBackend: windows version=vista
04-08 09:39 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-08 09:39 DEBUG  WindowsBackend: windows_sp=None
04-08 09:39 DEBUG  WindowsBackend: windows_build=7600
04-08 09:39 DEBUG  WindowsBackend: gmt=10
04-08 09:39 DEBUG  WindowsBackend: country=AU
04-08 09:39 DEBUG  WindowsBackend: timezone=Australia/Sydney
04-08 09:39 DEBUG  WindowsBackend: windows_username=Darren
04-08 09:39 DEBUG  WindowsBackend: user_full_name=Darren
04-08 09:39 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-08 09:39 DEBUG  WindowsBackend: windows_language_code=1033
04-08 09:39 DEBUG  WindowsBackend: windows_language=English
04-08 09:39 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
04-08 09:39 DEBUG  WindowsBackend: bootloader=vista
04-08 09:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5248.00390625 mb free ntfs)
04-08 09:39 DEBUG  WindowsBackend: drive=Drive(B: hd 4936.59375 mb free ntfs)
04-08 09:39 DEBUG  WindowsBackend: drive=Drive(C: hd 5248.00390625 mb free ntfs)
04-08 09:39 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-08 09:39 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-08 09:39 DEBUG  WindowsBackend: drive=Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:39 DEBUG  WindowsBackend: drive=Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:39 DEBUG  WindowsBackend: drive=Drive(H: removable 5423.125 mb free fat32)
04-08 09:39 DEBUG  WindowsBackend: drive=Drive(I: removable 630.125 mb free fat)
04-08 09:39 DEBUG  WindowsBackend: uninstaller_path=None
04-08 09:39 DEBUG  WindowsBackend: previous_target_dir=None
04-08 09:39 DEBUG  WindowsBackend: previous_distro_name=None
04-08 09:39 DEBUG  WindowsBackend: keyboard_id=-268366839
04-08 09:39 DEBUG  WindowsBackend: keyboard_layout=au
04-08 09:39 DEBUG  WindowsBackend: keyboard_variant=
04-08 09:39 DEBUG  CommonBackend: python locale=('en_AU', 'cp1252')
04-08 09:39 DEBUG  CommonBackend: locale=en_AU.UTF-8
04-08 09:39 DEBUG  WindowsBackend: total_memory_mb=2038.04296875
04-08 09:39 DEBUG  CommonBackend: Searching ISOs on USB devices
04-08 09:39 DEBUG  CommonBackend: Searching for local CDs
04-08 09:39 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:39 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:39 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
04-08 09:39 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:39 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:39 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
04-08 09:39 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:39 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:39 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:39 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:39 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp is a valid Ubuntu CD
04-08 09:39 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp is a valid Ubuntu CD
04-08 09:39 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp is a valid Ubuntu Netbook Remix CD
04-08 09:39 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp is a valid Kubuntu CD
04-08 09:39 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp is a valid Kubuntu CD
04-08 09:39 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp is a valid Kubuntu Netbook CD
04-08 09:39 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp is a valid Xubuntu CD
04-08 09:39 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp is a valid Xubuntu CD
04-08 09:39 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp is a valid Mythbuntu CD
04-08 09:39 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp is a valid Mythbuntu CD
04-08 09:39 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\casper\filesystem.squashfs
04-08 09:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 09:39 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
04-08 09:39 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
04-08 09:39 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-08 09:39 INFO   root: Running the CD menu...
04-08 09:39 DEBUG  WindowsFrontend: __init__...
04-08 09:39 DEBUG  WindowsFrontend: on_init...
04-08 09:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\translations, languages=['en_AU', 'en']
04-08 09:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\translations, languages=['en_AU', 'en']
04-08 09:39 INFO   root: CD menu finished
04-08 09:39 INFO   root: Running the installer...
04-08 09:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\translations, languages=['en_AU', 'en']
04-08 09:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\translations, languages=['en_AU', 'en']
04-08 09:40 DEBUG  WinuiInstallationPage: target_drive=B:, installation_size=3000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=darren
04-08 09:40 INFO   root: Received settings
04-08 09:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\translations, languages=['en_US', 'en']
04-08 09:40 DEBUG  TaskList: # Running tasklist...
04-08 09:40 DEBUG  TaskList: ## Running select_target_dir...
04-08 09:40 INFO   WindowsBackend: Installing into B:\ubuntu
04-08 09:40 DEBUG  TaskList: ## Finished select_target_dir
04-08 09:40 DEBUG  TaskList: ## Running create_dir_structure...
04-08 09:40 DEBUG  CommonBackend: Creating dir B:\ubuntu
04-08 09:40 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks
04-08 09:40 DEBUG  CommonBackend: Creating dir B:\ubuntu\install
04-08 09:40 DEBUG  CommonBackend: Creating dir B:\ubuntu\install\boot
04-08 09:40 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks\boot
04-08 09:40 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks\boot\grub
04-08 09:40 DEBUG  CommonBackend: Creating dir B:\ubuntu\install\boot\grub
04-08 09:40 DEBUG  TaskList: ## Finished create_dir_structure
04-08 09:40 DEBUG  TaskList: ## Running uncompress_target_dir...
04-08 09:40 DEBUG  TaskList: ## Finished uncompress_target_dir
04-08 09:40 DEBUG  TaskList: ## Running create_uninstaller...
04-08 09:40 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> B:\ubuntu\uninstall-wubi.exe
04-08 09:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString B:\ubuntu\uninstall-wubi.exe
04-08 09:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir B:\ubuntu
04-08 09:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-08 09:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon B:\ubuntu\Ubuntu.ico
04-08 09:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
04-08 09:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-08 09:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-08 09:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-08 09:40 DEBUG  TaskList: ## Finished create_uninstaller
04-08 09:40 DEBUG  TaskList: ## Running copy_installation_files...
04-08 09:40 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\data\custom-installation -> B:\ubuntu\install\custom-installation
04-08 09:40 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\winboot -> B:\ubuntu\winboot
04-08 09:40 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pylD2A.tmp\data\images\Ubuntu.ico -> B:\ubuntu\Ubuntu.ico
04-08 09:40 DEBUG  TaskList: ## Finished copy_installation_files
04-08 09:40 DEBUG  TaskList: ## Running get_iso...
04-08 09:40 DEBUG  TaskList: New task copy_file
04-08 09:40 DEBUG  TaskList: ### Running copy_file...
04-08 09:40 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
04-08 09:40 DEBUG  TaskList: # Cancelling tasklist
04-08 09:40 DEBUG  TaskList: New task check_iso
04-08 09:40 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
04-08 09:40 DEBUG  CommonBackend: Searching for local ISO
04-08 09:40 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-08 09:40 DEBUG  TaskList: New task get_metalink
04-08 09:40 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-08 09:40 DEBUG  TaskList: # Cancelling tasklist
04-08 09:40 DEBUG  TaskList: # Finished tasklist
04-08 09:41 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-08 09:41 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
04-08 09:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-08 09:41 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\data
04-08 09:41 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\bin\7z.exe
04-08 09:41 DEBUG  CommonBackend: Fetching basic info...
04-08 09:41 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-08 09:41 DEBUG  CommonBackend: platform=win32
04-08 09:41 DEBUG  CommonBackend: osname=nt
04-08 09:41 DEBUG  CommonBackend: language=en_AU
04-08 09:41 DEBUG  CommonBackend: encoding=cp1252
04-08 09:41 DEBUG  WindowsBackend: arch=amd64
04-08 09:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\data\isolist.ini
04-08 09:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-08 09:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-08 09:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-08 09:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-08 09:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-08 09:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-08 09:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-08 09:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-08 09:41 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-08 09:41 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-08 09:41 DEBUG  WindowsBackend: Fetching host info...
04-08 09:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-08 09:41 DEBUG  WindowsBackend: windows version=vista
04-08 09:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-08 09:41 DEBUG  WindowsBackend: windows_sp=None
04-08 09:41 DEBUG  WindowsBackend: windows_build=7600
04-08 09:41 DEBUG  WindowsBackend: gmt=10
04-08 09:41 DEBUG  WindowsBackend: country=AU
04-08 09:41 DEBUG  WindowsBackend: timezone=Australia/Sydney
04-08 09:41 DEBUG  WindowsBackend: windows_username=Darren
04-08 09:41 DEBUG  WindowsBackend: user_full_name=Darren
04-08 09:41 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-08 09:41 DEBUG  WindowsBackend: windows_language_code=1033
04-08 09:41 DEBUG  WindowsBackend: windows_language=English
04-08 09:41 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
04-08 09:41 DEBUG  WindowsBackend: bootloader=vista
04-08 09:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5249.0078125 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(B: hd 4905.05859375 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(C: hd 5249.0078125 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(H: removable 5423.125 mb free fat32)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(I: removable 630.125 mb free fat)
04-08 09:41 DEBUG  WindowsBackend: uninstaller_path=B:\ubuntu\uninstall-wubi.exe
04-08 09:41 DEBUG  WindowsBackend: previous_target_dir=B:\ubuntu
04-08 09:41 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-08 09:41 DEBUG  WindowsBackend: keyboard_id=-268366839
04-08 09:41 DEBUG  WindowsBackend: keyboard_layout=au
04-08 09:41 DEBUG  WindowsBackend: keyboard_variant=
04-08 09:41 DEBUG  CommonBackend: python locale=('en_AU', 'cp1252')
04-08 09:41 DEBUG  CommonBackend: locale=en_AU.UTF-8
04-08 09:41 DEBUG  WindowsBackend: total_memory_mb=2038.04296875
04-08 09:41 DEBUG  CommonBackend: Searching ISOs on USB devices
04-08 09:41 DEBUG  CommonBackend: Searching for local CDs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Ubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Ubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Ubuntu Netbook Remix CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Kubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Kubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Kubuntu Netbook CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Xubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Xubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Mythbuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Mythbuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 09:41 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
04-08 09:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
04-08 09:41 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-08 09:41 INFO   root: Running the CD menu...
04-08 09:41 DEBUG  WindowsFrontend: __init__...
04-08 09:41 DEBUG  WindowsFrontend: on_init...
04-08 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\translations, languages=['en_AU', 'en']
04-08 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\translations, languages=['en_AU', 'en']
04-08 09:41 INFO   root: CD menu finished
04-08 09:41 INFO   root: Already installed, running the uninstaller...
04-08 09:41 INFO   root: Running the uninstaller...
04-08 09:41 INFO   CommonBackend: This is the uninstaller running
04-08 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\translations, languages=['en_AU', 'en']
04-08 09:41 INFO   root: Received settings
04-08 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\translations, languages=['en_AU', 'en']
04-08 09:41 DEBUG  TaskList: # Running tasklist...
04-08 09:41 DEBUG  TaskList: ## Running Backup ISO...
04-08 09:41 DEBUG  TaskList: ## Finished Backup ISO
04-08 09:41 DEBUG  TaskList: ## Running Remove bootloader entry...
04-08 09:41 DEBUG  WindowsBackend: Could not find bcd id
04-08 09:41 DEBUG  WindowsBackend: undo_bootini B:
04-08 09:41 DEBUG  WindowsBackend: undo_configsys Drive(B: hd 4905.05859375 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: undo_bootini C:
04-08 09:41 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 5249.0078125 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: undo_bootini F:
04-08 09:41 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: undo_bootini G:
04-08 09:41 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: undo_bootini H:
04-08 09:41 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 5423.125 mb free fat32)
04-08 09:41 DEBUG  WindowsBackend: undo_bootini I:
04-08 09:41 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 630.125 mb free fat)
04-08 09:41 DEBUG  TaskList: ## Finished Remove bootloader entry
04-08 09:41 DEBUG  TaskList: ## Running Remove target dir...
04-08 09:41 DEBUG  CommonBackend: Deleting B:\ubuntu
04-08 09:41 DEBUG  TaskList: ## Finished Remove target dir
04-08 09:41 DEBUG  TaskList: ## Running Remove registry key...
04-08 09:41 DEBUG  TaskList: ## Finished Remove registry key
04-08 09:41 DEBUG  TaskList: # Finished tasklist
04-08 09:41 INFO   root: Almost finished uninstalling
04-08 09:41 INFO   root: Finished uninstallation
04-08 09:41 DEBUG  CommonBackend: Fetching basic info...
04-08 09:41 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-08 09:41 DEBUG  CommonBackend: platform=win32
04-08 09:41 DEBUG  CommonBackend: osname=nt
04-08 09:41 DEBUG  WindowsBackend: arch=amd64
04-08 09:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\data\isolist.ini
04-08 09:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-08 09:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-08 09:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-08 09:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-08 09:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-08 09:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-08 09:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-08 09:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-08 09:41 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-08 09:41 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-08 09:41 DEBUG  WindowsBackend: Fetching host info...
04-08 09:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-08 09:41 DEBUG  WindowsBackend: windows version=vista
04-08 09:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-08 09:41 DEBUG  WindowsBackend: windows_sp=None
04-08 09:41 DEBUG  WindowsBackend: windows_build=7600
04-08 09:41 DEBUG  WindowsBackend: gmt=10
04-08 09:41 DEBUG  WindowsBackend: country=AU
04-08 09:41 DEBUG  WindowsBackend: timezone=Australia/Sydney
04-08 09:41 DEBUG  WindowsBackend: windows_username=Darren
04-08 09:41 DEBUG  WindowsBackend: user_full_name=Darren
04-08 09:41 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-08 09:41 DEBUG  WindowsBackend: windows_language_code=1033
04-08 09:41 DEBUG  WindowsBackend: windows_language=English
04-08 09:41 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
04-08 09:41 DEBUG  WindowsBackend: bootloader=vista
04-08 09:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5248.98828125 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(B: hd 4936.58984375 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(C: hd 5248.98828125 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(H: removable 5423.125 mb free fat32)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(I: removable 630.125 mb free fat)
04-08 09:41 DEBUG  WindowsBackend: uninstaller_path=None
04-08 09:41 DEBUG  WindowsBackend: previous_target_dir=None
04-08 09:41 DEBUG  WindowsBackend: previous_distro_name=None
04-08 09:41 DEBUG  WindowsBackend: keyboard_id=-268366839
04-08 09:41 DEBUG  WindowsBackend: keyboard_layout=au
04-08 09:41 DEBUG  WindowsBackend: keyboard_variant=
04-08 09:41 DEBUG  WindowsBackend: total_memory_mb=2038.04296875
04-08 09:41 DEBUG  CommonBackend: Searching ISOs on USB devices
04-08 09:41 DEBUG  CommonBackend: Searching for local CDs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Ubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Ubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Ubuntu Netbook Remix CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Kubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Kubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Kubuntu Netbook CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Xubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Xubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Mythbuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp is a valid Mythbuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 09:41 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-08 09:41 INFO   root: Running the installer...
04-08 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\translations, languages=['en_AU', 'en']
04-08 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl7EA1.tmp\translations, languages=['en_AU', 'en']
04-08 09:41 INFO   WindowsFrontend: Operation cancelled
04-08 09:41 DEBUG  WindowsFrontend: frontend.quit
04-08 09:41 DEBUG  WindowsFrontend: frontend.on_quit
04-08 09:41 DEBUG  root: application.on_quit
04-08 09:41 INFO   root: sys.exit
04-08 09:41 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-08 09:41 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
04-08 09:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-08 09:41 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\data
04-08 09:41 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\bin\7z.exe
04-08 09:41 DEBUG  CommonBackend: Fetching basic info...
04-08 09:41 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-08 09:41 DEBUG  CommonBackend: platform=win32
04-08 09:41 DEBUG  CommonBackend: osname=nt
04-08 09:41 DEBUG  CommonBackend: language=en_AU
04-08 09:41 DEBUG  CommonBackend: encoding=cp1252
04-08 09:41 DEBUG  WindowsBackend: arch=amd64
04-08 09:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\data\isolist.ini
04-08 09:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-08 09:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-08 09:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-08 09:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-08 09:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-08 09:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-08 09:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-08 09:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-08 09:41 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-08 09:41 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-08 09:41 DEBUG  WindowsBackend: Fetching host info...
04-08 09:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-08 09:41 DEBUG  WindowsBackend: windows version=vista
04-08 09:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-08 09:41 DEBUG  WindowsBackend: windows_sp=None
04-08 09:41 DEBUG  WindowsBackend: windows_build=7600
04-08 09:41 DEBUG  WindowsBackend: gmt=10
04-08 09:41 DEBUG  WindowsBackend: country=AU
04-08 09:41 DEBUG  WindowsBackend: timezone=Australia/Sydney
04-08 09:41 DEBUG  WindowsBackend: windows_username=Darren
04-08 09:41 DEBUG  WindowsBackend: user_full_name=Darren
04-08 09:41 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-08 09:41 DEBUG  WindowsBackend: windows_language_code=1033
04-08 09:41 DEBUG  WindowsBackend: windows_language=English
04-08 09:41 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
04-08 09:41 DEBUG  WindowsBackend: bootloader=vista
04-08 09:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5248.27734375 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(B: hd 4947.09375 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(C: hd 5248.27734375 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(H: removable 5423.125 mb free fat32)
04-08 09:41 DEBUG  WindowsBackend: drive=Drive(I: removable 630.125 mb free fat)
04-08 09:41 DEBUG  WindowsBackend: uninstaller_path=None
04-08 09:41 DEBUG  WindowsBackend: previous_target_dir=None
04-08 09:41 DEBUG  WindowsBackend: previous_distro_name=None
04-08 09:41 DEBUG  WindowsBackend: keyboard_id=-268366839
04-08 09:41 DEBUG  WindowsBackend: keyboard_layout=au
04-08 09:41 DEBUG  WindowsBackend: keyboard_variant=
04-08 09:41 DEBUG  CommonBackend: python locale=('en_AU', 'cp1252')
04-08 09:41 DEBUG  CommonBackend: locale=en_AU.UTF-8
04-08 09:41 DEBUG  WindowsBackend: total_memory_mb=2038.04296875
04-08 09:41 DEBUG  CommonBackend: Searching ISOs on USB devices
04-08 09:41 DEBUG  CommonBackend: Searching for local CDs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:41 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp is a valid Ubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp is a valid Ubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp is a valid Ubuntu Netbook Remix CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp is a valid Kubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp is a valid Kubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp is a valid Kubuntu Netbook CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp is a valid Xubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp is a valid Xubuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp is a valid Mythbuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp is a valid Mythbuntu CD
04-08 09:41 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\casper\filesystem.squashfs
04-08 09:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 09:41 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
04-08 09:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
04-08 09:41 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-08 09:41 INFO   root: Running the CD menu...
04-08 09:41 DEBUG  WindowsFrontend: __init__...
04-08 09:41 DEBUG  WindowsFrontend: on_init...
04-08 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\translations, languages=['en_AU', 'en']
04-08 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\translations, languages=['en_AU', 'en']
04-08 09:41 INFO   root: CD menu finished
04-08 09:41 INFO   root: Running the installer...
04-08 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\translations, languages=['en_AU', 'en']
04-08 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\translations, languages=['en_AU', 'en']
04-08 09:41 DEBUG  WinuiInstallationPage: target_drive=B:, installation_size=3000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=darren
04-08 09:41 INFO   root: Received settings
04-08 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\translations, languages=['en_US', 'en']
04-08 09:41 DEBUG  TaskList: # Running tasklist...
04-08 09:41 DEBUG  TaskList: ## Running select_target_dir...
04-08 09:41 INFO   WindowsBackend: Installing into B:\ubuntu
04-08 09:41 DEBUG  TaskList: ## Finished select_target_dir
04-08 09:41 DEBUG  TaskList: ## Running create_dir_structure...
04-08 09:41 DEBUG  CommonBackend: Creating dir B:\ubuntu
04-08 09:41 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks
04-08 09:41 DEBUG  CommonBackend: Creating dir B:\ubuntu\install
04-08 09:41 DEBUG  CommonBackend: Creating dir B:\ubuntu\install\boot
04-08 09:41 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks\boot
04-08 09:41 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks\boot\grub
04-08 09:41 DEBUG  CommonBackend: Creating dir B:\ubuntu\install\boot\grub
04-08 09:41 DEBUG  TaskList: ## Finished create_dir_structure
04-08 09:41 DEBUG  TaskList: ## Running uncompress_target_dir...
04-08 09:41 DEBUG  TaskList: ## Finished uncompress_target_dir
04-08 09:41 DEBUG  TaskList: ## Running create_uninstaller...
04-08 09:41 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> B:\ubuntu\uninstall-wubi.exe
04-08 09:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString B:\ubuntu\uninstall-wubi.exe
04-08 09:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir B:\ubuntu
04-08 09:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-08 09:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon B:\ubuntu\Ubuntu.ico
04-08 09:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
04-08 09:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-08 09:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-08 09:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-08 09:41 DEBUG  TaskList: ## Finished create_uninstaller
04-08 09:41 DEBUG  TaskList: ## Running copy_installation_files...
04-08 09:41 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\data\custom-installation -> B:\ubuntu\install\custom-installation
04-08 09:41 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\winboot -> B:\ubuntu\winboot
04-08 09:41 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pylDB6.tmp\data\images\Ubuntu.ico -> B:\ubuntu\Ubuntu.ico
04-08 09:41 DEBUG  TaskList: ## Finished copy_installation_files
04-08 09:41 DEBUG  TaskList: ## Running get_iso...
04-08 09:41 DEBUG  TaskList: New task copy_file
04-08 09:41 DEBUG  TaskList: ### Running copy_file...
04-08 09:42 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
04-08 09:42 DEBUG  TaskList: # Cancelling tasklist
04-08 09:42 DEBUG  TaskList: New task check_iso
04-08 09:42 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
04-08 09:42 DEBUG  CommonBackend: Searching for local ISO
04-08 09:42 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-08 09:42 DEBUG  TaskList: New task get_metalink
04-08 09:42 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-08 09:42 DEBUG  TaskList: # Cancelling tasklist
04-08 09:42 DEBUG  TaskList: # Finished tasklist
04-08 09:44 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-08 09:44 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
04-08 09:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-08 09:44 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\data
04-08 09:44 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\bin\7z.exe
04-08 09:44 DEBUG  CommonBackend: Fetching basic info...
04-08 09:44 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-08 09:44 DEBUG  CommonBackend: platform=win32
04-08 09:44 DEBUG  CommonBackend: osname=nt
04-08 09:44 DEBUG  CommonBackend: language=en_AU
04-08 09:44 DEBUG  CommonBackend: encoding=cp1252
04-08 09:44 DEBUG  WindowsBackend: arch=amd64
04-08 09:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\data\isolist.ini
04-08 09:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-08 09:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-08 09:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-08 09:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-08 09:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-08 09:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-08 09:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-08 09:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-08 09:44 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-08 09:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-08 09:44 DEBUG  WindowsBackend: Fetching host info...
04-08 09:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-08 09:44 DEBUG  WindowsBackend: windows version=vista
04-08 09:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-08 09:44 DEBUG  WindowsBackend: windows_sp=None
04-08 09:44 DEBUG  WindowsBackend: windows_build=7600
04-08 09:44 DEBUG  WindowsBackend: gmt=10
04-08 09:44 DEBUG  WindowsBackend: country=AU
04-08 09:44 DEBUG  WindowsBackend: timezone=Australia/Sydney
04-08 09:44 DEBUG  WindowsBackend: windows_username=Darren
04-08 09:44 DEBUG  WindowsBackend: user_full_name=Darren
04-08 09:44 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-08 09:44 DEBUG  WindowsBackend: windows_language_code=1033
04-08 09:44 DEBUG  WindowsBackend: windows_language=English
04-08 09:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
04-08 09:44 DEBUG  WindowsBackend: bootloader=vista
04-08 09:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5241.375 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(B: hd 4914.87109375 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(C: hd 5241.375 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(H: removable 5423.125 mb free fat32)
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(I: removable 630.125 mb free fat)
04-08 09:44 DEBUG  WindowsBackend: uninstaller_path=B:\ubuntu\uninstall-wubi.exe
04-08 09:44 DEBUG  WindowsBackend: previous_target_dir=B:\ubuntu
04-08 09:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-08 09:44 DEBUG  WindowsBackend: keyboard_id=-268366839
04-08 09:44 DEBUG  WindowsBackend: keyboard_layout=au
04-08 09:44 DEBUG  WindowsBackend: keyboard_variant=
04-08 09:44 DEBUG  CommonBackend: python locale=('en_AU', 'cp1252')
04-08 09:44 DEBUG  CommonBackend: locale=en_AU.UTF-8
04-08 09:44 DEBUG  WindowsBackend: total_memory_mb=2038.04296875
04-08 09:44 DEBUG  CommonBackend: Searching ISOs on USB devices
04-08 09:44 DEBUG  CommonBackend: Searching for local CDs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp is a valid Ubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp is a valid Ubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp is a valid Ubuntu Netbook Remix CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp is a valid Kubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp is a valid Kubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp is a valid Kubuntu Netbook CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp is a valid Xubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp is a valid Xubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp is a valid Mythbuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp is a valid Mythbuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 09:44 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
04-08 09:44 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
04-08 09:44 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-08 09:44 INFO   root: Running the CD menu...
04-08 09:44 DEBUG  WindowsFrontend: __init__...
04-08 09:44 DEBUG  WindowsFrontend: on_init...
04-08 09:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\translations, languages=['en_AU', 'en']
04-08 09:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\translations, languages=['en_AU', 'en']
04-08 09:44 INFO   root: CD menu finished
04-08 09:44 INFO   root: Already installed, running the uninstaller...
04-08 09:44 INFO   root: Running the uninstaller...
04-08 09:44 INFO   CommonBackend: This is the uninstaller running
04-08 09:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\translations, languages=['en_AU', 'en']
04-08 09:44 INFO   root: Received settings
04-08 09:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl5698.tmp\translations, languages=['en_AU', 'en']
04-08 09:44 DEBUG  TaskList: # Running tasklist...
04-08 09:44 DEBUG  TaskList: ## Running Backup ISO...
04-08 09:44 DEBUG  TaskList: ## Finished Backup ISO
04-08 09:44 DEBUG  TaskList: ## Running Remove bootloader entry...
04-08 09:44 DEBUG  WindowsBackend: Could not find bcd id
04-08 09:44 DEBUG  WindowsBackend: undo_bootini B:
04-08 09:44 DEBUG  WindowsBackend: undo_configsys Drive(B: hd 4914.87109375 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: undo_bootini C:
04-08 09:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 5241.375 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: undo_bootini F:
04-08 09:44 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: undo_bootini G:
04-08 09:44 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: undo_bootini H:
04-08 09:44 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 5423.125 mb free fat32)
04-08 09:44 DEBUG  WindowsBackend: undo_bootini I:
04-08 09:44 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 630.125 mb free fat)
04-08 09:44 DEBUG  TaskList: ## Finished Remove bootloader entry
04-08 09:44 DEBUG  TaskList: ## Running Remove target dir...
04-08 09:44 DEBUG  CommonBackend: Deleting B:\ubuntu
04-08 09:44 ERROR  TaskList: [Errno 13] Permission denied removing B:\ubuntu\install\installation.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 313, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 13] Permission denied removing B:\ubuntu\install\installation.iso
04-08 09:44 DEBUG  TaskList: # Cancelling tasklist
04-08 09:44 DEBUG  TaskList: # Finished tasklist
04-08 09:44 ERROR  root: [Errno 13] Permission denied removing B:\ubuntu\install\installation.iso
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 143, in run_installer
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 313, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 13] Permission denied removing B:\ubuntu\install\installation.iso
04-08 09:44 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-08 09:44 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
04-08 09:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-08 09:44 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\data
04-08 09:44 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\bin\7z.exe
04-08 09:44 DEBUG  CommonBackend: Fetching basic info...
04-08 09:44 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-08 09:44 DEBUG  CommonBackend: platform=win32
04-08 09:44 DEBUG  CommonBackend: osname=nt
04-08 09:44 DEBUG  CommonBackend: language=en_AU
04-08 09:44 DEBUG  CommonBackend: encoding=cp1252
04-08 09:44 DEBUG  WindowsBackend: arch=amd64
04-08 09:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\data\isolist.ini
04-08 09:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-08 09:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-08 09:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-08 09:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-08 09:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-08 09:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-08 09:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-08 09:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-08 09:44 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-08 09:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-08 09:44 DEBUG  WindowsBackend: Fetching host info...
04-08 09:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-08 09:44 DEBUG  WindowsBackend: windows version=vista
04-08 09:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-08 09:44 DEBUG  WindowsBackend: windows_sp=None
04-08 09:44 DEBUG  WindowsBackend: windows_build=7600
04-08 09:44 DEBUG  WindowsBackend: gmt=10
04-08 09:44 DEBUG  WindowsBackend: country=AU
04-08 09:44 DEBUG  WindowsBackend: timezone=Australia/Sydney
04-08 09:44 DEBUG  WindowsBackend: windows_username=Darren
04-08 09:44 DEBUG  WindowsBackend: user_full_name=Darren
04-08 09:44 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-08 09:44 DEBUG  WindowsBackend: windows_language_code=1033
04-08 09:44 DEBUG  WindowsBackend: windows_language=English
04-08 09:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
04-08 09:44 DEBUG  WindowsBackend: bootloader=vista
04-08 09:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5240.75 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(B: hd 4914.8828125 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(C: hd 5240.75 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(H: removable 5423.125 mb free fat32)
04-08 09:44 DEBUG  WindowsBackend: drive=Drive(I: removable 630.125 mb free fat)
04-08 09:44 DEBUG  WindowsBackend: uninstaller_path=B:\ubuntu\uninstall-wubi.exe
04-08 09:44 DEBUG  WindowsBackend: previous_target_dir=B:\ubuntu
04-08 09:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-08 09:44 DEBUG  WindowsBackend: keyboard_id=-268366839
04-08 09:44 DEBUG  WindowsBackend: keyboard_layout=au
04-08 09:44 DEBUG  WindowsBackend: keyboard_variant=
04-08 09:44 DEBUG  CommonBackend: python locale=('en_AU', 'cp1252')
04-08 09:44 DEBUG  CommonBackend: locale=en_AU.UTF-8
04-08 09:44 DEBUG  WindowsBackend: total_memory_mb=2038.04296875
04-08 09:44 DEBUG  CommonBackend: Searching ISOs on USB devices
04-08 09:44 DEBUG  CommonBackend: Searching for local CDs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:44 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp is a valid Ubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp is a valid Ubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp is a valid Ubuntu Netbook Remix CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp is a valid Kubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp is a valid Kubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp is a valid Kubuntu Netbook CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp is a valid Xubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp is a valid Xubuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp is a valid Mythbuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp is a valid Mythbuntu CD
04-08 09:44 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\casper\filesystem.squashfs
04-08 09:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 09:44 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
04-08 09:44 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
04-08 09:44 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-08 09:44 INFO   root: Running the CD menu...
04-08 09:44 DEBUG  WindowsFrontend: __init__...
04-08 09:44 DEBUG  WindowsFrontend: on_init...
04-08 09:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\translations, languages=['en_AU', 'en']
04-08 09:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\translations, languages=['en_AU', 'en']
04-08 09:44 INFO   root: CD menu finished
04-08 09:44 INFO   root: Already installed, running the uninstaller...
04-08 09:44 INFO   root: Running the uninstaller...
04-08 09:44 INFO   CommonBackend: This is the uninstaller running
04-08 09:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\translations, languages=['en_AU', 'en']
04-08 09:44 INFO   root: Received settings
04-08 09:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl8C28.tmp\translations, languages=['en_AU', 'en']
04-08 09:44 DEBUG  TaskList: # Running tasklist...
04-08 09:44 DEBUG  TaskList: ## Running Backup ISO...
04-08 09:44 DEBUG  TaskList: ## Finished Backup ISO
04-08 09:44 DEBUG  TaskList: ## Running Remove bootloader entry...
04-08 09:44 DEBUG  WindowsBackend: Could not find bcd id
04-08 09:44 DEBUG  WindowsBackend: undo_bootini B:
04-08 09:44 DEBUG  WindowsBackend: undo_configsys Drive(B: hd 4914.8828125 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: undo_bootini C:
04-08 09:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 5240.75 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: undo_bootini F:
04-08 09:44 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: undo_bootini G:
04-08 09:44 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:44 DEBUG  WindowsBackend: undo_bootini H:
04-08 09:44 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 5423.125 mb free fat32)
04-08 09:44 DEBUG  WindowsBackend: undo_bootini I:
04-08 09:44 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 630.125 mb free fat)
04-08 09:44 DEBUG  TaskList: ## Finished Remove bootloader entry
04-08 09:44 DEBUG  TaskList: ## Running Remove target dir...
04-08 09:44 DEBUG  CommonBackend: Deleting B:\ubuntu
04-08 09:44 ERROR  TaskList: [Errno 13] Permission denied removing B:\ubuntu\install\installation.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 313, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 13] Permission denied removing B:\ubuntu\install\installation.iso
04-08 09:44 DEBUG  TaskList: # Cancelling tasklist
04-08 09:44 DEBUG  TaskList: # Finished tasklist
04-08 09:44 ERROR  root: [Errno 13] Permission denied removing B:\ubuntu\install\installation.iso
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 143, in run_installer
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 313, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 13] Permission denied removing B:\ubuntu\install\installation.iso
04-08 09:45 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-08 09:45 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
04-08 09:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-08 09:45 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\data
04-08 09:45 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\bin\7z.exe
04-08 09:45 DEBUG  CommonBackend: Fetching basic info...
04-08 09:45 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-08 09:45 DEBUG  CommonBackend: platform=win32
04-08 09:45 DEBUG  CommonBackend: osname=nt
04-08 09:45 DEBUG  CommonBackend: language=en_AU
04-08 09:45 DEBUG  CommonBackend: encoding=cp1252
04-08 09:45 DEBUG  WindowsBackend: arch=amd64
04-08 09:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\data\isolist.ini
04-08 09:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-08 09:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-08 09:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-08 09:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-08 09:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-08 09:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-08 09:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-08 09:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-08 09:45 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-08 09:45 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-08 09:45 DEBUG  WindowsBackend: Fetching host info...
04-08 09:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-08 09:45 DEBUG  WindowsBackend: windows version=vista
04-08 09:45 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-08 09:45 DEBUG  WindowsBackend: windows_sp=None
04-08 09:45 DEBUG  WindowsBackend: windows_build=7600
04-08 09:45 DEBUG  WindowsBackend: gmt=10
04-08 09:45 DEBUG  WindowsBackend: country=AU
04-08 09:45 DEBUG  WindowsBackend: timezone=Australia/Sydney
04-08 09:45 DEBUG  WindowsBackend: windows_username=Darren
04-08 09:45 DEBUG  WindowsBackend: user_full_name=Darren
04-08 09:45 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-08 09:45 DEBUG  WindowsBackend: windows_language_code=1033
04-08 09:45 DEBUG  WindowsBackend: windows_language=English
04-08 09:45 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
04-08 09:45 DEBUG  WindowsBackend: bootloader=vista
04-08 09:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5247.3515625 mb free ntfs)
04-08 09:45 DEBUG  WindowsBackend: drive=Drive(B: hd 4947.09375 mb free ntfs)
04-08 09:45 DEBUG  WindowsBackend: drive=Drive(C: hd 5247.3515625 mb free ntfs)
04-08 09:45 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-08 09:45 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-08 09:45 DEBUG  WindowsBackend: drive=Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:45 DEBUG  WindowsBackend: drive=Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:45 DEBUG  WindowsBackend: drive=Drive(H: removable 5423.125 mb free fat32)
04-08 09:45 DEBUG  WindowsBackend: drive=Drive(I: removable 630.125 mb free fat)
04-08 09:45 DEBUG  WindowsBackend: uninstaller_path=B:\ubuntu\uninstall-wubi.exe
04-08 09:45 DEBUG  WindowsBackend: previous_target_dir=B:\ubuntu
04-08 09:45 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-08 09:45 DEBUG  WindowsBackend: keyboard_id=-268366839
04-08 09:45 DEBUG  WindowsBackend: keyboard_layout=au
04-08 09:45 DEBUG  WindowsBackend: keyboard_variant=
04-08 09:45 DEBUG  CommonBackend: python locale=('en_AU', 'cp1252')
04-08 09:45 DEBUG  CommonBackend: locale=en_AU.UTF-8
04-08 09:45 DEBUG  WindowsBackend: total_memory_mb=2038.04296875
04-08 09:45 DEBUG  CommonBackend: Searching ISOs on USB devices
04-08 09:45 DEBUG  CommonBackend: Searching for local CDs
04-08 09:45 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:45 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:45 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
04-08 09:45 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:45 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:45 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
04-08 09:45 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:45 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:45 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:45 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:45 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp is a valid Ubuntu CD
04-08 09:45 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp is a valid Ubuntu CD
04-08 09:45 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp is a valid Ubuntu Netbook Remix CD
04-08 09:45 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp is a valid Kubuntu CD
04-08 09:45 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp is a valid Kubuntu CD
04-08 09:45 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp is a valid Kubuntu Netbook CD
04-08 09:45 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp is a valid Xubuntu CD
04-08 09:45 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp is a valid Xubuntu CD
04-08 09:45 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp is a valid Mythbuntu CD
04-08 09:45 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp is a valid Mythbuntu CD
04-08 09:45 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\casper\filesystem.squashfs
04-08 09:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 09:45 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
04-08 09:45 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
04-08 09:45 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-08 09:45 INFO   root: Running the CD menu...
04-08 09:45 DEBUG  WindowsFrontend: __init__...
04-08 09:45 DEBUG  WindowsFrontend: on_init...
04-08 09:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\translations, languages=['en_AU', 'en']
04-08 09:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\translations, languages=['en_AU', 'en']
04-08 09:45 INFO   root: CD menu finished
04-08 09:45 INFO   root: Running the installer...
04-08 09:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\translations, languages=['en_AU', 'en']
04-08 09:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl82A7.tmp\translations, languages=['en_AU', 'en']
04-08 09:45 INFO   WindowsFrontend: Operation cancelled
04-08 09:45 DEBUG  WindowsFrontend: frontend.quit
04-08 09:45 DEBUG  WindowsFrontend: frontend.on_quit
04-08 09:45 DEBUG  root: application.on_quit
04-08 09:45 INFO   root: sys.exit
04-08 09:46 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-08 09:46 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
04-08 09:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-08 09:46 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\data
04-08 09:46 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\bin\7z.exe
04-08 09:46 DEBUG  CommonBackend: Fetching basic info...
04-08 09:46 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-08 09:46 DEBUG  CommonBackend: platform=win32
04-08 09:46 DEBUG  CommonBackend: osname=nt
04-08 09:46 DEBUG  CommonBackend: language=en_AU
04-08 09:46 DEBUG  CommonBackend: encoding=cp1252
04-08 09:46 DEBUG  WindowsBackend: arch=amd64
04-08 09:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\data\isolist.ini
04-08 09:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-08 09:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-08 09:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-08 09:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-08 09:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-08 09:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-08 09:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-08 09:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-08 09:46 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-08 09:46 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-08 09:46 DEBUG  WindowsBackend: Fetching host info...
04-08 09:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-08 09:46 DEBUG  WindowsBackend: windows version=vista
04-08 09:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-08 09:46 DEBUG  WindowsBackend: windows_sp=None
04-08 09:46 DEBUG  WindowsBackend: windows_build=7600
04-08 09:46 DEBUG  WindowsBackend: gmt=10
04-08 09:46 DEBUG  WindowsBackend: country=AU
04-08 09:46 DEBUG  WindowsBackend: timezone=Australia/Sydney
04-08 09:46 DEBUG  WindowsBackend: windows_username=Darren
04-08 09:46 DEBUG  WindowsBackend: user_full_name=Darren
04-08 09:46 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-08 09:46 DEBUG  WindowsBackend: windows_language_code=1033
04-08 09:46 DEBUG  WindowsBackend: windows_language=English
04-08 09:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
04-08 09:46 DEBUG  WindowsBackend: bootloader=vista
04-08 09:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5246.703125 mb free ntfs)
04-08 09:46 DEBUG  WindowsBackend: drive=Drive(C: hd 5246.703125 mb free ntfs)
04-08 09:46 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-08 09:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-08 09:46 DEBUG  WindowsBackend: drive=Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:46 DEBUG  WindowsBackend: drive=Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:46 DEBUG  WindowsBackend: drive=Drive(H: removable 5423.125 mb free fat32)
04-08 09:46 DEBUG  WindowsBackend: drive=Drive(I: removable 630.125 mb free fat)
04-08 09:46 DEBUG  WindowsBackend: uninstaller_path=B:\ubuntu\uninstall-wubi.exe
04-08 09:46 DEBUG  WindowsBackend: previous_target_dir=B:\ubuntu
04-08 09:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-08 09:46 DEBUG  WindowsBackend: keyboard_id=-268366839
04-08 09:46 DEBUG  WindowsBackend: keyboard_layout=au
04-08 09:46 DEBUG  WindowsBackend: keyboard_variant=
04-08 09:46 DEBUG  CommonBackend: python locale=('en_AU', 'cp1252')
04-08 09:46 DEBUG  CommonBackend: locale=en_AU.UTF-8
04-08 09:46 DEBUG  WindowsBackend: total_memory_mb=2038.04296875
04-08 09:46 DEBUG  CommonBackend: Searching ISOs on USB devices
04-08 09:46 DEBUG  CommonBackend: Searching for local CDs
04-08 09:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp is a valid Ubuntu CD
04-08 09:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\casper\filesystem.squashfs
04-08 09:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp is a valid Ubuntu CD
04-08 09:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\casper\filesystem.squashfs
04-08 09:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp is a valid Ubuntu Netbook Remix CD
04-08 09:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\casper\filesystem.squashfs
04-08 09:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp is a valid Kubuntu CD
04-08 09:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\casper\filesystem.squashfs
04-08 09:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp is a valid Kubuntu CD
04-08 09:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\casper\filesystem.squashfs
04-08 09:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp is a valid Kubuntu Netbook CD
04-08 09:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\casper\filesystem.squashfs
04-08 09:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp is a valid Xubuntu CD
04-08 09:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\casper\filesystem.squashfs
04-08 09:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp is a valid Xubuntu CD
04-08 09:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\casper\filesystem.squashfs
04-08 09:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp is a valid Mythbuntu CD
04-08 09:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\casper\filesystem.squashfs
04-08 09:46 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp is a valid Mythbuntu CD
04-08 09:46 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\casper\filesystem.squashfs
04-08 09:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 09:46 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
04-08 09:46 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
04-08 09:46 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-08 09:46 INFO   root: Running the CD menu...
04-08 09:46 DEBUG  WindowsFrontend: __init__...
04-08 09:46 DEBUG  WindowsFrontend: on_init...
04-08 09:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\translations, languages=['en_AU', 'en']
04-08 09:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\translations, languages=['en_AU', 'en']
04-08 09:46 INFO   root: CD menu finished
04-08 09:46 INFO   root: Running the installer...
04-08 09:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\translations, languages=['en_AU', 'en']
04-08 09:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl8C48.tmp\translations, languages=['en_AU', 'en']
04-08 09:46 INFO   WindowsFrontend: Operation cancelled
04-08 09:46 DEBUG  WindowsFrontend: frontend.quit
04-08 09:46 DEBUG  WindowsFrontend: frontend.on_quit
04-08 09:46 DEBUG  root: application.on_quit
04-08 09:46 INFO   root: sys.exit
04-08 09:47 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-08 09:47 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
04-08 09:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-08 09:47 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\data
04-08 09:47 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\bin\7z.exe
04-08 09:47 DEBUG  CommonBackend: Fetching basic info...
04-08 09:47 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-08 09:47 DEBUG  CommonBackend: platform=win32
04-08 09:47 DEBUG  CommonBackend: osname=nt
04-08 09:47 DEBUG  CommonBackend: language=en_AU
04-08 09:47 DEBUG  CommonBackend: encoding=cp1252
04-08 09:47 DEBUG  WindowsBackend: arch=amd64
04-08 09:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\data\isolist.ini
04-08 09:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-08 09:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-08 09:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-08 09:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-08 09:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-08 09:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-08 09:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-08 09:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-08 09:47 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-08 09:47 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-08 09:47 DEBUG  WindowsBackend: Fetching host info...
04-08 09:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-08 09:47 DEBUG  WindowsBackend: windows version=vista
04-08 09:47 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-08 09:47 DEBUG  WindowsBackend: windows_sp=None
04-08 09:47 DEBUG  WindowsBackend: windows_build=7600
04-08 09:47 DEBUG  WindowsBackend: gmt=10
04-08 09:47 DEBUG  WindowsBackend: country=AU
04-08 09:47 DEBUG  WindowsBackend: timezone=Australia/Sydney
04-08 09:47 DEBUG  WindowsBackend: windows_username=Darren
04-08 09:47 DEBUG  WindowsBackend: user_full_name=Darren
04-08 09:47 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-08 09:47 DEBUG  WindowsBackend: windows_language_code=1033
04-08 09:47 DEBUG  WindowsBackend: windows_language=English
04-08 09:47 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
04-08 09:47 DEBUG  WindowsBackend: bootloader=vista
04-08 09:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5246.37890625 mb free ntfs)
04-08 09:47 DEBUG  WindowsBackend: drive=Drive(B: hd 0.0 mb free )
04-08 09:47 DEBUG  WindowsBackend: drive=Drive(C: hd 5246.37890625 mb free ntfs)
04-08 09:47 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-08 09:47 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-08 09:47 DEBUG  WindowsBackend: drive=Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:47 DEBUG  WindowsBackend: drive=Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:47 DEBUG  WindowsBackend: drive=Drive(H: removable 5423.125 mb free fat32)
04-08 09:47 DEBUG  WindowsBackend: drive=Drive(I: removable 630.125 mb free fat)
04-08 09:47 DEBUG  WindowsBackend: uninstaller_path=B:\ubuntu\uninstall-wubi.exe
04-08 09:47 DEBUG  WindowsBackend: previous_target_dir=B:\ubuntu
04-08 09:47 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-08 09:47 DEBUG  WindowsBackend: keyboard_id=-268366839
04-08 09:47 DEBUG  WindowsBackend: keyboard_layout=au
04-08 09:47 DEBUG  WindowsBackend: keyboard_variant=
04-08 09:47 DEBUG  CommonBackend: python locale=('en_AU', 'cp1252')
04-08 09:47 DEBUG  CommonBackend: locale=en_AU.UTF-8
04-08 09:47 DEBUG  WindowsBackend: total_memory_mb=2038.04296875
04-08 09:47 DEBUG  CommonBackend: Searching ISOs on USB devices
04-08 09:47 DEBUG  CommonBackend: Searching for local CDs
04-08 09:47 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:47 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:47 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
04-08 09:47 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:47 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:47 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
04-08 09:47 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:47 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:47 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:47 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:47 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp is a valid Ubuntu CD
04-08 09:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp is a valid Ubuntu CD
04-08 09:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp is a valid Ubuntu Netbook Remix CD
04-08 09:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp is a valid Kubuntu CD
04-08 09:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp is a valid Kubuntu CD
04-08 09:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp is a valid Kubuntu Netbook CD
04-08 09:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp is a valid Xubuntu CD
04-08 09:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp is a valid Xubuntu CD
04-08 09:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp is a valid Mythbuntu CD
04-08 09:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp is a valid Mythbuntu CD
04-08 09:47 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\casper\filesystem.squashfs
04-08 09:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 09:47 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
04-08 09:47 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
04-08 09:47 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-08 09:47 INFO   root: Running the CD menu...
04-08 09:47 DEBUG  WindowsFrontend: __init__...
04-08 09:47 DEBUG  WindowsFrontend: on_init...
04-08 09:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\translations, languages=['en_AU', 'en']
04-08 09:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\translations, languages=['en_AU', 'en']
04-08 09:47 INFO   root: CD menu finished
04-08 09:47 INFO   root: Running the installer...
04-08 09:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\translations, languages=['en_AU', 'en']
04-08 09:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pyl251D.tmp\translations, languages=['en_AU', 'en']
04-08 09:47 DEBUG  WindowsFrontend: frontend.on_quit
04-08 09:47 DEBUG  root: application.on_quit
04-08 09:47 INFO   root: sys.exit
04-08 09:54 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-08 09:54 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
04-08 09:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
04-08 09:54 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\data
04-08 09:54 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\bin\7z.exe
04-08 09:54 DEBUG  CommonBackend: Fetching basic info...
04-08 09:54 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-08 09:54 DEBUG  CommonBackend: platform=win32
04-08 09:54 DEBUG  CommonBackend: osname=nt
04-08 09:54 DEBUG  CommonBackend: language=en_AU
04-08 09:54 DEBUG  CommonBackend: encoding=cp1252
04-08 09:54 DEBUG  WindowsBackend: arch=amd64
04-08 09:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\data\isolist.ini
04-08 09:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-08 09:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-08 09:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-08 09:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-08 09:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-08 09:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-08 09:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-08 09:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-08 09:54 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-08 09:54 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-08 09:54 DEBUG  WindowsBackend: Fetching host info...
04-08 09:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-08 09:54 DEBUG  WindowsBackend: windows version=vista
04-08 09:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-08 09:54 DEBUG  WindowsBackend: windows_sp=None
04-08 09:54 DEBUG  WindowsBackend: windows_build=7600
04-08 09:54 DEBUG  WindowsBackend: gmt=10
04-08 09:54 DEBUG  WindowsBackend: country=AU
04-08 09:54 DEBUG  WindowsBackend: timezone=Australia/Sydney
04-08 09:54 DEBUG  WindowsBackend: windows_username=Darren
04-08 09:54 DEBUG  WindowsBackend: user_full_name=Darren
04-08 09:54 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-08 09:54 DEBUG  WindowsBackend: windows_language_code=1033
04-08 09:54 DEBUG  WindowsBackend: windows_language=English
04-08 09:54 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
04-08 09:54 DEBUG  WindowsBackend: bootloader=vista
04-08 09:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5247.76953125 mb free ntfs)
04-08 09:54 DEBUG  WindowsBackend: drive=Drive(B: hd 4947.1171875 mb free ntfs)
04-08 09:54 DEBUG  WindowsBackend: drive=Drive(C: hd 5247.76953125 mb free ntfs)
04-08 09:54 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-08 09:54 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-08 09:54 DEBUG  WindowsBackend: drive=Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:54 DEBUG  WindowsBackend: drive=Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:54 DEBUG  WindowsBackend: drive=Drive(H: removable 5423.125 mb free fat32)
04-08 09:54 DEBUG  WindowsBackend: drive=Drive(I: removable 630.125 mb free fat)
04-08 09:54 DEBUG  WindowsBackend: uninstaller_path=B:\ubuntu\uninstall-wubi.exe
04-08 09:54 DEBUG  WindowsBackend: previous_target_dir=B:\ubuntu
04-08 09:54 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-08 09:54 DEBUG  WindowsBackend: keyboard_id=-268366839
04-08 09:54 DEBUG  WindowsBackend: keyboard_layout=au
04-08 09:54 DEBUG  WindowsBackend: keyboard_variant=
04-08 09:54 DEBUG  CommonBackend: python locale=('en_AU', 'cp1252')
04-08 09:54 DEBUG  CommonBackend: locale=en_AU.UTF-8
04-08 09:54 DEBUG  WindowsBackend: total_memory_mb=2038.04296875
04-08 09:54 DEBUG  CommonBackend: Searching ISOs on USB devices
04-08 09:54 DEBUG  CommonBackend: Searching for local CDs
04-08 09:54 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:54 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:54 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
04-08 09:54 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:54 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:54 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
04-08 09:54 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:54 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:54 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:54 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:54 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp is a valid Ubuntu CD
04-08 09:54 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp is a valid Ubuntu CD
04-08 09:54 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp is a valid Ubuntu Netbook Remix CD
04-08 09:54 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp is a valid Kubuntu CD
04-08 09:54 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp is a valid Kubuntu CD
04-08 09:54 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp is a valid Kubuntu Netbook CD
04-08 09:54 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp is a valid Xubuntu CD
04-08 09:54 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp is a valid Xubuntu CD
04-08 09:54 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp is a valid Mythbuntu CD
04-08 09:54 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp is a valid Mythbuntu CD
04-08 09:54 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\casper\filesystem.squashfs
04-08 09:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 09:54 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
04-08 09:54 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
04-08 09:54 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-08 09:54 INFO   root: Running the CD menu...
04-08 09:54 DEBUG  WindowsFrontend: __init__...
04-08 09:54 DEBUG  WindowsFrontend: on_init...
04-08 09:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\translations, languages=['en_AU', 'en']
04-08 09:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\translations, languages=['en_AU', 'en']
04-08 09:54 INFO   root: CD menu finished
04-08 09:54 INFO   root: Running the installer...
04-08 09:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\translations, languages=['en_AU', 'en']
04-08 09:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\translations, languages=['en_AU', 'en']
04-08 09:54 DEBUG  WinuiInstallationPage: target_drive=B:, installation_size=3000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=darren
04-08 09:54 INFO   root: Received settings
04-08 09:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\translations, languages=['en_US', 'en']
04-08 09:54 DEBUG  TaskList: # Running tasklist...
04-08 09:54 DEBUG  TaskList: ## Running select_target_dir...
04-08 09:54 INFO   WindowsBackend: Installing into B:\ubuntu
04-08 09:54 DEBUG  TaskList: ## Finished select_target_dir
04-08 09:54 DEBUG  TaskList: ## Running create_dir_structure...
04-08 09:54 DEBUG  CommonBackend: Creating dir B:\ubuntu
04-08 09:54 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks
04-08 09:54 DEBUG  CommonBackend: Creating dir B:\ubuntu\install
04-08 09:54 DEBUG  CommonBackend: Creating dir B:\ubuntu\install\boot
04-08 09:54 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks\boot
04-08 09:54 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks\boot\grub
04-08 09:54 DEBUG  CommonBackend: Creating dir B:\ubuntu\install\boot\grub
04-08 09:54 DEBUG  TaskList: ## Finished create_dir_structure
04-08 09:54 DEBUG  TaskList: ## Running uncompress_target_dir...
04-08 09:54 DEBUG  TaskList: ## Finished uncompress_target_dir
04-08 09:54 DEBUG  TaskList: ## Running create_uninstaller...
04-08 09:54 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> B:\ubuntu\uninstall-wubi.exe
04-08 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString B:\ubuntu\uninstall-wubi.exe
04-08 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir B:\ubuntu
04-08 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-08 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon B:\ubuntu\Ubuntu.ico
04-08 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
04-08 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-08 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-08 09:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-08 09:54 DEBUG  TaskList: ## Finished create_uninstaller
04-08 09:54 DEBUG  TaskList: ## Running copy_installation_files...
04-08 09:54 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\data\custom-installation -> B:\ubuntu\install\custom-installation
04-08 09:54 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\winboot -> B:\ubuntu\winboot
04-08 09:54 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pylD49D.tmp\data\images\Ubuntu.ico -> B:\ubuntu\Ubuntu.ico
04-08 09:54 DEBUG  TaskList: ## Finished copy_installation_files
04-08 09:54 DEBUG  TaskList: ## Running get_iso...
04-08 09:54 DEBUG  TaskList: New task copy_file
04-08 09:54 DEBUG  TaskList: ### Running copy_file...
04-08 09:55 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
04-08 09:55 DEBUG  TaskList: # Cancelling tasklist
04-08 09:55 DEBUG  TaskList: New task check_iso
04-08 09:55 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
04-08 09:55 DEBUG  CommonBackend: Searching for local ISO
04-08 09:55 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-08 09:55 DEBUG  TaskList: New task get_metalink
04-08 09:55 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-08 09:55 DEBUG  TaskList: # Cancelling tasklist
04-08 09:55 DEBUG  TaskList: # Finished tasklist
04-08 09:58 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-08 09:58 DEBUG  root: Logfile is c:\users\darren\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
04-08 09:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
04-08 09:58 DEBUG  CommonBackend: data_dir=C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\data
04-08 09:58 DEBUG  WindowsBackend: 7z=C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\bin\7z.exe
04-08 09:58 DEBUG  CommonBackend: Fetching basic info...
04-08 09:58 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-08 09:58 DEBUG  CommonBackend: platform=win32
04-08 09:58 DEBUG  CommonBackend: osname=nt
04-08 09:58 DEBUG  CommonBackend: language=en_AU
04-08 09:58 DEBUG  CommonBackend: encoding=cp1252
04-08 09:58 DEBUG  WindowsBackend: arch=amd64
04-08 09:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\data\isolist.ini
04-08 09:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-08 09:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-08 09:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-08 09:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-08 09:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-08 09:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-08 09:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-08 09:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-08 09:58 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-08 09:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-08 09:58 DEBUG  WindowsBackend: Fetching host info...
04-08 09:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-08 09:58 DEBUG  WindowsBackend: windows version=vista
04-08 09:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-08 09:58 DEBUG  WindowsBackend: windows_sp=None
04-08 09:58 DEBUG  WindowsBackend: windows_build=7600
04-08 09:58 DEBUG  WindowsBackend: gmt=10
04-08 09:58 DEBUG  WindowsBackend: country=AU
04-08 09:58 DEBUG  WindowsBackend: timezone=Australia/Sydney
04-08 09:58 DEBUG  WindowsBackend: windows_username=Darren
04-08 09:58 DEBUG  WindowsBackend: user_full_name=Darren
04-08 09:58 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-08 09:58 DEBUG  WindowsBackend: windows_language_code=1033
04-08 09:58 DEBUG  WindowsBackend: windows_language=English
04-08 09:58 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
04-08 09:58 DEBUG  WindowsBackend: bootloader=vista
04-08 09:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5246.63671875 mb free ntfs)
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(B: hd 4915.58203125 mb free ntfs)
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(C: hd 5246.63671875 mb free ntfs)
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(H: removable 5423.125 mb free fat32)
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(I: removable 630.125 mb free fat)
04-08 09:58 DEBUG  WindowsBackend: uninstaller_path=B:\ubuntu\uninstall-wubi.exe
04-08 09:58 DEBUG  WindowsBackend: previous_target_dir=B:\ubuntu
04-08 09:58 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-08 09:58 DEBUG  WindowsBackend: keyboard_id=-268366839
04-08 09:58 DEBUG  WindowsBackend: keyboard_layout=au
04-08 09:58 DEBUG  WindowsBackend: keyboard_variant=
04-08 09:58 DEBUG  CommonBackend: python locale=('en_AU', 'cp1252')
04-08 09:58 DEBUG  CommonBackend: locale=en_AU.UTF-8
04-08 09:58 DEBUG  WindowsBackend: total_memory_mb=2038.04296875
04-08 09:58 DEBUG  CommonBackend: Searching ISOs on USB devices
04-08 09:58 DEBUG  CommonBackend: Searching for local CDs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Ubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Ubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Ubuntu Netbook Remix CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Kubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Kubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Kubuntu Netbook CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Xubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Xubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Mythbuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Mythbuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 09:58 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
04-08 09:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
04-08 09:58 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-08 09:58 INFO   root: Running the CD menu...
04-08 09:58 DEBUG  WindowsFrontend: __init__...
04-08 09:58 DEBUG  WindowsFrontend: on_init...
04-08 09:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\translations, languages=['en_AU', 'en']
04-08 09:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\translations, languages=['en_AU', 'en']
04-08 09:58 INFO   root: CD menu finished
04-08 09:58 INFO   root: Already installed, running the uninstaller...
04-08 09:58 INFO   root: Running the uninstaller...
04-08 09:58 INFO   CommonBackend: This is the uninstaller running
04-08 09:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\translations, languages=['en_AU', 'en']
04-08 09:58 INFO   root: Received settings
04-08 09:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\translations, languages=['en_AU', 'en']
04-08 09:58 DEBUG  TaskList: # Running tasklist...
04-08 09:58 DEBUG  TaskList: ## Running Backup ISO...
04-08 09:58 DEBUG  TaskList: ## Finished Backup ISO
04-08 09:58 DEBUG  TaskList: ## Running Remove bootloader entry...
04-08 09:58 DEBUG  WindowsBackend: Could not find bcd id
04-08 09:58 DEBUG  WindowsBackend: undo_bootini B:
04-08 09:58 DEBUG  WindowsBackend: undo_configsys Drive(B: hd 4915.58203125 mb free ntfs)
04-08 09:58 DEBUG  WindowsBackend: undo_bootini C:
04-08 09:58 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 5246.63671875 mb free ntfs)
04-08 09:58 DEBUG  WindowsBackend: undo_bootini F:
04-08 09:58 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:58 DEBUG  WindowsBackend: undo_bootini G:
04-08 09:58 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:58 DEBUG  WindowsBackend: undo_bootini H:
04-08 09:58 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 5423.125 mb free fat32)
04-08 09:58 DEBUG  WindowsBackend: undo_bootini I:
04-08 09:58 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 630.125 mb free fat)
04-08 09:58 DEBUG  TaskList: ## Finished Remove bootloader entry
04-08 09:58 DEBUG  TaskList: ## Running Remove target dir...
04-08 09:58 DEBUG  CommonBackend: Deleting B:\ubuntu
04-08 09:58 DEBUG  TaskList: ## Finished Remove target dir
04-08 09:58 DEBUG  TaskList: ## Running Remove registry key...
04-08 09:58 DEBUG  TaskList: ## Finished Remove registry key
04-08 09:58 DEBUG  TaskList: # Finished tasklist
04-08 09:58 INFO   root: Almost finished uninstalling
04-08 09:58 INFO   root: Finished uninstallation
04-08 09:58 DEBUG  CommonBackend: Fetching basic info...
04-08 09:58 DEBUG  CommonBackend: original_exe=D:\wubi.exe
04-08 09:58 DEBUG  CommonBackend: platform=win32
04-08 09:58 DEBUG  CommonBackend: osname=nt
04-08 09:58 DEBUG  WindowsBackend: arch=amd64
04-08 09:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\data\isolist.ini
04-08 09:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-08 09:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-08 09:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-08 09:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-08 09:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-08 09:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-08 09:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-08 09:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-08 09:58 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-08 09:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-08 09:58 DEBUG  WindowsBackend: Fetching host info...
04-08 09:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-08 09:58 DEBUG  WindowsBackend: windows version=vista
04-08 09:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-08 09:58 DEBUG  WindowsBackend: windows_sp=None
04-08 09:58 DEBUG  WindowsBackend: windows_build=7600
04-08 09:58 DEBUG  WindowsBackend: gmt=10
04-08 09:58 DEBUG  WindowsBackend: country=AU
04-08 09:58 DEBUG  WindowsBackend: timezone=Australia/Sydney
04-08 09:58 DEBUG  WindowsBackend: windows_username=Darren
04-08 09:58 DEBUG  WindowsBackend: user_full_name=Darren
04-08 09:58 DEBUG  WindowsBackend: user_directory=C:\Users\Darren
04-08 09:58 DEBUG  WindowsBackend: windows_language_code=1033
04-08 09:58 DEBUG  WindowsBackend: windows_language=English
04-08 09:58 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz
04-08 09:58 DEBUG  WindowsBackend: bootloader=vista
04-08 09:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5246.53125 mb free ntfs)
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(B: hd 4947.11328125 mb free ntfs)
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(C: hd 5246.53125 mb free ntfs)
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(F: hd 363336.734375 mb free ntfs)
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(G: hd 393585.167969 mb free ntfs)
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(H: removable 5423.125 mb free fat32)
04-08 09:58 DEBUG  WindowsBackend: drive=Drive(I: removable 630.125 mb free fat)
04-08 09:58 DEBUG  WindowsBackend: uninstaller_path=None
04-08 09:58 DEBUG  WindowsBackend: previous_target_dir=None
04-08 09:58 DEBUG  WindowsBackend: previous_distro_name=None
04-08 09:58 DEBUG  WindowsBackend: keyboard_id=-268366839
04-08 09:58 DEBUG  WindowsBackend: keyboard_layout=au
04-08 09:58 DEBUG  WindowsBackend: keyboard_variant=
04-08 09:58 DEBUG  WindowsBackend: total_memory_mb=2038.04296875
04-08 09:58 DEBUG  CommonBackend: Searching ISOs on USB devices
04-08 09:58 DEBUG  CommonBackend: Searching for local CDs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
04-08 09:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Ubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Ubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Ubuntu Netbook Remix CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Kubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Kubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Kubuntu Netbook CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Xubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Xubuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Mythbuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp is a valid Mythbuntu CD
04-08 09:58 DEBUG  Distro:     does not contain C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\casper\filesystem.squashfs
04-08 09:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 09:58 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-08 09:58 INFO   root: Running the installer...
04-08 09:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\translations, languages=['en_AU', 'en']
04-08 09:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\translations, languages=['en_AU', 'en']
04-08 09:59 DEBUG  WinuiInstallationPage: target_drive=B:, installation_size=3000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=darren
04-08 09:59 INFO   root: Received settings
04-08 09:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\translations, languages=['en_US', 'en']
04-08 09:59 DEBUG  TaskList: # Running tasklist...
04-08 09:59 DEBUG  TaskList: ## Running select_target_dir...
04-08 09:59 INFO   WindowsBackend: Installing into B:\ubuntu
04-08 09:59 DEBUG  TaskList: ## Finished select_target_dir
04-08 09:59 DEBUG  TaskList: ## Running create_dir_structure...
04-08 09:59 DEBUG  CommonBackend: Creating dir B:\ubuntu
04-08 09:59 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks
04-08 09:59 DEBUG  CommonBackend: Creating dir B:\ubuntu\install
04-08 09:59 DEBUG  CommonBackend: Creating dir B:\ubuntu\install\boot
04-08 09:59 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks\boot
04-08 09:59 DEBUG  CommonBackend: Creating dir B:\ubuntu\disks\boot\grub
04-08 09:59 DEBUG  CommonBackend: Creating dir B:\ubuntu\install\boot\grub
04-08 09:59 DEBUG  TaskList: ## Finished create_dir_structure
04-08 09:59 DEBUG  TaskList: ## Running uncompress_target_dir...
04-08 09:59 DEBUG  TaskList: ## Finished uncompress_target_dir
04-08 09:59 DEBUG  TaskList: ## Running create_uninstaller...
04-08 09:59 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> B:\ubuntu\uninstall-wubi.exe
04-08 09:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString B:\ubuntu\uninstall-wubi.exe
04-08 09:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir B:\ubuntu
04-08 09:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-08 09:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon B:\ubuntu\Ubuntu.ico
04-08 09:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
04-08 09:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-08 09:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-08 09:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-08 09:59 DEBUG  TaskList: ## Finished create_uninstaller
04-08 09:59 DEBUG  TaskList: ## Running copy_installation_files...
04-08 09:59 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\data\custom-installation -> B:\ubuntu\install\custom-installation
04-08 09:59 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\winboot -> B:\ubuntu\winboot
04-08 09:59 DEBUG  WindowsBackend: Copying C:\Users\Darren\AppData\Local\Temp\pylAAA1.tmp\data\images\Ubuntu.ico -> B:\ubuntu\Ubuntu.ico
04-08 09:59 DEBUG  TaskList: ## Finished copy_installation_files
04-08 09:59 DEBUG  TaskList: ## Running get_iso...
04-08 09:59 DEBUG  TaskList: New task copy_file
04-08 09:59 DEBUG  TaskList: ### Running copy_file...
04-08 09:59 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
04-08 09:59 DEBUG  TaskList: # Cancelling tasklist
04-08 09:59 DEBUG  TaskList: New task check_iso
04-08 09:59 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
04-08 09:59 DEBUG  CommonBackend: Searching for local ISO
04-08 09:59 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-08 09:59 DEBUG  TaskList: New task get_metalink
04-08 09:59 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-08 09:59 DEBUG  TaskList: # Cancelling tasklist
04-08 09:59 DEBUG  TaskList: # Finished tasklist

---

