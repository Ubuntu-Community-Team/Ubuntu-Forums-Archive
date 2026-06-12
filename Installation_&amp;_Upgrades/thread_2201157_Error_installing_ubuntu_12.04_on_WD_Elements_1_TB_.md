---
title: "Error installing ubuntu 12.04 on WD Elements 1 TB external"
date: 2014-01-22
forum: Installation &amp; Upgrades
---

### Post by americandollar22 on 2014-01-22
I've been trying to install ubuntu via the windows installer for a while now because installing it after booting from from a live USB/CD isn't working. Whenever I try that method, it tells me that no root filesystem is defined on the partition I want to install to.

The problem I'm having with this method is as follows:

[IMG]http://i44.tinypic.com/2i9i62p.png[/IMG]

And here's the log dump. If it repeats itself I apologize, I ran this a couple of times to make sure it wasn't just a fluke:

01-22 19:19 INFO   root: === wubi 12.04.1 rev273 ===
01-22 19:19 DEBUG  root: Logfile is c:\users\sean\appdata\local\temp\wubi-12.04.1-rev273.log
01-22 19:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
01-22 19:19 DEBUG  CommonBackend: data_dir=C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\data
01-22 19:19 DEBUG  WindowsBackend: 7z=C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\bin\7z.exe
01-22 19:19 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-22 19:19 DEBUG  CommonBackend: Fetching basic info...
01-22 19:19 DEBUG  CommonBackend: original_exe=G:\wubi.exe
01-22 19:19 DEBUG  CommonBackend: platform=win32
01-22 19:19 DEBUG  CommonBackend: osname=nt
01-22 19:19 DEBUG  CommonBackend: language=en_US
01-22 19:19 DEBUG  CommonBackend: encoding=cp1252
01-22 19:19 DEBUG  WindowsBackend: arch=amd64
01-22 19:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\data\isolist.ini
01-22 19:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-22 19:19 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
01-22 19:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-22 19:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-22 19:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-22 19:19 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
01-22 19:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-22 19:19 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
01-22 19:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-22 19:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-22 19:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-22 19:19 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
01-22 19:19 DEBUG  WindowsBackend: Fetching host info...
01-22 19:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-22 19:19 DEBUG  WindowsBackend: windows version=vista
01-22 19:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-22 19:19 DEBUG  WindowsBackend: windows_sp=None
01-22 19:19 DEBUG  WindowsBackend: windows_build=7601
01-22 19:19 DEBUG  WindowsBackend: gmt=-7
01-22 19:19 DEBUG  WindowsBackend: country=US
01-22 19:19 DEBUG  WindowsBackend: timezone=America/Denver
01-22 19:19 DEBUG  WindowsBackend: windows_username=Sean
01-22 19:19 DEBUG  WindowsBackend: user_full_name=Sean
01-22 19:19 DEBUG  WindowsBackend: user_directory=C:\Users\Sean
01-22 19:19 DEBUG  WindowsBackend: windows_language_code=1033
01-22 19:19 DEBUG  WindowsBackend: windows_language=English
01-22 19:19 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2370M CPU @ 2.40GHz
01-22 19:19 DEBUG  WindowsBackend: bootloader=vista
01-22 19:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 508347.140625 mb free ntfs)
01-22 19:19 DEBUG  WindowsBackend: drive=Drive(C: hd 508347.140625 mb free ntfs)
01-22 19:19 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-22 19:19 DEBUG  WindowsBackend: drive=Drive(E: hd 198598.636719 mb free ntfs)
01-22 19:19 DEBUG  WindowsBackend: drive=Drive(F: hd 612784.132813 mb free ntfs)
01-22 19:19 DEBUG  WindowsBackend: drive=Drive(G: removable 6910.98046875 mb free fat32)
01-22 19:19 DEBUG  WindowsBackend: drive=Drive(Y: hd 5003.76171875 mb free ntfs)
01-22 19:19 DEBUG  WindowsBackend: uninstaller_path=None
01-22 19:19 DEBUG  WindowsBackend: previous_target_dir=None
01-22 19:19 DEBUG  WindowsBackend: previous_distro_name=None
01-22 19:19 DEBUG  WindowsBackend: keyboard_id=67699721
01-22 19:19 DEBUG  WindowsBackend: keyboard_layout=us
01-22 19:19 DEBUG  WindowsBackend: keyboard_variant=
01-22 19:19 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-22 19:19 DEBUG  CommonBackend: locale=en_US.UTF-8
01-22 19:19 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
01-22 19:19 DEBUG  CommonBackend: Searching ISOs on USB devices
01-22 19:19 DEBUG  CommonBackend: Searching for local CDs
01-22 19:19 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp is a valid Ubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp is a valid Ubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp is a valid Kubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp is a valid Kubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp is a valid Xubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp is a valid Xubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp is a valid Mythbuntu CD
01-22 19:19 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp is a valid Mythbuntu CD
01-22 19:19 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp is a valid Edubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp is a valid Edubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp is a valid Lubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp is a valid Lubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-22 19:19 DEBUG  Distro:   parsing info from str=Ubuntu 12.04.3 LTS "Precise Pangolin" - Release amd64 (20130820.1)
01-22 19:19 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04.3', 'build': '20130820.1', 'codename': 'Precise Pangolin', 'arch': 'amd64'}
01-22 19:19 DEBUG  Distro: wrong version: 12.04.3 != 12.04.2
01-22 19:19 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:19 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:19 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:19 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:19 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:19 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-22 19:19 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:19 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-22 19:19 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:19 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:19 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:19 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:19 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:19 DEBUG  Distro:   checking whether Y:\ is a valid Ubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether Y:\ is a valid Ubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether Y:\ is a valid Kubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether Y:\ is a valid Kubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether Y:\ is a valid Xubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether Y:\ is a valid Xubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether Y:\ is a valid Mythbuntu CD
01-22 19:19 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether Y:\ is a valid Mythbuntu CD
01-22 19:19 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether Y:\ is a valid Edubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether Y:\ is a valid Edubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether Y:\ is a valid Lubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:19 DEBUG  Distro:   checking whether Y:\ is a valid Lubuntu CD
01-22 19:19 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:19 INFO   root: Running the installer...
01-22 19:19 DEBUG  WindowsFrontend: __init__...
01-22 19:19 DEBUG  WindowsFrontend: on_init...
01-22 19:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\translations, languages=['en_US', 'en']
01-22 19:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\translations, languages=['en_US', 'en']
01-22 19:20 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sean
01-22 19:20 INFO   root: Received settings
01-22 19:20 DEBUG  CommonBackend: Searching for local CD
01-22 19:20 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp is a valid Ubuntu CD
01-22 19:20 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\casper\filesystem.squashfs
01-22 19:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 19:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-22 19:20 DEBUG  Distro: wrong version: 12.04.3 != 12.04.2
01-22 19:20 DEBUG  Distro:   checking whether Y:\ is a valid Ubuntu CD
01-22 19:20 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:20 DEBUG  CommonBackend: Searching for local ISO
01-22 19:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sean\AppData\Local\Temp\pyl5884.tmp\translations, languages=['en_US', 'en']
01-22 19:20 DEBUG  TaskList: # Running tasklist...
01-22 19:20 DEBUG  TaskList: ## Running select_target_dir...
01-22 19:20 INFO   WindowsBackend: Installing into E:\ubuntu
01-22 19:20 DEBUG  TaskList: ## Finished select_target_dir
01-22 19:20 DEBUG  TaskList: ## Running create_dir_structure...
01-22 19:20 DEBUG  CommonBackend: Creating dir E:\ubuntu
01-22 19:20 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
01-22 19:20 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
01-22 19:20 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
01-22 19:20 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
01-22 19:20 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
01-22 19:20 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
01-22 19:20 DEBUG  TaskList: ## Finished create_dir_structure
01-22 19:20 DEBUG  TaskList: ## Running create_uninstaller...
01-22 19:20 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
01-22 19:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
01-22 19:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
01-22 19:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-22 19:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
01-22 19:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04.1-rev273
01-22 19:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-22 19:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-22 19:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-22 19:20 DEBUG  TaskList: ## Finished create_uninstaller
01-22 19:20 DEBUG  TaskList: ## Running create_preseed_diskimage...
01-22 19:20 DEBUG  TaskList: ## Finished create_preseed_diskimage
01-22 19:20 DEBUG  TaskList: ## Running get_diskimage...
01-22 19:20 DEBUG  TaskList: New task download
01-22 19:20 DEBUG  TaskList: ### Running download...
01-22 19:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > E:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
01-22 19:20 ERROR  TaskList: [Errno 14] HTTP Error 404: Not Found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 77, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 404: Not Found
01-22 19:20 ERROR  TaskList: Non fatal error [Errno 14] HTTP Error 404: Not Found in task download
01-22 19:20 DEBUG  TaskList: ### Finished download
01-22 19:20 DEBUG  TaskList: New task download
01-22 19:20 DEBUG  TaskList: ### Running download...
01-22 19:20 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/precise/wubi/current/amd64.tar.xz](http://cdimage.ubuntu.com/precise/wubi/current/amd64.tar.xz) > E:\ubuntu\disks\amd64.tar.xz
01-22 19:20 DEBUG  downloader: Download start filename=E:\ubuntu\disks\amd64.tar.xz, url=http://cdimage.ubuntu.com/precise/wubi/current/amd64.tar.xz, basename=amd64.tar.xz, length=545608520, text=None
01-22 19:41 DEBUG  TaskList: ### Finished download
01-22 19:41 DEBUG  downloader: download finished (read 545608520 bytes)
01-22 19:41 DEBUG  TaskList: ## Finished get_diskimage
01-22 19:41 DEBUG  TaskList: ## Running extract_diskimage...
01-22 19:43 DEBUG  TaskList: ## Finished extract_diskimage
01-22 19:43 DEBUG  TaskList: ## Running choose_disk_sizes...
01-22 19:43 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
01-22 19:43 DEBUG  TaskList: ## Finished choose_disk_sizes
01-22 19:43 DEBUG  TaskList: ## Running expand_diskimage...
01-22 19:43 DEBUG  TaskList: ## Finished expand_diskimage
01-22 19:43 DEBUG  TaskList: ## Running create_swap_diskimage...
01-22 19:43 DEBUG  TaskList: ## Finished create_swap_diskimage
01-22 19:43 DEBUG  TaskList: ## Running modify_bootloader...
01-22 19:43 DEBUG  TaskList: New task modify_bcd
01-22 19:43 DEBUG  TaskList: ### Running modify_bcd...
01-22 19:43 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 508347.140625 mb free ntfs)
01-22 19:43 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 694, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=
>>stdout=
01-22 19:43 DEBUG  TaskList: # Cancelling tasklist
01-22 19:43 DEBUG  TaskList: New task modify_bcd
01-22 19:43 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 694, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=
>>stdout=
01-22 19:43 DEBUG  TaskList: New task modify_bcd
01-22 19:43 DEBUG  TaskList: New task modify_bcd
01-22 19:43 DEBUG  TaskList: New task modify_bcd
01-22 19:43 DEBUG  TaskList: ## Finished modify_bootloader
01-22 19:43 DEBUG  TaskList: # Finished tasklist
01-22 19:43 INFO   root: === wubi 12.04.1 rev273 ===
01-22 19:43 DEBUG  root: Logfile is c:\users\sean\appdata\local\temp\wubi-12.04.1-rev273.log
01-22 19:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
01-22 19:43 DEBUG  CommonBackend: data_dir=C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\data
01-22 19:43 DEBUG  WindowsBackend: 7z=C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\bin\7z.exe
01-22 19:43 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-22 19:43 DEBUG  CommonBackend: Fetching basic info...
01-22 19:43 DEBUG  CommonBackend: original_exe=G:\wubi.exe
01-22 19:43 DEBUG  CommonBackend: platform=win32
01-22 19:43 DEBUG  CommonBackend: osname=nt
01-22 19:43 DEBUG  CommonBackend: language=en_US
01-22 19:43 DEBUG  CommonBackend: encoding=cp1252
01-22 19:43 DEBUG  WindowsBackend: arch=amd64
01-22 19:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\data\isolist.ini
01-22 19:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-22 19:43 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
01-22 19:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-22 19:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-22 19:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-22 19:43 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
01-22 19:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-22 19:43 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
01-22 19:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-22 19:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-22 19:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-22 19:43 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
01-22 19:43 DEBUG  WindowsBackend: Fetching host info...
01-22 19:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-22 19:43 DEBUG  WindowsBackend: windows version=vista
01-22 19:43 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-22 19:43 DEBUG  WindowsBackend: windows_sp=None
01-22 19:43 DEBUG  WindowsBackend: windows_build=7601
01-22 19:43 DEBUG  WindowsBackend: gmt=-7
01-22 19:43 DEBUG  WindowsBackend: country=US
01-22 19:43 DEBUG  WindowsBackend: timezone=America/Denver
01-22 19:43 DEBUG  WindowsBackend: windows_username=Sean
01-22 19:43 DEBUG  WindowsBackend: user_full_name=Sean
01-22 19:43 DEBUG  WindowsBackend: user_directory=C:\Users\Sean
01-22 19:43 DEBUG  WindowsBackend: windows_language_code=1033
01-22 19:43 DEBUG  WindowsBackend: windows_language=English
01-22 19:43 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2370M CPU @ 2.40GHz
01-22 19:43 DEBUG  WindowsBackend: bootloader=vista
01-22 19:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 508343.152344 mb free ntfs)
01-22 19:43 DEBUG  WindowsBackend: drive=Drive(C: hd 508343.152344 mb free ntfs)
01-22 19:43 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-22 19:43 DEBUG  WindowsBackend: drive=Drive(E: hd 195374.921875 mb free ntfs)
01-22 19:43 DEBUG  WindowsBackend: drive=Drive(F: hd 612784.132813 mb free ntfs)
01-22 19:43 DEBUG  WindowsBackend: drive=Drive(G: removable 6910.98046875 mb free fat32)
01-22 19:43 DEBUG  WindowsBackend: drive=Drive(Y: hd 5003.76171875 mb free ntfs)
01-22 19:43 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
01-22 19:43 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
01-22 19:43 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-22 19:43 DEBUG  WindowsBackend: keyboard_id=67699721
01-22 19:43 DEBUG  WindowsBackend: keyboard_layout=us
01-22 19:43 DEBUG  WindowsBackend: keyboard_variant=
01-22 19:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-22 19:43 DEBUG  CommonBackend: locale=en_US.UTF-8
01-22 19:43 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
01-22 19:43 DEBUG  CommonBackend: Searching ISOs on USB devices
01-22 19:43 DEBUG  CommonBackend: Searching for local CDs
01-22 19:43 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Ubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Ubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Kubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Kubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Xubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Xubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Mythbuntu CD
01-22 19:43 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Mythbuntu CD
01-22 19:43 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Edubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Edubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Lubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Lubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 19:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 19:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 19:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 19:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-22 19:43 DEBUG  Distro:   parsing info from str=Ubuntu 12.04.3 LTS "Precise Pangolin" - Release amd64 (20130820.1)
01-22 19:43 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04.3', 'build': '20130820.1', 'codename': 'Precise Pangolin', 'arch': 'amd64'}
01-22 19:43 DEBUG  Distro: wrong version: 12.04.3 != 12.04.2
01-22 19:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:43 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:43 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-22 19:43 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-22 19:43 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:43 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:43 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:43 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:43 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:43 DEBUG  Distro:   checking whether Y:\ is a valid Ubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether Y:\ is a valid Ubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether Y:\ is a valid Kubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether Y:\ is a valid Kubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether Y:\ is a valid Xubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether Y:\ is a valid Xubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether Y:\ is a valid Mythbuntu CD
01-22 19:43 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether Y:\ is a valid Mythbuntu CD
01-22 19:43 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether Y:\ is a valid Edubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether Y:\ is a valid Edubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether Y:\ is a valid Lubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:43 DEBUG  Distro:   checking whether Y:\ is a valid Lubuntu CD
01-22 19:43 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:43 INFO   root: Already installed, running the uninstaller...
01-22 19:43 INFO   root: Running the uninstaller...
01-22 19:43 INFO   CommonBackend: This is the uninstaller running
01-22 19:43 DEBUG  WindowsFrontend: __init__...
01-22 19:43 DEBUG  WindowsFrontend: on_init...
01-22 19:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\translations, languages=['en_US', 'en']
01-22 19:44 INFO   root: Received settings
01-22 19:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\translations, languages=['en_US', 'en']
01-22 19:44 DEBUG  TaskList: # Running tasklist...
01-22 19:44 DEBUG  TaskList: ## Running Remove bootloader entry...
01-22 19:44 DEBUG  WindowsBackend: Could not find bcd id
01-22 19:44 DEBUG  WindowsBackend: undo_bootini C:
01-22 19:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 508343.152344 mb free ntfs)
01-22 19:44 DEBUG  WindowsBackend: undo_bootini E:
01-22 19:44 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 195374.921875 mb free ntfs)
01-22 19:44 DEBUG  WindowsBackend: undo_bootini F:
01-22 19:44 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 612784.132813 mb free ntfs)
01-22 19:44 DEBUG  WindowsBackend: undo_bootini G:
01-22 19:44 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 6910.98046875 mb free fat32)
01-22 19:44 DEBUG  WindowsBackend: undo_bootini Y:
01-22 19:44 DEBUG  WindowsBackend: undo_configsys Drive(Y: hd 5003.76171875 mb free ntfs)
01-22 19:44 DEBUG  TaskList: ## Finished Remove bootloader entry
01-22 19:44 DEBUG  TaskList: ## Running Remove target dir...
01-22 19:44 DEBUG  CommonBackend: Deleting E:\ubuntu
01-22 19:44 DEBUG  TaskList: ## Finished Remove target dir
01-22 19:44 DEBUG  TaskList: ## Running Remove registry key...
01-22 19:44 DEBUG  TaskList: ## Finished Remove registry key
01-22 19:44 DEBUG  TaskList: # Finished tasklist
01-22 19:44 INFO   root: Almost finished uninstalling
01-22 19:44 INFO   root: Finished uninstallation
01-22 19:44 DEBUG  CommonBackend: Fetching basic info...
01-22 19:44 DEBUG  CommonBackend: original_exe=G:\wubi.exe
01-22 19:44 DEBUG  CommonBackend: platform=win32
01-22 19:44 DEBUG  CommonBackend: osname=nt
01-22 19:44 DEBUG  WindowsBackend: arch=amd64
01-22 19:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\data\isolist.ini
01-22 19:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-22 19:44 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
01-22 19:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-22 19:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-22 19:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-22 19:44 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
01-22 19:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-22 19:44 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
01-22 19:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-22 19:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-22 19:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-22 19:44 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
01-22 19:44 DEBUG  WindowsBackend: Fetching host info...
01-22 19:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-22 19:44 DEBUG  WindowsBackend: windows version=vista
01-22 19:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-22 19:44 DEBUG  WindowsBackend: windows_sp=None
01-22 19:44 DEBUG  WindowsBackend: windows_build=7601
01-22 19:44 DEBUG  WindowsBackend: gmt=-7
01-22 19:44 DEBUG  WindowsBackend: country=US
01-22 19:44 DEBUG  WindowsBackend: timezone=America/Denver
01-22 19:44 DEBUG  WindowsBackend: windows_username=Sean
01-22 19:44 DEBUG  WindowsBackend: user_full_name=Sean
01-22 19:44 DEBUG  WindowsBackend: user_directory=C:\Users\Sean
01-22 19:44 DEBUG  WindowsBackend: windows_language_code=1033
01-22 19:44 DEBUG  WindowsBackend: windows_language=English
01-22 19:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2370M CPU @ 2.40GHz
01-22 19:44 DEBUG  WindowsBackend: bootloader=vista
01-22 19:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 508343.140625 mb free ntfs)
01-22 19:44 DEBUG  WindowsBackend: drive=Drive(C: hd 508343.140625 mb free ntfs)
01-22 19:44 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-22 19:44 DEBUG  WindowsBackend: drive=Drive(E: hd 198598.636719 mb free ntfs)
01-22 19:44 DEBUG  WindowsBackend: drive=Drive(F: hd 612784.132813 mb free ntfs)
01-22 19:44 DEBUG  WindowsBackend: drive=Drive(G: removable 6910.98046875 mb free fat32)
01-22 19:44 DEBUG  WindowsBackend: drive=Drive(Y: hd 5003.76171875 mb free ntfs)
01-22 19:44 DEBUG  WindowsBackend: uninstaller_path=None
01-22 19:44 DEBUG  WindowsBackend: previous_target_dir=None
01-22 19:44 DEBUG  WindowsBackend: previous_distro_name=None
01-22 19:44 DEBUG  WindowsBackend: keyboard_id=67699721
01-22 19:44 DEBUG  WindowsBackend: keyboard_layout=us
01-22 19:44 DEBUG  WindowsBackend: keyboard_variant=
01-22 19:44 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
01-22 19:44 DEBUG  CommonBackend: Searching ISOs on USB devices
01-22 19:44 DEBUG  CommonBackend: Searching for local CDs
01-22 19:44 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Kubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Kubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Xubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Xubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Mythbuntu CD
01-22 19:44 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Mythbuntu CD
01-22 19:44 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Edubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Edubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Lubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Lubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 19:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 19:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 19:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 19:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 19:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 19:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro: wrong version: 12.04.3 != 12.04.2
01-22 19:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-22 19:44 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-22 19:44 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:44 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:44 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:44 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:44 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain G:\casper\vmlinuz
01-22 19:44 DEBUG  Distro:   checking whether Y:\ is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether Y:\ is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether Y:\ is a valid Kubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether Y:\ is a valid Kubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether Y:\ is a valid Xubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether Y:\ is a valid Xubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether Y:\ is a valid Mythbuntu CD
01-22 19:44 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether Y:\ is a valid Mythbuntu CD
01-22 19:44 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether Y:\ is a valid Edubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether Y:\ is a valid Edubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether Y:\ is a valid Lubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether Y:\ is a valid Lubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:44 INFO   root: Running the installer...
01-22 19:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\translations, languages=['en_US', 'en']
01-22 19:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\translations, languages=['en_US', 'en']
01-22 19:44 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sean
01-22 19:44 INFO   root: Received settings
01-22 19:44 DEBUG  CommonBackend: Searching for local CD
01-22 19:44 DEBUG  Distro:   checking whether C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 19:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro: wrong version: 12.04.3 != 12.04.2
01-22 19:44 DEBUG  Distro:   checking whether Y:\ is a valid Ubuntu CD
01-22 19:44 DEBUG  Distro:     does not contain Y:\casper\filesystem.squashfs
01-22 19:44 DEBUG  CommonBackend: Searching for local ISO
01-22 19:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Sean\AppData\Local\Temp\pylB7A5.tmp\translations, languages=['en_US', 'en']
01-22 19:44 DEBUG  TaskList: # Running tasklist...
01-22 19:44 DEBUG  TaskList: ## Running select_target_dir...
01-22 19:44 INFO   WindowsBackend: Installing into E:\ubuntu
01-22 19:44 DEBUG  TaskList: ## Finished select_target_dir
01-22 19:44 DEBUG  TaskList: ## Running create_dir_structure...
01-22 19:44 DEBUG  CommonBackend: Creating dir E:\ubuntu
01-22 19:44 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
01-22 19:44 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
01-22 19:44 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
01-22 19:44 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
01-22 19:44 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
01-22 19:44 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
01-22 19:44 DEBUG  TaskList: ## Finished create_dir_structure
01-22 19:44 DEBUG  TaskList: ## Running create_uninstaller...
01-22 19:44 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
01-22 19:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
01-22 19:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
01-22 19:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-22 19:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
01-22 19:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04.1-rev273
01-22 19:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-22 19:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-22 19:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-22 19:44 DEBUG  TaskList: ## Finished create_uninstaller
01-22 19:44 DEBUG  TaskList: ## Running create_preseed_diskimage...
01-22 19:44 DEBUG  TaskList: ## Finished create_preseed_diskimage
01-22 19:44 DEBUG  TaskList: ## Running get_diskimage...
01-22 19:44 DEBUG  TaskList: New task download
01-22 19:44 DEBUG  TaskList: ### Running download...
01-22 19:44 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > E:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
01-22 19:44 ERROR  TaskList: [Errno 14] HTTP Error 404: Not Found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 77, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 404: Not Found
01-22 19:44 ERROR  TaskList: Non fatal error [Errno 14] HTTP Error 404: Not Found in task download
01-22 19:44 DEBUG  TaskList: ### Finished download
01-22 19:44 DEBUG  TaskList: New task download
01-22 19:44 DEBUG  TaskList: ### Running download...
01-22 19:44 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/precise/wubi/current/amd64.tar.xz](http://cdimage.ubuntu.com/precise/wubi/current/amd64.tar.xz) > E:\ubuntu\disks\amd64.tar.xz
01-22 19:44 DEBUG  downloader: Download start filename=E:\ubuntu\disks\amd64.tar.xz, url=http://cdimage.ubuntu.com/precise/wubi/current/amd64.tar.xz, basename=amd64.tar.xz, length=545608520, text=None
01-22 20:05 DEBUG  TaskList: ### Finished download
01-22 20:05 DEBUG  downloader: download finished (read 545608520 bytes)
01-22 20:05 DEBUG  TaskList: ## Finished get_diskimage
01-22 20:05 DEBUG  TaskList: ## Running extract_diskimage...
01-22 20:06 DEBUG  TaskList: ## Finished extract_diskimage
01-22 20:06 DEBUG  TaskList: ## Running choose_disk_sizes...
01-22 20:06 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
01-22 20:06 DEBUG  TaskList: ## Finished choose_disk_sizes
01-22 20:06 DEBUG  TaskList: ## Running expand_diskimage...
01-22 20:06 DEBUG  TaskList: ## Finished expand_diskimage
01-22 20:06 DEBUG  TaskList: ## Running create_swap_diskimage...
01-22 20:06 DEBUG  TaskList: ## Finished create_swap_diskimage
01-22 20:06 DEBUG  TaskList: ## Running modify_bootloader...
01-22 20:06 DEBUG  TaskList: New task modify_bcd
01-22 20:06 DEBUG  TaskList: ### Running modify_bcd...
01-22 20:06 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 508343.140625 mb free ntfs)
01-22 20:06 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 694, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=
>>stdout=
01-22 20:06 DEBUG  TaskList: # Cancelling tasklist
01-22 20:06 DEBUG  TaskList: New task modify_bcd
01-22 20:06 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 694, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=
>>stdout=
01-22 20:06 DEBUG  TaskList: New task modify_bcd
01-22 20:06 DEBUG  TaskList: New task modify_bcd
01-22 20:06 DEBUG  TaskList: New task modify_bcd
01-22 20:06 DEBUG  TaskList: ## Finished modify_bootloader
01-22 20:06 DEBUG  TaskList: # Finished tasklist

---

### Post by tfrue on 2014-01-23
Well, I would say go to the Ubuntu website, re download Ubuntu, 13.10 or 12.04.3 LTS, and burn it to a CD or USB and try and live boot again. Also, don't use the WUBI installer, it's deprecated. If you are wanting Ubuntu to have its own partition, then I would use the Disk Manager in Window's to partition yourself a section, then while you are in Ubuntu installer, choose "Something Else" and select the partition that you created for yourself.

Here is a link to their desktop downloading page.
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Before you do all of this, how old/new is this computer? Newer computers that come pre-installed with Win 8 are set up differently than before so partitioning and installing would be a whole new ball game, but that is of course if you have anything related to that.

---

### Post by americandollar22 on 2014-01-23
> **tfrue said:**
> Well, I would say go to the Ubuntu website, re download Ubuntu, 13.10 or 12.04.3 LTS, and burn it to a CD or USB and try and live boot again. Also, don't use the WUBI installer, it's deprecated. If you are wanting Ubuntu to have its own partition, then I would use the Disk Manager in Window's to partition yourself a section, then while you are in Ubuntu installer, choose "Something Else" and select the partition that you created for yourself.

Here is a link to their desktop downloading page.
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Before you do all of this, how old/new is this computer? Newer computers that come pre-installed with Win 8 are set up differently than before so partitioning and installing would be a whole new ball game, but that is of course if you have anything related to that.

It's definitely not the download, I've tried this with multiple isos. I'm not installing ubuntu on my PC, I'm installing it on a WD Elements external drive that doesn't have an OS on it. I'm running windows 7, and I hate windows 8, never gonna use it. Haha.

---

### Post by tfrue on 2014-01-24
Then live boot into Ubuntu, run the installer, choose "Something Else", select the entire disk of the external drive, make sure that grub will install to the external drive (which is probably /dev/sdb), and you should be good.

Just remember that you will have to choose to boot from that drive, but you may experience problems with BIOS booting the incorrect boot loader if you boot from a PC with a HDD with Windows and your external drive plugged in.

---

### Post by fantab on 2014-01-24
You have used Windows Ubuntu Installer, aka WUBI. Bad choice. Don't use it.

Boot with Ubuntu live DVD/USB then "Try Ubuntu without installing", plug in your Ext HDD and open Terminal [ctrl+alt+T]. Run the following commands and post its output here.
```
sudo parted -l
sudo fdisk -l
```.

I presume that your Ext HDD has USB plugin. In that case check in your BIOS to see if USB booting is enabled... confirm this.

---

### Post by americandollar22 on 2014-01-24
> **tfrue said:**
> Then live boot into Ubuntu, run the installer, choose "Something Else", select the entire disk of the external drive, make sure that grub will install to the external drive (which is probably /dev/sdb), and you should be good.

Just remember that you will have to choose to boot from that drive, but you may experience problems with BIOS booting the incorrect boot loader if you boot from a PC with a HDD with Windows and your external drive plugged in.I will try this and get back to you. Stay tuned.

I'm not sure that will be a problem because I've booted from unetbootin flash drives in the past, and that my laptop is able to boot from USB.

> **fantab said:**
> You have used Windows Ubuntu Installer, aka WUBI. Bad choice. Don't use it.

Boot with Ubuntu live DVD/USB then "Try Ubuntu without installing", plug in your Ext HDD and open Terminal [ctrl+alt+T]. Run the following commands and post its output here.
```
sudo parted -l
sudo fdisk -l
```.

I presume that your Ext HDD has USB plugin. In that case check in your BIOS to see if USB booting is enabled... confirm this.
I'll try this if the other guy's method fails. Stay tuned as well, I'll probably get back to both of you at the same time, though it won't be for a few hours since I've got class.

Yes, USB booting is enabled.

---

### Post by americandollar22 on 2014-01-26
Update. I made a live DVD but it refuses to boot when I select it in BIOS. I just get a blank screen with a cursor.

---

