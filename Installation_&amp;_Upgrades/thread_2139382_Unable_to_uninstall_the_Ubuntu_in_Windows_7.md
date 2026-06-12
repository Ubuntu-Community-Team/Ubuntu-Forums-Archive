---
title: "Unable to uninstall the Ubuntu in Windows 7"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by Safeeq on 2013-04-26
I have been using Ubuntu 13.04 for the past few months and yesterday there was an auto update run & since then the Ubuntu is loading properly. When I try to uninstall the Ubuntu, its not getting uninstalled and throwing some exceptions.


[ATTACH=CONFIG]241826[/ATTACH]

Log file:

12-19 22:42 INFO   root: === wubi 11.10 rev245 ===
12-19 22:42 DEBUG  root: Logfile is c:\users\safeeq\appdata\local\temp\wubi-11.10-rev245.log
12-19 22:42 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Safeeq\\Downloads\\wubi.exe"']
12-19 22:42 DEBUG  CommonBackend: data_dir=C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\data
12-19 22:42 DEBUG  WindowsBackend: 7z=C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\bin\7z.exe
12-19 22:42 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-19 22:42 DEBUG  CommonBackend: Fetching basic info...
12-19 22:42 DEBUG  CommonBackend: original_exe=C:\Users\Safeeq\Downloads\wubi.exe
12-19 22:42 DEBUG  CommonBackend: platform=win32
12-19 22:42 DEBUG  CommonBackend: osname=nt
12-19 22:42 DEBUG  CommonBackend: language=en_US
12-19 22:42 DEBUG  CommonBackend: encoding=cp1252
12-19 22:42 DEBUG  WindowsBackend: arch=amd64
12-19 22:42 DEBUG  CommonBackend: Parsing isolist=C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\data\isolist.ini
12-19 22:42 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-19 22:42 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-19 22:42 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-19 22:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-19 22:42 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-19 22:42 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-19 22:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-19 22:42 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-19 22:42 DEBUG  WindowsBackend: Fetching host info...
12-19 22:42 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-19 22:42 DEBUG  WindowsBackend: windows version=vista
12-19 22:42 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-19 22:42 DEBUG  WindowsBackend: windows_sp=None
12-19 22:42 DEBUG  WindowsBackend: windows_build=7601
12-19 22:42 DEBUG  WindowsBackend: gmt=-5
12-19 22:42 DEBUG  WindowsBackend: country=US
12-19 22:42 DEBUG  WindowsBackend: timezone=America/New_York
12-19 22:42 DEBUG  WindowsBackend: windows_username=Safeeq
12-19 22:42 DEBUG  WindowsBackend: user_full_name=Safeeq
12-19 22:42 DEBUG  WindowsBackend: user_directory=C:\Users\Safeeq
12-19 22:42 DEBUG  WindowsBackend: windows_language_code=1033
12-19 22:42 DEBUG  WindowsBackend: windows_language=English
12-19 22:42 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
12-19 22:42 DEBUG  WindowsBackend: bootloader=vista
12-19 22:42 DEBUG  WindowsBackend: system_drive=Drive(C: hd 423708.589844 mb free ntfs)
12-19 22:42 DEBUG  WindowsBackend: drive=Drive(C: hd 423708.589844 mb free ntfs)
12-19 22:42 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
12-19 22:42 DEBUG  WindowsBackend: uninstaller_path=None
12-19 22:42 DEBUG  WindowsBackend: previous_target_dir=None
12-19 22:42 DEBUG  WindowsBackend: previous_distro_name=None
12-19 22:42 DEBUG  WindowsBackend: keyboard_id=67699721
12-19 22:42 DEBUG  WindowsBackend: keyboard_layout=us
12-19 22:42 DEBUG  WindowsBackend: keyboard_variant=
12-19 22:42 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-19 22:42 DEBUG  CommonBackend: locale=en_US.UTF-8
12-19 22:42 DEBUG  WindowsBackend: total_memory_mb=4043.859375
12-19 22:42 DEBUG  CommonBackend: Searching ISOs on USB devices
12-19 22:42 DEBUG  CommonBackend: Searching for local CDs
12-19 22:42 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp is a valid Ubuntu CD
12-19 22:42 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\casper\filesystem.squashfs
12-19 22:42 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp is a valid Ubuntu CD
12-19 22:42 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\casper\filesystem.squashfs
12-19 22:42 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp is a valid Kubuntu CD
12-19 22:42 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\casper\filesystem.squashfs
12-19 22:42 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp is a valid Kubuntu CD
12-19 22:42 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\casper\filesystem.squashfs
12-19 22:42 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp is a valid Xubuntu CD
12-19 22:42 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\casper\filesystem.squashfs
12-19 22:42 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp is a valid Xubuntu CD
12-19 22:42 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\casper\filesystem.squashfs
12-19 22:42 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp is a valid Mythbuntu CD
12-19 22:42 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\casper\filesystem.squashfs
12-19 22:42 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp is a valid Mythbuntu CD
12-19 22:42 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\casper\filesystem.squashfs
12-19 22:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-19 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-19 22:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-19 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-19 22:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-19 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-19 22:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-19 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-19 22:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-19 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-19 22:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-19 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-19 22:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-19 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-19 22:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-19 22:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-19 22:42 INFO   root: Running the installer...
12-19 22:42 DEBUG  WindowsFrontend: __init__...
12-19 22:42 DEBUG  WindowsFrontend: on_init...
12-19 22:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\translations, languages=['en_US', 'en']
12-19 22:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\translations, languages=['en_US', 'en']
12-19 22:43 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=faraza
12-19 22:43 INFO   root: Received settings
12-19 22:43 DEBUG  CommonBackend: Searching for local CD
12-19 22:43 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp is a valid Ubuntu CD
12-19 22:43 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\casper\filesystem.squashfs
12-19 22:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-19 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-19 22:43 DEBUG  CommonBackend: Searching for local ISO
12-19 22:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\translations, languages=['en_US', 'en']
12-19 22:43 DEBUG  TaskList: # Running tasklist...
12-19 22:43 DEBUG  TaskList: ## Running select_target_dir...
12-19 22:43 INFO   WindowsBackend: Installing into C:\ubuntu
12-19 22:43 DEBUG  TaskList: ## Finished select_target_dir
12-19 22:43 DEBUG  TaskList: ## Running create_dir_structure...
12-19 22:43 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-19 22:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-19 22:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-19 22:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-19 22:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-19 22:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-19 22:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-19 22:43 DEBUG  TaskList: ## Finished create_dir_structure
12-19 22:43 DEBUG  TaskList: ## Running create_uninstaller...
12-19 22:43 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Safeeq\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-19 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-19 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-19 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-19 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-19 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-19 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-19 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-19 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-19 22:43 DEBUG  TaskList: ## Finished create_uninstaller
12-19 22:43 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-19 22:43 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-19 22:43 DEBUG  TaskList: ## Running get_diskimage...
12-19 22:43 DEBUG  TaskList: New task download
12-19 22:43 DEBUG  TaskList: ### Running download...
12-19 22:43 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-19 22:43 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-19 23:33 DEBUG  TaskList: ### Finished download
12-19 23:33 DEBUG  downloader: download finished (read 507143012 bytes)
12-19 23:33 DEBUG  TaskList: ## Finished get_diskimage
12-19 23:33 DEBUG  TaskList: ## Running extract_diskimage...
12-19 23:34 DEBUG  TaskList: ## Finished extract_diskimage
12-19 23:34 DEBUG  TaskList: ## Running choose_disk_sizes...
12-19 23:34 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
12-19 23:34 DEBUG  TaskList: ## Finished choose_disk_sizes
12-19 23:34 DEBUG  TaskList: ## Running expand_diskimage...
12-19 23:35 DEBUG  TaskList: ## Finished expand_diskimage
12-19 23:35 DEBUG  TaskList: ## Running create_swap_diskimage...
12-19 23:35 DEBUG  TaskList: ## Finished create_swap_diskimage
12-19 23:35 DEBUG  TaskList: ## Running modify_bootloader...
12-19 23:35 DEBUG  TaskList: New task modify_bcd
12-19 23:35 DEBUG  TaskList: ### Running modify_bcd...
12-19 23:35 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 423708.589844 mb free ntfs)
12-19 23:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc}
12-19 23:35 DEBUG  TaskList: ### Finished modify_bcd
12-19 23:35 DEBUG  TaskList: ## Finished modify_bootloader
12-19 23:35 DEBUG  TaskList: ## Running diskimage_bootloader...
12-19 23:35 DEBUG  WindowsBackend: Copying C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\winboot -> C:\ubuntu\winboot
12-19 23:35 DEBUG  TaskList: ## Finished diskimage_bootloader
12-19 23:35 DEBUG  TaskList: # Finished tasklist
12-19 23:35 INFO   root: Almost finished installing
12-19 23:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pylE4A3.tmp\translations, languages=['en_US', 'en']
12-19 23:35 INFO   root: Finished installation
12-19 23:35 INFO   root: Rebooting
12-19 23:35 DEBUG  TaskList: # Running tasklist...
12-19 23:35 DEBUG  TaskList: ## Running reboot...
12-19 23:35 DEBUG  TaskList: ## Finished reboot
12-19 23:35 DEBUG  TaskList: # Finished tasklist
12-19 23:35 DEBUG  root: application.quit
12-19 23:35 DEBUG  WindowsFrontend: frontend.quit
12-19 23:35 DEBUG  WindowsFrontend: frontend.on_quit
12-19 23:35 DEBUG  root: application.on_quit
12-19 23:35 INFO   root: sys.exit
02-28 10:59 INFO   root: === wubi 11.10 rev245 ===
02-28 10:59 DEBUG  root: Logfile is c:\users\safeeq\appdata\local\temp\wubi-11.10-rev245.log
02-28 10:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
02-28 10:59 DEBUG  CommonBackend: data_dir=C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp\data
02-28 10:59 DEBUG  WindowsBackend: 7z=C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp\bin\7z.exe
02-28 10:59 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-28 10:59 DEBUG  CommonBackend: Fetching basic info...
02-28 10:59 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-28 10:59 DEBUG  CommonBackend: platform=win32
02-28 10:59 DEBUG  CommonBackend: osname=nt
02-28 10:59 DEBUG  CommonBackend: language=en_US
02-28 10:59 DEBUG  CommonBackend: encoding=cp1252
02-28 10:59 DEBUG  WindowsBackend: arch=amd64
02-28 10:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp\data\isolist.ini
02-28 10:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-28 10:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-28 10:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-28 10:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-28 10:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-28 10:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-28 10:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-28 10:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-28 10:59 DEBUG  WindowsBackend: Fetching host info...
02-28 10:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-28 10:59 DEBUG  WindowsBackend: windows version=vista
02-28 10:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-28 10:59 DEBUG  WindowsBackend: windows_sp=None
02-28 10:59 DEBUG  WindowsBackend: windows_build=7601
02-28 10:59 DEBUG  WindowsBackend: gmt=-5
02-28 10:59 DEBUG  WindowsBackend: country=US
02-28 10:59 DEBUG  WindowsBackend: timezone=America/New_York
02-28 10:59 DEBUG  WindowsBackend: windows_username=Safeeq
02-28 10:59 DEBUG  WindowsBackend: user_full_name=Safeeq
02-28 10:59 DEBUG  WindowsBackend: user_directory=C:\Users\Safeeq
02-28 10:59 DEBUG  WindowsBackend: windows_language_code=1033
02-28 10:59 DEBUG  WindowsBackend: windows_language=English
02-28 10:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
02-28 10:59 DEBUG  WindowsBackend: bootloader=vista
02-28 10:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 394415.152344 mb free ntfs)
02-28 10:59 DEBUG  WindowsBackend: drive=Drive(C: hd 394415.152344 mb free ntfs)
02-28 10:59 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-28 10:59 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-28 10:59 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-28 10:59 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-28 10:59 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-28 10:59 DEBUG  WindowsBackend: keyboard_id=67699721
02-28 10:59 DEBUG  WindowsBackend: keyboard_layout=us
02-28 10:59 DEBUG  WindowsBackend: keyboard_variant=
02-28 10:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-28 10:59 DEBUG  CommonBackend: locale=en_US.UTF-8
02-28 10:59 DEBUG  WindowsBackend: total_memory_mb=4043.859375
02-28 10:59 DEBUG  CommonBackend: Searching ISOs on USB devices
02-28 10:59 DEBUG  CommonBackend: Searching for local CDs
02-28 10:59 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp is a valid Ubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp is a valid Ubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp is a valid Kubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp is a valid Kubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp is a valid Xubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp is a valid Xubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp is a valid Mythbuntu CD
02-28 10:59 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp is a valid Mythbuntu CD
02-28 10:59 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-28 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-28 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-28 10:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-28 10:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 10:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-28 10:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 10:59 INFO   root: Running the uninstaller...
02-28 10:59 INFO   CommonBackend: This is the uninstaller running
02-28 10:59 DEBUG  WindowsFrontend: __init__...
02-28 10:59 DEBUG  WindowsFrontend: on_init...
02-28 10:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pyl3F51.tmp\translations, languages=['en_US', 'en']
02-28 10:59 INFO   WindowsFrontend: Operation cancelled
02-28 10:59 DEBUG  WindowsFrontend: frontend.quit
02-28 10:59 DEBUG  WindowsFrontend: frontend.on_quit
02-28 10:59 DEBUG  root: application.on_quit
02-28 10:59 INFO   root: sys.exit
02-28 11:00 INFO   root: === wubi 11.10 rev245 ===
02-28 11:00 DEBUG  root: Logfile is c:\users\safeeq\appdata\local\temp\wubi-11.10-rev245.log
02-28 11:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Safeeq\\Downloads\\wubi.exe"']
02-28 11:00 DEBUG  CommonBackend: data_dir=C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp\data
02-28 11:00 DEBUG  WindowsBackend: 7z=C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp\bin\7z.exe
02-28 11:00 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-28 11:00 DEBUG  CommonBackend: Fetching basic info...
02-28 11:00 DEBUG  CommonBackend: original_exe=C:\Users\Safeeq\Downloads\wubi.exe
02-28 11:00 DEBUG  CommonBackend: platform=win32
02-28 11:00 DEBUG  CommonBackend: osname=nt
02-28 11:00 DEBUG  CommonBackend: language=en_US
02-28 11:00 DEBUG  CommonBackend: encoding=cp1252
02-28 11:00 DEBUG  WindowsBackend: arch=amd64
02-28 11:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp\data\isolist.ini
02-28 11:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-28 11:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-28 11:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-28 11:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-28 11:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-28 11:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-28 11:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-28 11:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-28 11:00 DEBUG  WindowsBackend: Fetching host info...
02-28 11:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-28 11:00 DEBUG  WindowsBackend: windows version=vista
02-28 11:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-28 11:00 DEBUG  WindowsBackend: windows_sp=None
02-28 11:00 DEBUG  WindowsBackend: windows_build=7601
02-28 11:00 DEBUG  WindowsBackend: gmt=-5
02-28 11:00 DEBUG  WindowsBackend: country=US
02-28 11:00 DEBUG  WindowsBackend: timezone=America/New_York
02-28 11:00 DEBUG  WindowsBackend: windows_username=Safeeq
02-28 11:00 DEBUG  WindowsBackend: user_full_name=Safeeq
02-28 11:00 DEBUG  WindowsBackend: user_directory=C:\Users\Safeeq
02-28 11:00 DEBUG  WindowsBackend: windows_language_code=1033
02-28 11:00 DEBUG  WindowsBackend: windows_language=English
02-28 11:00 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
02-28 11:00 DEBUG  WindowsBackend: bootloader=vista
02-28 11:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 394424.335938 mb free ntfs)
02-28 11:00 DEBUG  WindowsBackend: drive=Drive(C: hd 394424.335938 mb free ntfs)
02-28 11:00 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-28 11:00 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-28 11:00 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-28 11:00 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-28 11:00 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-28 11:00 DEBUG  WindowsBackend: keyboard_id=67699721
02-28 11:00 DEBUG  WindowsBackend: keyboard_layout=us
02-28 11:00 DEBUG  WindowsBackend: keyboard_variant=
02-28 11:00 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-28 11:00 DEBUG  CommonBackend: locale=en_US.UTF-8
02-28 11:00 DEBUG  WindowsBackend: total_memory_mb=4043.859375
02-28 11:00 DEBUG  CommonBackend: Searching ISOs on USB devices
02-28 11:00 DEBUG  CommonBackend: Searching for local CDs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp is a valid Ubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp is a valid Ubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp is a valid Kubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp is a valid Kubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp is a valid Xubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp is a valid Xubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp is a valid Mythbuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp is a valid Mythbuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 INFO   root: Already installed, running the uninstaller...
02-28 11:00 INFO   root: Running the uninstaller...
02-28 11:00 INFO   CommonBackend: This is the uninstaller running
02-28 11:00 DEBUG  WindowsFrontend: __init__...
02-28 11:00 DEBUG  WindowsFrontend: on_init...
02-28 11:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pylB8C4.tmp\translations, languages=['en_US', 'en']
02-28 11:00 INFO   WindowsFrontend: Operation cancelled
02-28 11:00 DEBUG  WindowsFrontend: frontend.quit
02-28 11:00 DEBUG  WindowsFrontend: frontend.on_quit
02-28 11:00 DEBUG  root: application.on_quit
02-28 11:00 INFO   root: sys.exit
02-28 11:00 INFO   root: === wubi 11.10 rev245 ===
02-28 11:00 DEBUG  root: Logfile is c:\users\safeeq\appdata\local\temp\wubi-11.10-rev245.log
02-28 11:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
02-28 11:00 DEBUG  CommonBackend: data_dir=C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp\data
02-28 11:00 DEBUG  WindowsBackend: 7z=C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp\bin\7z.exe
02-28 11:00 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-28 11:00 DEBUG  CommonBackend: Fetching basic info...
02-28 11:00 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-28 11:00 DEBUG  CommonBackend: platform=win32
02-28 11:00 DEBUG  CommonBackend: osname=nt
02-28 11:00 DEBUG  CommonBackend: language=en_US
02-28 11:00 DEBUG  CommonBackend: encoding=cp1252
02-28 11:00 DEBUG  WindowsBackend: arch=amd64
02-28 11:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp\data\isolist.ini
02-28 11:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-28 11:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-28 11:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-28 11:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-28 11:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-28 11:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-28 11:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-28 11:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-28 11:00 DEBUG  WindowsBackend: Fetching host info...
02-28 11:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-28 11:00 DEBUG  WindowsBackend: windows version=vista
02-28 11:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-28 11:00 DEBUG  WindowsBackend: windows_sp=None
02-28 11:00 DEBUG  WindowsBackend: windows_build=7601
02-28 11:00 DEBUG  WindowsBackend: gmt=-5
02-28 11:00 DEBUG  WindowsBackend: country=US
02-28 11:00 DEBUG  WindowsBackend: timezone=America/New_York
02-28 11:00 DEBUG  WindowsBackend: windows_username=Safeeq
02-28 11:00 DEBUG  WindowsBackend: user_full_name=Safeeq
02-28 11:00 DEBUG  WindowsBackend: user_directory=C:\Users\Safeeq
02-28 11:00 DEBUG  WindowsBackend: windows_language_code=1033
02-28 11:00 DEBUG  WindowsBackend: windows_language=English
02-28 11:00 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
02-28 11:00 DEBUG  WindowsBackend: bootloader=vista
02-28 11:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 394413.769531 mb free ntfs)
02-28 11:00 DEBUG  WindowsBackend: drive=Drive(C: hd 394413.769531 mb free ntfs)
02-28 11:00 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-28 11:00 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-28 11:00 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-28 11:00 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-28 11:00 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-28 11:00 DEBUG  WindowsBackend: keyboard_id=67699721
02-28 11:00 DEBUG  WindowsBackend: keyboard_layout=us
02-28 11:00 DEBUG  WindowsBackend: keyboard_variant=
02-28 11:00 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-28 11:00 DEBUG  CommonBackend: locale=en_US.UTF-8
02-28 11:00 DEBUG  WindowsBackend: total_memory_mb=4043.859375
02-28 11:00 DEBUG  CommonBackend: Searching ISOs on USB devices
02-28 11:00 DEBUG  CommonBackend: Searching for local CDs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp is a valid Ubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp is a valid Ubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp is a valid Kubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp is a valid Kubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp is a valid Xubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp is a valid Xubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp is a valid Mythbuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp is a valid Mythbuntu CD
02-28 11:00 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-28 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-28 11:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-28 11:00 INFO   root: Running the uninstaller...
02-28 11:00 INFO   CommonBackend: This is the uninstaller running
02-28 11:00 DEBUG  WindowsFrontend: __init__...
02-28 11:00 DEBUG  WindowsFrontend: on_init...
02-28 11:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp\translations, languages=['en_US', 'en']
02-28 11:00 INFO   root: Received settings
02-28 11:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp\translations, languages=['en_US', 'en']
02-28 11:00 DEBUG  TaskList: # Running tasklist...
02-28 11:00 DEBUG  TaskList: ## Running Remove bootloader entry...
02-28 11:00 DEBUG  WindowsBackend: Removing bcd entry {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc}
02-28 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
02-28 11:00 DEBUG  WindowsBackend: undo_bootini C:
02-28 11:00 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 394413.769531 mb free ntfs)
02-28 11:00 DEBUG  WindowsBackend: undo_bootini Q:
02-28 11:00 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
02-28 11:00 DEBUG  TaskList: ## Finished Remove bootloader entry
02-28 11:00 DEBUG  TaskList: ## Running Remove target dir...
02-28 11:00 DEBUG  CommonBackend: Deleting C:\ubuntu
02-28 11:00 DEBUG  TaskList: ## Finished Remove target dir
02-28 11:00 DEBUG  TaskList: ## Running Remove registry key...
02-28 11:00 DEBUG  TaskList: ## Finished Remove registry key
02-28 11:00 DEBUG  TaskList: # Finished tasklist
02-28 11:00 INFO   root: Almost finished uninstalling
02-28 11:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pylDB22.tmp\translations, languages=['en_US', 'en']
02-28 11:00 INFO   root: Finished uninstallation
02-28 11:00 DEBUG  root: application.quit
02-28 11:00 DEBUG  WindowsFrontend: frontend.quit
02-28 11:00 DEBUG  WindowsFrontend: frontend.on_quit
02-28 11:00 DEBUG  root: application.on_quit
02-28 11:00 INFO   root: sys.exit
04-26 10:02 INFO   root: === wubi 11.10 rev245 ===
04-26 10:02 DEBUG  root: Logfile is c:\users\safeeq\appdata\local\temp\wubi-11.10-rev245.log
04-26 10:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
04-26 10:02 DEBUG  CommonBackend: data_dir=C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp\data
04-26 10:02 DEBUG  WindowsBackend: 7z=C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp\bin\7z.exe
04-26 10:02 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-26 10:02 DEBUG  CommonBackend: Fetching basic info...
04-26 10:02 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-26 10:02 DEBUG  CommonBackend: platform=win32
04-26 10:02 DEBUG  CommonBackend: osname=nt
04-26 10:02 DEBUG  CommonBackend: language=en_US
04-26 10:02 DEBUG  CommonBackend: encoding=cp1252
04-26 10:02 DEBUG  WindowsBackend: arch=amd64
04-26 10:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp\data\isolist.ini
04-26 10:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 10:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 10:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 10:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 10:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 10:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 10:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 10:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 10:02 DEBUG  WindowsBackend: Fetching host info...
04-26 10:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 10:02 DEBUG  WindowsBackend: windows version=vista
04-26 10:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-26 10:02 DEBUG  WindowsBackend: windows_sp=None
04-26 10:02 DEBUG  WindowsBackend: windows_build=7601
04-26 10:02 DEBUG  WindowsBackend: gmt=-5
04-26 10:02 DEBUG  WindowsBackend: country=US
04-26 10:02 DEBUG  WindowsBackend: timezone=America/New_York
04-26 10:02 DEBUG  WindowsBackend: windows_username=Safeeq
04-26 10:02 DEBUG  WindowsBackend: user_full_name=Safeeq
04-26 10:02 DEBUG  WindowsBackend: user_directory=C:\Users\Safeeq
04-26 10:02 DEBUG  WindowsBackend: windows_language_code=1033
04-26 10:02 DEBUG  WindowsBackend: windows_language=English
04-26 10:02 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
04-26 10:02 DEBUG  WindowsBackend: bootloader=vista
04-26 10:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392335.816406 mb free ntfs)
04-26 10:02 DEBUG  WindowsBackend: drive=Drive(C: hd 392335.816406 mb free ntfs)
04-26 10:02 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-26 10:02 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-26 10:02 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-26 10:02 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-26 10:02 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-26 10:02 DEBUG  WindowsBackend: keyboard_id=67699721
04-26 10:02 DEBUG  WindowsBackend: keyboard_layout=us
04-26 10:02 DEBUG  WindowsBackend: keyboard_variant=
04-26 10:02 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-26 10:02 DEBUG  CommonBackend: locale=en_US.UTF-8
04-26 10:02 DEBUG  WindowsBackend: total_memory_mb=4043.859375
04-26 10:02 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 10:02 DEBUG  CommonBackend: Searching for local CDs
04-26 10:02 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp is a valid Ubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp is a valid Ubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp is a valid Kubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp is a valid Kubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp is a valid Xubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp is a valid Xubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp is a valid Mythbuntu CD
04-26 10:02 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp is a valid Mythbuntu CD
04-26 10:02 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 10:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-26 10:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-26 10:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:02 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-26 10:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:02 INFO   root: Running the uninstaller...
04-26 10:02 INFO   CommonBackend: This is the uninstaller running
04-26 10:02 DEBUG  WindowsFrontend: __init__...
04-26 10:02 DEBUG  WindowsFrontend: on_init...
04-26 10:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp\translations, languages=['en_US', 'en']
04-26 10:02 INFO   root: Received settings
04-26 10:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pyl118C.tmp\translations, languages=['en_US', 'en']
04-26 10:02 DEBUG  TaskList: # Running tasklist...
04-26 10:02 DEBUG  TaskList: ## Running Remove bootloader entry...
04-26 10:02 DEBUG  WindowsBackend: Removing bcd entry {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc}
04-26 10:03 ERROR  TaskList: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-26 10:03 DEBUG  TaskList: # Cancelling tasklist
04-26 10:03 DEBUG  TaskList: # Finished tasklist
04-26 10:03 ERROR  root: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-26 10:03 INFO   root: === wubi 11.10 rev245 ===
04-26 10:03 DEBUG  root: Logfile is c:\users\safeeq\appdata\local\temp\wubi-11.10-rev245.log
04-26 10:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
04-26 10:03 DEBUG  CommonBackend: data_dir=C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp\data
04-26 10:03 DEBUG  WindowsBackend: 7z=C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp\bin\7z.exe
04-26 10:03 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-26 10:03 DEBUG  CommonBackend: Fetching basic info...
04-26 10:03 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-26 10:03 DEBUG  CommonBackend: platform=win32
04-26 10:03 DEBUG  CommonBackend: osname=nt
04-26 10:03 DEBUG  CommonBackend: language=en_US
04-26 10:03 DEBUG  CommonBackend: encoding=cp1252
04-26 10:03 DEBUG  WindowsBackend: arch=amd64
04-26 10:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp\data\isolist.ini
04-26 10:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 10:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 10:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 10:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 10:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 10:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 10:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 10:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 10:03 DEBUG  WindowsBackend: Fetching host info...
04-26 10:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 10:03 DEBUG  WindowsBackend: windows version=vista
04-26 10:03 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
04-26 10:03 DEBUG  WindowsBackend: windows_sp=None
04-26 10:03 DEBUG  WindowsBackend: windows_build=6000
04-26 10:03 DEBUG  WindowsBackend: gmt=-5
04-26 10:03 DEBUG  WindowsBackend: country=US
04-26 10:03 DEBUG  WindowsBackend: timezone=America/New_York
04-26 10:03 DEBUG  WindowsBackend: windows_username=Safeeq
04-26 10:03 DEBUG  WindowsBackend: user_full_name=Safeeq
04-26 10:03 DEBUG  WindowsBackend: user_directory=C:\Users\Safeeq
04-26 10:03 DEBUG  WindowsBackend: windows_language_code=1033
04-26 10:03 DEBUG  WindowsBackend: windows_language=English
04-26 10:03 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
04-26 10:03 DEBUG  WindowsBackend: bootloader=vista
04-26 10:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392341.140625 mb free ntfs)
04-26 10:03 DEBUG  WindowsBackend: drive=Drive(C: hd 392341.140625 mb free ntfs)
04-26 10:03 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-26 10:03 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-26 10:03 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-26 10:03 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-26 10:03 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-26 10:03 DEBUG  WindowsBackend: keyboard_id=67699721
04-26 10:03 DEBUG  WindowsBackend: keyboard_layout=us
04-26 10:03 DEBUG  WindowsBackend: keyboard_variant=
04-26 10:03 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-26 10:03 DEBUG  CommonBackend: locale=en_US.UTF-8
04-26 10:03 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
04-26 10:03 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 10:03 DEBUG  CommonBackend: Searching for local CDs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 INFO   root: Running the uninstaller...
04-26 10:03 INFO   CommonBackend: This is the uninstaller running
04-26 10:03 DEBUG  WindowsFrontend: __init__...
04-26 10:03 DEBUG  WindowsFrontend: on_init...
04-26 10:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp\translations, languages=['en_US', 'en']
04-26 10:03 INFO   root: Received settings
04-26 10:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pyl6A46.tmp\translations, languages=['en_US', 'en']
04-26 10:03 DEBUG  TaskList: # Running tasklist...
04-26 10:03 DEBUG  TaskList: ## Running Remove bootloader entry...
04-26 10:03 DEBUG  WindowsBackend: Removing bcd entry {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc}
04-26 10:03 ERROR  TaskList: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-26 10:03 DEBUG  TaskList: # Cancelling tasklist
04-26 10:03 DEBUG  TaskList: # Finished tasklist
04-26 10:03 ERROR  root: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-26 10:03 INFO   root: === wubi 11.10 rev245 ===
04-26 10:03 DEBUG  root: Logfile is c:\users\safeeq\appdata\local\temp\wubi-11.10-rev245.log
04-26 10:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
04-26 10:03 DEBUG  CommonBackend: data_dir=C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp\data
04-26 10:03 DEBUG  WindowsBackend: 7z=C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp\bin\7z.exe
04-26 10:03 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-26 10:03 DEBUG  CommonBackend: Fetching basic info...
04-26 10:03 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-26 10:03 DEBUG  CommonBackend: platform=win32
04-26 10:03 DEBUG  CommonBackend: osname=nt
04-26 10:03 DEBUG  CommonBackend: language=en_US
04-26 10:03 DEBUG  CommonBackend: encoding=cp1252
04-26 10:03 DEBUG  WindowsBackend: arch=amd64
04-26 10:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp\data\isolist.ini
04-26 10:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 10:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 10:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 10:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 10:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 10:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 10:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 10:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 10:03 DEBUG  WindowsBackend: Fetching host info...
04-26 10:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 10:03 DEBUG  WindowsBackend: windows version=vista
04-26 10:03 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
04-26 10:03 DEBUG  WindowsBackend: windows_sp=None
04-26 10:03 DEBUG  WindowsBackend: windows_build=6000
04-26 10:03 DEBUG  WindowsBackend: gmt=-5
04-26 10:03 DEBUG  WindowsBackend: country=US
04-26 10:03 DEBUG  WindowsBackend: timezone=America/New_York
04-26 10:03 DEBUG  WindowsBackend: windows_username=Safeeq
04-26 10:03 DEBUG  WindowsBackend: user_full_name=Safeeq
04-26 10:03 DEBUG  WindowsBackend: user_directory=C:\Users\Safeeq
04-26 10:03 DEBUG  WindowsBackend: windows_language_code=1033
04-26 10:03 DEBUG  WindowsBackend: windows_language=English
04-26 10:03 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
04-26 10:03 DEBUG  WindowsBackend: bootloader=vista
04-26 10:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392335.742188 mb free ntfs)
04-26 10:03 DEBUG  WindowsBackend: drive=Drive(C: hd 392335.742188 mb free ntfs)
04-26 10:03 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-26 10:03 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-26 10:03 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-26 10:03 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-26 10:03 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-26 10:03 DEBUG  WindowsBackend: keyboard_id=67699721
04-26 10:03 DEBUG  WindowsBackend: keyboard_layout=us
04-26 10:03 DEBUG  WindowsBackend: keyboard_variant=
04-26 10:03 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-26 10:03 DEBUG  CommonBackend: locale=en_US.UTF-8
04-26 10:03 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
04-26 10:03 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 10:03 DEBUG  CommonBackend: Searching for local CDs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 INFO   root: Running the uninstaller...
04-26 10:03 INFO   CommonBackend: This is the uninstaller running
04-26 10:03 DEBUG  WindowsFrontend: __init__...
04-26 10:03 DEBUG  WindowsFrontend: on_init...
04-26 10:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp\translations, languages=['en_US', 'en']
04-26 10:03 INFO   root: Received settings
04-26 10:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pyl9990.tmp\translations, languages=['en_US', 'en']
04-26 10:03 DEBUG  TaskList: # Running tasklist...
04-26 10:03 DEBUG  TaskList: ## Running Remove bootloader entry...
04-26 10:03 DEBUG  WindowsBackend: Removing bcd entry {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc}
04-26 10:03 ERROR  TaskList: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-26 10:03 DEBUG  TaskList: # Cancelling tasklist
04-26 10:03 DEBUG  TaskList: # Finished tasklist
04-26 10:03 ERROR  root: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-26 10:03 INFO   root: === wubi 11.10 rev245 ===
04-26 10:03 DEBUG  root: Logfile is c:\users\safeeq\appdata\local\temp\wubi-11.10-rev245.log
04-26 10:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
04-26 10:03 DEBUG  CommonBackend: data_dir=C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp\data
04-26 10:03 DEBUG  WindowsBackend: 7z=C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp\bin\7z.exe
04-26 10:03 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-26 10:03 DEBUG  CommonBackend: Fetching basic info...
04-26 10:03 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-26 10:03 DEBUG  CommonBackend: platform=win32
04-26 10:03 DEBUG  CommonBackend: osname=nt
04-26 10:03 DEBUG  CommonBackend: language=en_US
04-26 10:03 DEBUG  CommonBackend: encoding=cp1252
04-26 10:03 DEBUG  WindowsBackend: arch=amd64
04-26 10:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp\data\isolist.ini
04-26 10:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 10:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 10:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 10:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 10:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 10:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 10:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 10:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 10:03 DEBUG  WindowsBackend: Fetching host info...
04-26 10:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 10:03 DEBUG  WindowsBackend: windows version=vista
04-26 10:03 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
04-26 10:03 DEBUG  WindowsBackend: windows_sp=None
04-26 10:03 DEBUG  WindowsBackend: windows_build=6000
04-26 10:03 DEBUG  WindowsBackend: gmt=-5
04-26 10:03 DEBUG  WindowsBackend: country=US
04-26 10:03 DEBUG  WindowsBackend: timezone=America/New_York
04-26 10:03 DEBUG  WindowsBackend: windows_username=Safeeq
04-26 10:03 DEBUG  WindowsBackend: user_full_name=Safeeq
04-26 10:03 DEBUG  WindowsBackend: user_directory=C:\Users\Safeeq
04-26 10:03 DEBUG  WindowsBackend: windows_language_code=1033
04-26 10:03 DEBUG  WindowsBackend: windows_language=English
04-26 10:03 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
04-26 10:03 DEBUG  WindowsBackend: bootloader=vista
04-26 10:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392337.625 mb free ntfs)
04-26 10:03 DEBUG  WindowsBackend: drive=Drive(C: hd 392337.625 mb free ntfs)
04-26 10:03 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-26 10:03 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-26 10:03 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-26 10:03 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-26 10:03 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-26 10:03 DEBUG  WindowsBackend: keyboard_id=67699721
04-26 10:03 DEBUG  WindowsBackend: keyboard_layout=us
04-26 10:03 DEBUG  WindowsBackend: keyboard_variant=
04-26 10:03 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-26 10:03 DEBUG  CommonBackend: locale=en_US.UTF-8
04-26 10:03 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
04-26 10:03 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 10:03 DEBUG  CommonBackend: Searching for local CDs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-26 10:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 10:03 INFO   root: Running the uninstaller...
04-26 10:03 INFO   CommonBackend: This is the uninstaller running
04-26 10:03 DEBUG  WindowsFrontend: __init__...
04-26 10:03 DEBUG  WindowsFrontend: on_init...
04-26 10:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pyl8FEF.tmp\translations, languages=['en_US', 'en']
04-26 15:46 INFO   root: === wubi 11.10 rev245 ===
04-26 15:46 DEBUG  root: Logfile is c:\users\safeeq\appdata\local\temp\wubi-11.10-rev245.log
04-26 15:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
04-26 15:46 DEBUG  CommonBackend: data_dir=C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp\data
04-26 15:46 DEBUG  WindowsBackend: 7z=C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp\bin\7z.exe
04-26 15:46 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-26 15:46 DEBUG  CommonBackend: Fetching basic info...
04-26 15:46 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-26 15:46 DEBUG  CommonBackend: platform=win32
04-26 15:46 DEBUG  CommonBackend: osname=nt
04-26 15:46 DEBUG  CommonBackend: language=en_US
04-26 15:46 DEBUG  CommonBackend: encoding=cp1252
04-26 15:46 DEBUG  WindowsBackend: arch=amd64
04-26 15:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp\data\isolist.ini
04-26 15:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 15:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 15:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 15:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 15:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 15:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 15:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 15:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 15:46 DEBUG  WindowsBackend: Fetching host info...
04-26 15:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 15:46 DEBUG  WindowsBackend: windows version=vista
04-26 15:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-26 15:46 DEBUG  WindowsBackend: windows_sp=None
04-26 15:46 DEBUG  WindowsBackend: windows_build=7601
04-26 15:46 DEBUG  WindowsBackend: gmt=-5
04-26 15:46 DEBUG  WindowsBackend: country=US
04-26 15:46 DEBUG  WindowsBackend: timezone=America/New_York
04-26 15:46 DEBUG  WindowsBackend: windows_username=Safeeq
04-26 15:46 DEBUG  WindowsBackend: user_full_name=Safeeq
04-26 15:46 DEBUG  WindowsBackend: user_directory=C:\Users\Safeeq
04-26 15:46 DEBUG  WindowsBackend: windows_language_code=1033
04-26 15:46 DEBUG  WindowsBackend: windows_language=English
04-26 15:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
04-26 15:46 DEBUG  WindowsBackend: bootloader=vista
04-26 15:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 390249.464844 mb free ntfs)
04-26 15:46 DEBUG  WindowsBackend: drive=Drive(C: hd 390249.464844 mb free ntfs)
04-26 15:46 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-26 15:46 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-26 15:46 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-26 15:46 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-26 15:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-26 15:46 DEBUG  WindowsBackend: keyboard_id=67699721
04-26 15:46 DEBUG  WindowsBackend: keyboard_layout=us
04-26 15:46 DEBUG  WindowsBackend: keyboard_variant=
04-26 15:46 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-26 15:46 DEBUG  CommonBackend: locale=en_US.UTF-8
04-26 15:46 DEBUG  WindowsBackend: total_memory_mb=4043.859375
04-26 15:46 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 15:46 DEBUG  CommonBackend: Searching for local CDs
04-26 15:46 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp is a valid Ubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp is a valid Ubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp is a valid Kubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp is a valid Kubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp is a valid Xubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp is a valid Xubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp is a valid Mythbuntu CD
04-26 15:46 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp is a valid Mythbuntu CD
04-26 15:46 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 15:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-26 15:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-26 15:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:46 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-26 15:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:46 INFO   root: Running the uninstaller...
04-26 15:46 INFO   CommonBackend: This is the uninstaller running
04-26 15:46 DEBUG  WindowsFrontend: __init__...
04-26 15:46 DEBUG  WindowsFrontend: on_init...
04-26 15:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp\translations, languages=['en_US', 'en']
04-26 15:46 INFO   root: Received settings
04-26 15:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pylF4D9.tmp\translations, languages=['en_US', 'en']
04-26 15:46 DEBUG  TaskList: # Running tasklist...
04-26 15:46 DEBUG  TaskList: ## Running Remove bootloader entry...
04-26 15:46 DEBUG  WindowsBackend: Removing bcd entry {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc}
04-26 15:46 ERROR  TaskList: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-26 15:46 DEBUG  TaskList: # Cancelling tasklist
04-26 15:46 DEBUG  TaskList: # Finished tasklist
04-26 15:46 ERROR  root: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-26 15:50 INFO   root: === wubi 11.10 rev245 ===
04-26 15:50 DEBUG  root: Logfile is c:\users\safeeq\appdata\local\temp\wubi-11.10-rev245.log
04-26 15:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
04-26 15:50 DEBUG  CommonBackend: data_dir=C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp\data
04-26 15:50 DEBUG  WindowsBackend: 7z=C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp\bin\7z.exe
04-26 15:50 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-26 15:50 DEBUG  CommonBackend: Fetching basic info...
04-26 15:50 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-26 15:50 DEBUG  CommonBackend: platform=win32
04-26 15:50 DEBUG  CommonBackend: osname=nt
04-26 15:50 DEBUG  CommonBackend: language=en_US
04-26 15:50 DEBUG  CommonBackend: encoding=cp1252
04-26 15:50 DEBUG  WindowsBackend: arch=amd64
04-26 15:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp\data\isolist.ini
04-26 15:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 15:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 15:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 15:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 15:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 15:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 15:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 15:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 15:50 DEBUG  WindowsBackend: Fetching host info...
04-26 15:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 15:50 DEBUG  WindowsBackend: windows version=vista
04-26 15:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-26 15:50 DEBUG  WindowsBackend: windows_sp=None
04-26 15:50 DEBUG  WindowsBackend: windows_build=7601
04-26 15:50 DEBUG  WindowsBackend: gmt=-5
04-26 15:50 DEBUG  WindowsBackend: country=US
04-26 15:50 DEBUG  WindowsBackend: timezone=America/New_York
04-26 15:50 DEBUG  WindowsBackend: windows_username=Safeeq
04-26 15:50 DEBUG  WindowsBackend: user_full_name=Safeeq
04-26 15:50 DEBUG  WindowsBackend: user_directory=C:\Users\Safeeq
04-26 15:50 DEBUG  WindowsBackend: windows_language_code=1033
04-26 15:50 DEBUG  WindowsBackend: windows_language=English
04-26 15:50 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
04-26 15:50 DEBUG  WindowsBackend: bootloader=vista
04-26 15:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 390274.25 mb free ntfs)
04-26 15:50 DEBUG  WindowsBackend: drive=Drive(C: hd 390274.273438 mb free ntfs)
04-26 15:50 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-26 15:50 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-26 15:50 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-26 15:50 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-26 15:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-26 15:50 DEBUG  WindowsBackend: keyboard_id=67699721
04-26 15:50 DEBUG  WindowsBackend: keyboard_layout=us
04-26 15:50 DEBUG  WindowsBackend: keyboard_variant=
04-26 15:50 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-26 15:50 DEBUG  CommonBackend: locale=en_US.UTF-8
04-26 15:50 DEBUG  WindowsBackend: total_memory_mb=4043.859375
04-26 15:50 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 15:50 DEBUG  CommonBackend: Searching for local CDs
04-26 15:50 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp is a valid Ubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp is a valid Ubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp is a valid Kubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp is a valid Kubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp is a valid Xubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp is a valid Xubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp is a valid Mythbuntu CD
04-26 15:50 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp is a valid Mythbuntu CD
04-26 15:50 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 15:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 15:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-26 15:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-26 15:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:50 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-26 15:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:50 INFO   root: Running the uninstaller...
04-26 15:50 INFO   CommonBackend: This is the uninstaller running
04-26 15:50 DEBUG  WindowsFrontend: __init__...
04-26 15:50 DEBUG  WindowsFrontend: on_init...
04-26 15:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp\translations, languages=['en_US', 'en']
04-26 15:50 INFO   root: Received settings
04-26 15:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pylFB10.tmp\translations, languages=['en_US', 'en']
04-26 15:50 DEBUG  TaskList: # Running tasklist...
04-26 15:50 DEBUG  TaskList: ## Running Remove bootloader entry...
04-26 15:50 DEBUG  WindowsBackend: Removing bcd entry {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc}
04-26 15:50 ERROR  TaskList: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-26 15:50 DEBUG  TaskList: # Cancelling tasklist
04-26 15:50 ERROR  root: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-26 15:50 DEBUG  TaskList: # Finished tasklist
04-26 15:52 INFO   root: === wubi 11.10 rev245 ===
04-26 15:52 DEBUG  root: Logfile is c:\users\safeeq\appdata\local\temp\wubi-11.10-rev245.log
04-26 15:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
04-26 15:52 DEBUG  CommonBackend: data_dir=C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp\data
04-26 15:52 DEBUG  WindowsBackend: 7z=C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp\bin\7z.exe
04-26 15:52 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-26 15:52 DEBUG  CommonBackend: Fetching basic info...
04-26 15:52 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-26 15:52 DEBUG  CommonBackend: platform=win32
04-26 15:52 DEBUG  CommonBackend: osname=nt
04-26 15:52 DEBUG  CommonBackend: language=en_US
04-26 15:52 DEBUG  CommonBackend: encoding=cp1252
04-26 15:52 DEBUG  WindowsBackend: arch=amd64
04-26 15:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp\data\isolist.ini
04-26 15:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-26 15:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-26 15:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-26 15:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-26 15:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-26 15:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-26 15:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-26 15:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-26 15:52 DEBUG  WindowsBackend: Fetching host info...
04-26 15:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-26 15:52 DEBUG  WindowsBackend: windows version=vista
04-26 15:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-26 15:52 DEBUG  WindowsBackend: windows_sp=None
04-26 15:52 DEBUG  WindowsBackend: windows_build=7601
04-26 15:52 DEBUG  WindowsBackend: gmt=-5
04-26 15:52 DEBUG  WindowsBackend: country=US
04-26 15:52 DEBUG  WindowsBackend: timezone=America/New_York
04-26 15:52 DEBUG  WindowsBackend: windows_username=Safeeq
04-26 15:52 DEBUG  WindowsBackend: user_full_name=Safeeq
04-26 15:52 DEBUG  WindowsBackend: user_directory=C:\Users\Safeeq
04-26 15:52 DEBUG  WindowsBackend: windows_language_code=1033
04-26 15:52 DEBUG  WindowsBackend: windows_language=English
04-26 15:52 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
04-26 15:52 DEBUG  WindowsBackend: bootloader=vista
04-26 15:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 390182.695313 mb free ntfs)
04-26 15:52 DEBUG  WindowsBackend: drive=Drive(C: hd 390182.695313 mb free ntfs)
04-26 15:52 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-26 15:52 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-26 15:52 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-26 15:52 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-26 15:52 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-26 15:52 DEBUG  WindowsBackend: keyboard_id=67699721
04-26 15:52 DEBUG  WindowsBackend: keyboard_layout=us
04-26 15:52 DEBUG  WindowsBackend: keyboard_variant=
04-26 15:52 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-26 15:52 DEBUG  CommonBackend: locale=en_US.UTF-8
04-26 15:52 DEBUG  WindowsBackend: total_memory_mb=4043.859375
04-26 15:52 DEBUG  CommonBackend: Searching ISOs on USB devices
04-26 15:52 DEBUG  CommonBackend: Searching for local CDs
04-26 15:52 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp is a valid Ubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp is a valid Ubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp is a valid Kubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp is a valid Kubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp is a valid Xubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp is a valid Xubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp is a valid Mythbuntu CD
04-26 15:52 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp is a valid Mythbuntu CD
04-26 15:52 DEBUG  Distro:     does not contain C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-26 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
04-26 15:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-26 15:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:52 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
04-26 15:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
04-26 15:52 INFO   root: Running the uninstaller...
04-26 15:52 INFO   CommonBackend: This is the uninstaller running
04-26 15:52 DEBUG  WindowsFrontend: __init__...
04-26 15:52 DEBUG  WindowsFrontend: on_init...
04-26 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp\translations, languages=['en_US', 'en']
04-26 15:53 INFO   root: Received settings
04-26 15:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Safeeq\AppData\Local\Temp\pyl2B25.tmp\translations, languages=['en_US', 'en']
04-26 15:53 DEBUG  TaskList: # Running tasklist...
04-26 15:53 DEBUG  TaskList: ## Running Remove bootloader entry...
04-26 15:53 DEBUG  WindowsBackend: Removing bcd entry {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc}
04-26 15:53 ERROR  TaskList: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-26 15:53 DEBUG  TaskList: # Cancelling tasklist
04-26 15:53 DEBUG  TaskList: # Finished tasklist
04-26 15:53 ERROR  root: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\windows\sysnative\bcdedit.exe /delete {d85d5997-fdb3-11e0-b3fe-83a1978ba3cc} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=





Tried the below as well but didnt help


C:\>Diskpart C:\Diskpart> List volume C:\Diskpart> Select volume 1 (Considering this is 100 MB system partition) c:\Diskpart> Online volume C:\Diskpart> exit

---

### Post by bcbc on 2013-04-26
That's a bug in the 11.10 wubi. Refer to this...[URL="https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F"]
https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F[/URL]

---

### Post by Safeeq on 2013-04-26
I did the changes to *bcdedit /delete {GUID}* but couldn't find the regedit "Wubi". I was able to traverse until "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall" but couldnt find Wubi. 

Please let me know if I am doing anything incorrectly.

---

### Post by bcbc on 2013-04-26
If you've deleted the ubuntu directory, the bcdedit entry, and the registry entry is not there, then I guess it's all gone... so there's nothing more to worry about.

---

