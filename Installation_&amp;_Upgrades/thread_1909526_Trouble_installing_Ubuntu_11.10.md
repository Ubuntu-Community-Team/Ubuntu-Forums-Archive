---
title: "Trouble installing Ubuntu 11.10"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by toddjs7 on 2012-01-15
I am trouble installing Ubuntu 11.10 inside Windows7 which both are 64bit? It gives me a error message " No such file directory, for more information, please see the log file    C:\users\username\appdata\local\temp\wubi-11.10-rev245.log "   I have tried it on two computers and it gives my the same error message?

 [COLOR=Red]I have tried the [/COLOR][COLOR=Red]Disc and Windows installer[/COLOR][COLOR=Red] and other things but no luck? I never had this problem before and don't if was Microsoft update that cause this or not?     I always could install this without no problems before!      What can do get this installed????     Please help me out!!!![/COLOR]

THE LOG FILE BELOW:
```

01-15 00:41 INFO   root: === wubi 11.10 rev245 ===
01-15 00:41 DEBUG  root: Logfile is c:\users\win7msi\appdata\local\temp\wubi-11.10-rev245.log
01-15 00:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Win7MSI\\Downloads\\wubi.exe"']
01-15 00:41 DEBUG  CommonBackend: data_dir=C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp\data
01-15 00:41 DEBUG  WindowsBackend: 7z=C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp\bin\7z.exe
01-15 00:41 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-15 00:41 DEBUG  CommonBackend: Fetching basic info...
01-15 00:41 DEBUG  CommonBackend: original_exe=C:\Users\Win7MSI\Downloads\wubi.exe
01-15 00:41 DEBUG  CommonBackend: platform=win32
01-15 00:41 DEBUG  CommonBackend: osname=nt
01-15 00:41 DEBUG  CommonBackend: language=en_US
01-15 00:41 DEBUG  CommonBackend: encoding=cp1252
01-15 00:41 DEBUG  WindowsBackend: arch=amd64
01-15 00:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp\data\isolist.ini
01-15 00:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-15 00:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-15 00:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-15 00:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-15 00:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-15 00:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-15 00:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-15 00:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-15 00:41 DEBUG  WindowsBackend: Fetching host info...
01-15 00:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-15 00:41 DEBUG  WindowsBackend: windows version=vista
01-15 00:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-15 00:41 DEBUG  WindowsBackend: windows_sp=None
01-15 00:41 DEBUG  WindowsBackend: windows_build=7601
01-15 00:41 DEBUG  WindowsBackend: gmt=-5
01-15 00:41 DEBUG  WindowsBackend: country=US
01-15 00:41 DEBUG  WindowsBackend: timezone=America/New_York
01-15 00:41 DEBUG  WindowsBackend: windows_username=Win7MSI
01-15 00:41 DEBUG  WindowsBackend: user_full_name=Win7MSI
01-15 00:41 DEBUG  WindowsBackend: user_directory=C:\Users\Win7MSI
01-15 00:41 DEBUG  WindowsBackend: windows_language_code=1033
01-15 00:41 DEBUG  WindowsBackend: windows_language=English
01-15 00:41 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 955 Processor
01-15 00:41 DEBUG  WindowsBackend: bootloader=vista
01-15 00:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72859.0351563 mb free ntfs)
01-15 00:41 DEBUG  WindowsBackend: drive=Drive(C: hd 72859.0351563 mb free ntfs)
01-15 00:41 DEBUG  WindowsBackend: drive=Drive(D: hd 0.0 mb free )
01-15 00:41 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-15 00:41 DEBUG  WindowsBackend: uninstaller_path=None
01-15 00:41 DEBUG  WindowsBackend: previous_target_dir=None
01-15 00:41 DEBUG  WindowsBackend: previous_distro_name=None
01-15 00:41 DEBUG  WindowsBackend: keyboard_id=67699721
01-15 00:41 DEBUG  WindowsBackend: keyboard_layout=us
01-15 00:41 DEBUG  WindowsBackend: keyboard_variant=
01-15 00:41 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-15 00:41 DEBUG  CommonBackend: locale=en_US.UTF-8
01-15 00:41 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
01-15 00:41 DEBUG  CommonBackend: Searching ISOs on USB devices
01-15 00:41 DEBUG  CommonBackend: Searching for local CDs
01-15 00:41 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp is a valid Ubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp is a valid Ubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp is a valid Kubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp is a valid Kubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp is a valid Xubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp is a valid Xubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp is a valid Mythbuntu CD
01-15 00:41 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp is a valid Mythbuntu CD
01-15 00:41 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-15 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-15 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-15 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-15 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 00:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-15 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 00:41 INFO   root: Running the installer...
01-15 00:41 DEBUG  WindowsFrontend: __init__...
01-15 00:41 DEBUG  WindowsFrontend: on_init...
01-15 00:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp\translations, languages=['en_US', 'en']
01-15 00:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp\translations, languages=['en_US', 'en']
01-15 00:42 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=15000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=win7msi
01-15 00:42 INFO   root: Received settings
01-15 00:42 DEBUG  CommonBackend: Searching for local CD
01-15 00:42 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp is a valid Ubuntu CD
01-15 00:42 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp\casper\filesystem.squashfs
01-15 00:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-15 00:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 00:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-15 00:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 00:42 DEBUG  CommonBackend: Searching for local ISO
01-15 00:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Win7MSI\AppData\Local\Temp\pyl92EB.tmp\translations, languages=['en_US', 'en']
01-15 00:42 DEBUG  TaskList: # Running tasklist...
01-15 00:42 DEBUG  TaskList: ## Running select_target_dir...
01-15 00:42 INFO   WindowsBackend: Installing into C:\ubuntu
01-15 00:42 DEBUG  TaskList: ## Finished select_target_dir
01-15 00:42 DEBUG  TaskList: ## Running create_dir_structure...
01-15 00:42 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-15 00:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-15 00:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-15 00:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-15 00:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-15 00:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-15 00:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-15 00:42 DEBUG  TaskList: ## Finished create_dir_structure
01-15 00:42 DEBUG  TaskList: ## Running create_uninstaller...
01-15 00:42 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Win7MSI\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-15 00:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-15 00:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-15 00:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-15 00:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-15 00:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
01-15 00:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-15 00:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-15 00:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-15 00:42 DEBUG  TaskList: ## Finished create_uninstaller
01-15 00:42 DEBUG  TaskList: ## Running create_preseed_diskimage...
01-15 00:42 DEBUG  TaskList: ## Finished create_preseed_diskimage
01-15 00:42 DEBUG  TaskList: ## Running get_diskimage...
01-15 00:42 DEBUG  TaskList: New task download
01-15 00:42 DEBUG  TaskList: ### Running download...
01-15 00:42 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
01-15 00:42 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
01-15 00:43 INFO   WindowsFrontend: Operation cancelled
01-15 00:43 DEBUG  WindowsFrontend: frontend.quit
01-15 00:43 DEBUG  WindowsFrontend: frontend.on_quit
01-15 00:43 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
01-15 00:43 DEBUG  TaskList: # Cancelling tasklist
01-15 00:43 DEBUG  downloader: download finished (read 56098816 bytes)
01-15 00:43 DEBUG  TaskList: ### Finished download
01-15 00:44 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
01-15 00:44 DEBUG  root: application.on_quit
01-15 00:44 DEBUG  root: Forceful exit
01-15 00:44 INFO   root: sys.exit
01-15 12:40 INFO   root: === wubi 11.10 rev245 ===
01-15 12:40 DEBUG  root: Logfile is c:\users\win7msi\appdata\local\temp\wubi-11.10-rev245.log
01-15 12:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Win7MSI\\Downloads\\wubi.exe"']
01-15 12:40 DEBUG  CommonBackend: data_dir=C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\data
01-15 12:40 DEBUG  WindowsBackend: 7z=C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\bin\7z.exe
01-15 12:40 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-15 12:40 DEBUG  CommonBackend: Fetching basic info...
01-15 12:40 DEBUG  CommonBackend: original_exe=C:\Users\Win7MSI\Downloads\wubi.exe
01-15 12:40 DEBUG  CommonBackend: platform=win32
01-15 12:40 DEBUG  CommonBackend: osname=nt
01-15 12:40 DEBUG  CommonBackend: language=en_US
01-15 12:40 DEBUG  CommonBackend: encoding=cp1252
01-15 12:40 DEBUG  WindowsBackend: arch=amd64
01-15 12:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\data\isolist.ini
01-15 12:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-15 12:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-15 12:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-15 12:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-15 12:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-15 12:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-15 12:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-15 12:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-15 12:40 DEBUG  WindowsBackend: Fetching host info...
01-15 12:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-15 12:40 DEBUG  WindowsBackend: windows version=vista
01-15 12:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-15 12:40 DEBUG  WindowsBackend: windows_sp=None
01-15 12:40 DEBUG  WindowsBackend: windows_build=7601
01-15 12:40 DEBUG  WindowsBackend: gmt=-5
01-15 12:40 DEBUG  WindowsBackend: country=US
01-15 12:40 DEBUG  WindowsBackend: timezone=America/New_York
01-15 12:40 DEBUG  WindowsBackend: windows_username=Win7MSI
01-15 12:40 DEBUG  WindowsBackend: user_full_name=Win7MSI
01-15 12:40 DEBUG  WindowsBackend: user_directory=C:\Users\Win7MSI
01-15 12:40 DEBUG  WindowsBackend: windows_language_code=1033
01-15 12:40 DEBUG  WindowsBackend: windows_language=English
01-15 12:40 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 955 Processor
01-15 12:40 DEBUG  WindowsBackend: bootloader=vista
01-15 12:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72724.03125 mb free ntfs)
01-15 12:40 DEBUG  WindowsBackend: drive=Drive(C: hd 72724.03125 mb free ntfs)
01-15 12:40 DEBUG  WindowsBackend: drive=Drive(D: hd 0.0 mb free )
01-15 12:40 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-15 12:40 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-15 12:40 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-15 12:40 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-15 12:40 DEBUG  WindowsBackend: keyboard_id=67699721
01-15 12:40 DEBUG  WindowsBackend: keyboard_layout=us
01-15 12:40 DEBUG  WindowsBackend: keyboard_variant=
01-15 12:40 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-15 12:40 DEBUG  CommonBackend: locale=en_US.UTF-8
01-15 12:40 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
01-15 12:40 DEBUG  CommonBackend: Searching ISOs on USB devices
01-15 12:40 DEBUG  CommonBackend: Searching for local CDs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Ubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Ubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Kubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Kubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Xubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Xubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Mythbuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Mythbuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 INFO   root: Already installed, running the uninstaller...
01-15 12:40 INFO   root: Running the uninstaller...
01-15 12:40 INFO   CommonBackend: This is the uninstaller running
01-15 12:40 DEBUG  WindowsFrontend: __init__...
01-15 12:40 DEBUG  WindowsFrontend: on_init...
01-15 12:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\translations, languages=['en_US', 'en']
01-15 12:40 INFO   root: Received settings
01-15 12:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\translations, languages=['en_US', 'en']
01-15 12:40 DEBUG  TaskList: # Running tasklist...
01-15 12:40 DEBUG  TaskList: ## Running Remove bootloader entry...
01-15 12:40 DEBUG  WindowsBackend: Could not find bcd id
01-15 12:40 DEBUG  WindowsBackend: undo_bootini C:
01-15 12:40 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 72724.03125 mb free ntfs)
01-15 12:40 DEBUG  WindowsBackend: undo_bootini D:
01-15 12:40 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 0.0 mb free )
01-15 12:40 DEBUG  TaskList: ## Finished Remove bootloader entry
01-15 12:40 DEBUG  TaskList: ## Running Remove target dir...
01-15 12:40 DEBUG  CommonBackend: Deleting C:\ubuntu
01-15 12:40 DEBUG  TaskList: ## Finished Remove target dir
01-15 12:40 DEBUG  TaskList: ## Running Remove registry key...
01-15 12:40 DEBUG  TaskList: ## Finished Remove registry key
01-15 12:40 DEBUG  TaskList: # Finished tasklist
01-15 12:40 INFO   root: Almost finished uninstalling
01-15 12:40 INFO   root: Finished uninstallation
01-15 12:40 DEBUG  CommonBackend: Fetching basic info...
01-15 12:40 DEBUG  CommonBackend: original_exe=C:\Users\Win7MSI\Downloads\wubi.exe
01-15 12:40 DEBUG  CommonBackend: platform=win32
01-15 12:40 DEBUG  CommonBackend: osname=nt
01-15 12:40 DEBUG  WindowsBackend: arch=amd64
01-15 12:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\data\isolist.ini
01-15 12:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-15 12:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-15 12:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-15 12:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-15 12:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-15 12:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-15 12:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-15 12:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-15 12:40 DEBUG  WindowsBackend: Fetching host info...
01-15 12:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-15 12:40 DEBUG  WindowsBackend: windows version=vista
01-15 12:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-15 12:40 DEBUG  WindowsBackend: windows_sp=None
01-15 12:40 DEBUG  WindowsBackend: windows_build=7601
01-15 12:40 DEBUG  WindowsBackend: gmt=-5
01-15 12:40 DEBUG  WindowsBackend: country=US
01-15 12:40 DEBUG  WindowsBackend: timezone=America/New_York
01-15 12:40 DEBUG  WindowsBackend: windows_username=Win7MSI
01-15 12:40 DEBUG  WindowsBackend: user_full_name=Win7MSI
01-15 12:40 DEBUG  WindowsBackend: user_directory=C:\Users\Win7MSI
01-15 12:40 DEBUG  WindowsBackend: windows_language_code=1033
01-15 12:40 DEBUG  WindowsBackend: windows_language=English
01-15 12:40 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 955 Processor
01-15 12:40 DEBUG  WindowsBackend: bootloader=vista
01-15 12:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 72779.8789063 mb free ntfs)
01-15 12:40 DEBUG  WindowsBackend: drive=Drive(C: hd 72779.8789063 mb free ntfs)
01-15 12:40 DEBUG  WindowsBackend: drive=Drive(D: hd 0.0 mb free )
01-15 12:40 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-15 12:40 DEBUG  WindowsBackend: uninstaller_path=None
01-15 12:40 DEBUG  WindowsBackend: previous_target_dir=None
01-15 12:40 DEBUG  WindowsBackend: previous_distro_name=None
01-15 12:40 DEBUG  WindowsBackend: keyboard_id=67699721
01-15 12:40 DEBUG  WindowsBackend: keyboard_layout=us
01-15 12:40 DEBUG  WindowsBackend: keyboard_variant=
01-15 12:40 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
01-15 12:40 DEBUG  CommonBackend: Searching ISOs on USB devices
01-15 12:40 DEBUG  CommonBackend: Searching for local CDs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Ubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Ubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Kubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Kubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Xubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Xubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Mythbuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Mythbuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 INFO   root: Running the installer...
01-15 12:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\translations, languages=['en_US', 'en']
01-15 12:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\translations, languages=['en_US', 'en']
01-15 12:40 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=win7msi
01-15 12:40 INFO   root: Received settings
01-15 12:40 DEBUG  CommonBackend: Searching for local CD
01-15 12:40 DEBUG  Distro:   checking whether C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp is a valid Ubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-15 12:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-15 12:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-15 12:40 DEBUG  CommonBackend: Searching for local ISO
01-15 12:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\translations, languages=['en_US', 'en']
01-15 12:40 DEBUG  TaskList: # Running tasklist...
01-15 12:40 DEBUG  TaskList: ## Running select_target_dir...
01-15 12:40 INFO   WindowsBackend: Installing into C:\ubuntu
01-15 12:40 DEBUG  TaskList: ## Finished select_target_dir
01-15 12:40 DEBUG  TaskList: ## Running create_dir_structure...
01-15 12:40 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-15 12:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-15 12:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-15 12:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-15 12:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-15 12:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-15 12:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-15 12:40 DEBUG  TaskList: ## Finished create_dir_structure
01-15 12:40 DEBUG  TaskList: ## Running create_uninstaller...
01-15 12:40 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Win7MSI\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-15 12:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-15 12:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-15 12:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-15 12:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-15 12:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
01-15 12:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-15 12:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-15 12:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-15 12:40 DEBUG  TaskList: ## Finished create_uninstaller
01-15 12:40 DEBUG  TaskList: ## Running create_preseed_diskimage...
01-15 12:40 DEBUG  TaskList: ## Finished create_preseed_diskimage
01-15 12:40 DEBUG  TaskList: ## Running get_diskimage...
01-15 12:40 DEBUG  TaskList: New task download
01-15 12:40 DEBUG  TaskList: ### Running download...
01-15 12:40 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
01-15 12:40 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
01-15 12:57 DEBUG  TaskList: ### Finished download
01-15 12:57 DEBUG  downloader: download finished (read 507143012 bytes)
01-15 12:57 DEBUG  TaskList: ## Finished get_diskimage
01-15 12:57 DEBUG  TaskList: ## Running extract_diskimage...
01-15 12:58 DEBUG  TaskList: ## Finished extract_diskimage
01-15 12:58 DEBUG  TaskList: ## Running choose_disk_sizes...
01-15 12:58 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
01-15 12:58 DEBUG  TaskList: ## Finished choose_disk_sizes
01-15 12:58 DEBUG  TaskList: ## Running expand_diskimage...
01-15 13:00 DEBUG  TaskList: ## Finished expand_diskimage
01-15 13:00 DEBUG  TaskList: ## Running create_swap_diskimage...
01-15 13:00 DEBUG  TaskList: ## Finished create_swap_diskimage
01-15 13:00 DEBUG  TaskList: ## Running modify_bootloader...
01-15 13:00 DEBUG  TaskList: New task modify_bcd
01-15 13:00 DEBUG  TaskList: ### Running modify_bcd...
01-15 13:00 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 72779.8789063 mb free ntfs)
01-15 13:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {3526856b-3e40-11e1-a764-fd1d152f3183}
01-15 13:00 DEBUG  TaskList: ### Finished modify_bcd
01-15 13:00 DEBUG  TaskList: New task modify_bcd
01-15 13:00 DEBUG  TaskList: ### Running modify_bcd...
01-15 13:00 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 0.0 mb free )
01-15 13:00 DEBUG  WindowsBackend: BCD has already been modified
01-15 13:00 DEBUG  TaskList: ### Finished modify_bcd
01-15 13:00 DEBUG  TaskList: ## Finished modify_bootloader
01-15 13:00 DEBUG  TaskList: ## Running diskimage_bootloader...
01-15 13:00 DEBUG  WindowsBackend: Copying C:\Users\Win7MSI\AppData\Local\Temp\pylE4C2.tmp\winboot -> C:\ubuntu\winboot
01-15 13:00 ERROR  TaskList: [Errno 2] No such file or directory: 'D:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'D:\\wubildr'
01-15 13:00 DEBUG  TaskList: # Cancelling tasklist
01-15 13:00 DEBUG  TaskList: # Finished tasklist
01-15 13:00 ERROR  root: [Errno 2] No such file or directory: 'D:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'D:\\wubildr'

  
```

---

