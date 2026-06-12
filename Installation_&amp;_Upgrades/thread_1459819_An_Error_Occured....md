---
title: "An Error Occured:..."
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by Sharpie Mustache on 2010-04-21
I'm using WUBI to install Ubuntu, and I've run into this problem: When I run WUBI (Mind you, I select "Run as..." and run it as Administrator) and it's installing, I run into this little problem:
"An Error Occurred: Permission denied 
For more information, please see the log file: c:\docume~1\admini~1\locals~1\temp\wubi-9.10ubuntu1-rev160.log" around half way through the installation. What do I do? (I have the log if you need me to post it..) Quite frustrating. :confused:

---

### Post by Sef on 2010-04-22
> I have the log if you need me to post it..

Please post that log, so we can see what is going on.

---

### Post by Sharpie Mustache on 2010-04-22
Alrighty, here it is:

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
04-21 16:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-21 16:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
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
04-21 16:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink) > C:\ubuntu\install
04-21 16:58 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
04-21 16:59 DEBUG  downloader: download finished (read 26651 bytes)
04-21 16:59 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > C:\ubuntu\install
04-21 16:59 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
04-21 16:59 DEBUG  downloader: download finished (read 562 bytes)
04-21 16:59 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
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
04-21 16:59 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
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
04-21 17:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-21 17:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
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
04-21 17:14 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink) > C:\ubuntu\install
04-21 17:14 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
04-21 17:14 DEBUG  downloader: download finished (read 26651 bytes)
04-21 17:14 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > C:\ubuntu\install
04-21 17:14 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
04-21 17:14 DEBUG  downloader: download finished (read 562 bytes)
04-21 17:14 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
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
04-21 17:14 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
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

---

### Post by Sharpie Mustache on 2010-04-22
Bump.

---

