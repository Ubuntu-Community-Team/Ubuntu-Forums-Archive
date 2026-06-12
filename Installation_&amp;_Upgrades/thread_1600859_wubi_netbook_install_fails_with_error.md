---
title: "wubi netbook install fails with error"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by apple_pie on 2010-10-19
hello, I am having trouble installing Ubuntu Netbook using Wubi on an Asus Eee PC 1001P with Windows 7 Starter.

After a long time downloading the ISO, I get this message:

```


---------------------------
Ubuntu Netbook Installer
---------------------------
An error occurred:

Could not retrieve the required installation files

For more information, please see the log file: c:\users\username\appdata\local\temp\wubi-10.04.1-rev190.log
---------------------------
OK   
---------------------------

```


The log file contains the following:

```



10-18 13:10 INFO   root: === wubi 10.04.1 rev190 ===
10-18 13:10 DEBUG  root: Logfile is c:\users\username\appdata\local\temp\wubi-10.04.1-rev190.log
10-18 13:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\username\\Downloads\\wubi.exe"']
10-18 13:10 DEBUG  CommonBackend: data_dir=C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\data
10-18 13:10 DEBUG  WindowsBackend: 7z=C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\bin\7z.exe
10-18 13:10 DEBUG  CommonBackend: Fetching basic info...
10-18 13:10 DEBUG  CommonBackend: original_exe=C:\Users\username\Downloads\wubi.exe
10-18 13:10 DEBUG  CommonBackend: platform=win32
10-18 13:10 DEBUG  CommonBackend: osname=nt
10-18 13:10 DEBUG  CommonBackend: language=en_US
10-18 13:10 DEBUG  CommonBackend: encoding=cp1252
10-18 13:10 DEBUG  WindowsBackend: arch=amd64
10-18 13:10 DEBUG  CommonBackend: Parsing isolist=C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\data\isolist.ini
10-18 13:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-18 13:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-18 13:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-18 13:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-18 13:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-18 13:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-18 13:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-18 13:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-18 13:10 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-18 13:10 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-18 13:10 DEBUG  WindowsBackend: Fetching host info...
10-18 13:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-18 13:10 DEBUG  WindowsBackend: windows version=vista
10-18 13:10 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
10-18 13:10 DEBUG  WindowsBackend: windows_sp=None
10-18 13:10 DEBUG  WindowsBackend: windows_build=7600
10-18 13:10 DEBUG  WindowsBackend: gmt=-6
10-18 13:10 DEBUG  WindowsBackend: country=US
10-18 13:10 DEBUG  WindowsBackend: timezone=America/Chicago
10-18 13:10 DEBUG  WindowsBackend: windows_username=username
10-18 13:10 DEBUG  WindowsBackend: user_full_name=username
10-18 13:10 DEBUG  WindowsBackend: user_directory=C:\Users\username
10-18 13:10 DEBUG  WindowsBackend: windows_language_code=1033
10-18 13:10 DEBUG  WindowsBackend: windows_language=English
10-18 13:10 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
10-18 13:10 DEBUG  WindowsBackend: bootloader=vista
10-18 13:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 77532.390625 mb free ntfs)
10-18 13:10 DEBUG  WindowsBackend: drive=Drive(C: hd 77532.390625 mb free ntfs)
10-18 13:10 DEBUG  WindowsBackend: drive=Drive(D: hd 125587.421875 mb free ntfs)
10-18 13:10 DEBUG  WindowsBackend: uninstaller_path=None
10-18 13:10 DEBUG  WindowsBackend: previous_target_dir=None
10-18 13:10 DEBUG  WindowsBackend: previous_distro_name=None
10-18 13:10 DEBUG  WindowsBackend: keyboard_id=67699721
10-18 13:10 DEBUG  WindowsBackend: keyboard_layout=us
10-18 13:10 DEBUG  WindowsBackend: keyboard_variant=
10-18 13:10 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-18 13:10 DEBUG  CommonBackend: locale=en_US.UTF-8
10-18 13:10 DEBUG  WindowsBackend: total_memory_mb=1014.1796875
10-18 13:10 DEBUG  CommonBackend: Searching ISOs on USB devices
10-18 13:10 DEBUG  CommonBackend: Searching for local CDs
10-18 13:10 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl1B18.tmp is a valid Ubuntu CD
10-18 13:10 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl1B18.tmp is a valid Ubuntu CD
10-18 13:10 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl1B18.tmp is a valid Ubuntu Netbook CD
10-18 13:10 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl1B18.tmp is a valid Kubuntu CD
10-18 13:10 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl1B18.tmp is a valid Kubuntu CD
10-18 13:10 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl1B18.tmp is a valid Kubuntu Netbook CD
10-18 13:10 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl1B18.tmp is a valid Xubuntu CD
10-18 13:10 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl1B18.tmp is a valid Xubuntu CD
10-18 13:10 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl1B18.tmp is a valid Mythbuntu CD
10-18 13:10 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl1B18.tmp is a valid Mythbuntu CD
10-18 13:10 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-18 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
10-18 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 13:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 13:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 13:10 INFO   root: Running the installer...
10-18 13:10 DEBUG  WindowsFrontend: __init__...
10-18 13:10 DEBUG  WindowsFrontend: on_init...
10-18 13:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\translations, languages=['en_US', 'en']
10-18 13:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\translations, languages=['en_US', 'en']
10-18 13:45 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_US, locale=en_US.UTF-8, username=username
10-18 13:45 INFO   root: Received settings
10-18 13:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\translations, languages=['en_US', 'en']
10-18 13:45 DEBUG  TaskList: # Running tasklist...
10-18 13:45 DEBUG  TaskList: ## Running select_target_dir...
10-18 13:45 INFO   WindowsBackend: Installing into C:\ubuntu
10-18 13:45 DEBUG  TaskList: ## Finished select_target_dir
10-18 13:45 DEBUG  TaskList: ## Running create_dir_structure...
10-18 13:45 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-18 13:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-18 13:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-18 13:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-18 13:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-18 13:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-18 13:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-18 13:45 DEBUG  TaskList: ## Finished create_dir_structure
10-18 13:45 DEBUG  TaskList: ## Running uncompress_target_dir...
10-18 13:45 DEBUG  TaskList: ## Finished uncompress_target_dir
10-18 13:45 DEBUG  TaskList: ## Running create_uninstaller...
10-18 13:45 DEBUG  WindowsBackend: Copying uninstaller C:\Users\username\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-18 13:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-18 13:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-18 13:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
10-18 13:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
10-18 13:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
10-18 13:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
10-18 13:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-18 13:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-18 13:45 DEBUG  TaskList: ## Finished create_uninstaller
10-18 13:45 DEBUG  TaskList: ## Running copy_installation_files...
10-18 13:45 DEBUG  WindowsBackend: Copying C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-18 13:45 DEBUG  WindowsBackend: Copying C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\winboot -> C:\ubuntu\winboot
10-18 13:45 DEBUG  WindowsBackend: Copying C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
10-18 13:45 DEBUG  TaskList: ## Finished copy_installation_files
10-18 13:45 DEBUG  TaskList: ## Running get_iso...
10-18 13:45 DEBUG  CommonBackend: Searching for local CD
10-18 13:45 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl1B18.tmp is a valid Ubuntu Netbook CD
10-18 13:45 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl1B18.tmp\casper\filesystem.squashfs
10-18 13:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-18 13:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 13:45 DEBUG  CommonBackend: Searching for local ISO
10-18 13:45 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\Users\username\Downloads\ubuntu-10.10-netbook-i386.iso
10-18 13:45 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\username\Downloads\ubuntu-10.10-netbook-i386.iso
10-18 13:45 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
10-18 13:45 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
10-18 13:45 DEBUG  Distro: wrong version: 10.10 != 10.04.1
10-18 13:45 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-18 13:45 DEBUG  TaskList: New task get_metalink
10-18 13:45 DEBUG  TaskList: ### Running get_metalink...
10-18 13:45 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.metalink) > C:\ubuntu\install
10-18 13:45 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-netbook-i386.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.metalink, basename=ubuntu-10.04-netbook-i386.metalink, length=36061, text=None
10-18 13:45 DEBUG  downloader: download finished (read 36061 bytes)
10-18 13:45 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > C:\ubuntu\install
10-18 13:45 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=651, text=None
10-18 13:45 DEBUG  downloader: download finished (read 651 bytes)
10-18 13:45 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
10-18 13:45 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
10-18 13:45 DEBUG  downloader: download finished (read 189 bytes)
10-18 13:45 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
10-18 13:45 INFO   saplog: Checking block bindings..
10-18 13:45 INFO   saplog: Key verified successfully.
10-18 13:45 DEBUG  CommonBackend: metalink md5sums:
a293f05f7be5e61937b1c277c6a69262  ubuntu-10.04-netbook-armel+dove.metalink
dece0df9abb10efb1f590f759cccf340  ubuntu-10.04-netbook-armel+imx51.metalink
a3805816968bf7199e080ba653a19ac1  ubuntu-10.04-netbook-i386.metalink
94706d50d0375fe01b4b480a9c875a7f  ubuntu-10.04.1-alternate-amd64.metalink
7e94a4ebedb1dcfc4fe376f5a96c45aa  ubuntu-10.04.1-alternate-i386.metalink
974c01945586ebcbb672f11ce6df0e39  ubuntu-10.04.1-desktop-amd64.metalink
b3b2f75f70c5216d1325a5a02f3770ce  ubuntu-10.04.1-desktop-i386.metalink
8b0786e4978a123ce91e87181eb0f570  ubuntu-10.04.1-server-amd64.metalink
56dff8fca4d2612eb035a909092f5016  ubuntu-10.04.1-server-i386.metalink

10-18 13:45 DEBUG  TaskList: ### Finished get_metalink
10-18 13:45 DEBUG  TaskList: New task download
10-18 13:45 DEBUG  TaskList: ### Running download...
10-18 13:45 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04.1/ubuntu-10.04-netbook-i386.iso.torrent](http://releases.ubuntu.com/10.04.1/ubuntu-10.04-netbook-i386.iso.torrent) > C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 14:04 DEBUG  TaskList: ### Finished download
10-18 14:04 DEBUG  TaskList: New task check_iso
10-18 14:04 DEBUG  TaskList: ### Running check_iso...
10-18 14:04 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 14:04 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 14:04 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 14:04 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.04 "Lucid Lynx" - Release i386 (20100429.4)
10-18 14:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.04', 'build': '20100429.4', 'codename': 'Lucid Lynx', 'arch': 'i386'}
10-18 14:04 DEBUG  Distro: wrong version: 10.04 != 10.04.1
10-18 14:04 DEBUG  TaskList: ### Finished check_iso
10-18 14:04 DEBUG  TaskList: New task download
10-18 14:04 DEBUG  TaskList: ### Running download...
10-18 14:04 DEBUG  downloader: downloading [http://ubuntu.saudi.net.sa/releases/10.04.1/ubuntu-10.04-netbook-i386.iso](http://ubuntu.saudi.net.sa/releases/10.04.1/ubuntu-10.04-netbook-i386.iso) > C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 14:04 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso, url=http://ubuntu.saudi.net.sa/releases/10.04.1/ubuntu-10.04-netbook-i386.iso, basename=ubuntu-10.04-netbook-i386.iso, length=733837312, text=None
10-18 14:29 DEBUG  TaskList: ### Finished download
10-18 14:29 DEBUG  downloader: download finished (read 733837312 bytes)
10-18 14:29 DEBUG  TaskList: New task check_iso
10-18 14:29 DEBUG  TaskList: ### Running check_iso...
10-18 14:29 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 14:29 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 14:29 DEBUG  Distro: wrong version: 10.04 != 10.04.1
10-18 14:29 DEBUG  TaskList: ### Finished check_iso
10-18 14:29 DEBUG  TaskList: New task download
10-18 14:29 DEBUG  TaskList: ### Running download...
10-18 14:29 DEBUG  downloader: downloading [http://ftp.riken.jp/Linux/ubuntu-iso/CDs/10.04.1/ubuntu-10.04-netbook-i386.iso](http://ftp.riken.jp/Linux/ubuntu-iso/CDs/10.04.1/ubuntu-10.04-netbook-i386.iso) > C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 14:29 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso, url=http://ftp.riken.jp/Linux/ubuntu-iso/CDs/10.04.1/ubuntu-10.04-netbook-i386.iso, basename=ubuntu-10.04-netbook-i386.iso, length=733837312, text=None
10-18 15:18 DEBUG  TaskList: ### Finished download
10-18 15:18 DEBUG  downloader: download finished (read 733837312 bytes)
10-18 15:18 DEBUG  TaskList: New task check_iso
10-18 15:18 DEBUG  TaskList: ### Running check_iso...
10-18 15:18 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 15:18 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 15:18 DEBUG  Distro: wrong version: 10.04 != 10.04.1
10-18 15:18 DEBUG  TaskList: ### Finished check_iso
10-18 15:18 DEBUG  TaskList: New task download
10-18 15:18 DEBUG  TaskList: ### Running download...
10-18 15:18 DEBUG  downloader: downloading [http://ftp.heanet.ie/pub/ubuntu-releases/10.04.1/ubuntu-10.04-netbook-i386.iso](http://ftp.heanet.ie/pub/ubuntu-releases/10.04.1/ubuntu-10.04-netbook-i386.iso) > C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 15:18 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso, url=http://ftp.heanet.ie/pub/ubuntu-releases/10.04.1/ubuntu-10.04-netbook-i386.iso, basename=ubuntu-10.04-netbook-i386.iso, length=733837312, text=None
10-18 15:38 DEBUG  TaskList: ### Finished download
10-18 15:38 DEBUG  downloader: download finished (read 733837312 bytes)
10-18 15:38 DEBUG  TaskList: New task check_iso
10-18 15:38 DEBUG  TaskList: ### Running check_iso...
10-18 15:38 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 15:38 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 15:38 DEBUG  Distro: wrong version: 10.04 != 10.04.1
10-18 15:38 DEBUG  TaskList: ### Finished check_iso
10-18 15:38 DEBUG  TaskList: New task download
10-18 15:38 DEBUG  TaskList: ### Running download...
10-18 15:38 DEBUG  downloader: downloading [http://ftp.halifax.rwth-aachen.de/ubuntu-releases/10.04.1/ubuntu-10.04-netbook-i386.iso](http://ftp.halifax.rwth-aachen.de/ubuntu-releases/10.04.1/ubuntu-10.04-netbook-i386.iso) > C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 15:38 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso, url=http://ftp.halifax.rwth-aachen.de/ubuntu-releases/10.04.1/ubuntu-10.04-netbook-i386.iso, basename=ubuntu-10.04-netbook-i386.iso, length=733837312, text=None
10-18 16:03 DEBUG  TaskList: ### Finished download
10-18 16:03 DEBUG  downloader: download finished (read 733837312 bytes)
10-18 16:03 DEBUG  TaskList: New task check_iso
10-18 16:03 DEBUG  TaskList: ### Running check_iso...
10-18 16:03 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 16:03 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 16:03 DEBUG  Distro: wrong version: 10.04 != 10.04.1
10-18 16:03 DEBUG  TaskList: ### Finished check_iso
10-18 16:03 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
10-18 16:03 DEBUG  TaskList: # Cancelling tasklist
10-18 16:03 DEBUG  TaskList: # Finished tasklist
10-18 16:03 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
10-18 16:03 INFO   root: === wubi 10.04.1 rev190 ===
10-18 16:03 DEBUG  root: Logfile is c:\users\username\appdata\local\temp\wubi-10.04.1-rev190.log
10-18 16:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\username\\Downloads\\wubi.exe"']
10-18 16:03 DEBUG  CommonBackend: data_dir=C:\Users\username\AppData\Local\Temp\pyl3244.tmp\data
10-18 16:03 DEBUG  WindowsBackend: 7z=C:\Users\username\AppData\Local\Temp\pyl3244.tmp\bin\7z.exe
10-18 16:03 DEBUG  CommonBackend: Fetching basic info...
10-18 16:03 DEBUG  CommonBackend: original_exe=C:\Users\username\Downloads\wubi.exe
10-18 16:03 DEBUG  CommonBackend: platform=win32
10-18 16:03 DEBUG  CommonBackend: osname=nt
10-18 16:03 DEBUG  CommonBackend: language=en_US
10-18 16:03 DEBUG  CommonBackend: encoding=cp1252
10-18 16:03 DEBUG  WindowsBackend: arch=amd64
10-18 16:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\username\AppData\Local\Temp\pyl3244.tmp\data\isolist.ini
10-18 16:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-18 16:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-18 16:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-18 16:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-18 16:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-18 16:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-18 16:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-18 16:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-18 16:03 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-18 16:03 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-18 16:03 DEBUG  WindowsBackend: Fetching host info...
10-18 16:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-18 16:03 DEBUG  WindowsBackend: windows version=vista
10-18 16:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
10-18 16:03 DEBUG  WindowsBackend: windows_sp=None
10-18 16:03 DEBUG  WindowsBackend: windows_build=7600
10-18 16:03 DEBUG  WindowsBackend: gmt=-6
10-18 16:03 DEBUG  WindowsBackend: country=US
10-18 16:03 DEBUG  WindowsBackend: timezone=America/Chicago
10-18 16:03 DEBUG  WindowsBackend: windows_username=username
10-18 16:03 DEBUG  WindowsBackend: user_full_name=username
10-18 16:03 DEBUG  WindowsBackend: user_directory=C:\Users\username
10-18 16:03 DEBUG  WindowsBackend: windows_language_code=1033
10-18 16:03 DEBUG  WindowsBackend: windows_language=English
10-18 16:03 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
10-18 16:03 DEBUG  WindowsBackend: bootloader=vista
10-18 16:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 76937.1328125 mb free ntfs)
10-18 16:03 DEBUG  WindowsBackend: drive=Drive(C: hd 76937.1328125 mb free ntfs)
10-18 16:03 DEBUG  WindowsBackend: drive=Drive(D: hd 125587.421875 mb free ntfs)
10-18 16:03 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-18 16:03 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-18 16:03 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
10-18 16:03 DEBUG  WindowsBackend: keyboard_id=67699721
10-18 16:03 DEBUG  WindowsBackend: keyboard_layout=us
10-18 16:03 DEBUG  WindowsBackend: keyboard_variant=
10-18 16:03 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-18 16:03 DEBUG  CommonBackend: locale=en_US.UTF-8
10-18 16:03 DEBUG  WindowsBackend: total_memory_mb=1014.1796875
10-18 16:03 DEBUG  CommonBackend: Searching ISOs on USB devices
10-18 16:03 DEBUG  CommonBackend: Searching for local CDs
10-18 16:03 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Ubuntu CD
10-18 16:03 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Ubuntu CD
10-18 16:03 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Ubuntu Netbook CD
10-18 16:03 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Kubuntu CD
10-18 16:03 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Kubuntu CD
10-18 16:03 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Kubuntu Netbook CD
10-18 16:03 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Xubuntu CD
10-18 16:03 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Xubuntu CD
10-18 16:03 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Mythbuntu CD
10-18 16:03 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Mythbuntu CD
10-18 16:03 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-18 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
10-18 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:03 INFO   root: Already installed, running the uninstaller...
10-18 16:03 INFO   root: Running the uninstaller...
10-18 16:03 INFO   CommonBackend: This is the uninstaller running
10-18 16:03 DEBUG  WindowsFrontend: __init__...
10-18 16:03 DEBUG  WindowsFrontend: on_init...
10-18 16:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\username\AppData\Local\Temp\pyl3244.tmp\translations, languages=['en_US', 'en']
10-18 16:04 INFO   root: Received settings
10-18 16:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\username\AppData\Local\Temp\pyl3244.tmp\translations, languages=['en_US', 'en']
10-18 16:04 DEBUG  TaskList: # Running tasklist...
10-18 16:04 DEBUG  TaskList: ## Running Backup ISO...
10-18 16:04 DEBUG  TaskList: ## Finished Backup ISO
10-18 16:04 DEBUG  TaskList: ## Running Remove bootloader entry...
10-18 16:04 DEBUG  WindowsBackend: Could not find bcd id
10-18 16:04 DEBUG  WindowsBackend: undo_bootini C:
10-18 16:04 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 76937.1328125 mb free ntfs)
10-18 16:04 DEBUG  WindowsBackend: undo_bootini D:
10-18 16:04 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 125587.421875 mb free ntfs)
10-18 16:04 DEBUG  TaskList: ## Finished Remove bootloader entry
10-18 16:04 DEBUG  TaskList: ## Running Remove target dir...
10-18 16:04 DEBUG  CommonBackend: Deleting C:\ubuntu
10-18 16:04 DEBUG  TaskList: ## Finished Remove target dir
10-18 16:04 DEBUG  TaskList: ## Running Remove registry key...
10-18 16:04 DEBUG  TaskList: ## Finished Remove registry key
10-18 16:04 DEBUG  TaskList: # Finished tasklist
10-18 16:04 INFO   root: Almost finished uninstalling
10-18 16:04 INFO   root: Finished uninstallation
10-18 16:04 DEBUG  CommonBackend: Fetching basic info...
10-18 16:04 DEBUG  CommonBackend: original_exe=C:\Users\username\Downloads\wubi.exe
10-18 16:04 DEBUG  CommonBackend: platform=win32
10-18 16:04 DEBUG  CommonBackend: osname=nt
10-18 16:04 DEBUG  WindowsBackend: arch=amd64
10-18 16:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\username\AppData\Local\Temp\pyl3244.tmp\data\isolist.ini
10-18 16:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-18 16:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-18 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-18 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-18 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-18 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-18 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-18 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-18 16:04 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-18 16:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-18 16:04 DEBUG  WindowsBackend: Fetching host info...
10-18 16:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-18 16:04 DEBUG  WindowsBackend: windows version=vista
10-18 16:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
10-18 16:04 DEBUG  WindowsBackend: windows_sp=None
10-18 16:04 DEBUG  WindowsBackend: windows_build=7600
10-18 16:04 DEBUG  WindowsBackend: gmt=-6
10-18 16:04 DEBUG  WindowsBackend: country=US
10-18 16:04 DEBUG  WindowsBackend: timezone=America/Chicago
10-18 16:04 DEBUG  WindowsBackend: windows_username=username
10-18 16:04 DEBUG  WindowsBackend: user_full_name=username
10-18 16:04 DEBUG  WindowsBackend: user_directory=C:\Users\username
10-18 16:04 DEBUG  WindowsBackend: windows_language_code=1033
10-18 16:04 DEBUG  WindowsBackend: windows_language=English
10-18 16:04 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
10-18 16:04 DEBUG  WindowsBackend: bootloader=vista
10-18 16:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 76938.6796875 mb free ntfs)
10-18 16:04 DEBUG  WindowsBackend: drive=Drive(C: hd 76938.6796875 mb free ntfs)
10-18 16:04 DEBUG  WindowsBackend: drive=Drive(D: hd 125587.421875 mb free ntfs)
10-18 16:04 DEBUG  WindowsBackend: uninstaller_path=None
10-18 16:04 DEBUG  WindowsBackend: previous_target_dir=None
10-18 16:04 DEBUG  WindowsBackend: previous_distro_name=None
10-18 16:04 DEBUG  WindowsBackend: keyboard_id=67699721
10-18 16:04 DEBUG  WindowsBackend: keyboard_layout=us
10-18 16:04 DEBUG  WindowsBackend: keyboard_variant=
10-18 16:04 DEBUG  WindowsBackend: total_memory_mb=1014.1796875
10-18 16:04 DEBUG  CommonBackend: Searching ISOs on USB devices
10-18 16:04 DEBUG  CommonBackend: Searching for local CDs
10-18 16:04 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Ubuntu CD
10-18 16:04 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Ubuntu CD
10-18 16:04 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Ubuntu Netbook CD
10-18 16:04 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Kubuntu CD
10-18 16:04 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Kubuntu CD
10-18 16:04 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Kubuntu Netbook CD
10-18 16:04 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Xubuntu CD
10-18 16:04 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Xubuntu CD
10-18 16:04 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Mythbuntu CD
10-18 16:04 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl3244.tmp is a valid Mythbuntu CD
10-18 16:04 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl3244.tmp\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-18 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
10-18 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:04 INFO   root: Running the installer...
10-18 16:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\username\AppData\Local\Temp\pyl3244.tmp\translations, languages=['en_US', 'en']
10-18 16:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\username\AppData\Local\Temp\pyl3244.tmp\translations, languages=['en_US', 'en']
10-18 16:04 INFO   WindowsFrontend: Operation cancelled
10-18 16:04 DEBUG  WindowsFrontend: frontend.quit
10-18 16:04 DEBUG  WindowsFrontend: frontend.on_quit
10-18 16:04 DEBUG  root: application.on_quit
10-18 16:04 INFO   root: sys.exit
10-18 16:06 INFO   root: === wubi 10.04.1 rev190 ===
10-18 16:06 DEBUG  root: Logfile is c:\users\username\appdata\local\temp\wubi-10.04.1-rev190.log
10-18 16:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\username\\Downloads\\wubi.exe"']
10-18 16:06 DEBUG  CommonBackend: data_dir=C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\data
10-18 16:06 DEBUG  WindowsBackend: 7z=C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\bin\7z.exe
10-18 16:06 DEBUG  CommonBackend: Fetching basic info...
10-18 16:06 DEBUG  CommonBackend: original_exe=C:\Users\username\Downloads\wubi.exe
10-18 16:06 DEBUG  CommonBackend: platform=win32
10-18 16:06 DEBUG  CommonBackend: osname=nt
10-18 16:06 DEBUG  CommonBackend: language=en_US
10-18 16:06 DEBUG  CommonBackend: encoding=cp1252
10-18 16:06 DEBUG  WindowsBackend: arch=amd64
10-18 16:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\data\isolist.ini
10-18 16:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-18 16:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-18 16:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-18 16:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-18 16:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-18 16:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-18 16:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-18 16:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-18 16:06 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-18 16:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-18 16:06 DEBUG  WindowsBackend: Fetching host info...
10-18 16:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-18 16:06 DEBUG  WindowsBackend: windows version=vista
10-18 16:06 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
10-18 16:06 DEBUG  WindowsBackend: windows_sp=None
10-18 16:06 DEBUG  WindowsBackend: windows_build=7600
10-18 16:06 DEBUG  WindowsBackend: gmt=-6
10-18 16:06 DEBUG  WindowsBackend: country=US
10-18 16:06 DEBUG  WindowsBackend: timezone=America/Chicago
10-18 16:06 DEBUG  WindowsBackend: windows_username=username
10-18 16:06 DEBUG  WindowsBackend: user_full_name=username
10-18 16:06 DEBUG  WindowsBackend: user_directory=C:\Users\username
10-18 16:06 DEBUG  WindowsBackend: windows_language_code=1033
10-18 16:06 DEBUG  WindowsBackend: windows_language=English
10-18 16:06 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
10-18 16:06 DEBUG  WindowsBackend: bootloader=vista
10-18 16:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 76938.1601563 mb free ntfs)
10-18 16:06 DEBUG  WindowsBackend: drive=Drive(C: hd 76938.1601563 mb free ntfs)
10-18 16:06 DEBUG  WindowsBackend: drive=Drive(D: hd 125587.421875 mb free ntfs)
10-18 16:06 DEBUG  WindowsBackend: uninstaller_path=None
10-18 16:06 DEBUG  WindowsBackend: previous_target_dir=None
10-18 16:06 DEBUG  WindowsBackend: previous_distro_name=None
10-18 16:06 DEBUG  WindowsBackend: keyboard_id=67699721
10-18 16:06 DEBUG  WindowsBackend: keyboard_layout=us
10-18 16:06 DEBUG  WindowsBackend: keyboard_variant=
10-18 16:06 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-18 16:06 DEBUG  CommonBackend: locale=en_US.UTF-8
10-18 16:06 DEBUG  WindowsBackend: total_memory_mb=1014.1796875
10-18 16:06 DEBUG  CommonBackend: Searching ISOs on USB devices
10-18 16:06 DEBUG  CommonBackend: Searching for local CDs
10-18 16:06 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp is a valid Ubuntu CD
10-18 16:06 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp is a valid Ubuntu CD
10-18 16:06 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp is a valid Ubuntu Netbook CD
10-18 16:06 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp is a valid Kubuntu CD
10-18 16:06 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp is a valid Kubuntu CD
10-18 16:06 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp is a valid Kubuntu Netbook CD
10-18 16:06 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp is a valid Xubuntu CD
10-18 16:06 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp is a valid Xubuntu CD
10-18 16:06 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp is a valid Mythbuntu CD
10-18 16:06 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp is a valid Mythbuntu CD
10-18 16:06 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-18 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
10-18 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:06 INFO   root: Running the installer...
10-18 16:06 DEBUG  WindowsFrontend: __init__...
10-18 16:06 DEBUG  WindowsFrontend: on_init...
10-18 16:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\translations, languages=['en_US', 'en']
10-18 16:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\translations, languages=['en_US', 'en']
10-18 16:07 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_US, locale=en_US.UTF-8, username=username
10-18 16:07 INFO   root: Received settings
10-18 16:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\translations, languages=['en_US', 'en']
10-18 16:07 DEBUG  TaskList: # Running tasklist...
10-18 16:07 DEBUG  TaskList: ## Running select_target_dir...
10-18 16:07 INFO   WindowsBackend: Installing into C:\ubuntu
10-18 16:07 DEBUG  TaskList: ## Finished select_target_dir
10-18 16:07 DEBUG  TaskList: ## Running create_dir_structure...
10-18 16:07 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-18 16:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-18 16:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-18 16:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-18 16:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-18 16:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-18 16:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-18 16:07 DEBUG  TaskList: ## Finished create_dir_structure
10-18 16:07 DEBUG  TaskList: ## Running uncompress_target_dir...
10-18 16:07 DEBUG  TaskList: ## Finished uncompress_target_dir
10-18 16:07 DEBUG  TaskList: ## Running create_uninstaller...
10-18 16:07 DEBUG  WindowsBackend: Copying uninstaller C:\Users\username\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-18 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-18 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-18 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
10-18 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
10-18 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
10-18 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
10-18 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-18 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-18 16:07 DEBUG  TaskList: ## Finished create_uninstaller
10-18 16:07 DEBUG  TaskList: ## Running copy_installation_files...
10-18 16:07 DEBUG  WindowsBackend: Copying C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-18 16:07 DEBUG  WindowsBackend: Copying C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\winboot -> C:\ubuntu\winboot
10-18 16:07 DEBUG  WindowsBackend: Copying C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
10-18 16:07 DEBUG  TaskList: ## Finished copy_installation_files
10-18 16:07 DEBUG  TaskList: ## Running get_iso...
10-18 16:07 DEBUG  CommonBackend: Searching for local CD
10-18 16:07 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp is a valid Ubuntu Netbook CD
10-18 16:07 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pyl4FC2.tmp\casper\filesystem.squashfs
10-18 16:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-18 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 16:07 DEBUG  CommonBackend: Searching for local ISO
10-18 16:07 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\Users\username\Downloads\ubuntu-10.10-netbook-i386.iso
10-18 16:07 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\username\Downloads\ubuntu-10.10-netbook-i386.iso
10-18 16:07 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
10-18 16:07 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
10-18 16:07 DEBUG  Distro: wrong version: 10.10 != 10.04.1
10-18 16:07 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-18 16:07 DEBUG  TaskList: New task get_metalink
10-18 16:07 DEBUG  TaskList: ### Running get_metalink...
10-18 16:07 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.metalink) > C:\ubuntu\install
10-18 16:07 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-netbook-i386.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.metalink, basename=ubuntu-10.04-netbook-i386.metalink, length=36061, text=None
10-18 16:07 DEBUG  downloader: download finished (read 36061 bytes)
10-18 16:07 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > C:\ubuntu\install
10-18 16:07 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=651, text=None
10-18 16:07 DEBUG  downloader: download finished (read 651 bytes)
10-18 16:07 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
10-18 16:07 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
10-18 16:07 DEBUG  downloader: download finished (read 189 bytes)
10-18 16:07 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
10-18 16:07 INFO   saplog: Checking block bindings..
10-18 16:07 INFO   saplog: Key verified successfully.
10-18 16:07 DEBUG  CommonBackend: metalink md5sums:
a293f05f7be5e61937b1c277c6a69262  ubuntu-10.04-netbook-armel+dove.metalink
dece0df9abb10efb1f590f759cccf340  ubuntu-10.04-netbook-armel+imx51.metalink
a3805816968bf7199e080ba653a19ac1  ubuntu-10.04-netbook-i386.metalink
94706d50d0375fe01b4b480a9c875a7f  ubuntu-10.04.1-alternate-amd64.metalink
7e94a4ebedb1dcfc4fe376f5a96c45aa  ubuntu-10.04.1-alternate-i386.metalink
974c01945586ebcbb672f11ce6df0e39  ubuntu-10.04.1-desktop-amd64.metalink
b3b2f75f70c5216d1325a5a02f3770ce  ubuntu-10.04.1-desktop-i386.metalink
8b0786e4978a123ce91e87181eb0f570  ubuntu-10.04.1-server-amd64.metalink
56dff8fca4d2612eb035a909092f5016  ubuntu-10.04.1-server-i386.metalink

10-18 16:07 DEBUG  TaskList: ### Finished get_metalink
10-18 16:07 DEBUG  TaskList: New task download
10-18 16:07 DEBUG  TaskList: ### Running download...
10-18 16:07 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04.1/ubuntu-10.04-netbook-i386.iso.torrent](http://releases.ubuntu.com/10.04.1/ubuntu-10.04-netbook-i386.iso.torrent) > C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 16:53 DEBUG  TaskList: ### Finished download
10-18 16:53 DEBUG  TaskList: New task check_iso
10-18 16:53 DEBUG  TaskList: ### Running check_iso...
10-18 16:53 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 16:53 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 16:53 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 16:53 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.04 "Lucid Lynx" - Release i386 (20100429.4)
10-18 16:53 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.04', 'build': '20100429.4', 'codename': 'Lucid Lynx', 'arch': 'i386'}
10-18 16:53 DEBUG  Distro: wrong version: 10.04 != 10.04.1
10-18 16:53 DEBUG  TaskList: ### Finished check_iso
10-18 16:53 DEBUG  TaskList: New task download
10-18 16:53 DEBUG  TaskList: ### Running download...
10-18 16:53 DEBUG  downloader: downloading [http://ubuntu.saudi.net.sa/releases/10.04.1/ubuntu-10.04-netbook-i386.iso](http://ubuntu.saudi.net.sa/releases/10.04.1/ubuntu-10.04-netbook-i386.iso) > C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-18 16:53 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso, url=http://ubuntu.saudi.net.sa/releases/10.04.1/ubuntu-10.04-netbook-i386.iso, basename=ubuntu-10.04-netbook-i386.iso, length=733837312, text=None
10-18 17:36 INFO   WindowsFrontend: Operation cancelled
10-18 17:36 DEBUG  WindowsFrontend: frontend.quit
10-18 17:36 DEBUG  WindowsFrontend: frontend.on_quit
10-18 17:36 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
10-18 17:36 DEBUG  TaskList: # Cancelling tasklist
10-18 17:36 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
10-18 17:36 DEBUG  root: application.on_quit
10-18 17:36 DEBUG  root: Forceful exit
10-18 17:36 INFO   root: sys.exit
10-18 23:16 INFO   root: === wubi 10.04.1 rev190 ===
10-18 23:16 DEBUG  root: Logfile is c:\users\username\appdata\local\temp\wubi-10.04.1-rev190.log
10-18 23:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\username\\Downloads\\wubi.exe"']
10-18 23:16 DEBUG  CommonBackend: data_dir=C:\Users\username\AppData\Local\Temp\pylABBE.tmp\data
10-18 23:16 DEBUG  WindowsBackend: 7z=C:\Users\username\AppData\Local\Temp\pylABBE.tmp\bin\7z.exe
10-18 23:16 DEBUG  CommonBackend: Fetching basic info...
10-18 23:16 DEBUG  CommonBackend: original_exe=C:\Users\username\Downloads\wubi.exe
10-18 23:16 DEBUG  CommonBackend: platform=win32
10-18 23:16 DEBUG  CommonBackend: osname=nt
10-18 23:16 DEBUG  CommonBackend: language=en_US
10-18 23:16 DEBUG  CommonBackend: encoding=cp1252
10-18 23:16 DEBUG  WindowsBackend: arch=amd64
10-18 23:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\username\AppData\Local\Temp\pylABBE.tmp\data\isolist.ini
10-18 23:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-18 23:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-18 23:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-18 23:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-18 23:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-18 23:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-18 23:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-18 23:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-18 23:16 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-18 23:16 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-18 23:16 DEBUG  WindowsBackend: Fetching host info...
10-18 23:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-18 23:16 DEBUG  WindowsBackend: windows version=vista
10-18 23:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
10-18 23:16 DEBUG  WindowsBackend: windows_sp=None
10-18 23:16 DEBUG  WindowsBackend: windows_build=7600
10-18 23:16 DEBUG  WindowsBackend: gmt=-6
10-18 23:16 DEBUG  WindowsBackend: country=US
10-18 23:16 DEBUG  WindowsBackend: timezone=America/Chicago
10-18 23:16 DEBUG  WindowsBackend: windows_username=username
10-18 23:16 DEBUG  WindowsBackend: user_full_name=username
10-18 23:16 DEBUG  WindowsBackend: user_directory=C:\Users\username
10-18 23:16 DEBUG  WindowsBackend: windows_language_code=1033
10-18 23:16 DEBUG  WindowsBackend: windows_language=English
10-18 23:16 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
10-18 23:16 DEBUG  WindowsBackend: bootloader=vista
10-18 23:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 76581.6679688 mb free ntfs)
10-18 23:16 DEBUG  WindowsBackend: drive=Drive(C: hd 76581.6679688 mb free ntfs)
10-18 23:16 DEBUG  WindowsBackend: drive=Drive(D: hd 125322.253906 mb free ntfs)
10-18 23:16 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-18 23:16 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-18 23:16 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
10-18 23:16 DEBUG  WindowsBackend: keyboard_id=67699721
10-18 23:16 DEBUG  WindowsBackend: keyboard_layout=us
10-18 23:16 DEBUG  WindowsBackend: keyboard_variant=
10-18 23:16 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-18 23:16 DEBUG  CommonBackend: locale=en_US.UTF-8
10-18 23:16 DEBUG  WindowsBackend: total_memory_mb=1014.1796875
10-18 23:16 DEBUG  CommonBackend: Searching ISOs on USB devices
10-18 23:16 DEBUG  CommonBackend: Searching for local CDs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Ubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Ubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Ubuntu Netbook CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Kubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Kubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Kubuntu Netbook CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Xubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Xubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Mythbuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Mythbuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 INFO   root: Already installed, running the uninstaller...
10-18 23:16 INFO   root: Running the uninstaller...
10-18 23:16 INFO   CommonBackend: This is the uninstaller running
10-18 23:16 DEBUG  WindowsFrontend: __init__...
10-18 23:16 DEBUG  WindowsFrontend: on_init...
10-18 23:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\username\AppData\Local\Temp\pylABBE.tmp\translations, languages=['en_US', 'en']
10-18 23:16 INFO   root: Received settings
10-18 23:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\username\AppData\Local\Temp\pylABBE.tmp\translations, languages=['en_US', 'en']
10-18 23:16 DEBUG  TaskList: # Running tasklist...
10-18 23:16 DEBUG  TaskList: ## Running Backup ISO...
10-18 23:16 DEBUG  TaskList: ## Finished Backup ISO
10-18 23:16 DEBUG  TaskList: ## Running Remove bootloader entry...
10-18 23:16 DEBUG  WindowsBackend: Could not find bcd id
10-18 23:16 DEBUG  WindowsBackend: undo_bootini C:
10-18 23:16 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 76581.6679688 mb free ntfs)
10-18 23:16 DEBUG  WindowsBackend: undo_bootini D:
10-18 23:16 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 125322.253906 mb free ntfs)
10-18 23:16 DEBUG  TaskList: ## Finished Remove bootloader entry
10-18 23:16 DEBUG  TaskList: ## Running Remove target dir...
10-18 23:16 DEBUG  CommonBackend: Deleting C:\ubuntu
10-18 23:16 DEBUG  TaskList: ## Finished Remove target dir
10-18 23:16 DEBUG  TaskList: ## Running Remove registry key...
10-18 23:16 DEBUG  TaskList: ## Finished Remove registry key
10-18 23:16 DEBUG  TaskList: # Finished tasklist
10-18 23:16 INFO   root: Almost finished uninstalling
10-18 23:16 INFO   root: Finished uninstallation
10-18 23:16 DEBUG  CommonBackend: Fetching basic info...
10-18 23:16 DEBUG  CommonBackend: original_exe=C:\Users\username\Downloads\wubi.exe
10-18 23:16 DEBUG  CommonBackend: platform=win32
10-18 23:16 DEBUG  CommonBackend: osname=nt
10-18 23:16 DEBUG  WindowsBackend: arch=amd64
10-18 23:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\username\AppData\Local\Temp\pylABBE.tmp\data\isolist.ini
10-18 23:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-18 23:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-18 23:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-18 23:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-18 23:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-18 23:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-18 23:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-18 23:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-18 23:16 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-18 23:16 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-18 23:16 DEBUG  WindowsBackend: Fetching host info...
10-18 23:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-18 23:16 DEBUG  WindowsBackend: windows version=vista
10-18 23:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
10-18 23:16 DEBUG  WindowsBackend: windows_sp=None
10-18 23:16 DEBUG  WindowsBackend: windows_build=7600
10-18 23:16 DEBUG  WindowsBackend: gmt=-6
10-18 23:16 DEBUG  WindowsBackend: country=US
10-18 23:16 DEBUG  WindowsBackend: timezone=America/Chicago
10-18 23:16 DEBUG  WindowsBackend: windows_username=username
10-18 23:16 DEBUG  WindowsBackend: user_full_name=username
10-18 23:16 DEBUG  WindowsBackend: user_directory=C:\Users\username
10-18 23:16 DEBUG  WindowsBackend: windows_language_code=1033
10-18 23:16 DEBUG  WindowsBackend: windows_language=English
10-18 23:16 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
10-18 23:16 DEBUG  WindowsBackend: bootloader=vista
10-18 23:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 76771.3085938 mb free ntfs)
10-18 23:16 DEBUG  WindowsBackend: drive=Drive(C: hd 76771.3085938 mb free ntfs)
10-18 23:16 DEBUG  WindowsBackend: drive=Drive(D: hd 125312.253906 mb free ntfs)
10-18 23:16 DEBUG  WindowsBackend: uninstaller_path=None
10-18 23:16 DEBUG  WindowsBackend: previous_target_dir=None
10-18 23:16 DEBUG  WindowsBackend: previous_distro_name=None
10-18 23:16 DEBUG  WindowsBackend: keyboard_id=67699721
10-18 23:16 DEBUG  WindowsBackend: keyboard_layout=us
10-18 23:16 DEBUG  WindowsBackend: keyboard_variant=
10-18 23:16 DEBUG  WindowsBackend: total_memory_mb=1014.1796875
10-18 23:16 DEBUG  CommonBackend: Searching ISOs on USB devices
10-18 23:16 DEBUG  CommonBackend: Searching for local CDs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Ubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Ubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Ubuntu Netbook CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Kubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Kubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Kubuntu Netbook CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Xubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Xubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Mythbuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Mythbuntu CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 INFO   root: Running the installer...
10-18 23:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\username\AppData\Local\Temp\pylABBE.tmp\translations, languages=['en_US', 'en']
10-18 23:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\username\AppData\Local\Temp\pylABBE.tmp\translations, languages=['en_US', 'en']
10-18 23:16 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_US, locale=en_US.UTF-8, username=username
10-18 23:16 INFO   root: Received settings
10-18 23:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\username\AppData\Local\Temp\pylABBE.tmp\translations, languages=['en_US', 'en']
10-18 23:16 DEBUG  TaskList: # Running tasklist...
10-18 23:16 DEBUG  TaskList: ## Running select_target_dir...
10-18 23:16 INFO   WindowsBackend: Installing into C:\ubuntu
10-18 23:16 DEBUG  TaskList: ## Finished select_target_dir
10-18 23:16 DEBUG  TaskList: ## Running create_dir_structure...
10-18 23:16 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-18 23:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-18 23:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-18 23:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-18 23:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-18 23:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-18 23:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-18 23:16 DEBUG  TaskList: ## Finished create_dir_structure
10-18 23:16 DEBUG  TaskList: ## Running uncompress_target_dir...
10-18 23:16 DEBUG  TaskList: ## Finished uncompress_target_dir
10-18 23:16 DEBUG  TaskList: ## Running create_uninstaller...
10-18 23:16 DEBUG  WindowsBackend: Copying uninstaller C:\Users\username\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-18 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-18 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-18 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
10-18 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
10-18 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
10-18 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
10-18 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-18 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-18 23:16 DEBUG  TaskList: ## Finished create_uninstaller
10-18 23:16 DEBUG  TaskList: ## Running copy_installation_files...
10-18 23:16 DEBUG  WindowsBackend: Copying C:\Users\username\AppData\Local\Temp\pylABBE.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-18 23:16 DEBUG  WindowsBackend: Copying C:\Users\username\AppData\Local\Temp\pylABBE.tmp\winboot -> C:\ubuntu\winboot
10-18 23:16 DEBUG  WindowsBackend: Copying C:\Users\username\AppData\Local\Temp\pylABBE.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
10-18 23:16 DEBUG  TaskList: ## Finished copy_installation_files
10-18 23:16 DEBUG  TaskList: ## Running get_iso...
10-18 23:16 DEBUG  CommonBackend: Searching for local CD
10-18 23:16 DEBUG  Distro:   checking whether C:\Users\username\AppData\Local\Temp\pylABBE.tmp is a valid Ubuntu Netbook CD
10-18 23:16 DEBUG  Distro:     does not contain C:\Users\username\AppData\Local\Temp\pylABBE.tmp\casper\filesystem.squashfs
10-18 23:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-18 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 23:16 DEBUG  CommonBackend: Searching for local ISO
10-18 23:16 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\Users\username\Downloads\ubuntu-10.10-netbook-i386.iso
10-18 23:16 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\username\Downloads\ubuntu-10.10-netbook-i386.iso
10-18 23:16 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
10-18 23:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
10-18 23:16 DEBUG  Distro: wrong version: 10.10 != 10.04.1
10-18 23:16 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-18 23:16 DEBUG  TaskList: New task get_metalink
10-18 23:16 DEBUG  TaskList: ### Running get_metalink...
10-18 23:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.metalink) > C:\ubuntu\install
10-18 23:16 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-netbook-i386.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.metalink, basename=ubuntu-10.04-netbook-i386.metalink, length=36061, text=None
10-18 23:16 DEBUG  downloader: download finished (read 36061 bytes)
10-18 23:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > C:\ubuntu\install
10-18 23:16 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=651, text=None
10-18 23:16 DEBUG  downloader: download finished (read 651 bytes)
10-18 23:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
10-18 23:16 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
10-18 23:16 DEBUG  downloader: download finished (read 189 bytes)
10-18 23:16 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
10-18 23:16 INFO   saplog: Checking block bindings..
10-18 23:16 INFO   saplog: Key verified successfully.
10-18 23:16 DEBUG  CommonBackend: metalink md5sums:
a293f05f7be5e61937b1c277c6a69262  ubuntu-10.04-netbook-armel+dove.metalink
dece0df9abb10efb1f590f759cccf340  ubuntu-10.04-netbook-armel+imx51.metalink
a3805816968bf7199e080ba653a19ac1  ubuntu-10.04-netbook-i386.metalink
94706d50d0375fe01b4b480a9c875a7f  ubuntu-10.04.1-alternate-amd64.metalink
7e94a4ebedb1dcfc4fe376f5a96c45aa  ubuntu-10.04.1-alternate-i386.metalink
974c01945586ebcbb672f11ce6df0e39  ubuntu-10.04.1-desktop-amd64.metalink
b3b2f75f70c5216d1325a5a02f3770ce  ubuntu-10.04.1-desktop-i386.metalink
8b0786e4978a123ce91e87181eb0f570  ubuntu-10.04.1-server-amd64.metalink
56dff8fca4d2612eb035a909092f5016  ubuntu-10.04.1-server-i386.metalink

10-18 23:16 DEBUG  TaskList: ### Finished get_metalink
10-18 23:16 DEBUG  TaskList: New task download
10-18 23:16 DEBUG  TaskList: ### Running download...
10-18 23:16 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04.1/ubuntu-10.04-netbook-i386.iso.torrent](http://releases.ubuntu.com/10.04.1/ubuntu-10.04-netbook-i386.iso.torrent) > C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 00:26 DEBUG  TaskList: ### Finished download
10-19 00:26 DEBUG  TaskList: New task check_iso
10-19 00:26 DEBUG  TaskList: ### Running check_iso...
10-19 00:26 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 00:26 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 00:26 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 00:26 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.04 "Lucid Lynx" - Release i386 (20100429.4)
10-19 00:26 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.04', 'build': '20100429.4', 'codename': 'Lucid Lynx', 'arch': 'i386'}
10-19 00:26 DEBUG  Distro: wrong version: 10.04 != 10.04.1
10-19 00:26 DEBUG  TaskList: ### Finished check_iso
10-19 00:26 DEBUG  TaskList: New task download
10-19 00:26 DEBUG  TaskList: ### Running download...
10-19 00:26 DEBUG  downloader: downloading [http://ubuntu.saudi.net.sa/releases/10.04.1/ubuntu-10.04-netbook-i386.iso](http://ubuntu.saudi.net.sa/releases/10.04.1/ubuntu-10.04-netbook-i386.iso) > C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 00:26 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso, url=http://ubuntu.saudi.net.sa/releases/10.04.1/ubuntu-10.04-netbook-i386.iso, basename=ubuntu-10.04-netbook-i386.iso, length=733837312, text=None
10-19 01:03 DEBUG  TaskList: ### Finished download
10-19 01:03 DEBUG  downloader: download finished (read 733837312 bytes)
10-19 01:03 DEBUG  TaskList: New task check_iso
10-19 01:03 DEBUG  TaskList: ### Running check_iso...
10-19 01:03 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 01:03 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 01:03 DEBUG  Distro: wrong version: 10.04 != 10.04.1
10-19 01:03 DEBUG  TaskList: ### Finished check_iso
10-19 01:03 DEBUG  TaskList: New task download
10-19 01:03 DEBUG  TaskList: ### Running download...
10-19 01:03 DEBUG  downloader: downloading [http://ftp.riken.jp/Linux/ubuntu-iso/CDs/10.04.1/ubuntu-10.04-netbook-i386.iso](http://ftp.riken.jp/Linux/ubuntu-iso/CDs/10.04.1/ubuntu-10.04-netbook-i386.iso) > C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 01:03 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso, url=http://ftp.riken.jp/Linux/ubuntu-iso/CDs/10.04.1/ubuntu-10.04-netbook-i386.iso, basename=ubuntu-10.04-netbook-i386.iso, length=733837312, text=None
10-19 02:08 DEBUG  TaskList: ### Finished download
10-19 02:08 DEBUG  downloader: download finished (read 733837312 bytes)
10-19 02:08 DEBUG  TaskList: New task check_iso
10-19 02:08 DEBUG  TaskList: ### Running check_iso...
10-19 02:08 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 02:08 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 02:08 DEBUG  Distro: wrong version: 10.04 != 10.04.1
10-19 02:08 DEBUG  TaskList: ### Finished check_iso
10-19 02:08 DEBUG  TaskList: New task download
10-19 02:08 DEBUG  TaskList: ### Running download...
10-19 02:08 DEBUG  downloader: downloading [http://ftp.heanet.ie/pub/ubuntu-releases/10.04.1/ubuntu-10.04-netbook-i386.iso](http://ftp.heanet.ie/pub/ubuntu-releases/10.04.1/ubuntu-10.04-netbook-i386.iso) > C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 02:08 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso, url=http://ftp.heanet.ie/pub/ubuntu-releases/10.04.1/ubuntu-10.04-netbook-i386.iso, basename=ubuntu-10.04-netbook-i386.iso, length=733837312, text=None
10-19 02:32 DEBUG  TaskList: ### Finished download
10-19 02:32 DEBUG  downloader: download finished (read 733837312 bytes)
10-19 02:32 DEBUG  TaskList: New task check_iso
10-19 02:32 DEBUG  TaskList: ### Running check_iso...
10-19 02:32 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 02:32 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 02:32 DEBUG  Distro: wrong version: 10.04 != 10.04.1
10-19 02:32 DEBUG  TaskList: ### Finished check_iso
10-19 02:32 DEBUG  TaskList: New task download
10-19 02:32 DEBUG  TaskList: ### Running download...
10-19 02:32 DEBUG  downloader: downloading [http://ftp.halifax.rwth-aachen.de/ubuntu-releases/10.04.1/ubuntu-10.04-netbook-i386.iso](http://ftp.halifax.rwth-aachen.de/ubuntu-releases/10.04.1/ubuntu-10.04-netbook-i386.iso) > C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 02:32 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso, url=http://ftp.halifax.rwth-aachen.de/ubuntu-releases/10.04.1/ubuntu-10.04-netbook-i386.iso, basename=ubuntu-10.04-netbook-i386.iso, length=733837312, text=None
10-19 02:54 DEBUG  TaskList: ### Finished download
10-19 02:54 DEBUG  downloader: download finished (read 733837312 bytes)
10-19 02:54 DEBUG  TaskList: New task check_iso
10-19 02:54 DEBUG  TaskList: ### Running check_iso...
10-19 02:54 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 02:54 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
10-19 02:54 DEBUG  Distro: wrong version: 10.04 != 10.04.1
10-19 02:54 DEBUG  TaskList: ### Finished check_iso
10-19 02:54 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
10-19 02:54 DEBUG  TaskList: # Cancelling tasklist
10-19 02:54 DEBUG  TaskList: # Finished tasklist
10-19 02:54 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files


```


I'd appreciate any help on resolving this. Also, if there is any way to have Wubi use a downloaded ISO for the netbook edition in the same folder as the exe instead of downloading it, that would be nice.

---

### Post by bcbc on 2010-10-19
Your wubi.exe is at 10.04.1 (each wubi.exe is specifically for a certain release). But there is no netbook 10.04.1, only 10.04.

So you need the correct wubi.exe version. And then yes, it will use the downloaded .iso if it's in the same folder as wubi.exe.

You can get the 10.04 wubi.exe either from the .iso itself (by mounting and copying it) or you can find it [here]("http://people.canonical.com/~evand/wubi/lucid/") as wubi-r189.exe

---

### Post by apple_pie on 2010-10-19
Thanks bcbc, that seems to have works. Thanks for the explanation too. I guess I assumed that the exe just downloaded the most recent stable version.

---

### Post by bcbc on 2010-10-19
> **apple_pie said:**
> Thanks bcbc, that seems to have works. Thanks for the explanation too. I guess I assumed that the exe just downloaded the most recent stable version.

The most recent version is 10.10 maverick. I don't know why the wubi.exe hasn't been updated to 10.10 yet although you can find it at any of the download mirrors e.g. [http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/) 

I don't believe any new release is more stable than the next - but 10.04 is a long term support release so would tend to be more stable over time.

---

### Post by bcbc on 2010-10-19
See [http://www.ubuntu.com/netbook/features](http://www.ubuntu.com/netbook/features) for info on the latest features on Ubuntu 10.10 netbook.

Note, while you can upgrade from 10.04 to 10.10 it's better to do a fresh install (and quicker) - the upgrade has some known issues - see release notes for more details.

---

### Post by Frogs Hair on 2010-10-19
Wubi 10.10 is included in the ISO down load , in the past it was updated with each release . I know some Wubi  users and have let them use my 10.10 live cd to update . The Wubi .org website has changed also , it looks like part of Ubuntu website now.

---

### Post by apple_pie on 2010-10-19
Cool, thanks for the followup. I may give 10.10 a shot this weekend.

---

