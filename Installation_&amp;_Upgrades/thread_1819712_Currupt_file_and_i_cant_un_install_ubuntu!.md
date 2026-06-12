---
title: "Currupt file and i cant un install ubuntu!"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by ThyEpik on 2011-08-06
I have read the log here it is 07-16 09:09 INFO   root: === wubi 11.04 rev211 ===
07-16 09:09 DEBUG  root: Logfile is c:\users\elijah\appdata\local\temp\wubi-11.04-rev211.log
07-16 09:09 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Elijah\\Downloads\\wubi.exe"']
07-16 09:09 DEBUG  CommonBackend: data_dir=C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp\data
07-16 09:09 DEBUG  WindowsBackend: 7z=C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp\bin\7z.exe
07-16 09:09 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-16 09:09 DEBUG  CommonBackend: Fetching basic info...
07-16 09:09 DEBUG  CommonBackend: original_exe=C:\Users\Elijah\Downloads\wubi.exe
07-16 09:09 DEBUG  CommonBackend: platform=win32
07-16 09:09 DEBUG  CommonBackend: osname=nt
07-16 09:09 DEBUG  CommonBackend: language=en_US
07-16 09:09 DEBUG  CommonBackend: encoding=cp1252
07-16 09:09 DEBUG  WindowsBackend: arch=amd64
07-16 09:09 DEBUG  CommonBackend: Parsing isolist=C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp\data\isolist.ini
07-16 09:09 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-16 09:09 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-16 09:09 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-16 09:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-16 09:09 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-16 09:09 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-16 09:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-16 09:09 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-16 09:09 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-16 09:09 DEBUG  WindowsBackend: Fetching host info...
07-16 09:09 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-16 09:09 DEBUG  WindowsBackend: windows version=vista
07-16 09:09 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-16 09:09 DEBUG  WindowsBackend: windows_sp=None
07-16 09:09 DEBUG  WindowsBackend: windows_build=7600
07-16 09:09 DEBUG  WindowsBackend: gmt=-5
07-16 09:09 DEBUG  WindowsBackend: country=US
07-16 09:09 DEBUG  WindowsBackend: timezone=America/New_York
07-16 09:09 DEBUG  WindowsBackend: windows_username=Elijah
07-16 09:09 DEBUG  WindowsBackend: user_full_name=Elijah
07-16 09:09 DEBUG  WindowsBackend: user_directory=C:\Users\Elijah
07-16 09:09 DEBUG  WindowsBackend: windows_language_code=1033
07-16 09:09 DEBUG  WindowsBackend: windows_language=English
07-16 09:09 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M500
07-16 09:09 DEBUG  WindowsBackend: bootloader=vista
07-16 09:09 DEBUG  WindowsBackend: system_drive=Drive(C: hd 85058.1328125 mb free ntfs)
07-16 09:09 DEBUG  WindowsBackend: drive=Drive(C: hd 85058.1328125 mb free ntfs)
07-16 09:09 DEBUG  WindowsBackend: drive=Drive(D: hd 2249.28515625 mb free ntfs)
07-16 09:09 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-16 09:09 DEBUG  WindowsBackend: uninstaller_path=None
07-16 09:09 DEBUG  WindowsBackend: previous_target_dir=None
07-16 09:09 DEBUG  WindowsBackend: previous_distro_name=None
07-16 09:09 DEBUG  WindowsBackend: keyboard_id=67699721
07-16 09:09 DEBUG  WindowsBackend: keyboard_layout=us
07-16 09:09 DEBUG  WindowsBackend: keyboard_variant=
07-16 09:09 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-16 09:09 DEBUG  CommonBackend: locale=en_US.UTF-8
07-16 09:09 DEBUG  WindowsBackend: total_memory_mb=3836.1953125
07-16 09:09 DEBUG  CommonBackend: Searching ISOs on USB devices
07-16 09:09 DEBUG  CommonBackend: Searching for local CDs
07-16 09:09 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp is a valid Ubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp is a valid Ubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp is a valid Ubuntu Netbook CD
07-16 09:09 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp is a valid Kubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp is a valid Kubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp is a valid Xubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp is a valid Xubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp is a valid Mythbuntu CD
07-16 09:09 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp is a valid Mythbuntu CD
07-16 09:09 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-16 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-16 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-16 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-16 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-16 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-16 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-16 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:09 INFO   root: Running the installer...
07-16 09:09 DEBUG  WindowsFrontend: __init__...
07-16 09:09 DEBUG  WindowsFrontend: on_init...
07-16 09:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp\translations, languages=['en_US', 'en']
07-16 09:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pyl5BF5.tmp\translations, languages=['en_US', 'en']
07-16 09:11 INFO   WindowsFrontend: Operation cancelled
07-16 09:11 DEBUG  WindowsFrontend: frontend.quit
07-16 09:11 DEBUG  WindowsFrontend: frontend.on_quit
07-16 09:11 DEBUG  root: application.on_quit
07-16 09:11 INFO   root: sys.exit
07-16 09:12 INFO   root: === wubi 11.04 rev211 ===
07-16 09:12 DEBUG  root: Logfile is c:\users\elijah\appdata\local\temp\wubi-11.04-rev211.log
07-16 09:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Elijah\\Downloads\\wubi.exe"']
07-16 09:12 DEBUG  CommonBackend: data_dir=C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\data
07-16 09:12 DEBUG  WindowsBackend: 7z=C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\bin\7z.exe
07-16 09:12 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-16 09:12 DEBUG  CommonBackend: Fetching basic info...
07-16 09:12 DEBUG  CommonBackend: original_exe=C:\Users\Elijah\Downloads\wubi.exe
07-16 09:12 DEBUG  CommonBackend: platform=win32
07-16 09:12 DEBUG  CommonBackend: osname=nt
07-16 09:12 DEBUG  CommonBackend: language=en_US
07-16 09:12 DEBUG  CommonBackend: encoding=cp1252
07-16 09:12 DEBUG  WindowsBackend: arch=amd64
07-16 09:12 DEBUG  CommonBackend: Parsing isolist=C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\data\isolist.ini
07-16 09:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-16 09:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-16 09:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-16 09:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-16 09:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-16 09:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-16 09:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-16 09:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-16 09:12 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-16 09:12 DEBUG  WindowsBackend: Fetching host info...
07-16 09:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-16 09:12 DEBUG  WindowsBackend: windows version=vista
07-16 09:12 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-16 09:12 DEBUG  WindowsBackend: windows_sp=None
07-16 09:12 DEBUG  WindowsBackend: windows_build=7600
07-16 09:12 DEBUG  WindowsBackend: gmt=-5
07-16 09:12 DEBUG  WindowsBackend: country=US
07-16 09:12 DEBUG  WindowsBackend: timezone=America/New_York
07-16 09:12 DEBUG  WindowsBackend: windows_username=Elijah
07-16 09:12 DEBUG  WindowsBackend: user_full_name=Elijah
07-16 09:12 DEBUG  WindowsBackend: user_directory=C:\Users\Elijah
07-16 09:12 DEBUG  WindowsBackend: windows_language_code=1033
07-16 09:12 DEBUG  WindowsBackend: windows_language=English
07-16 09:12 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M500
07-16 09:12 DEBUG  WindowsBackend: bootloader=vista
07-16 09:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 169714.640625 mb free ntfs)
07-16 09:12 DEBUG  WindowsBackend: drive=Drive(C: hd 169714.640625 mb free ntfs)
07-16 09:12 DEBUG  WindowsBackend: drive=Drive(D: hd 2249.28515625 mb free ntfs)
07-16 09:12 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-16 09:12 DEBUG  WindowsBackend: uninstaller_path=None
07-16 09:12 DEBUG  WindowsBackend: previous_target_dir=None
07-16 09:12 DEBUG  WindowsBackend: previous_distro_name=None
07-16 09:12 DEBUG  WindowsBackend: keyboard_id=67699721
07-16 09:12 DEBUG  WindowsBackend: keyboard_layout=us
07-16 09:12 DEBUG  WindowsBackend: keyboard_variant=
07-16 09:12 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-16 09:12 DEBUG  CommonBackend: locale=en_US.UTF-8
07-16 09:12 DEBUG  WindowsBackend: total_memory_mb=3836.1953125
07-16 09:12 DEBUG  CommonBackend: Searching ISOs on USB devices
07-16 09:12 DEBUG  CommonBackend: Searching for local CDs
07-16 09:12 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp is a valid Ubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp is a valid Ubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp is a valid Ubuntu Netbook CD
07-16 09:12 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp is a valid Kubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp is a valid Kubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp is a valid Xubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp is a valid Xubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp is a valid Mythbuntu CD
07-16 09:12 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp is a valid Mythbuntu CD
07-16 09:12 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-16 09:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-16 09:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-16 09:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-16 09:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-16 09:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-16 09:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:12 INFO   root: Running the installer...
07-16 09:12 DEBUG  WindowsFrontend: __init__...
07-16 09:12 DEBUG  WindowsFrontend: on_init...
07-16 09:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\translations, languages=['en_US', 'en']
07-16 09:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\translations, languages=['en_US', 'en']
07-16 09:12 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=elijah
07-16 09:12 INFO   root: Received settings
07-16 09:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\translations, languages=['en_US', 'en']
07-16 09:12 DEBUG  TaskList: # Running tasklist...
07-16 09:12 DEBUG  TaskList: ## Running select_target_dir...
07-16 09:12 INFO   WindowsBackend: Installing into C:\ubuntu
07-16 09:12 DEBUG  TaskList: ## Finished select_target_dir
07-16 09:12 DEBUG  TaskList: ## Running create_dir_structure...
07-16 09:12 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-16 09:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-16 09:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-16 09:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-16 09:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-16 09:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-16 09:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-16 09:12 DEBUG  TaskList: ## Finished create_dir_structure
07-16 09:12 DEBUG  TaskList: ## Running uncompress_target_dir...
07-16 09:12 DEBUG  TaskList: ## Finished uncompress_target_dir
07-16 09:12 DEBUG  TaskList: ## Running create_uninstaller...
07-16 09:12 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Elijah\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-16 09:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-16 09:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-16 09:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-16 09:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-16 09:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
07-16 09:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-16 09:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-16 09:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-16 09:12 DEBUG  TaskList: ## Finished create_uninstaller
07-16 09:12 DEBUG  TaskList: ## Running copy_installation_files...
07-16 09:12 DEBUG  WindowsBackend: Copying C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-16 09:12 DEBUG  WindowsBackend: Copying C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\winboot -> C:\ubuntu\winboot
07-16 09:12 DEBUG  WindowsBackend: Copying C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-16 09:12 DEBUG  TaskList: ## Finished copy_installation_files
07-16 09:12 DEBUG  TaskList: ## Running get_iso...
07-16 09:12 DEBUG  CommonBackend: Searching for local CD
07-16 09:12 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp is a valid Ubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-16 09:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-16 09:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-16 09:12 DEBUG  CommonBackend: Searching for local ISO
07-16 09:12 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-16 09:12 DEBUG  TaskList: New task get_metalink
07-16 09:12 DEBUG  TaskList: ### Running get_metalink...
07-16 09:12 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
07-16 09:12 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
07-16 09:12 DEBUG  downloader: download finished (read 28363 bytes)
07-16 09:12 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
07-16 09:12 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
07-16 09:12 DEBUG  downloader: download finished (read 874 bytes)
07-16 09:12 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
07-16 09:12 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
07-16 09:12 DEBUG  downloader: download finished (read 198 bytes)
07-16 09:12 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-16 09:12 INFO   saplog: Checking block bindings..
07-16 09:12 INFO   saplog: Key verified successfully.
07-16 09:12 DEBUG  CommonBackend: metalink md5sums:
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

07-16 09:12 DEBUG  TaskList: ### Finished get_metalink
07-16 09:12 DEBUG  TaskList: New task download
07-16 09:12 DEBUG  TaskList: ### Running download...
07-16 09:12 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-16 09:23 DEBUG  TaskList: ### Finished download
07-16 09:23 DEBUG  TaskList: New task check_iso
07-16 09:23 DEBUG  TaskList: ### Running check_iso...
07-16 09:23 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-16 09:23 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-16 09:23 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-16 09:23 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
07-16 09:23 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
07-16 09:23 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-16 09:23 DEBUG  TaskList: New task get_file_md5
07-16 09:23 DEBUG  TaskList: #### Running get_file_md5...
07-16 09:24 DEBUG  TaskList: #### Finished get_file_md5
07-16 09:24 DEBUG  TaskList: ### Finished check_iso
07-16 09:24 DEBUG  TaskList: ## Finished get_iso
07-16 09:24 DEBUG  TaskList: ## Running extract_kernel...
07-16 09:24 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-16 09:24 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-16 09:24 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-16 09:24 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-16 09:24 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
07-16 09:24 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
07-16 09:24 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 45a7bee6779b8cd75634a70fd7a566dd == 45a7bee6779b8cd75634a70fd7a566dd
07-16 09:24 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
07-16 09:24 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 4aa66b9da42e1a3f667ab0c8009cc801 == 4aa66b9da42e1a3f667ab0c8009cc801
07-16 09:24 DEBUG  TaskList: ## Finished extract_kernel
07-16 09:24 DEBUG  TaskList: ## Running choose_disk_sizes...
07-16 09:24 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
07-16 09:24 DEBUG  TaskList: ## Finished choose_disk_sizes
07-16 09:24 DEBUG  TaskList: ## Running create_preseed...
07-16 09:24 DEBUG  TaskList: ## Finished create_preseed
07-16 09:24 DEBUG  TaskList: ## Running modify_bootloader...
07-16 09:24 DEBUG  TaskList: New task modify_bcd
07-16 09:24 DEBUG  TaskList: ### Running modify_bcd...
07-16 09:24 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 169714.640625 mb free ntfs)
07-16 09:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {77ff3b99-a13b-11e0-9b82-fafe4c629065}
07-16 09:24 DEBUG  TaskList: ### Finished modify_bcd
07-16 09:24 DEBUG  TaskList: New task modify_bcd
07-16 09:24 DEBUG  TaskList: ### Running modify_bcd...
07-16 09:24 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 2249.28515625 mb free ntfs)
07-16 09:24 DEBUG  WindowsBackend: BCD has already been modified
07-16 09:24 DEBUG  TaskList: ### Finished modify_bcd
07-16 09:24 DEBUG  TaskList: ## Finished modify_bootloader
07-16 09:24 DEBUG  TaskList: ## Running modify_grub_configuration...
07-16 09:24 DEBUG  TaskList: ## Finished modify_grub_configuration
07-16 09:24 DEBUG  TaskList: ## Running create_virtual_disks...
07-16 09:24 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 16744MB
07-16 09:24 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
07-16 09:24 DEBUG  TaskList: ## Finished create_virtual_disks
07-16 09:24 DEBUG  TaskList: ## Running uncompress_files...
07-16 09:24 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
07-16 09:24 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
07-16 09:24 DEBUG  TaskList: ## Finished uncompress_files
07-16 09:24 DEBUG  TaskList: ## Running eject_cd...
07-16 09:24 DEBUG  TaskList: ## Finished eject_cd
07-16 09:24 DEBUG  TaskList: # Finished tasklist
07-16 09:24 INFO   root: Almost finished installing
07-16 09:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pyl2A4B.tmp\translations, languages=['en_US', 'en']
07-16 09:33 INFO   root: Finished installation
07-16 09:33 DEBUG  root: application.quit
07-16 09:33 DEBUG  WindowsFrontend: frontend.quit
07-16 09:33 DEBUG  WindowsFrontend: frontend.on_quit
07-16 09:33 DEBUG  root: application.on_quit
07-16 09:33 INFO   root: sys.exit
07-17 10:55 INFO   root: === wubi 11.04 rev211 ===
07-17 10:55 DEBUG  root: Logfile is c:\users\elijah\appdata\local\temp\wubi-11.04-rev211.log
07-17 10:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Elijah\\Downloads\\wubi.exe"']
07-17 10:55 DEBUG  CommonBackend: data_dir=C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp\data
07-17 10:55 DEBUG  WindowsBackend: 7z=C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp\bin\7z.exe
07-17 10:55 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-17 10:55 DEBUG  CommonBackend: Fetching basic info...
07-17 10:55 DEBUG  CommonBackend: original_exe=C:\Users\Elijah\Downloads\wubi.exe
07-17 10:55 DEBUG  CommonBackend: platform=win32
07-17 10:55 DEBUG  CommonBackend: osname=nt
07-17 10:55 DEBUG  CommonBackend: language=en_US
07-17 10:55 DEBUG  CommonBackend: encoding=cp1252
07-17 10:55 DEBUG  WindowsBackend: arch=amd64
07-17 10:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp\data\isolist.ini
07-17 10:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-17 10:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-17 10:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-17 10:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-17 10:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-17 10:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-17 10:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-17 10:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-17 10:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-17 10:55 DEBUG  WindowsBackend: Fetching host info...
07-17 10:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-17 10:55 DEBUG  WindowsBackend: windows version=vista
07-17 10:55 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-17 10:55 DEBUG  WindowsBackend: windows_sp=None
07-17 10:55 DEBUG  WindowsBackend: windows_build=7600
07-17 10:55 DEBUG  WindowsBackend: gmt=-5
07-17 10:55 DEBUG  WindowsBackend: country=US
07-17 10:55 DEBUG  WindowsBackend: timezone=America/New_York
07-17 10:55 DEBUG  WindowsBackend: windows_username=Elijah
07-17 10:55 DEBUG  WindowsBackend: user_full_name=Elijah
07-17 10:55 DEBUG  WindowsBackend: user_directory=C:\Users\Elijah
07-17 10:55 DEBUG  WindowsBackend: windows_language_code=1033
07-17 10:55 DEBUG  WindowsBackend: windows_language=English
07-17 10:55 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M500
07-17 10:55 DEBUG  WindowsBackend: bootloader=vista
07-17 10:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 151701.734375 mb free ntfs)
07-17 10:55 DEBUG  WindowsBackend: drive=Drive(C: hd 151701.734375 mb free ntfs)
07-17 10:55 DEBUG  WindowsBackend: drive=Drive(D: hd 2249.28515625 mb free ntfs)
07-17 10:55 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-17 10:55 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-17 10:55 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-17 10:55 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-17 10:55 DEBUG  WindowsBackend: keyboard_id=67699721
07-17 10:55 DEBUG  WindowsBackend: keyboard_layout=us
07-17 10:55 DEBUG  WindowsBackend: keyboard_variant=
07-17 10:55 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-17 10:55 DEBUG  CommonBackend: locale=en_US.UTF-8
07-17 10:55 DEBUG  WindowsBackend: total_memory_mb=3836.1953125
07-17 10:55 DEBUG  CommonBackend: Searching ISOs on USB devices
07-17 10:55 DEBUG  CommonBackend: Searching for local CDs
07-17 10:55 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp is a valid Ubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp is a valid Ubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp is a valid Ubuntu Netbook CD
07-17 10:55 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp is a valid Kubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp is a valid Kubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp is a valid Xubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp is a valid Xubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp is a valid Mythbuntu CD
07-17 10:55 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp is a valid Mythbuntu CD
07-17 10:55 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-17 10:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-17 10:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-17 10:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-17 10:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-17 10:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-17 10:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 10:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-17 10:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 10:55 INFO   root: Already installed, running the uninstaller...
07-17 10:55 INFO   root: Running the uninstaller...
07-17 10:55 INFO   CommonBackend: This is the uninstaller running
07-17 10:55 DEBUG  WindowsFrontend: __init__...
07-17 10:55 DEBUG  WindowsFrontend: on_init...
07-17 10:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp\translations, languages=['en_US', 'en']
07-17 10:55 INFO   root: Received settings
07-17 10:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pyl4894.tmp\translations, languages=['en_US', 'en']
07-17 10:55 DEBUG  TaskList: # Running tasklist...
07-17 10:55 DEBUG  TaskList: ## Running Backup ISO...
07-17 10:55 DEBUG  TaskList: ## Finished Backup ISO
07-17 10:55 DEBUG  TaskList: ## Running Remove bootloader entry...
07-17 10:55 DEBUG  WindowsBackend: Removing bcd entry {77ff3b99-a13b-11e0-9b82-fafe4c629065}
07-17 10:55 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
07-17 10:55 DEBUG  TaskList: # Cancelling tasklist
07-17 10:55 DEBUG  TaskList: # Finished tasklist
07-17 10:55 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
07-17 11:14 INFO   root: === wubi 11.04 rev211 ===
07-17 11:14 DEBUG  root: Logfile is c:\users\elijah\appdata\local\temp\wubi-11.04-rev211.log
07-17 11:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Elijah\\Downloads\\wubi.exe"']
07-17 11:14 DEBUG  CommonBackend: data_dir=C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\data
07-17 11:14 DEBUG  WindowsBackend: 7z=C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\bin\7z.exe
07-17 11:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-17 11:14 DEBUG  CommonBackend: Fetching basic info...
07-17 11:14 DEBUG  CommonBackend: original_exe=C:\Users\Elijah\Downloads\wubi.exe
07-17 11:14 DEBUG  CommonBackend: platform=win32
07-17 11:14 DEBUG  CommonBackend: osname=nt
07-17 11:14 DEBUG  CommonBackend: language=en_US
07-17 11:14 DEBUG  CommonBackend: encoding=cp1252
07-17 11:14 DEBUG  WindowsBackend: arch=amd64
07-17 11:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\data\isolist.ini
07-17 11:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-17 11:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-17 11:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-17 11:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-17 11:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-17 11:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-17 11:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-17 11:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-17 11:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-17 11:14 DEBUG  WindowsBackend: Fetching host info...
07-17 11:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-17 11:14 DEBUG  WindowsBackend: windows version=vista
07-17 11:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-17 11:14 DEBUG  WindowsBackend: windows_sp=None
07-17 11:14 DEBUG  WindowsBackend: windows_build=7600
07-17 11:14 DEBUG  WindowsBackend: gmt=-5
07-17 11:14 DEBUG  WindowsBackend: country=US
07-17 11:14 DEBUG  WindowsBackend: timezone=America/New_York
07-17 11:14 DEBUG  WindowsBackend: windows_username=Elijah
07-17 11:14 DEBUG  WindowsBackend: user_full_name=Elijah
07-17 11:14 DEBUG  WindowsBackend: user_directory=C:\Users\Elijah
07-17 11:14 DEBUG  WindowsBackend: windows_language_code=1033
07-17 11:14 DEBUG  WindowsBackend: windows_language=English
07-17 11:14 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M500
07-17 11:14 DEBUG  WindowsBackend: bootloader=vista
07-17 11:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 169143.824219 mb free ntfs)
07-17 11:14 DEBUG  WindowsBackend: drive=Drive(C: hd 169143.824219 mb free ntfs)
07-17 11:14 DEBUG  WindowsBackend: drive=Drive(D: hd 2249.28515625 mb free ntfs)
07-17 11:14 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-17 11:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-17 11:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-17 11:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-17 11:14 DEBUG  WindowsBackend: keyboard_id=67699721
07-17 11:14 DEBUG  WindowsBackend: keyboard_layout=us
07-17 11:14 DEBUG  WindowsBackend: keyboard_variant=
07-17 11:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-17 11:14 DEBUG  CommonBackend: locale=en_US.UTF-8
07-17 11:14 DEBUG  WindowsBackend: total_memory_mb=3836.1953125
07-17 11:14 DEBUG  CommonBackend: Searching ISOs on USB devices
07-17 11:14 DEBUG  CommonBackend: Searching for local CDs
07-17 11:14 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp is a valid Ubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp is a valid Ubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp is a valid Ubuntu Netbook CD
07-17 11:14 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp is a valid Kubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp is a valid Kubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp is a valid Xubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp is a valid Xubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp is a valid Mythbuntu CD
07-17 11:14 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp is a valid Mythbuntu CD
07-17 11:14 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-17 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-17 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-17 11:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-17 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-17 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-17 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 11:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-17 11:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 11:14 INFO   root: Running the installer...
07-17 11:14 DEBUG  WindowsFrontend: __init__...
07-17 11:14 DEBUG  WindowsFrontend: on_init...
07-17 11:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\translations, languages=['en_US', 'en']
07-17 11:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\translations, languages=['en_US', 'en']
07-17 11:15 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=elijah
07-17 11:15 INFO   root: Received settings
07-17 11:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\translations, languages=['en_US', 'en']
07-17 11:15 DEBUG  TaskList: # Running tasklist...
07-17 11:15 DEBUG  TaskList: ## Running select_target_dir...
07-17 11:15 INFO   WindowsBackend: Installing into C:\ubuntu
07-17 11:15 DEBUG  TaskList: ## Finished select_target_dir
07-17 11:15 DEBUG  TaskList: ## Running create_dir_structure...
07-17 11:15 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-17 11:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-17 11:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-17 11:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-17 11:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-17 11:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-17 11:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-17 11:15 DEBUG  TaskList: ## Finished create_dir_structure
07-17 11:15 DEBUG  TaskList: ## Running uncompress_target_dir...
07-17 11:15 DEBUG  TaskList: ## Finished uncompress_target_dir
07-17 11:15 DEBUG  TaskList: ## Running create_uninstaller...
07-17 11:15 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Elijah\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-17 11:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-17 11:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-17 11:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-17 11:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-17 11:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
07-17 11:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-17 11:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-17 11:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-17 11:15 DEBUG  TaskList: ## Finished create_uninstaller
07-17 11:15 DEBUG  TaskList: ## Running copy_installation_files...
07-17 11:15 DEBUG  WindowsBackend: Copying C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-17 11:15 DEBUG  WindowsBackend: Copying C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\winboot -> C:\ubuntu\winboot
07-17 11:15 DEBUG  WindowsBackend: Copying C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-17 11:15 DEBUG  TaskList: ## Finished copy_installation_files
07-17 11:15 DEBUG  TaskList: ## Running get_iso...
07-17 11:15 DEBUG  CommonBackend: Searching for local CD
07-17 11:15 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp is a valid Ubuntu CD
07-17 11:15 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\casper\filesystem.squashfs
07-17 11:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-17 11:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-17 11:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-17 11:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-17 11:15 DEBUG  CommonBackend: Searching for local ISO
07-17 11:15 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-17 11:15 DEBUG  TaskList: New task get_metalink
07-17 11:15 DEBUG  TaskList: ### Running get_metalink...
07-17 11:15 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
07-17 11:15 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
07-17 11:15 DEBUG  downloader: download finished (read 28363 bytes)
07-17 11:15 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
07-17 11:15 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
07-17 11:15 DEBUG  downloader: download finished (read 874 bytes)
07-17 11:15 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
07-17 11:15 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
07-17 11:15 DEBUG  downloader: download finished (read 198 bytes)
07-17 11:15 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-17 11:15 INFO   saplog: Checking block bindings..
07-17 11:15 INFO   saplog: Key verified successfully.
07-17 11:15 DEBUG  CommonBackend: metalink md5sums:
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

07-17 11:15 DEBUG  TaskList: ### Finished get_metalink
07-17 11:15 DEBUG  TaskList: New task download
07-17 11:15 DEBUG  TaskList: ### Running download...
07-17 11:15 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-17 11:26 DEBUG  TaskList: ### Finished download
07-17 11:26 DEBUG  TaskList: New task check_iso
07-17 11:26 DEBUG  TaskList: ### Running check_iso...
07-17 11:26 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-17 11:26 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-17 11:26 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-17 11:26 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
07-17 11:26 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
07-17 11:26 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-17 11:26 DEBUG  TaskList: New task get_file_md5
07-17 11:26 DEBUG  TaskList: #### Running get_file_md5...
07-17 11:26 DEBUG  TaskList: #### Finished get_file_md5
07-17 11:26 DEBUG  TaskList: ### Finished check_iso
07-17 11:26 DEBUG  TaskList: ## Finished get_iso
07-17 11:26 DEBUG  TaskList: ## Running extract_kernel...
07-17 11:26 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-17 11:26 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-17 11:26 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-17 11:26 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-17 11:26 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
07-17 11:26 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
07-17 11:26 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 45a7bee6779b8cd75634a70fd7a566dd == 45a7bee6779b8cd75634a70fd7a566dd
07-17 11:26 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
07-17 11:26 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 4aa66b9da42e1a3f667ab0c8009cc801 == 4aa66b9da42e1a3f667ab0c8009cc801
07-17 11:26 DEBUG  TaskList: ## Finished extract_kernel
07-17 11:26 DEBUG  TaskList: ## Running choose_disk_sizes...
07-17 11:26 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
07-17 11:26 DEBUG  TaskList: ## Finished choose_disk_sizes
07-17 11:26 DEBUG  TaskList: ## Running create_preseed...
07-17 11:26 DEBUG  TaskList: ## Finished create_preseed
07-17 11:26 DEBUG  TaskList: ## Running modify_bootloader...
07-17 11:26 DEBUG  TaskList: New task modify_bcd
07-17 11:26 DEBUG  TaskList: ### Running modify_bcd...
07-17 11:26 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 169143.824219 mb free ntfs)
07-17 11:26 DEBUG  WindowsBackend: BCD has already been modified
07-17 11:26 DEBUG  TaskList: ### Finished modify_bcd
07-17 11:26 DEBUG  TaskList: New task modify_bcd
07-17 11:26 DEBUG  TaskList: ### Running modify_bcd...
07-17 11:26 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 2249.28515625 mb free ntfs)
07-17 11:26 DEBUG  WindowsBackend: BCD has already been modified
07-17 11:26 DEBUG  TaskList: ### Finished modify_bcd
07-17 11:26 DEBUG  TaskList: ## Finished modify_bootloader
07-17 11:26 DEBUG  TaskList: ## Running modify_grub_configuration...
07-17 11:26 DEBUG  TaskList: ## Finished modify_grub_configuration
07-17 11:26 DEBUG  TaskList: ## Running create_virtual_disks...
07-17 11:26 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 16744MB
07-17 11:26 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
07-17 11:26 DEBUG  TaskList: ## Finished create_virtual_disks
07-17 11:26 DEBUG  TaskList: ## Running uncompress_files...
07-17 11:26 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
07-17 11:26 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
07-17 11:26 DEBUG  TaskList: ## Finished uncompress_files
07-17 11:26 DEBUG  TaskList: ## Running eject_cd...
07-17 11:26 DEBUG  TaskList: ## Finished eject_cd
07-17 11:26 DEBUG  TaskList: # Finished tasklist
07-17 11:26 INFO   root: Almost finished installing
07-17 11:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pyl54F2.tmp\translations, languages=['en_US', 'en']
07-17 11:26 INFO   root: Finished installation
07-17 11:26 DEBUG  root: application.quit
07-17 11:26 DEBUG  WindowsFrontend: frontend.quit
07-17 11:26 DEBUG  WindowsFrontend: frontend.on_quit
07-17 11:26 DEBUG  root: application.on_quit
07-17 11:26 INFO   root: sys.exit
08-02 22:07 INFO   root: === wubi 11.04 rev211 ===
08-02 22:07 DEBUG  root: Logfile is c:\users\elijah\appdata\local\temp\wubi-11.04-rev211.log
08-02 22:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Elijah\\Desktop\\server\\wubi.exe"']
08-02 22:07 DEBUG  CommonBackend: data_dir=C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp\data
08-02 22:07 DEBUG  WindowsBackend: 7z=C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp\bin\7z.exe
08-02 22:07 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-02 22:07 DEBUG  CommonBackend: Fetching basic info...
08-02 22:07 DEBUG  CommonBackend: original_exe=C:\Users\Elijah\Desktop\server\wubi.exe
08-02 22:07 DEBUG  CommonBackend: platform=win32
08-02 22:07 DEBUG  CommonBackend: osname=nt
08-02 22:07 DEBUG  CommonBackend: language=en_US
08-02 22:07 DEBUG  CommonBackend: encoding=cp1252
08-02 22:07 DEBUG  WindowsBackend: arch=amd64
08-02 22:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp\data\isolist.ini
08-02 22:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-02 22:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-02 22:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-02 22:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-02 22:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-02 22:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-02 22:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-02 22:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-02 22:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-02 22:07 DEBUG  WindowsBackend: Fetching host info...
08-02 22:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-02 22:07 DEBUG  WindowsBackend: windows version=vista
08-02 22:07 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-02 22:07 DEBUG  WindowsBackend: windows_sp=None
08-02 22:07 DEBUG  WindowsBackend: windows_build=7600
08-02 22:07 DEBUG  WindowsBackend: gmt=-5
08-02 22:07 DEBUG  WindowsBackend: country=US
08-02 22:07 DEBUG  WindowsBackend: timezone=America/New_York
08-02 22:07 DEBUG  WindowsBackend: windows_username=Elijah
08-02 22:07 DEBUG  WindowsBackend: user_full_name=Elijah
08-02 22:07 DEBUG  WindowsBackend: user_directory=C:\Users\Elijah
08-02 22:07 DEBUG  WindowsBackend: windows_language_code=1033
08-02 22:07 DEBUG  WindowsBackend: windows_language=English
08-02 22:07 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M500
08-02 22:07 DEBUG  WindowsBackend: bootloader=vista
08-02 22:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139235.691406 mb free ntfs)
08-02 22:07 DEBUG  WindowsBackend: drive=Drive(C: hd 139235.691406 mb free ntfs)
08-02 22:07 DEBUG  WindowsBackend: drive=Drive(D: hd 2210.78515625 mb free ntfs)
08-02 22:07 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-02 22:07 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-02 22:07 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-02 22:07 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-02 22:07 DEBUG  WindowsBackend: keyboard_id=67699721
08-02 22:07 DEBUG  WindowsBackend: keyboard_layout=us
08-02 22:07 DEBUG  WindowsBackend: keyboard_variant=
08-02 22:07 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-02 22:07 DEBUG  CommonBackend: locale=en_US.UTF-8
08-02 22:07 DEBUG  WindowsBackend: total_memory_mb=3836.1953125
08-02 22:07 DEBUG  CommonBackend: Searching ISOs on USB devices
08-02 22:07 DEBUG  CommonBackend: Searching for local CDs
08-02 22:07 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp is a valid Ubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp is a valid Ubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp is a valid Ubuntu Netbook CD
08-02 22:07 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp is a valid Kubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp is a valid Kubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp is a valid Xubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp is a valid Xubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp is a valid Mythbuntu CD
08-02 22:07 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp is a valid Mythbuntu CD
08-02 22:07 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-02 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-02 22:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-02 22:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-02 22:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 22:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-02 22:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 22:07 INFO   root: Already installed, running the uninstaller...
08-02 22:07 INFO   root: Running the uninstaller...
08-02 22:07 INFO   CommonBackend: This is the uninstaller running
08-02 22:07 DEBUG  WindowsFrontend: __init__...
08-02 22:07 DEBUG  WindowsFrontend: on_init...
08-02 22:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp\translations, languages=['en_US', 'en']
08-02 22:07 INFO   root: Received settings
08-02 22:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pylE131.tmp\translations, languages=['en_US', 'en']
08-02 22:07 DEBUG  TaskList: # Running tasklist...
08-02 22:07 DEBUG  TaskList: ## Running Backup ISO...
08-02 22:07 DEBUG  TaskList: ## Finished Backup ISO
08-02 22:07 DEBUG  TaskList: ## Running Remove bootloader entry...
08-02 22:07 DEBUG  WindowsBackend: Removing bcd entry {77ff3b99-a13b-11e0-9b82-fafe4c629065}
08-02 22:07 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
08-02 22:07 DEBUG  TaskList: # Cancelling tasklist
08-02 22:07 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
08-02 22:07 DEBUG  TaskList: # Finished tasklist
08-06 15:30 INFO   root: === wubi 11.04 rev211 ===
08-06 15:30 DEBUG  root: Logfile is c:\users\elijah\appdata\local\temp\wubi-11.04-rev211.log
08-06 15:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
08-06 15:30 DEBUG  CommonBackend: data_dir=C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp\data
08-06 15:30 DEBUG  WindowsBackend: 7z=C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp\bin\7z.exe
08-06 15:30 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-06 15:30 DEBUG  CommonBackend: Fetching basic info...
08-06 15:30 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
08-06 15:30 DEBUG  CommonBackend: platform=win32
08-06 15:30 DEBUG  CommonBackend: osname=nt
08-06 15:30 DEBUG  CommonBackend: language=en_US
08-06 15:30 DEBUG  CommonBackend: encoding=cp1252
08-06 15:30 DEBUG  WindowsBackend: arch=amd64
08-06 15:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp\data\isolist.ini
08-06 15:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-06 15:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-06 15:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-06 15:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-06 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-06 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-06 15:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-06 15:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-06 15:30 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-06 15:30 DEBUG  WindowsBackend: Fetching host info...
08-06 15:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-06 15:30 DEBUG  WindowsBackend: windows version=vista
08-06 15:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-06 15:30 DEBUG  WindowsBackend: windows_sp=None
08-06 15:30 DEBUG  WindowsBackend: windows_build=7600
08-06 15:30 DEBUG  WindowsBackend: gmt=-5
08-06 15:30 DEBUG  WindowsBackend: country=US
08-06 15:30 DEBUG  WindowsBackend: timezone=America/New_York
08-06 15:30 DEBUG  WindowsBackend: windows_username=Elijah
08-06 15:30 DEBUG  WindowsBackend: user_full_name=Elijah
08-06 15:30 DEBUG  WindowsBackend: user_directory=C:\Users\Elijah
08-06 15:30 DEBUG  WindowsBackend: windows_language_code=1033
08-06 15:30 DEBUG  WindowsBackend: windows_language=English
08-06 15:30 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M500
08-06 15:30 DEBUG  WindowsBackend: bootloader=vista
08-06 15:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 147099.960938 mb free ntfs)
08-06 15:30 DEBUG  WindowsBackend: drive=Drive(C: hd 147099.960938 mb free ntfs)
08-06 15:30 DEBUG  WindowsBackend: drive=Drive(D: hd 2210.7890625 mb free ntfs)
08-06 15:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-06 15:30 DEBUG  WindowsBackend: drive=Drive(F: removable 900.28125 mb free fat)
08-06 15:30 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-06 15:30 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-06 15:30 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-06 15:30 DEBUG  WindowsBackend: keyboard_id=67699721
08-06 15:30 DEBUG  WindowsBackend: keyboard_layout=us
08-06 15:30 DEBUG  WindowsBackend: keyboard_variant=
08-06 15:30 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-06 15:30 DEBUG  CommonBackend: locale=en_US.UTF-8
08-06 15:30 DEBUG  WindowsBackend: total_memory_mb=3836.1953125
08-06 15:30 DEBUG  CommonBackend: Searching ISOs on USB devices
08-06 15:30 DEBUG  CommonBackend: Searching for local CDs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp is a valid Ubuntu Netbook CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 INFO   root: Running the uninstaller...
08-06 15:30 INFO   CommonBackend: This is the uninstaller running
08-06 15:30 DEBUG  WindowsFrontend: __init__...
08-06 15:30 DEBUG  WindowsFrontend: on_init...
08-06 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp\translations, languages=['en_US', 'en']
08-06 15:30 INFO   root: Received settings
08-06 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pyl86E2.tmp\translations, languages=['en_US', 'en']
08-06 15:30 DEBUG  TaskList: # Running tasklist...
08-06 15:30 DEBUG  TaskList: ## Running Backup ISO...
08-06 15:30 DEBUG  TaskList: ## Finished Backup ISO
08-06 15:30 DEBUG  TaskList: ## Running Remove bootloader entry...
08-06 15:30 DEBUG  WindowsBackend: Removing bcd entry {77ff3b99-a13b-11e0-9b82-fafe4c629065}
08-06 15:30 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
08-06 15:30 DEBUG  TaskList: # Cancelling tasklist
08-06 15:30 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 123, in select_task
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
08-06 15:30 DEBUG  TaskList: # Finished tasklist
08-06 15:30 INFO   root: === wubi 11.04 rev211 ===
08-06 15:30 DEBUG  root: Logfile is c:\users\elijah\appdata\local\temp\wubi-11.04-rev211.log
08-06 15:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
08-06 15:30 DEBUG  CommonBackend: data_dir=C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp\data
08-06 15:30 DEBUG  WindowsBackend: 7z=C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp\bin\7z.exe
08-06 15:30 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-06 15:30 DEBUG  CommonBackend: Fetching basic info...
08-06 15:30 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
08-06 15:30 DEBUG  CommonBackend: platform=win32
08-06 15:30 DEBUG  CommonBackend: osname=nt
08-06 15:30 DEBUG  CommonBackend: language=en_US
08-06 15:30 DEBUG  CommonBackend: encoding=cp1252
08-06 15:30 DEBUG  WindowsBackend: arch=amd64
08-06 15:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp\data\isolist.ini
08-06 15:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-06 15:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-06 15:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-06 15:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-06 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-06 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-06 15:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-06 15:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-06 15:30 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-06 15:30 DEBUG  WindowsBackend: Fetching host info...
08-06 15:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-06 15:30 DEBUG  WindowsBackend: windows version=vista
08-06 15:30 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
08-06 15:30 DEBUG  WindowsBackend: windows_sp=None
08-06 15:30 DEBUG  WindowsBackend: windows_build=6000
08-06 15:30 DEBUG  WindowsBackend: gmt=-5
08-06 15:30 DEBUG  WindowsBackend: country=US
08-06 15:30 DEBUG  WindowsBackend: timezone=America/New_York
08-06 15:30 DEBUG  WindowsBackend: windows_username=Elijah
08-06 15:30 DEBUG  WindowsBackend: user_full_name=Elijah
08-06 15:30 DEBUG  WindowsBackend: user_directory=C:\Users\Elijah
08-06 15:30 DEBUG  WindowsBackend: windows_language_code=1033
08-06 15:30 DEBUG  WindowsBackend: windows_language=English
08-06 15:30 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M500
08-06 15:30 DEBUG  WindowsBackend: bootloader=vista
08-06 15:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 147099.679688 mb free ntfs)
08-06 15:30 DEBUG  WindowsBackend: drive=Drive(C: hd 147099.679688 mb free ntfs)
08-06 15:30 DEBUG  WindowsBackend: drive=Drive(D: hd 2210.7890625 mb free ntfs)
08-06 15:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-06 15:30 DEBUG  WindowsBackend: drive=Drive(F: removable 900.28125 mb free fat)
08-06 15:30 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-06 15:30 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-06 15:30 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-06 15:30 DEBUG  WindowsBackend: keyboard_id=67699721
08-06 15:30 DEBUG  WindowsBackend: keyboard_layout=us
08-06 15:30 DEBUG  WindowsBackend: keyboard_variant=
08-06 15:30 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-06 15:30 DEBUG  CommonBackend: locale=en_US.UTF-8
08-06 15:30 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
08-06 15:30 DEBUG  CommonBackend: Searching ISOs on USB devices
08-06 15:30 DEBUG  CommonBackend: Searching for local CDs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp is a valid Ubuntu Netbook CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-06 15:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:30 INFO   root: Running the uninstaller...
08-06 15:30 INFO   CommonBackend: This is the uninstaller running
08-06 15:30 DEBUG  WindowsFrontend: __init__...
08-06 15:30 DEBUG  WindowsFrontend: on_init...
08-06 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp\translations, languages=['en_US', 'en']
08-06 15:30 INFO   root: Received settings
08-06 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pylE3FF.tmp\translations, languages=['en_US', 'en']
08-06 15:30 DEBUG  TaskList: # Running tasklist...
08-06 15:30 DEBUG  TaskList: ## Running Backup ISO...
08-06 15:30 DEBUG  TaskList: ## Finished Backup ISO
08-06 15:30 DEBUG  TaskList: ## Running Remove bootloader entry...
08-06 15:30 DEBUG  WindowsBackend: Removing bcd entry {77ff3b99-a13b-11e0-9b82-fafe4c629065}
08-06 15:30 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
08-06 15:30 DEBUG  TaskList: # Cancelling tasklist
08-06 15:30 DEBUG  TaskList: # Finished tasklist
08-06 15:30 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 123, in select_task
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
08-06 15:31 INFO   root: === wubi 11.04 rev211 ===
08-06 15:31 DEBUG  root: Logfile is c:\users\elijah\appdata\local\temp\wubi-11.04-rev211.log
08-06 15:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
08-06 15:31 DEBUG  CommonBackend: data_dir=C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp\data
08-06 15:31 DEBUG  WindowsBackend: 7z=C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp\bin\7z.exe
08-06 15:31 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-06 15:31 DEBUG  CommonBackend: Fetching basic info...
08-06 15:31 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
08-06 15:31 DEBUG  CommonBackend: platform=win32
08-06 15:31 DEBUG  CommonBackend: osname=nt
08-06 15:31 DEBUG  CommonBackend: language=en_US
08-06 15:31 DEBUG  CommonBackend: encoding=cp1252
08-06 15:31 DEBUG  WindowsBackend: arch=amd64
08-06 15:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp\data\isolist.ini
08-06 15:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-06 15:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-06 15:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-06 15:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-06 15:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-06 15:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-06 15:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-06 15:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-06 15:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-06 15:31 DEBUG  WindowsBackend: Fetching host info...
08-06 15:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-06 15:31 DEBUG  WindowsBackend: windows version=vista
08-06 15:31 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
08-06 15:31 DEBUG  WindowsBackend: windows_sp=None
08-06 15:31 DEBUG  WindowsBackend: windows_build=6000
08-06 15:31 DEBUG  WindowsBackend: gmt=-5
08-06 15:31 DEBUG  WindowsBackend: country=US
08-06 15:31 DEBUG  WindowsBackend: timezone=America/New_York
08-06 15:31 DEBUG  WindowsBackend: windows_username=Elijah
08-06 15:31 DEBUG  WindowsBackend: user_full_name=Elijah
08-06 15:31 DEBUG  WindowsBackend: user_directory=C:\Users\Elijah
08-06 15:31 DEBUG  WindowsBackend: windows_language_code=1033
08-06 15:31 DEBUG  WindowsBackend: windows_language=English
08-06 15:31 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M500
08-06 15:31 DEBUG  WindowsBackend: bootloader=vista
08-06 15:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 147099.144531 mb free ntfs)
08-06 15:31 DEBUG  WindowsBackend: drive=Drive(C: hd 147099.144531 mb free ntfs)
08-06 15:31 DEBUG  WindowsBackend: drive=Drive(D: hd 2210.7890625 mb free ntfs)
08-06 15:31 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-06 15:31 DEBUG  WindowsBackend: drive=Drive(F: removable 900.28125 mb free fat)
08-06 15:31 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-06 15:31 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-06 15:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-06 15:31 DEBUG  WindowsBackend: keyboard_id=67699721
08-06 15:31 DEBUG  WindowsBackend: keyboard_layout=us
08-06 15:31 DEBUG  WindowsBackend: keyboard_variant=
08-06 15:31 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-06 15:31 DEBUG  CommonBackend: locale=en_US.UTF-8
08-06 15:31 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
08-06 15:31 DEBUG  CommonBackend: Searching ISOs on USB devices
08-06 15:31 DEBUG  CommonBackend: Searching for local CDs
08-06 15:31 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp is a valid Ubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp is a valid Ubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp is a valid Ubuntu Netbook CD
08-06 15:31 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp is a valid Kubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp is a valid Kubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp is a valid Xubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp is a valid Xubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp is a valid Mythbuntu CD
08-06 15:31 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp is a valid Mythbuntu CD
08-06 15:31 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-06 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-06 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-06 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-06 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-06 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-06 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-06 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-06 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-06 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-06 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:31 INFO   root: Running the uninstaller...
08-06 15:31 INFO   CommonBackend: This is the uninstaller running
08-06 15:31 DEBUG  WindowsFrontend: __init__...
08-06 15:31 DEBUG  WindowsFrontend: on_init...
08-06 15:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp\translations, languages=['en_US', 'en']
08-06 15:31 INFO   root: Received settings
08-06 15:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pylB8EA.tmp\translations, languages=['en_US', 'en']
08-06 15:31 DEBUG  TaskList: # Running tasklist...
08-06 15:31 DEBUG  TaskList: ## Running Backup ISO...
08-06 15:31 DEBUG  TaskList: ## Finished Backup ISO
08-06 15:31 DEBUG  TaskList: ## Running Remove bootloader entry...
08-06 15:31 DEBUG  WindowsBackend: Removing bcd entry {77ff3b99-a13b-11e0-9b82-fafe4c629065}
08-06 15:31 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
08-06 15:31 DEBUG  TaskList: # Cancelling tasklist
08-06 15:31 DEBUG  TaskList: # Finished tasklist
08-06 15:31 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 123, in select_task
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
08-06 15:32 INFO   root: === wubi 11.04 rev211 ===
08-06 15:32 DEBUG  root: Logfile is c:\users\elijah\appdata\local\temp\wubi-11.04-rev211.log
08-06 15:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
08-06 15:32 DEBUG  CommonBackend: data_dir=C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp\data
08-06 15:32 DEBUG  WindowsBackend: 7z=C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp\bin\7z.exe
08-06 15:32 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-06 15:32 DEBUG  CommonBackend: Fetching basic info...
08-06 15:32 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
08-06 15:32 DEBUG  CommonBackend: platform=win32
08-06 15:32 DEBUG  CommonBackend: osname=nt
08-06 15:32 DEBUG  CommonBackend: language=en_US
08-06 15:32 DEBUG  CommonBackend: encoding=cp1252
08-06 15:32 DEBUG  WindowsBackend: arch=amd64
08-06 15:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp\data\isolist.ini
08-06 15:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-06 15:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-06 15:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-06 15:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-06 15:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-06 15:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-06 15:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-06 15:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-06 15:32 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-06 15:32 DEBUG  WindowsBackend: Fetching host info...
08-06 15:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-06 15:32 DEBUG  WindowsBackend: windows version=vista
08-06 15:32 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
08-06 15:32 DEBUG  WindowsBackend: windows_sp=None
08-06 15:32 DEBUG  WindowsBackend: windows_build=6000
08-06 15:32 DEBUG  WindowsBackend: gmt=-5
08-06 15:32 DEBUG  WindowsBackend: country=US
08-06 15:32 DEBUG  WindowsBackend: timezone=America/New_York
08-06 15:32 DEBUG  WindowsBackend: windows_username=Elijah
08-06 15:32 DEBUG  WindowsBackend: user_full_name=Elijah
08-06 15:32 DEBUG  WindowsBackend: user_directory=C:\Users\Elijah
08-06 15:32 DEBUG  WindowsBackend: windows_language_code=1033
08-06 15:32 DEBUG  WindowsBackend: windows_language=English
08-06 15:32 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M500
08-06 15:32 DEBUG  WindowsBackend: bootloader=vista
08-06 15:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 147098.960938 mb free ntfs)
08-06 15:32 DEBUG  WindowsBackend: drive=Drive(C: hd 147098.960938 mb free ntfs)
08-06 15:32 DEBUG  WindowsBackend: drive=Drive(D: hd 2210.7890625 mb free ntfs)
08-06 15:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-06 15:32 DEBUG  WindowsBackend: drive=Drive(F: removable 900.28125 mb free fat)
08-06 15:32 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-06 15:32 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-06 15:32 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-06 15:32 DEBUG  WindowsBackend: keyboard_id=67699721
08-06 15:32 DEBUG  WindowsBackend: keyboard_layout=us
08-06 15:32 DEBUG  WindowsBackend: keyboard_variant=
08-06 15:32 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-06 15:32 DEBUG  CommonBackend: locale=en_US.UTF-8
08-06 15:32 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
08-06 15:32 DEBUG  CommonBackend: Searching ISOs on USB devices
08-06 15:32 DEBUG  CommonBackend: Searching for local CDs
08-06 15:32 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp is a valid Ubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp is a valid Ubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp is a valid Ubuntu Netbook CD
08-06 15:32 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp is a valid Kubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp is a valid Kubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp is a valid Xubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp is a valid Xubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp is a valid Mythbuntu CD
08-06 15:32 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp is a valid Mythbuntu CD
08-06 15:32 DEBUG  Distro:     does not contain C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-06 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-06 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-06 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-06 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-06 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-06 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-06 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-06 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-06 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-06 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-06 15:32 INFO   root: Running the uninstaller...
08-06 15:32 INFO   CommonBackend: This is the uninstaller running
08-06 15:32 DEBUG  WindowsFrontend: __init__...
08-06 15:32 DEBUG  WindowsFrontend: on_init...
08-06 15:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp\translations, languages=['en_US', 'en']
08-06 15:32 INFO   root: Received settings
08-06 15:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Elijah\AppData\Local\Temp\pylF676.tmp\translations, languages=['en_US', 'en']
08-06 15:32 DEBUG  TaskList: # Running tasklist...
08-06 15:32 DEBUG  TaskList: ## Running Backup ISO...
08-06 15:32 DEBUG  TaskList: ## Finished Backup ISO
08-06 15:32 DEBUG  TaskList: ## Running Remove bootloader entry...
08-06 15:32 DEBUG  WindowsBackend: Removing bcd entry {77ff3b99-a13b-11e0-9b82-fafe4c629065}
08-06 15:32 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
08-06 15:32 DEBUG  TaskList: # Cancelling tasklist
08-06 15:32 DEBUG  TaskList: # Finished tasklist
08-06 15:32 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 123, in select_task
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {77ff3b99-a13b-11e0-9b82-fafe4c629065} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=

---

### Post by bcbc on 2011-08-06
See [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

There is a section for manually uninstalling. If you cannot remove any files and it says they are corrupt, you need to run chkdsk: Computer, right-click on drive (e.g. C:), properties, tools, check disk for errors, fix automatically. If you installed on C: you need to reboot to complete the chkdsk.

---

### Post by cdavid13 on 2011-08-06
I ran into something like this and used a boot disc to wipe the HD and just started over it was a pain to loose everything but was rather quick.

---

### Post by maxar6 on 2011-08-06
Your best bet would be to get a new ubuntu instalation cd and then when it asks you how you want to partition it just tell it that you want ubuntu to be one big partition.

---

### Post by ThyEpik on 2011-08-06
Thanks, it helped alot now all i have to do is restart my machine!:biggrin:

---

### Post by maxar6 on 2011-08-06
Let me know how ubuntu works and you are welcome.

---

