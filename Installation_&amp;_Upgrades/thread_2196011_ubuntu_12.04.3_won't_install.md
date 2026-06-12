---
title: "ubuntu 12.04.3 won't install"
date: 2013-12-27
forum: Installation &amp; Upgrades
---

### Post by mark97 on 2013-12-27
I downloaded the ISO file (the MD5 checksum was ok) and burned it to a DVD. When I try to install it says there's errors and it won't install. The log file is below, any suggestions? It looks like the distribution package is expecting 12.04.2 instead of 12.04.3.


12-27 10:35 INFO   root: === wubi 12.04.1 rev273 ===
12-27 10:35 DEBUG  root: Logfile is c:\docume~1\customer\locals~1\temp\wubi-12.04.1-rev273.log
12-27 10:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
12-27 10:35 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\data
12-27 10:35 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\bin\7z.exe
12-27 10:35 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
12-27 10:35 DEBUG  CommonBackend: Fetching basic info...
12-27 10:35 DEBUG  CommonBackend: original_exe=D:\wubi.exe
12-27 10:35 DEBUG  CommonBackend: platform=win32
12-27 10:35 DEBUG  CommonBackend: osname=nt
12-27 10:35 DEBUG  CommonBackend: language=en_US
12-27 10:35 DEBUG  CommonBackend: encoding=cp1252
12-27 10:35 DEBUG  WindowsBackend: arch=amd64
12-27 10:35 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\data\isolist.ini
12-27 10:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-27 10:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-27 10:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-27 10:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-27 10:35 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-27 10:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-27 10:35 DEBUG  WindowsBackend: Fetching host info...
12-27 10:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-27 10:35 DEBUG  WindowsBackend: windows version=xp
12-27 10:35 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-27 10:35 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-27 10:35 DEBUG  WindowsBackend: windows_build=2600
12-27 10:35 DEBUG  WindowsBackend: gmt=-6
12-27 10:35 DEBUG  WindowsBackend: country=US
12-27 10:35 DEBUG  WindowsBackend: timezone=America/Chicago
12-27 10:35 DEBUG  WindowsBackend: windows_username=customer
12-27 10:35 DEBUG  WindowsBackend: user_full_name=customer
12-27 10:35 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\customer
12-27 10:35 DEBUG  WindowsBackend: windows_language_code=1033
12-27 10:35 DEBUG  WindowsBackend: windows_language=English
12-27 10:35 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 3400+
12-27 10:35 DEBUG  WindowsBackend: bootloader=xp
12-27 10:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 77247.0742188 mb free ntfs)
12-27 10:35 DEBUG  WindowsBackend: drive=Drive(C: hd 77247.0742188 mb free ntfs)
12-27 10:35 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
12-27 10:35 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-27 10:35 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-27 10:35 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-27 10:35 DEBUG  WindowsBackend: keyboard_id=67699721
12-27 10:35 DEBUG  WindowsBackend: keyboard_layout=us
12-27 10:35 DEBUG  WindowsBackend: keyboard_variant=
12-27 10:35 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-27 10:35 DEBUG  CommonBackend: locale=en_US.UTF-8
12-27 10:35 DEBUG  WindowsBackend: total_memory_mb=1023.359375
12-27 10:35 DEBUG  CommonBackend: Searching ISOs on USB devices
12-27 10:35 DEBUG  CommonBackend: Searching for local CDs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Ubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Ubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Kubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Kubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Xubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Xubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Mythbuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Mythbuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Edubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Edubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Lubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Lubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain D:\casper\vmlinuz.efi
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 10:35 DEBUG  Distro:   parsing info from str=Ubuntu 12.04.3 LTS "Precise Pangolin" - Release i386 (20130820.1)
12-27 10:35 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04.3', 'build': '20130820.1', 'codename': 'Precise Pangolin', 'arch': 'i386'}
12-27 10:35 DEBUG  Distro: wrong version: 12.04.3 != 12.04.2
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
12-27 10:35 INFO   root: Already installed, running the uninstaller...
12-27 10:35 INFO   root: Running the uninstaller...
12-27 10:35 INFO   CommonBackend: This is the uninstaller running
12-27 10:35 DEBUG  WindowsFrontend: __init__...
12-27 10:35 DEBUG  WindowsFrontend: on_init...
12-27 10:35 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\translations, languages=['en_US', 'en']
12-27 10:35 INFO   root: Received settings
12-27 10:35 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\translations, languages=['en_US', 'en']
12-27 10:35 DEBUG  TaskList: # Running tasklist...
12-27 10:35 DEBUG  TaskList: ## Running Remove bootloader entry...
12-27 10:35 ERROR  WindowsBackend: Cannot find bcdedit
12-27 10:35 DEBUG  WindowsBackend: undo_bootini C:
12-27 10:35 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 77247.0742188 mb free ntfs)
12-27 10:35 DEBUG  TaskList: ## Finished Remove bootloader entry
12-27 10:35 DEBUG  TaskList: ## Running Remove target dir...
12-27 10:35 DEBUG  CommonBackend: Deleting C:\ubuntu
12-27 10:35 DEBUG  TaskList: ## Finished Remove target dir
12-27 10:35 DEBUG  TaskList: ## Running Remove registry key...
12-27 10:35 DEBUG  TaskList: ## Finished Remove registry key
12-27 10:35 DEBUG  TaskList: # Finished tasklist
12-27 10:35 INFO   root: Almost finished uninstalling
12-27 10:35 INFO   root: Finished uninstallation
12-27 10:35 DEBUG  CommonBackend: Fetching basic info...
12-27 10:35 DEBUG  CommonBackend: original_exe=D:\wubi.exe
12-27 10:35 DEBUG  CommonBackend: platform=win32
12-27 10:35 DEBUG  CommonBackend: osname=nt
12-27 10:35 DEBUG  WindowsBackend: arch=amd64
12-27 10:35 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\data\isolist.ini
12-27 10:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-27 10:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-27 10:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-27 10:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-27 10:35 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-27 10:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-27 10:35 DEBUG  WindowsBackend: Fetching host info...
12-27 10:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-27 10:35 DEBUG  WindowsBackend: windows version=xp
12-27 10:35 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-27 10:35 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-27 10:35 DEBUG  WindowsBackend: windows_build=2600
12-27 10:35 DEBUG  WindowsBackend: gmt=-6
12-27 10:35 DEBUG  WindowsBackend: country=US
12-27 10:35 DEBUG  WindowsBackend: timezone=America/Chicago
12-27 10:35 DEBUG  WindowsBackend: windows_username=customer
12-27 10:35 DEBUG  WindowsBackend: user_full_name=customer
12-27 10:35 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\customer
12-27 10:35 DEBUG  WindowsBackend: windows_language_code=1033
12-27 10:35 DEBUG  WindowsBackend: windows_language=English
12-27 10:35 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 3400+
12-27 10:35 DEBUG  WindowsBackend: bootloader=xp
12-27 10:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 77249.453125 mb free ntfs)
12-27 10:35 DEBUG  WindowsBackend: drive=Drive(C: hd 77249.453125 mb free ntfs)
12-27 10:35 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
12-27 10:35 DEBUG  WindowsBackend: uninstaller_path=None
12-27 10:35 DEBUG  WindowsBackend: previous_target_dir=None
12-27 10:35 DEBUG  WindowsBackend: previous_distro_name=None
12-27 10:35 DEBUG  WindowsBackend: keyboard_id=67699721
12-27 10:35 DEBUG  WindowsBackend: keyboard_layout=us
12-27 10:35 DEBUG  WindowsBackend: keyboard_variant=
12-27 10:35 DEBUG  WindowsBackend: total_memory_mb=1023.359375
12-27 10:35 DEBUG  CommonBackend: Searching ISOs on USB devices
12-27 10:35 DEBUG  CommonBackend: Searching for local CDs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Ubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Ubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Kubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Kubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Xubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Xubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Mythbuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Mythbuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Edubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Edubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Lubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp is a valid Lubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain D:\casper\vmlinuz.efi
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 10:35 DEBUG  Distro: wrong version: 12.04.3 != 12.04.2
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
12-27 10:35 INFO   root: Running the installer...
12-27 10:35 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\translations, languages=['en_US', 'en']
12-27 10:35 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\customer\LOCALS~1\Temp\pylE.tmp\translations, languages=['en_US', 'en']
12-27 10:35 DEBUG  WindowsFrontend: frontend.on_quit
12-27 10:35 DEBUG  root: application.on_quit
12-27 10:35 INFO   root: sys.exit
12-27 10:35 INFO   root: === wubi 12.04.1 rev273 ===
12-27 10:35 DEBUG  root: Logfile is c:\docume~1\customer\locals~1\temp\wubi-12.04.1-rev273.log
12-27 10:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
12-27 10:35 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\data
12-27 10:35 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\bin\7z.exe
12-27 10:35 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
12-27 10:35 DEBUG  CommonBackend: Fetching basic info...
12-27 10:35 DEBUG  CommonBackend: original_exe=D:\wubi.exe
12-27 10:35 DEBUG  CommonBackend: platform=win32
12-27 10:35 DEBUG  CommonBackend: osname=nt
12-27 10:35 DEBUG  CommonBackend: language=en_US
12-27 10:35 DEBUG  CommonBackend: encoding=cp1252
12-27 10:35 DEBUG  WindowsBackend: arch=amd64
12-27 10:35 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\data\isolist.ini
12-27 10:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-27 10:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-27 10:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-27 10:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-27 10:35 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-27 10:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-27 10:35 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-27 10:35 DEBUG  WindowsBackend: Fetching host info...
12-27 10:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-27 10:35 DEBUG  WindowsBackend: windows version=xp
12-27 10:35 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-27 10:35 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-27 10:35 DEBUG  WindowsBackend: windows_build=2600
12-27 10:35 DEBUG  WindowsBackend: gmt=-6
12-27 10:35 DEBUG  WindowsBackend: country=US
12-27 10:35 DEBUG  WindowsBackend: timezone=America/Chicago
12-27 10:35 DEBUG  WindowsBackend: windows_username=customer
12-27 10:35 DEBUG  WindowsBackend: user_full_name=customer
12-27 10:35 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\customer
12-27 10:35 DEBUG  WindowsBackend: windows_language_code=1033
12-27 10:35 DEBUG  WindowsBackend: windows_language=English
12-27 10:35 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 3400+
12-27 10:35 DEBUG  WindowsBackend: bootloader=xp
12-27 10:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 77249.4375 mb free ntfs)
12-27 10:35 DEBUG  WindowsBackend: drive=Drive(C: hd 77249.4375 mb free ntfs)
12-27 10:35 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
12-27 10:35 DEBUG  WindowsBackend: uninstaller_path=None
12-27 10:35 DEBUG  WindowsBackend: previous_target_dir=None
12-27 10:35 DEBUG  WindowsBackend: previous_distro_name=None
12-27 10:35 DEBUG  WindowsBackend: keyboard_id=67699721
12-27 10:35 DEBUG  WindowsBackend: keyboard_layout=us
12-27 10:35 DEBUG  WindowsBackend: keyboard_variant=
12-27 10:35 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-27 10:35 DEBUG  CommonBackend: locale=en_US.UTF-8
12-27 10:35 DEBUG  WindowsBackend: total_memory_mb=1023.359375
12-27 10:35 DEBUG  CommonBackend: Searching ISOs on USB devices
12-27 10:35 DEBUG  CommonBackend: Searching for local CDs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp is a valid Ubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp is a valid Ubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp is a valid Kubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp is a valid Kubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp is a valid Xubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp is a valid Xubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp is a valid Mythbuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp is a valid Mythbuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp is a valid Edubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp is a valid Edubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp is a valid Lubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp is a valid Lubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 10:35 DEBUG  Distro:     does not contain D:\casper\vmlinuz.efi
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 10:35 DEBUG  Distro:   parsing info from str=Ubuntu 12.04.3 LTS "Precise Pangolin" - Release i386 (20130820.1)
12-27 10:35 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04.3', 'build': '20130820.1', 'codename': 'Precise Pangolin', 'arch': 'i386'}
12-27 10:35 DEBUG  Distro: wrong version: 12.04.3 != 12.04.2
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
12-27 10:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-27 10:35 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
12-27 10:35 INFO   root: Running the installer...
12-27 10:35 DEBUG  WindowsFrontend: __init__...
12-27 10:35 DEBUG  WindowsFrontend: on_init...
12-27 10:35 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\translations, languages=['en_US', 'en']
12-27 10:35 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\translations, languages=['en_US', 'en']
12-27 10:36 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=oldcomp
12-27 10:36 INFO   root: Received settings
12-27 10:36 DEBUG  CommonBackend: Searching for local CD
12-27 10:36 DEBUG  Distro:   checking whether C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp is a valid Ubuntu CD
12-27 10:36 DEBUG  Distro:     does not contain C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
12-27 10:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 10:36 DEBUG  Distro:     does not contain D:\casper\vmlinuz.efi
12-27 10:36 DEBUG  CommonBackend: Searching for local ISO
12-27 10:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\customer\LOCALS~1\Temp\pylF.tmp\translations, languages=['en_US', 'en']
12-27 10:36 DEBUG  TaskList: # Running tasklist...
12-27 10:36 DEBUG  TaskList: ## Running select_target_dir...
12-27 10:36 INFO   WindowsBackend: Installing into C:\ubuntu
12-27 10:36 DEBUG  TaskList: ## Finished select_target_dir
12-27 10:36 DEBUG  TaskList: ## Running create_dir_structure...
12-27 10:36 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-27 10:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-27 10:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-27 10:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-27 10:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-27 10:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-27 10:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-27 10:36 DEBUG  TaskList: ## Finished create_dir_structure
12-27 10:36 DEBUG  TaskList: ## Running create_uninstaller...
12-27 10:36 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-27 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-27 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-27 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-27 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-27 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04.1-rev273
12-27 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-27 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-27 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-27 10:36 DEBUG  TaskList: ## Finished create_uninstaller
12-27 10:36 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-27 10:36 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-27 10:36 DEBUG  TaskList: ## Running get_diskimage...
12-27 10:36 DEBUG  TaskList: New task download
12-27 10:36 DEBUG  TaskList: ### Running download...
12-27 10:36 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
12-27 10:36 ERROR  TaskList: unsupported operand type(s) for /: 'NoneType' and 'int'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 77, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1114, in _do_open
  File "\lib\wubi\backends\common\downloader.py", line 46, in start
TypeError: unsupported operand type(s) for /: 'NoneType' and 'int'
12-27 10:36 ERROR  TaskList: Non fatal error unsupported operand type(s) for /: 'NoneType' and 'int' in task download
12-27 10:36 DEBUG  TaskList: ### Finished download
12-27 10:36 DEBUG  TaskList: New task download
12-27 10:36 DEBUG  TaskList: ### Running download...
12-27 10:36 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/precise/wubi/current/amd64.tar.xz](http://cdimage.ubuntu.com/precise/wubi/current/amd64.tar.xz) > C:\ubuntu\disks\amd64.tar.xz
12-27 10:36 ERROR  TaskList: unsupported operand type(s) for /: 'NoneType' and 'int'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 77, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1114, in _do_open
  File "\lib\wubi\backends\common\downloader.py", line 46, in start
TypeError: unsupported operand type(s) for /: 'NoneType' and 'int'
12-27 10:36 ERROR  TaskList: Non fatal error unsupported operand type(s) for /: 'NoneType' and 'int' in task download
12-27 10:36 DEBUG  TaskList: ### Finished download
12-27 10:36 ERROR  TaskList: Could not retrieve the required disk image files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 592, in get_diskimage
Exception: Could not retrieve the required disk image files
12-27 10:36 DEBUG  TaskList: # Cancelling tasklist
12-27 10:36 ERROR  root: Could not retrieve the required disk image files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 592, in get_diskimage
Exception: Could not retrieve the required disk image files
12-27 10:36 DEBUG  TaskList: # Finished tasklist

---

### Post by hakuna_matata on 2013-12-28
The wubi.exe on .iso is older than the single wubi.exe. Try this one: 

[releases.ubuntu.com/precise/wubi.exe]("http://releases.ubuntu.com/precise/wubi.exe")

---

### Post by mark97 on 2013-12-30
The ISO burner wasn't working correctly, used a different one and it installed.

---

