---
title: "WUBI installation error: see ...rev160.log"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Sharpie Mustache on 2010-04-30
I downloaded WUBI to install Ubuntu 9.10, and (mostly) everything went smoothly, except at the end of the installation. After WUBI had finished downloading, an error pop-up window appeared stating that: "An error occured: Permission denied 
For more information, please see the log file: c:\docume~1\admini~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log"
(Please note that I ran WUBI as an administrator [right click, run as...])

Here's the log (put in code to look a bit neater):
```
04-21 16:55 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-21 16:55 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
04-21 16:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\HP_Administrator\\Desktop\\wubi.exe"']
04-21 16:55 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\data
04-21 16:55 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\bin\7z.exe
04-21 16:55 DEBUG  CommonBackend: Fetching basic info...
04-21 16:55 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\HP_Administrator\Desktop\wubi.exe
04-21 16:55 DEBUG  CommonBackend: platform=win32
04-21 16:55 DEBUG  CommonBackend: osname=nt
04-21 16:55 DEBUG  CommonBackend: language=en_US
04-21 16:55 DEBUG  CommonBackend: encoding=cp1252
04-21 16:55 DEBUG  WindowsBackend: arch=amd64
04-21 16:55 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\data\isolist.ini
04-21 16:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-21 16:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-21 16:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-21 16:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-21 16:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-21 16:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-21 16:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-21 16:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-21 16:55 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-21 16:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-21 16:55 DEBUG  WindowsBackend: Fetching host info...
04-21 16:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-21 16:55 DEBUG  WindowsBackend: windows version=xp
04-21 16:55 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-21 16:55 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-21 16:55 DEBUG  WindowsBackend: windows_build=2600
04-21 16:55 DEBUG  WindowsBackend: gmt=-8
04-21 16:55 DEBUG  WindowsBackend: country=US
04-21 16:55 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-21 16:55 DEBUG  WindowsBackend: windows_username=Administrator
04-21 16:55 DEBUG  WindowsBackend: user_full_name=Administrator
04-21 16:55 DEBUG  WindowsBackend: user_directory=
04-21 16:55 DEBUG  WindowsBackend: windows_language_code=1033
04-21 16:55 DEBUG  WindowsBackend: windows_language=English
04-21 16:55 DEBUG  WindowsBackend: processor_name=             Intel(R) Pentium(R) D  CPU 2.66GHz
04-21 16:55 DEBUG  WindowsBackend: bootloader=xp
04-21 16:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 142607.46875 mb free ntfs)
04-21 16:55 DEBUG  WindowsBackend: drive=Drive(C: hd 142607.46875 mb free ntfs)
04-21 16:55 DEBUG  WindowsBackend: drive=Drive(D: hd 3158.75390625 mb free fat32)
04-21 16:55 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-21 16:55 DEBUG  WindowsBackend: uninstaller_path=None
04-21 16:55 DEBUG  WindowsBackend: previous_target_dir=None
04-21 16:55 DEBUG  WindowsBackend: previous_distro_name=None
04-21 16:55 DEBUG  WindowsBackend: keyboard_id=67699721
04-21 16:55 DEBUG  WindowsBackend: keyboard_layout=us
04-21 16:55 DEBUG  WindowsBackend: keyboard_variant=
04-21 16:55 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-21 16:55 DEBUG  CommonBackend: locale=en_US.UTF-8
04-21 16:55 DEBUG  WindowsBackend: total_memory_mb=959.35546875
04-21 16:55 DEBUG  CommonBackend: Searching ISOs on USB devices
04-21 16:55 DEBUG  CommonBackend: Searching for local CDs
04-21 16:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp is a valid Ubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp is a valid Ubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp is a valid Ubuntu Netbook Remix CD
04-21 16:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp is a valid Kubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp is a valid Kubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp is a valid Kubuntu Netbook CD
04-21 16:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp is a valid Xubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp is a valid Xubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp is a valid Mythbuntu CD
04-21 16:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp is a valid Mythbuntu CD
04-21 16:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
04-21 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-21 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-21 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-21 16:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
04-21 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-21 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-21 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-21 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-21 16:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:55 INFO   root: Running the installer...
04-21 16:55 DEBUG  WindowsFrontend: __init__...
04-21 16:55 DEBUG  WindowsFrontend: on_init...
04-21 16:55 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\translations, languages=['en_US', 'en']
04-21 16:55 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\translations, languages=['en_US', 'en']
04-21 16:58 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
04-21 16:58 INFO   root: Received settings
04-21 16:58 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\translations, languages=['en_US', 'en']
04-21 16:58 DEBUG  TaskList: # Running tasklist...
04-21 16:58 DEBUG  TaskList: ## Running select_target_dir...
04-21 16:58 INFO   WindowsBackend: Installing into C:\ubuntu
04-21 16:58 DEBUG  TaskList: ## Finished select_target_dir
04-21 16:58 DEBUG  TaskList: ## Running create_dir_structure...
04-21 16:58 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-21 16:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-21 16:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-21 16:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-21 16:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-21 16:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-21 16:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-21 16:58 DEBUG  TaskList: ## Finished create_dir_structure
04-21 16:58 DEBUG  TaskList: ## Running uncompress_target_dir...
04-21 16:58 DEBUG  TaskList: ## Finished uncompress_target_dir
04-21 16:58 DEBUG  TaskList: ## Running create_uninstaller...
04-21 16:58 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\HP_Administrator\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-21 16:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-21 16:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-21 16:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-21 16:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-21 16:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
04-21 16:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-21 16:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
04-21 16:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
04-21 16:58 DEBUG  TaskList: ## Finished create_uninstaller
04-21 16:58 DEBUG  TaskList: ## Running copy_installation_files...
04-21 16:58 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-21 16:58 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\winboot -> C:\ubuntu\winboot
04-21 16:58 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-21 16:58 DEBUG  TaskList: ## Finished copy_installation_files
04-21 16:58 DEBUG  TaskList: ## Running get_iso...
04-21 16:58 DEBUG  CommonBackend: Searching for local CD
04-21 16:58 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp is a valid Ubuntu CD
04-21 16:58 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylD7.tmp\casper\filesystem.squashfs
04-21 16:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-21 16:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-21 16:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:58 DEBUG  CommonBackend: Searching for local ISO
04-21 16:58 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-21 16:58 DEBUG  TaskList: New task get_metalink
04-21 16:58 DEBUG  TaskList: ### Running get_metalink...
04-21 16:58 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink > C:\ubuntu\install
04-21 16:58 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
04-21 16:59 DEBUG  downloader: download finished (read 26651 bytes)
04-21 16:59 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink > C:\ubuntu\install
04-21 16:59 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
04-21 16:59 DEBUG  downloader: download finished (read 562 bytes)
04-21 16:59 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg > C:\ubuntu\install
04-21 16:59 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
04-21 16:59 DEBUG  downloader: download finished (read 189 bytes)
04-21 16:59 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-21 16:59 INFO   saplog: Checking block bindings..
04-21 16:59 INFO   saplog: Key verified successfully.
04-21 16:59 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

04-21 16:59 DEBUG  TaskList: ### Finished get_metalink
04-21 16:59 DEBUG  TaskList: New task download
04-21 16:59 DEBUG  TaskList: ### Running download...
04-21 16:59 DEBUG  btdownloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
04-21 16:59 INFO   WindowsFrontend: Operation cancelled
04-21 16:59 DEBUG  WindowsFrontend: frontend.quit
04-21 16:59 DEBUG  WindowsFrontend: frontend.on_quit
04-21 16:59 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
04-21 16:59 DEBUG  TaskList: # Cancelling tasklist
04-21 16:59 DEBUG  TaskList: ### Finished download
04-21 16:59 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
04-21 16:59 DEBUG  root: application.on_quit
04-21 16:59 DEBUG  root: Forceful exit
04-21 16:59 INFO   root: sys.exit
04-21 16:59 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-21 16:59 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
04-21 16:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\HP_Administrator\\Desktop\\wubi.exe"']
04-21 16:59 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\data
04-21 16:59 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\bin\7z.exe
04-21 16:59 DEBUG  CommonBackend: Fetching basic info...
04-21 16:59 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\HP_Administrator\Desktop\wubi.exe
04-21 16:59 DEBUG  CommonBackend: platform=win32
04-21 16:59 DEBUG  CommonBackend: osname=nt
04-21 16:59 DEBUG  CommonBackend: language=en_US
04-21 16:59 DEBUG  CommonBackend: encoding=cp1252
04-21 16:59 DEBUG  WindowsBackend: arch=amd64
04-21 16:59 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\data\isolist.ini
04-21 16:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-21 16:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-21 16:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-21 16:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-21 16:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-21 16:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-21 16:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-21 16:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-21 16:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-21 16:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-21 16:59 DEBUG  WindowsBackend: Fetching host info...
04-21 16:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-21 16:59 DEBUG  WindowsBackend: windows version=xp
04-21 16:59 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-21 16:59 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-21 16:59 DEBUG  WindowsBackend: windows_build=2600
04-21 16:59 DEBUG  WindowsBackend: gmt=-8
04-21 16:59 DEBUG  WindowsBackend: country=US
04-21 16:59 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-21 16:59 DEBUG  WindowsBackend: windows_username=Administrator
04-21 16:59 DEBUG  WindowsBackend: user_full_name=Administrator
04-21 16:59 DEBUG  WindowsBackend: user_directory=
04-21 16:59 DEBUG  WindowsBackend: windows_language_code=1033
04-21 16:59 DEBUG  WindowsBackend: windows_language=English
04-21 16:59 DEBUG  WindowsBackend: processor_name=             Intel(R) Pentium(R) D  CPU 2.66GHz
04-21 16:59 DEBUG  WindowsBackend: bootloader=xp
04-21 16:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 142606.15625 mb free ntfs)
04-21 16:59 DEBUG  WindowsBackend: drive=Drive(C: hd 142606.15625 mb free ntfs)
04-21 16:59 DEBUG  WindowsBackend: drive=Drive(D: hd 3158.75390625 mb free fat32)
04-21 16:59 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-21 16:59 DEBUG  WindowsBackend: uninstaller_path=None
04-21 16:59 DEBUG  WindowsBackend: previous_target_dir=None
04-21 16:59 DEBUG  WindowsBackend: previous_distro_name=None
04-21 16:59 DEBUG  WindowsBackend: keyboard_id=67699721
04-21 16:59 DEBUG  WindowsBackend: keyboard_layout=us
04-21 16:59 DEBUG  WindowsBackend: keyboard_variant=
04-21 16:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-21 16:59 DEBUG  CommonBackend: locale=en_US.UTF-8
04-21 16:59 DEBUG  WindowsBackend: total_memory_mb=959.35546875
04-21 16:59 DEBUG  CommonBackend: Searching ISOs on USB devices
04-21 16:59 DEBUG  CommonBackend: Searching for local CDs
04-21 16:59 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp is a valid Ubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp is a valid Ubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp is a valid Ubuntu Netbook Remix CD
04-21 16:59 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp is a valid Kubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp is a valid Kubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp is a valid Kubuntu Netbook CD
04-21 16:59 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp is a valid Xubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp is a valid Xubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp is a valid Mythbuntu CD
04-21 16:59 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp is a valid Mythbuntu CD
04-21 16:59 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
04-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
04-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 16:59 INFO   root: Running the installer...
04-21 16:59 DEBUG  WindowsFrontend: __init__...
04-21 16:59 DEBUG  WindowsFrontend: on_init...
04-21 16:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\translations, languages=['en_US', 'en']
04-21 16:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\translations, languages=['en_US', 'en']
04-21 17:14 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
04-21 17:14 INFO   root: Received settings
04-21 17:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\translations, languages=['en_US', 'en']
04-21 17:14 DEBUG  TaskList: # Running tasklist...
04-21 17:14 DEBUG  TaskList: ## Running select_target_dir...
04-21 17:14 INFO   WindowsBackend: Installing into C:\ubuntu
04-21 17:14 DEBUG  TaskList: ## Finished select_target_dir
04-21 17:14 DEBUG  TaskList: ## Running create_dir_structure...
04-21 17:14 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-21 17:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-21 17:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-21 17:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-21 17:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-21 17:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-21 17:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-21 17:14 DEBUG  TaskList: ## Finished create_dir_structure
04-21 17:14 DEBUG  TaskList: ## Running uncompress_target_dir...
04-21 17:14 DEBUG  TaskList: ## Finished uncompress_target_dir
04-21 17:14 DEBUG  TaskList: ## Running create_uninstaller...
04-21 17:14 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\HP_Administrator\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-21 17:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-21 17:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-21 17:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-21 17:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-21 17:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
04-21 17:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-21 17:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
04-21 17:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
04-21 17:14 DEBUG  TaskList: ## Finished create_uninstaller
04-21 17:14 DEBUG  TaskList: ## Running copy_installation_files...
04-21 17:14 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-21 17:14 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\winboot -> C:\ubuntu\winboot
04-21 17:14 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-21 17:14 DEBUG  TaskList: ## Finished copy_installation_files
04-21 17:14 DEBUG  TaskList: ## Running get_iso...
04-21 17:14 DEBUG  CommonBackend: Searching for local CD
04-21 17:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp is a valid Ubuntu CD
04-21 17:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylDE.tmp\casper\filesystem.squashfs
04-21 17:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-21 17:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-21 17:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-21 17:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-21 17:14 DEBUG  CommonBackend: Searching for local ISO
04-21 17:14 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-21 17:14 DEBUG  TaskList: New task get_metalink
04-21 17:14 DEBUG  TaskList: ### Running get_metalink...
04-21 17:14 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink > C:\ubuntu\install
04-21 17:14 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
04-21 17:14 DEBUG  downloader: download finished (read 26651 bytes)
04-21 17:14 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink > C:\ubuntu\install
04-21 17:14 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
04-21 17:14 DEBUG  downloader: download finished (read 562 bytes)
04-21 17:14 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg > C:\ubuntu\install
04-21 17:14 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
04-21 17:14 DEBUG  downloader: download finished (read 189 bytes)
04-21 17:14 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-21 17:14 INFO   saplog: Checking block bindings..
04-21 17:14 INFO   saplog: Key verified successfully.
04-21 17:14 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

04-21 17:14 DEBUG  TaskList: ### Finished get_metalink
04-21 17:14 DEBUG  TaskList: New task download
04-21 17:14 DEBUG  TaskList: ### Running download...
04-21 17:14 DEBUG  btdownloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
04-21 19:30 ERROR  TaskList: Traceback (most recent call last):
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


04-21 19:30 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
04-21 19:30 DEBUG  TaskList: ### Finished download
04-21 19:30 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'
04-21 19:30 DEBUG  TaskList: # Cancelling tasklist
04-21 19:30 DEBUG  TaskList: # Finished tasklist
04-21 19:30 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'
04-29 18:18 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-29 18:18 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
04-29 18:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\HP_Administrator\\Desktop\\wubi.exe"']
04-29 18:18 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\data
04-29 18:18 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\bin\7z.exe
04-29 18:18 DEBUG  CommonBackend: Fetching basic info...
04-29 18:18 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\HP_Administrator\Desktop\wubi.exe
04-29 18:18 DEBUG  CommonBackend: platform=win32
04-29 18:18 DEBUG  CommonBackend: osname=nt
04-29 18:18 DEBUG  CommonBackend: language=en_US
04-29 18:18 DEBUG  CommonBackend: encoding=cp1252
04-29 18:18 DEBUG  WindowsBackend: arch=amd64
04-29 18:18 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\data\isolist.ini
04-29 18:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-29 18:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-29 18:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-29 18:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-29 18:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-29 18:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-29 18:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-29 18:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-29 18:18 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-29 18:18 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-29 18:18 DEBUG  WindowsBackend: Fetching host info...
04-29 18:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-29 18:18 DEBUG  WindowsBackend: windows version=xp
04-29 18:18 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-29 18:18 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-29 18:18 DEBUG  WindowsBackend: windows_build=2600
04-29 18:18 DEBUG  WindowsBackend: gmt=-8
04-29 18:18 DEBUG  WindowsBackend: country=US
04-29 18:18 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-29 18:18 DEBUG  WindowsBackend: windows_username=Administrator
04-29 18:18 DEBUG  WindowsBackend: user_full_name=Administrator
04-29 18:18 DEBUG  WindowsBackend: user_directory=
04-29 18:18 DEBUG  WindowsBackend: windows_language_code=1033
04-29 18:18 DEBUG  WindowsBackend: windows_language=English
04-29 18:18 DEBUG  WindowsBackend: processor_name=             Intel(R) Pentium(R) D  CPU 2.66GHz
04-29 18:18 DEBUG  WindowsBackend: bootloader=xp
04-29 18:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 145280.53125 mb free ntfs)
04-29 18:18 DEBUG  WindowsBackend: drive=Drive(C: hd 145280.53125 mb free ntfs)
04-29 18:18 DEBUG  WindowsBackend: drive=Drive(D: hd 3158.72265625 mb free fat32)
04-29 18:18 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-29 18:18 DEBUG  WindowsBackend: uninstaller_path=None
04-29 18:18 DEBUG  WindowsBackend: previous_target_dir=None
04-29 18:18 DEBUG  WindowsBackend: previous_distro_name=None
04-29 18:18 DEBUG  WindowsBackend: keyboard_id=67699721
04-29 18:18 DEBUG  WindowsBackend: keyboard_layout=us
04-29 18:18 DEBUG  WindowsBackend: keyboard_variant=
04-29 18:18 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-29 18:18 DEBUG  CommonBackend: locale=en_US.UTF-8
04-29 18:18 DEBUG  WindowsBackend: total_memory_mb=959.35546875
04-29 18:18 DEBUG  CommonBackend: Searching ISOs on USB devices
04-29 18:18 DEBUG  CommonBackend: Searching for local CDs
04-29 18:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp is a valid Ubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp is a valid Ubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp is a valid Ubuntu Netbook Remix CD
04-29 18:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp is a valid Kubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp is a valid Kubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp is a valid Kubuntu Netbook CD
04-29 18:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp is a valid Xubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp is a valid Xubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp is a valid Mythbuntu CD
04-29 18:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp is a valid Mythbuntu CD
04-29 18:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
04-29 18:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-29 18:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-29 18:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-29 18:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
04-29 18:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-29 18:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-29 18:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-29 18:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-29 18:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:18 INFO   root: Running the installer...
04-29 18:18 DEBUG  WindowsFrontend: __init__...
04-29 18:18 DEBUG  WindowsFrontend: on_init...
04-29 18:18 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\translations, languages=['en_US', 'en']
04-29 18:18 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\translations, languages=['en_US', 'en']
04-29 18:19 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=user
04-29 18:19 INFO   root: Received settings
04-29 18:19 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\translations, languages=['en_US', 'en']
04-29 18:19 DEBUG  TaskList: # Running tasklist...
04-29 18:19 DEBUG  TaskList: ## Running select_target_dir...
04-29 18:19 INFO   WindowsBackend: Installing into C:\ubuntu
04-29 18:19 DEBUG  TaskList: ## Finished select_target_dir
04-29 18:19 DEBUG  TaskList: ## Running create_dir_structure...
04-29 18:19 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-29 18:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-29 18:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-29 18:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-29 18:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-29 18:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-29 18:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-29 18:19 DEBUG  TaskList: ## Finished create_dir_structure
04-29 18:19 DEBUG  TaskList: ## Running uncompress_target_dir...
04-29 18:19 DEBUG  TaskList: ## Finished uncompress_target_dir
04-29 18:19 DEBUG  TaskList: ## Running create_uninstaller...
04-29 18:19 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\HP_Administrator\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-29 18:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-29 18:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-29 18:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-29 18:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-29 18:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
04-29 18:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-29 18:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
04-29 18:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
04-29 18:19 DEBUG  TaskList: ## Finished create_uninstaller
04-29 18:19 DEBUG  TaskList: ## Running copy_installation_files...
04-29 18:19 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-29 18:19 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\winboot -> C:\ubuntu\winboot
04-29 18:19 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-29 18:19 DEBUG  TaskList: ## Finished copy_installation_files
04-29 18:19 DEBUG  TaskList: ## Running get_iso...
04-29 18:19 DEBUG  CommonBackend: Searching for local CD
04-29 18:19 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp is a valid Ubuntu CD
04-29 18:19 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylEB.tmp\casper\filesystem.squashfs
04-29 18:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-29 18:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-29 18:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:19 DEBUG  CommonBackend: Searching for local ISO
04-29 18:19 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\HP_Administrator\Desktop\Morphing-Morphix_0-1.iso
04-29 18:19 DEBUG  Distro:     wrong size: 266663936 < 600000000
04-29 18:19 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\HP_Administrator\Desktop\ubuntu-10.04-rc-desktop-i386.iso
04-29 18:19 DEBUG  WindowsBackend:   extracting .disk\info from C:\Documents and Settings\HP_Administrator\Desktop\ubuntu-10.04-rc-desktop-i386.iso
04-29 18:19 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 "Lucid Lynx" - Release Candidate i386 (20100419.1)
04-29 18:19 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release Candidate', 'version': '10.04', 'build': '20100419.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
04-29 18:19 DEBUG  Distro: wrong version: 10.04 != 9.10
04-29 18:19 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-29 18:19 DEBUG  TaskList: New task get_metalink
04-29 18:19 DEBUG  TaskList: ### Running get_metalink...
04-29 18:19 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink > C:\ubuntu\install
04-29 18:19 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
04-29 18:19 DEBUG  downloader: download finished (read 26651 bytes)
04-29 18:19 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink > C:\ubuntu\install
04-29 18:19 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
04-29 18:19 DEBUG  downloader: download finished (read 562 bytes)
04-29 18:19 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg > C:\ubuntu\install
04-29 18:19 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
04-29 18:19 DEBUG  downloader: download finished (read 189 bytes)
04-29 18:19 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-29 18:19 INFO   saplog: Checking block bindings..
04-29 18:19 INFO   saplog: Key verified successfully.
04-29 18:19 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

04-29 18:19 DEBUG  TaskList: ### Finished get_metalink
04-29 18:19 DEBUG  TaskList: New task download
04-29 18:19 DEBUG  TaskList: ### Running download...
04-29 18:19 DEBUG  btdownloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
04-29 18:22 DEBUG  WindowsFrontend: frontend.on_quit
04-29 18:22 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
04-29 18:22 DEBUG  TaskList: # Cancelling tasklist
04-29 18:22 DEBUG  TaskList: ### Finished download
04-29 18:22 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
04-29 18:22 DEBUG  root: application.on_quit
04-29 18:22 DEBUG  root: Forceful exit
04-29 18:22 INFO   root: sys.exit
04-29 18:51 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-29 18:51 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
04-29 18:51 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\HP_Administrator\\Desktop\\wubi.exe"']
04-29 18:51 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\data
04-29 18:51 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\bin\7z.exe
04-29 18:51 DEBUG  CommonBackend: Fetching basic info...
04-29 18:51 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\HP_Administrator\Desktop\wubi.exe
04-29 18:51 DEBUG  CommonBackend: platform=win32
04-29 18:51 DEBUG  CommonBackend: osname=nt
04-29 18:51 DEBUG  CommonBackend: language=en_US
04-29 18:51 DEBUG  CommonBackend: encoding=cp1252
04-29 18:51 DEBUG  WindowsBackend: arch=amd64
04-29 18:51 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\data\isolist.ini
04-29 18:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-29 18:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-29 18:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-29 18:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-29 18:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-29 18:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-29 18:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-29 18:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-29 18:51 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-29 18:51 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-29 18:51 DEBUG  WindowsBackend: Fetching host info...
04-29 18:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-29 18:51 DEBUG  WindowsBackend: windows version=xp
04-29 18:51 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-29 18:51 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-29 18:51 DEBUG  WindowsBackend: windows_build=2600
04-29 18:51 DEBUG  WindowsBackend: gmt=-8
04-29 18:51 DEBUG  WindowsBackend: country=US
04-29 18:51 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-29 18:51 DEBUG  WindowsBackend: windows_username=Administrator
04-29 18:51 DEBUG  WindowsBackend: user_full_name=Administrator
04-29 18:51 DEBUG  WindowsBackend: user_directory=
04-29 18:51 DEBUG  WindowsBackend: windows_language_code=1033
04-29 18:51 DEBUG  WindowsBackend: windows_language=English
04-29 18:51 DEBUG  WindowsBackend: processor_name=             Intel(R) Pentium(R) D  CPU 2.66GHz
04-29 18:51 DEBUG  WindowsBackend: bootloader=xp
04-29 18:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 145267.183594 mb free ntfs)
04-29 18:51 DEBUG  WindowsBackend: drive=Drive(C: hd 145267.183594 mb free ntfs)
04-29 18:51 DEBUG  WindowsBackend: drive=Drive(D: hd 3158.734375 mb free fat32)
04-29 18:51 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-29 18:51 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-29 18:51 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-29 18:51 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-29 18:51 DEBUG  WindowsBackend: keyboard_id=67699721
04-29 18:51 DEBUG  WindowsBackend: keyboard_layout=us
04-29 18:51 DEBUG  WindowsBackend: keyboard_variant=
04-29 18:51 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-29 18:51 DEBUG  CommonBackend: locale=en_US.UTF-8
04-29 18:51 DEBUG  WindowsBackend: total_memory_mb=959.35546875
04-29 18:51 DEBUG  CommonBackend: Searching ISOs on USB devices
04-29 18:51 DEBUG  CommonBackend: Searching for local CDs
04-29 18:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Ubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Ubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Ubuntu Netbook Remix CD
04-29 18:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Kubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Kubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Kubuntu Netbook CD
04-29 18:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Xubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Xubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Mythbuntu CD
04-29 18:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Mythbuntu CD
04-29 18:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
04-29 18:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-29 18:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-29 18:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-29 18:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
04-29 18:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-29 18:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-29 18:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-29 18:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-29 18:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:51 INFO   root: Already installed, running the uninstaller...
04-29 18:51 INFO   root: Running the uninstaller...
04-29 18:51 INFO   CommonBackend: This is the uninstaller running
04-29 18:51 DEBUG  WindowsFrontend: __init__...
04-29 18:51 DEBUG  WindowsFrontend: on_init...
04-29 18:51 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\translations, languages=['en_US', 'en']
04-29 18:52 INFO   root: Received settings
04-29 18:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\translations, languages=['en_US', 'en']
04-29 18:52 DEBUG  TaskList: # Running tasklist...
04-29 18:52 DEBUG  TaskList: ## Running Backup ISO...
04-29 18:52 DEBUG  TaskList: ## Finished Backup ISO
04-29 18:52 DEBUG  TaskList: ## Running Remove bootloader entry...
04-29 18:52 ERROR  WindowsBackend: Cannot find bcdedit
04-29 18:52 DEBUG  WindowsBackend: undo_bootini C:
04-29 18:52 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 145267.183594 mb free ntfs)
04-29 18:52 DEBUG  WindowsBackend: undo_bootini D:
04-29 18:52 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 3158.734375 mb free fat32)
04-29 18:52 DEBUG  TaskList: ## Finished Remove bootloader entry
04-29 18:52 DEBUG  TaskList: ## Running Remove target dir...
04-29 18:52 DEBUG  CommonBackend: Deleting C:\ubuntu
04-29 18:52 DEBUG  TaskList: ## Finished Remove target dir
04-29 18:52 DEBUG  TaskList: ## Running Remove registry key...
04-29 18:52 DEBUG  TaskList: ## Finished Remove registry key
04-29 18:52 DEBUG  TaskList: # Finished tasklist
04-29 18:52 INFO   root: Almost finished uninstalling
04-29 18:52 INFO   root: Finished uninstallation
04-29 18:52 DEBUG  CommonBackend: Fetching basic info...
04-29 18:52 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\HP_Administrator\Desktop\wubi.exe
04-29 18:52 DEBUG  CommonBackend: platform=win32
04-29 18:52 DEBUG  CommonBackend: osname=nt
04-29 18:52 DEBUG  WindowsBackend: arch=amd64
04-29 18:52 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\data\isolist.ini
04-29 18:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-29 18:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-29 18:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-29 18:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-29 18:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-29 18:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-29 18:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-29 18:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-29 18:52 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-29 18:52 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-29 18:52 DEBUG  WindowsBackend: Fetching host info...
04-29 18:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-29 18:52 DEBUG  WindowsBackend: windows version=xp
04-29 18:52 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-29 18:52 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-29 18:52 DEBUG  WindowsBackend: windows_build=2600
04-29 18:52 DEBUG  WindowsBackend: gmt=-8
04-29 18:52 DEBUG  WindowsBackend: country=US
04-29 18:52 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-29 18:52 DEBUG  WindowsBackend: windows_username=Administrator
04-29 18:52 DEBUG  WindowsBackend: user_full_name=Administrator
04-29 18:52 DEBUG  WindowsBackend: user_directory=
04-29 18:52 DEBUG  WindowsBackend: windows_language_code=1033
04-29 18:52 DEBUG  WindowsBackend: windows_language=English
04-29 18:52 DEBUG  WindowsBackend: processor_name=             Intel(R) Pentium(R) D  CPU 2.66GHz
04-29 18:52 DEBUG  WindowsBackend: bootloader=xp
04-29 18:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 145272.589844 mb free ntfs)
04-29 18:52 DEBUG  WindowsBackend: drive=Drive(C: hd 145272.589844 mb free ntfs)
04-29 18:52 DEBUG  WindowsBackend: drive=Drive(D: hd 3158.734375 mb free fat32)
04-29 18:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-29 18:52 DEBUG  WindowsBackend: uninstaller_path=None
04-29 18:52 DEBUG  WindowsBackend: previous_target_dir=None
04-29 18:52 DEBUG  WindowsBackend: previous_distro_name=None
04-29 18:52 DEBUG  WindowsBackend: keyboard_id=67699721
04-29 18:52 DEBUG  WindowsBackend: keyboard_layout=us
04-29 18:52 DEBUG  WindowsBackend: keyboard_variant=
04-29 18:52 DEBUG  WindowsBackend: total_memory_mb=959.35546875
04-29 18:52 DEBUG  CommonBackend: Searching ISOs on USB devices
04-29 18:52 DEBUG  CommonBackend: Searching for local CDs
04-29 18:52 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Ubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Ubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Ubuntu Netbook Remix CD
04-29 18:52 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Kubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Kubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Kubuntu Netbook CD
04-29 18:52 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Xubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Xubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Mythbuntu CD
04-29 18:52 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Mythbuntu CD
04-29 18:52 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
04-29 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-29 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-29 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-29 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
04-29 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-29 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-29 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-29 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:52 INFO   root: Running the installer...
04-29 18:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\translations, languages=['en_US', 'en']
04-29 18:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\translations, languages=['en_US', 'en']
04-29 18:52 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=user
04-29 18:52 INFO   root: Received settings
04-29 18:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\translations, languages=['en_US', 'en']
04-29 18:52 DEBUG  TaskList: # Running tasklist...
04-29 18:52 DEBUG  TaskList: ## Running select_target_dir...
04-29 18:52 INFO   WindowsBackend: Installing into C:\ubuntu
04-29 18:52 DEBUG  TaskList: ## Finished select_target_dir
04-29 18:52 DEBUG  TaskList: ## Running create_dir_structure...
04-29 18:52 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-29 18:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-29 18:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-29 18:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-29 18:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-29 18:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-29 18:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-29 18:52 DEBUG  TaskList: ## Finished create_dir_structure
04-29 18:52 DEBUG  TaskList: ## Running uncompress_target_dir...
04-29 18:52 DEBUG  TaskList: ## Finished uncompress_target_dir
04-29 18:52 DEBUG  TaskList: ## Running create_uninstaller...
04-29 18:52 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\HP_Administrator\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-29 18:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-29 18:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-29 18:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-29 18:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-29 18:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
04-29 18:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-29 18:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
04-29 18:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
04-29 18:52 DEBUG  TaskList: ## Finished create_uninstaller
04-29 18:52 DEBUG  TaskList: ## Running copy_installation_files...
04-29 18:52 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-29 18:52 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\winboot -> C:\ubuntu\winboot
04-29 18:52 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-29 18:52 DEBUG  TaskList: ## Finished copy_installation_files
04-29 18:52 DEBUG  TaskList: ## Running get_iso...
04-29 18:52 DEBUG  CommonBackend: Searching for local CD
04-29 18:52 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp is a valid Ubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl119.tmp\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-29 18:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-29 18:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-29 18:52 DEBUG  CommonBackend: Searching for local ISO
04-29 18:52 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\HP_Administrator\Desktop\Morphing-Morphix_0-1.iso
04-29 18:52 DEBUG  Distro:     wrong size: 266663936 < 600000000
04-29 18:52 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\HP_Administrator\Desktop\ubuntu-10.04-rc-desktop-i386.iso
04-29 18:52 DEBUG  WindowsBackend:   extracting .disk\info from C:\Documents and Settings\HP_Administrator\Desktop\ubuntu-10.04-rc-desktop-i386.iso
04-29 18:52 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 "Lucid Lynx" - Release Candidate i386 (20100419.1)
04-29 18:52 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release Candidate', 'version': '10.04', 'build': '20100419.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
04-29 18:52 DEBUG  Distro: wrong version: 10.04 != 9.10
04-29 18:52 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-29 18:52 DEBUG  TaskList: New task get_metalink
04-29 18:52 DEBUG  TaskList: ### Running get_metalink...
04-29 18:52 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink > C:\ubuntu\install
04-29 18:53 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
04-29 18:53 DEBUG  downloader: download finished (read 26651 bytes)
04-29 18:53 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink > C:\ubuntu\install
04-29 18:53 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
04-29 18:53 DEBUG  downloader: download finished (read 562 bytes)
04-29 18:53 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg > C:\ubuntu\install
04-29 18:53 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
04-29 18:53 DEBUG  downloader: download finished (read 189 bytes)
04-29 18:53 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-29 18:53 INFO   saplog: Checking block bindings..
04-29 18:53 INFO   saplog: Key verified successfully.
04-29 18:53 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

04-29 18:53 DEBUG  TaskList: ### Finished get_metalink
04-29 18:53 DEBUG  TaskList: New task download
04-29 18:53 DEBUG  TaskList: ### Running download...
04-29 18:53 DEBUG  btdownloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
04-29 18:56 INFO   WindowsFrontend: Operation cancelled
04-29 18:57 DEBUG  WindowsFrontend: frontend.quit
04-29 18:57 DEBUG  WindowsFrontend: frontend.on_quit
04-29 18:57 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
04-29 18:57 DEBUG  TaskList: # Cancelling tasklist
04-29 18:57 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
04-29 18:57 DEBUG  root: application.on_quit
04-29 18:57 DEBUG  root: Forceful exit
04-29 18:57 INFO   root: sys.exit
04-30 04:26 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-30 04:26 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
04-30 04:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\HP_Administrator\\Desktop\\wubi.exe"']
04-30 04:26 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\data
04-30 04:26 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\bin\7z.exe
04-30 04:26 DEBUG  CommonBackend: Fetching basic info...
04-30 04:26 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\HP_Administrator\Desktop\wubi.exe
04-30 04:26 DEBUG  CommonBackend: platform=win32
04-30 04:26 DEBUG  CommonBackend: osname=nt
04-30 04:26 DEBUG  CommonBackend: language=en_US
04-30 04:26 DEBUG  CommonBackend: encoding=cp1252
04-30 04:26 DEBUG  WindowsBackend: arch=amd64
04-30 04:26 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\data\isolist.ini
04-30 04:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-30 04:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-30 04:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-30 04:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-30 04:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-30 04:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-30 04:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-30 04:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-30 04:26 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-30 04:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-30 04:26 DEBUG  WindowsBackend: Fetching host info...
04-30 04:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-30 04:26 DEBUG  WindowsBackend: windows version=xp
04-30 04:26 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-30 04:26 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-30 04:26 DEBUG  WindowsBackend: windows_build=2600
04-30 04:26 DEBUG  WindowsBackend: gmt=-8
04-30 04:26 DEBUG  WindowsBackend: country=US
04-30 04:26 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-30 04:26 DEBUG  WindowsBackend: windows_username=Administrator
04-30 04:26 DEBUG  WindowsBackend: user_full_name=Administrator
04-30 04:26 DEBUG  WindowsBackend: user_directory=
04-30 04:26 DEBUG  WindowsBackend: windows_language_code=1033
04-30 04:26 DEBUG  WindowsBackend: windows_language=English
04-30 04:26 DEBUG  WindowsBackend: processor_name=             Intel(R) Pentium(R) D  CPU 2.66GHz
04-30 04:26 DEBUG  WindowsBackend: bootloader=xp
04-30 04:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 145259.511719 mb free ntfs)
04-30 04:26 DEBUG  WindowsBackend: drive=Drive(C: hd 145259.511719 mb free ntfs)
04-30 04:26 DEBUG  WindowsBackend: drive=Drive(D: hd 3158.73046875 mb free fat32)
04-30 04:26 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-30 04:26 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-30 04:26 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-30 04:26 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-30 04:26 DEBUG  WindowsBackend: keyboard_id=67699721
04-30 04:26 DEBUG  WindowsBackend: keyboard_layout=us
04-30 04:26 DEBUG  WindowsBackend: keyboard_variant=
04-30 04:26 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-30 04:26 DEBUG  CommonBackend: locale=en_US.UTF-8
04-30 04:26 DEBUG  WindowsBackend: total_memory_mb=959.35546875
04-30 04:26 DEBUG  CommonBackend: Searching ISOs on USB devices
04-30 04:26 DEBUG  CommonBackend: Searching for local CDs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Ubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Ubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Ubuntu Netbook Remix CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Kubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Kubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Kubuntu Netbook CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Xubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Xubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Mythbuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Mythbuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 INFO   root: Already installed, running the uninstaller...
04-30 04:26 INFO   root: Running the uninstaller...
04-30 04:26 INFO   CommonBackend: This is the uninstaller running
04-30 04:26 DEBUG  WindowsFrontend: __init__...
04-30 04:26 DEBUG  WindowsFrontend: on_init...
04-30 04:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\translations, languages=['en_US', 'en']
04-30 04:26 INFO   root: Received settings
04-30 04:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\translations, languages=['en_US', 'en']
04-30 04:26 DEBUG  TaskList: # Running tasklist...
04-30 04:26 DEBUG  TaskList: ## Running Backup ISO...
04-30 04:26 DEBUG  TaskList: ## Finished Backup ISO
04-30 04:26 DEBUG  TaskList: ## Running Remove bootloader entry...
04-30 04:26 ERROR  WindowsBackend: Cannot find bcdedit
04-30 04:26 DEBUG  WindowsBackend: undo_bootini C:
04-30 04:26 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 145259.511719 mb free ntfs)
04-30 04:26 DEBUG  WindowsBackend: undo_bootini D:
04-30 04:26 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 3158.73046875 mb free fat32)
04-30 04:26 DEBUG  TaskList: ## Finished Remove bootloader entry
04-30 04:26 DEBUG  TaskList: ## Running Remove target dir...
04-30 04:26 DEBUG  CommonBackend: Deleting C:\ubuntu
04-30 04:26 DEBUG  TaskList: ## Finished Remove target dir
04-30 04:26 DEBUG  TaskList: ## Running Remove registry key...
04-30 04:26 DEBUG  TaskList: ## Finished Remove registry key
04-30 04:26 DEBUG  TaskList: # Finished tasklist
04-30 04:26 INFO   root: Almost finished uninstalling
04-30 04:26 INFO   root: Finished uninstallation
04-30 04:26 DEBUG  CommonBackend: Fetching basic info...
04-30 04:26 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\HP_Administrator\Desktop\wubi.exe
04-30 04:26 DEBUG  CommonBackend: platform=win32
04-30 04:26 DEBUG  CommonBackend: osname=nt
04-30 04:26 DEBUG  WindowsBackend: arch=amd64
04-30 04:26 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\data\isolist.ini
04-30 04:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-30 04:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-30 04:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-30 04:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-30 04:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-30 04:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-30 04:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-30 04:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-30 04:26 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-30 04:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-30 04:26 DEBUG  WindowsBackend: Fetching host info...
04-30 04:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-30 04:26 DEBUG  WindowsBackend: windows version=xp
04-30 04:26 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-30 04:26 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-30 04:26 DEBUG  WindowsBackend: windows_build=2600
04-30 04:26 DEBUG  WindowsBackend: gmt=-8
04-30 04:26 DEBUG  WindowsBackend: country=US
04-30 04:26 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-30 04:26 DEBUG  WindowsBackend: windows_username=Administrator
04-30 04:26 DEBUG  WindowsBackend: user_full_name=Administrator
04-30 04:26 DEBUG  WindowsBackend: user_directory=
04-30 04:26 DEBUG  WindowsBackend: windows_language_code=1033
04-30 04:26 DEBUG  WindowsBackend: windows_language=English
04-30 04:26 DEBUG  WindowsBackend: processor_name=             Intel(R) Pentium(R) D  CPU 2.66GHz
04-30 04:26 DEBUG  WindowsBackend: bootloader=xp
04-30 04:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 145265.128906 mb free ntfs)
04-30 04:26 DEBUG  WindowsBackend: drive=Drive(C: hd 145265.128906 mb free ntfs)
04-30 04:26 DEBUG  WindowsBackend: drive=Drive(D: hd 3158.70703125 mb free fat32)
04-30 04:26 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-30 04:26 DEBUG  WindowsBackend: uninstaller_path=None
04-30 04:26 DEBUG  WindowsBackend: previous_target_dir=None
04-30 04:26 DEBUG  WindowsBackend: previous_distro_name=None
04-30 04:26 DEBUG  WindowsBackend: keyboard_id=67699721
04-30 04:26 DEBUG  WindowsBackend: keyboard_layout=us
04-30 04:26 DEBUG  WindowsBackend: keyboard_variant=
04-30 04:26 DEBUG  WindowsBackend: total_memory_mb=959.35546875
04-30 04:26 DEBUG  CommonBackend: Searching ISOs on USB devices
04-30 04:26 DEBUG  CommonBackend: Searching for local CDs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Ubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Ubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Ubuntu Netbook Remix CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Kubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Kubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Kubuntu Netbook CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Xubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Xubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Mythbuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Mythbuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 INFO   root: Running the installer...
04-30 04:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\translations, languages=['en_US', 'en']
04-30 04:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\translations, languages=['en_US', 'en']
04-30 04:26 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=user
04-30 04:26 INFO   root: Received settings
04-30 04:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\translations, languages=['en_US', 'en']
04-30 04:26 DEBUG  TaskList: # Running tasklist...
04-30 04:26 DEBUG  TaskList: ## Running select_target_dir...
04-30 04:26 INFO   WindowsBackend: Installing into C:\ubuntu
04-30 04:26 DEBUG  TaskList: ## Finished select_target_dir
04-30 04:26 DEBUG  TaskList: ## Running create_dir_structure...
04-30 04:26 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-30 04:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-30 04:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-30 04:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-30 04:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-30 04:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-30 04:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-30 04:26 DEBUG  TaskList: ## Finished create_dir_structure
04-30 04:26 DEBUG  TaskList: ## Running uncompress_target_dir...
04-30 04:26 DEBUG  TaskList: ## Finished uncompress_target_dir
04-30 04:26 DEBUG  TaskList: ## Running create_uninstaller...
04-30 04:26 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\HP_Administrator\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-30 04:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-30 04:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-30 04:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-30 04:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-30 04:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
04-30 04:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-30 04:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
04-30 04:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
04-30 04:26 DEBUG  TaskList: ## Finished create_uninstaller
04-30 04:26 DEBUG  TaskList: ## Running copy_installation_files...
04-30 04:26 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-30 04:26 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\winboot -> C:\ubuntu\winboot
04-30 04:26 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-30 04:26 DEBUG  TaskList: ## Finished copy_installation_files
04-30 04:26 DEBUG  TaskList: ## Running get_iso...
04-30 04:26 DEBUG  CommonBackend: Searching for local CD
04-30 04:26 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp is a valid Ubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl2CD.tmp\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 04:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-30 04:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 04:26 DEBUG  CommonBackend: Searching for local ISO
04-30 04:26 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\HP_Administrator\Desktop\Morphing-Morphix_0-1.iso
04-30 04:26 DEBUG  Distro:     wrong size: 266663936 < 600000000
04-30 04:26 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\HP_Administrator\Desktop\ubuntu-10.04-rc-desktop-i386.iso
04-30 04:26 DEBUG  WindowsBackend:   extracting .disk\info from C:\Documents and Settings\HP_Administrator\Desktop\ubuntu-10.04-rc-desktop-i386.iso
04-30 04:26 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 "Lucid Lynx" - Release Candidate i386 (20100419.1)
04-30 04:26 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release Candidate', 'version': '10.04', 'build': '20100419.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
04-30 04:26 DEBUG  Distro: wrong version: 10.04 != 9.10
04-30 04:26 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-30 04:26 DEBUG  TaskList: New task get_metalink
04-30 04:26 DEBUG  TaskList: ### Running get_metalink...
04-30 04:26 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink > C:\ubuntu\install
04-30 04:27 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
04-30 04:27 DEBUG  downloader: download finished (read 26651 bytes)
04-30 04:27 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink > C:\ubuntu\install
04-30 04:27 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
04-30 04:27 DEBUG  downloader: download finished (read 562 bytes)
04-30 04:27 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg > C:\ubuntu\install
04-30 04:27 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
04-30 04:27 DEBUG  downloader: download finished (read 189 bytes)
04-30 04:27 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-30 04:27 INFO   saplog: Checking block bindings..
04-30 04:27 INFO   saplog: Key verified successfully.
04-30 04:27 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

04-30 04:27 DEBUG  TaskList: ### Finished get_metalink
04-30 04:27 DEBUG  TaskList: New task download
04-30 04:27 DEBUG  TaskList: ### Running download...
04-30 04:27 DEBUG  btdownloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
04-30 04:33 INFO   WindowsFrontend: Operation cancelled
04-30 04:33 DEBUG  WindowsFrontend: frontend.quit
04-30 04:33 DEBUG  WindowsFrontend: frontend.on_quit
04-30 04:33 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
04-30 04:33 DEBUG  TaskList: # Cancelling tasklist
04-30 04:33 DEBUG  TaskList: ### Finished download
04-30 04:33 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
04-30 04:33 DEBUG  root: application.on_quit
04-30 04:33 DEBUG  root: Forceful exit
04-30 04:33 INFO   root: sys.exit
04-30 20:08 INFO   root: === wubi 9.10ubuntu1 rev160 ===
04-30 20:08 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log
04-30 20:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\HP_Administrator\\Desktop\\wubi.exe"']
04-30 20:08 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\data
04-30 20:08 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\bin\7z.exe
04-30 20:08 DEBUG  CommonBackend: Fetching basic info...
04-30 20:08 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\HP_Administrator\Desktop\wubi.exe
04-30 20:08 DEBUG  CommonBackend: platform=win32
04-30 20:08 DEBUG  CommonBackend: osname=nt
04-30 20:08 DEBUG  CommonBackend: language=en_US
04-30 20:08 DEBUG  CommonBackend: encoding=cp1252
04-30 20:08 DEBUG  WindowsBackend: arch=amd64
04-30 20:08 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\data\isolist.ini
04-30 20:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-30 20:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-30 20:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-30 20:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-30 20:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-30 20:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-30 20:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-30 20:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-30 20:08 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-30 20:08 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-30 20:08 DEBUG  WindowsBackend: Fetching host info...
04-30 20:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-30 20:08 DEBUG  WindowsBackend: windows version=xp
04-30 20:08 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-30 20:08 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-30 20:08 DEBUG  WindowsBackend: windows_build=2600
04-30 20:08 DEBUG  WindowsBackend: gmt=-8
04-30 20:08 DEBUG  WindowsBackend: country=US
04-30 20:08 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-30 20:08 DEBUG  WindowsBackend: windows_username=Administrator
04-30 20:08 DEBUG  WindowsBackend: user_full_name=Administrator
04-30 20:08 DEBUG  WindowsBackend: user_directory=
04-30 20:08 DEBUG  WindowsBackend: windows_language_code=1033
04-30 20:08 DEBUG  WindowsBackend: windows_language=English
04-30 20:08 DEBUG  WindowsBackend: processor_name=             Intel(R) Pentium(R) D  CPU 2.66GHz
04-30 20:08 DEBUG  WindowsBackend: bootloader=xp
04-30 20:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 145207.261719 mb free ntfs)
04-30 20:08 DEBUG  WindowsBackend: drive=Drive(C: hd 145207.261719 mb free ntfs)
04-30 20:08 DEBUG  WindowsBackend: drive=Drive(D: hd 3158.70703125 mb free fat32)
04-30 20:08 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-30 20:08 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-30 20:08 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-30 20:08 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-30 20:08 DEBUG  WindowsBackend: keyboard_id=67699721
04-30 20:08 DEBUG  WindowsBackend: keyboard_layout=us
04-30 20:08 DEBUG  WindowsBackend: keyboard_variant=
04-30 20:08 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-30 20:08 DEBUG  CommonBackend: locale=en_US.UTF-8
04-30 20:08 DEBUG  WindowsBackend: total_memory_mb=959.35546875
04-30 20:08 DEBUG  CommonBackend: Searching ISOs on USB devices
04-30 20:08 DEBUG  CommonBackend: Searching for local CDs
04-30 20:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Ubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Ubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Ubuntu Netbook Remix CD
04-30 20:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Kubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Kubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Kubuntu Netbook CD
04-30 20:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Xubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Xubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Mythbuntu CD
04-30 20:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Mythbuntu CD
04-30 20:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
04-30 20:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-30 20:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-30 20:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-30 20:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
04-30 20:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-30 20:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-30 20:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-30 20:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-30 20:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:08 INFO   root: Already installed, running the uninstaller...
04-30 20:08 INFO   root: Running the uninstaller...
04-30 20:08 INFO   CommonBackend: This is the uninstaller running
04-30 20:08 DEBUG  WindowsFrontend: __init__...
04-30 20:08 DEBUG  WindowsFrontend: on_init...
04-30 20:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\translations, languages=['en_US', 'en']
04-30 20:09 INFO   root: Received settings
04-30 20:09 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\translations, languages=['en_US', 'en']
04-30 20:09 DEBUG  TaskList: # Running tasklist...
04-30 20:09 DEBUG  TaskList: ## Running Backup ISO...
04-30 20:09 DEBUG  TaskList: ## Finished Backup ISO
04-30 20:09 DEBUG  TaskList: ## Running Remove bootloader entry...
04-30 20:09 ERROR  WindowsBackend: Cannot find bcdedit
04-30 20:09 DEBUG  WindowsBackend: undo_bootini C:
04-30 20:09 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 145207.261719 mb free ntfs)
04-30 20:09 DEBUG  WindowsBackend: undo_bootini D:
04-30 20:09 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 3158.70703125 mb free fat32)
04-30 20:09 DEBUG  TaskList: ## Finished Remove bootloader entry
04-30 20:09 DEBUG  TaskList: ## Running Remove target dir...
04-30 20:09 DEBUG  CommonBackend: Deleting C:\ubuntu
04-30 20:09 DEBUG  TaskList: ## Finished Remove target dir
04-30 20:09 DEBUG  TaskList: ## Running Remove registry key...
04-30 20:09 DEBUG  TaskList: ## Finished Remove registry key
04-30 20:09 DEBUG  TaskList: # Finished tasklist
04-30 20:09 INFO   root: Almost finished uninstalling
04-30 20:09 INFO   root: Finished uninstallation
04-30 20:09 DEBUG  CommonBackend: Fetching basic info...
04-30 20:09 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\HP_Administrator\Desktop\wubi.exe
04-30 20:09 DEBUG  CommonBackend: platform=win32
04-30 20:09 DEBUG  CommonBackend: osname=nt
04-30 20:09 DEBUG  WindowsBackend: arch=amd64
04-30 20:09 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\data\isolist.ini
04-30 20:09 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-30 20:09 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-30 20:09 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-30 20:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-30 20:09 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-30 20:09 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-30 20:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-30 20:09 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-30 20:09 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-30 20:09 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
04-30 20:09 DEBUG  WindowsBackend: Fetching host info...
04-30 20:09 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-30 20:09 DEBUG  WindowsBackend: windows version=xp
04-30 20:09 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-30 20:09 DEBUG  WindowsBackend: windows_sp=Service Pack 2
04-30 20:09 DEBUG  WindowsBackend: windows_build=2600
04-30 20:09 DEBUG  WindowsBackend: gmt=-8
04-30 20:09 DEBUG  WindowsBackend: country=US
04-30 20:09 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-30 20:09 DEBUG  WindowsBackend: windows_username=Administrator
04-30 20:09 DEBUG  WindowsBackend: user_full_name=Administrator
04-30 20:09 DEBUG  WindowsBackend: user_directory=
04-30 20:09 DEBUG  WindowsBackend: windows_language_code=1033
04-30 20:09 DEBUG  WindowsBackend: windows_language=English
04-30 20:09 DEBUG  WindowsBackend: processor_name=             Intel(R) Pentium(R) D  CPU 2.66GHz
04-30 20:09 DEBUG  WindowsBackend: bootloader=xp
04-30 20:09 DEBUG  WindowsBackend: system_drive=Drive(C: hd 145217.242188 mb free ntfs)
04-30 20:09 DEBUG  WindowsBackend: drive=Drive(C: hd 145217.242188 mb free ntfs)
04-30 20:09 DEBUG  WindowsBackend: drive=Drive(D: hd 3158.70703125 mb free fat32)
04-30 20:09 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-30 20:09 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-30 20:09 DEBUG  WindowsBackend: uninstaller_path=None
04-30 20:09 DEBUG  WindowsBackend: previous_target_dir=None
04-30 20:09 DEBUG  WindowsBackend: previous_distro_name=None
04-30 20:09 DEBUG  WindowsBackend: keyboard_id=67699721
04-30 20:09 DEBUG  WindowsBackend: keyboard_layout=us
04-30 20:09 DEBUG  WindowsBackend: keyboard_variant=
04-30 20:09 DEBUG  WindowsBackend: total_memory_mb=959.35546875
04-30 20:09 DEBUG  CommonBackend: Searching ISOs on USB devices
04-30 20:09 DEBUG  CommonBackend: Searching for local CDs
04-30 20:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Ubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Ubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Ubuntu Netbook Remix CD
04-30 20:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Kubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Kubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Kubuntu Netbook CD
04-30 20:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Xubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Xubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Mythbuntu CD
04-30 20:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Mythbuntu CD
04-30 20:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
04-30 20:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-30 20:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-30 20:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-30 20:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
04-30 20:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-30 20:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-30 20:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-30 20:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
04-30 20:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-30 20:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-30 20:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-30 20:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-30 20:09 INFO   root: Running the installer...
04-30 20:09 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\translations, languages=['en_US', 'en']
04-30 20:09 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\translations, languages=['en_US', 'en']
04-30 20:09 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=user
04-30 20:09 INFO   root: Received settings
04-30 20:09 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\translations, languages=['en_US', 'en']
04-30 20:09 DEBUG  TaskList: # Running tasklist...
04-30 20:09 DEBUG  TaskList: ## Running select_target_dir...
04-30 20:09 INFO   WindowsBackend: Installing into C:\ubuntu
04-30 20:09 DEBUG  TaskList: ## Finished select_target_dir
04-30 20:09 DEBUG  TaskList: ## Running create_dir_structure...
04-30 20:09 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-30 20:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-30 20:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-30 20:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-30 20:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-30 20:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-30 20:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-30 20:09 DEBUG  TaskList: ## Finished create_dir_structure
04-30 20:09 DEBUG  TaskList: ## Running uncompress_target_dir...
04-30 20:09 DEBUG  TaskList: ## Finished uncompress_target_dir
04-30 20:09 DEBUG  TaskList: ## Running create_uninstaller...
04-30 20:09 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\HP_Administrator\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-30 20:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-30 20:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-30 20:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-30 20:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-30 20:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
04-30 20:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-30 20:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
04-30 20:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
04-30 20:09 DEBUG  TaskList: ## Finished create_uninstaller
04-30 20:09 DEBUG  TaskList: ## Running copy_installation_files...
04-30 20:09 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-30 20:09 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\winboot -> C:\ubuntu\winboot
04-30 20:09 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-30 20:09 DEBUG  TaskList: ## Finished copy_installation_files
04-30 20:09 DEBUG  TaskList: ## Running get_iso...
04-30 20:09 DEBUG  CommonBackend: Searching for local CD
04-30 20:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp is a valid Ubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl38B.tmp\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-30 20:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-30 20:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-30 20:09 DEBUG  CommonBackend: Searching for local ISO
04-30 20:09 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-30 20:09 DEBUG  TaskList: New task get_metalink
04-30 20:09 DEBUG  TaskList: ### Running get_metalink...
04-30 20:09 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink > C:\ubuntu\install
04-30 20:09 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
04-30 20:09 DEBUG  downloader: download finished (read 26651 bytes)
04-30 20:09 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink > C:\ubuntu\install
04-30 20:09 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
04-30 20:09 DEBUG  downloader: download finished (read 562 bytes)
04-30 20:09 DEBUG  downloader: downloading http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg > C:\ubuntu\install
04-30 20:09 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
04-30 20:09 DEBUG  downloader: download finished (read 189 bytes)
04-30 20:09 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-30 20:09 INFO   saplog: Checking block bindings..
04-30 20:09 INFO   saplog: Key verified successfully.
04-30 20:09 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

04-30 20:09 DEBUG  TaskList: ### Finished get_metalink
04-30 20:09 DEBUG  TaskList: New task download
04-30 20:09 DEBUG  TaskList: ### Running download...
04-30 20:09 DEBUG  btdownloader: downloading http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
04-30 22:24 ERROR  TaskList: Traceback (most recent call last):
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


04-30 22:24 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
04-30 22:24 DEBUG  TaskList: ### Finished download
04-30 22:24 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'
04-30 22:24 DEBUG  TaskList: # Cancelling tasklist
04-30 22:24 DEBUG  TaskList: # Finished tasklist
04-30 22:24 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'
```

What went wrong?

---

### Post by Sharpie Mustache on 2010-04-30
Bump. I'm stumped. :confused:

---

### Post by Sharpie Mustache on 2010-04-30
This is a fairly big community; someone has to know what went wrong. :(

---

### Post by Sharpie Mustache on 2010-04-30
Thanks for the help guys. :(

---

### Post by Sharpie Mustache on 2010-05-01
:confused:

---

### Post by Sharpie Mustache on 2010-05-04
Bump.

---

### Post by Sharpie Mustache on 2010-05-11
Bump.

---

### Post by Mal'akh on 2010-06-03
Haha! Fail!

I'm facing the same problem right now. I'm trying to find a solution. If I do, I will post it here.

---

### Post by Mal'akh on 2010-06-03
OK I solved my problem.

Turns out even running it as an administrator doesn't work. If you're on Vista or 7 (I was on 7 x64), you need to turn off User Account Controls completely. Then I ran Wubi as administrator, and it worked! :) I'm posting this from my freshly-installed Lucid Lynx.

Hope that helped.

---

