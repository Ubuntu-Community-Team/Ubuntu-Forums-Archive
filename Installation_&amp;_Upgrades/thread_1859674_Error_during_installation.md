---
title: "Error during installation"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by ka_rim_2008 on 2011-10-14
When i try installing Wubi 11.10 it downloads and starts decompressing afterwards a message comes up saying:

> An error occured:
No such file or directory
See log file

I open the lof file and here is what it says:

> 10-13 22:51 INFO   root: === wubi 11.10 rev245 ===
10-13 22:51 DEBUG  root: Logfile is c:\users\karim\appdata\local\temp\wubi-11.10-rev245.log
10-13 22:51 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Karim\\Downloads\\wubi.exe"']
10-13 22:51 DEBUG  CommonBackend: data_dir=C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\data
10-13 22:51 DEBUG  WindowsBackend: 7z=C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\bin\7z.exe
10-13 22:51 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-13 22:51 DEBUG  CommonBackend: Fetching basic info...
10-13 22:51 DEBUG  CommonBackend: original_exe=C:\Users\Karim\Downloads\wubi.exe
10-13 22:51 DEBUG  CommonBackend: platform=win32
10-13 22:51 DEBUG  CommonBackend: osname=nt
10-13 22:51 DEBUG  CommonBackend: language=en_US
10-13 22:51 DEBUG  CommonBackend: encoding=cp1252
10-13 22:51 DEBUG  WindowsBackend: arch=amd64
10-13 22:51 DEBUG  CommonBackend: Parsing isolist=C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\data\isolist.ini
10-13 22:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-13 22:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-13 22:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-13 22:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-13 22:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-13 22:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-13 22:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-13 22:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-13 22:51 DEBUG  WindowsBackend: Fetching host info...
10-13 22:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-13 22:51 DEBUG  WindowsBackend: windows version=vista
10-13 22:51 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-13 22:51 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-13 22:51 DEBUG  WindowsBackend: windows_build=7601
10-13 22:51 DEBUG  WindowsBackend: gmt=2
10-13 22:51 DEBUG  WindowsBackend: country=US
10-13 22:51 DEBUG  WindowsBackend: timezone=America/New_York
10-13 22:51 DEBUG  WindowsBackend: windows_username=Karim
10-13 22:51 DEBUG  WindowsBackend: user_full_name=Karim
10-13 22:51 DEBUG  WindowsBackend: user_directory=C:\Users\Karim
10-13 22:51 DEBUG  WindowsBackend: windows_language_code=1033
10-13 22:51 DEBUG  WindowsBackend: windows_language=English
10-13 22:51 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz
10-13 22:51 DEBUG  WindowsBackend: bootloader=vista
10-13 22:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 51855.9570313 mb free ntfs)
10-13 22:51 DEBUG  WindowsBackend: drive=Drive(C: hd 51855.9570313 mb free ntfs)
10-13 22:51 DEBUG  WindowsBackend: drive=Drive(D: hd 44254.359375 mb free ntfs)
10-13 22:51 DEBUG  WindowsBackend: drive=Drive(E: hd 17600.1796875 mb free ntfs)
10-13 22:51 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
10-13 22:51 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
10-13 22:51 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-13 22:51 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
10-13 22:51 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
10-13 22:51 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
10-13 22:51 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free cdfs)
10-13 22:51 DEBUG  WindowsBackend: uninstaller_path=None
10-13 22:51 DEBUG  WindowsBackend: previous_target_dir=None
10-13 22:51 DEBUG  WindowsBackend: previous_distro_name=None
10-13 22:51 DEBUG  WindowsBackend: keyboard_id=67699721
10-13 22:51 DEBUG  WindowsBackend: keyboard_layout=us
10-13 22:51 DEBUG  WindowsBackend: keyboard_variant=
10-13 22:51 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-13 22:51 DEBUG  CommonBackend: locale=en_US.UTF-8
10-13 22:51 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
10-13 22:51 DEBUG  CommonBackend: Searching ISOs on USB devices
10-13 22:51 DEBUG  CommonBackend: Searching for local CDs
10-13 22:51 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp is a valid Xubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp is a valid Xubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp is a valid Mythbuntu CD
10-13 22:51 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp is a valid Mythbuntu CD
10-13 22:51 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-13 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-13 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-13 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-13 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-13 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-13 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-13 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-13 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-13 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-13 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-13 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-13 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
10-13 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-13 22:51 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
10-13 22:52 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-13 22:52 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
10-13 22:52 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-13 22:52 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
10-13 22:52 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-13 22:52 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
10-13 22:52 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-13 22:52 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-13 22:52 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-13 22:52 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-13 22:52 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-13 22:52 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
10-13 22:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-13 22:53 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
10-13 22:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-13 22:53 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
10-13 23:00 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-13 23:00 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
10-13 23:00 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-13 23:00 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
10-13 23:00 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-13 23:00 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
10-13 23:00 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-13 23:00 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
10-13 23:00 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-13 23:00 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
10-13 23:00 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-13 23:00 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
10-13 23:00 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-13 23:00 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
10-13 23:00 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-13 23:00 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
10-13 23:00 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-13 23:00 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
10-13 23:00 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-13 23:00 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
10-13 23:00 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-13 23:00 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
10-13 23:00 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-13 23:00 INFO   root: Running the installer...
10-13 23:00 DEBUG  WindowsFrontend: __init__...
10-13 23:00 DEBUG  WindowsFrontend: on_init...
10-13 23:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\translations, languages=['en_US', 'en']
10-13 23:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\translations, languages=['en_US', 'en']
10-13 23:02 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=karim
10-13 23:02 INFO   root: Received settings
10-13 23:02 DEBUG  CommonBackend: Searching for local CD
10-13 23:02 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp is a valid Ubuntu CD
10-13 23:02 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\casper\filesystem.squashfs
10-13 23:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-13 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-13 23:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-13 23:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-13 23:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-13 23:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-13 23:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-13 23:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-13 23:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-13 23:02 DEBUG  Distro:     dir does not exist
10-13 23:02 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-13 23:02 DEBUG  Distro:     dir does not exist
10-13 23:02 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
10-13 23:03 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-13 23:03 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-13 23:03 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-13 23:03 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
10-13 23:03 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-13 23:03 DEBUG  CommonBackend: Searching for local ISO
10-13 23:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\translations, languages=['en_US', 'en']
10-13 23:03 DEBUG  TaskList: # Running tasklist...
10-13 23:03 DEBUG  TaskList: ## Running select_target_dir...
10-13 23:03 INFO   WindowsBackend: Installing into D:\ubuntu
10-13 23:03 DEBUG  TaskList: ## Finished select_target_dir
10-13 23:03 DEBUG  TaskList: ## Running create_dir_structure...
10-13 23:03 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-13 23:03 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-13 23:03 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-13 23:03 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-13 23:03 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-13 23:03 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-13 23:03 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-13 23:03 DEBUG  TaskList: ## Finished create_dir_structure
10-13 23:03 DEBUG  TaskList: ## Running create_uninstaller...
10-13 23:03 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Karim\Downloads\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-13 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-13 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-13 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-13 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-13 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
10-13 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-13 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-13 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-13 23:03 DEBUG  TaskList: ## Finished create_uninstaller
10-13 23:03 DEBUG  TaskList: ## Running create_preseed_diskimage...
10-13 23:03 DEBUG  TaskList: ## Finished create_preseed_diskimage
10-13 23:03 DEBUG  TaskList: ## Running get_diskimage...
10-13 23:03 DEBUG  TaskList: New task download
10-13 23:03 DEBUG  TaskList: ### Running download...
10-13 23:03 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > D:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
10-13 23:04 DEBUG  downloader: Download start filename=D:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
10-13 23:55 DEBUG  TaskList: ### Finished download
10-13 23:55 DEBUG  downloader: download finished (read 507143012 bytes)
10-13 23:55 DEBUG  TaskList: ## Finished get_diskimage
10-13 23:55 DEBUG  TaskList: ## Running extract_diskimage...
10-13 23:56 DEBUG  TaskList: ## Finished extract_diskimage
10-13 23:56 DEBUG  TaskList: ## Running choose_disk_sizes...
10-13 23:56 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
10-13 23:56 DEBUG  TaskList: ## Finished choose_disk_sizes
10-13 23:56 DEBUG  TaskList: ## Running expand_diskimage...
10-13 23:59 DEBUG  TaskList: ## Finished expand_diskimage
10-13 23:59 DEBUG  TaskList: ## Running create_swap_diskimage...
10-13 23:59 DEBUG  TaskList: ## Finished create_swap_diskimage
10-13 23:59 DEBUG  TaskList: ## Running modify_bootloader...
10-13 23:59 DEBUG  TaskList: New task modify_bcd
10-13 23:59 DEBUG  TaskList: ### Running modify_bcd...
10-13 23:59 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 51855.9570313 mb free ntfs)
10-13 23:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {59d97309-8679-11df-acea-00038a000015}
10-13 23:59 DEBUG  TaskList: ### Finished modify_bcd
10-13 23:59 DEBUG  TaskList: New task modify_bcd
10-13 23:59 DEBUG  TaskList: ### Running modify_bcd...
10-13 23:59 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 44254.359375 mb free ntfs)
10-13 23:59 DEBUG  WindowsBackend: BCD has already been modified
10-13 23:59 DEBUG  TaskList: ### Finished modify_bcd
10-13 23:59 DEBUG  TaskList: New task modify_bcd
10-13 23:59 DEBUG  TaskList: ### Running modify_bcd...
10-13 23:59 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 17600.1796875 mb free ntfs)
10-13 23:59 DEBUG  WindowsBackend: BCD has already been modified
10-13 23:59 DEBUG  TaskList: ### Finished modify_bcd
10-13 23:59 DEBUG  TaskList: New task modify_bcd
10-13 23:59 DEBUG  TaskList: ### Running modify_bcd...
10-13 23:59 DEBUG  WindowsBackend: modify_bcd Drive(H: removable 0.0 mb free )
10-13 23:59 DEBUG  WindowsBackend: BCD has already been modified
10-13 23:59 DEBUG  TaskList: ### Finished modify_bcd
10-13 23:59 DEBUG  TaskList: New task modify_bcd
10-13 23:59 DEBUG  TaskList: ### Running modify_bcd...
10-13 23:59 DEBUG  WindowsBackend: modify_bcd Drive(I: removable 0.0 mb free )
10-13 23:59 DEBUG  WindowsBackend: BCD has already been modified
10-13 23:59 DEBUG  TaskList: ### Finished modify_bcd
10-13 23:59 DEBUG  TaskList: New task modify_bcd
10-13 23:59 DEBUG  TaskList: ### Running modify_bcd...
10-13 23:59 DEBUG  WindowsBackend: modify_bcd Drive(J: removable 0.0 mb free )
10-13 23:59 DEBUG  WindowsBackend: BCD has already been modified
10-13 23:59 DEBUG  TaskList: ### Finished modify_bcd
10-13 23:59 DEBUG  TaskList: New task modify_bcd
10-13 23:59 DEBUG  TaskList: ### Running modify_bcd...
10-13 23:59 DEBUG  WindowsBackend: modify_bcd Drive(K: removable 0.0 mb free )
10-13 23:59 DEBUG  WindowsBackend: BCD has already been modified
10-13 23:59 DEBUG  TaskList: ### Finished modify_bcd
10-13 23:59 DEBUG  TaskList: ## Finished modify_bootloader
10-13 23:59 DEBUG  TaskList: ## Running diskimage_bootloader...
10-13 23:59 DEBUG  WindowsBackend: Copying C:\Users\Karim\AppData\Local\Temp\pyl26E6.tmp\winboot -> D:\ubuntu\winboot
10-13 23:59 ERROR  TaskList: [Errno 2] No such file or directory: 'H:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'H:\\wubildr'
10-13 23:59 DEBUG  TaskList: # Cancelling tasklist
10-13 23:59 DEBUG  TaskList: # Finished tasklist
10-13 23:59 ERROR  root: [Errno 2] No such file or directory: 'H:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'H:\\wubildr'
10-14 09:44 INFO   root: === wubi 11.10 rev245 ===
10-14 09:44 DEBUG  root: Logfile is c:\users\karim\appdata\local\temp\wubi-11.10-rev245.log
10-14 09:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Karim\\Downloads\\wubi.exe"']
10-14 09:44 DEBUG  CommonBackend: data_dir=C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\data
10-14 09:44 DEBUG  WindowsBackend: 7z=C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\bin\7z.exe
10-14 09:44 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-14 09:44 DEBUG  CommonBackend: Fetching basic info...
10-14 09:44 DEBUG  CommonBackend: original_exe=C:\Users\Karim\Downloads\wubi.exe
10-14 09:44 DEBUG  CommonBackend: platform=win32
10-14 09:44 DEBUG  CommonBackend: osname=nt
10-14 09:44 DEBUG  CommonBackend: language=en_US
10-14 09:44 DEBUG  CommonBackend: encoding=cp1252
10-14 09:44 DEBUG  WindowsBackend: arch=amd64
10-14 09:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\data\isolist.ini
10-14 09:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-14 09:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-14 09:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-14 09:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-14 09:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-14 09:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-14 09:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-14 09:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-14 09:44 DEBUG  WindowsBackend: Fetching host info...
10-14 09:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-14 09:44 DEBUG  WindowsBackend: windows version=vista
10-14 09:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-14 09:44 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-14 09:44 DEBUG  WindowsBackend: windows_build=7601
10-14 09:44 DEBUG  WindowsBackend: gmt=2
10-14 09:44 DEBUG  WindowsBackend: country=US
10-14 09:44 DEBUG  WindowsBackend: timezone=America/New_York
10-14 09:44 DEBUG  WindowsBackend: windows_username=Karim
10-14 09:44 DEBUG  WindowsBackend: user_full_name=Karim
10-14 09:44 DEBUG  WindowsBackend: user_directory=C:\Users\Karim
10-14 09:44 DEBUG  WindowsBackend: windows_language_code=1033
10-14 09:44 DEBUG  WindowsBackend: windows_language=English
10-14 09:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz
10-14 09:44 DEBUG  WindowsBackend: bootloader=vista
10-14 09:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 51785.1210938 mb free ntfs)
10-14 09:44 DEBUG  WindowsBackend: drive=Drive(C: hd 51785.1210938 mb free ntfs)
10-14 09:44 DEBUG  WindowsBackend: drive=Drive(D: hd 38882.9609375 mb free ntfs)
10-14 09:44 DEBUG  WindowsBackend: drive=Drive(E: hd 17600.0507813 mb free ntfs)
10-14 09:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
10-14 09:44 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
10-14 09:44 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
10-14 09:44 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free cdfs)
10-14 09:44 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-14 09:44 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-14 09:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-14 09:44 DEBUG  WindowsBackend: keyboard_id=67699721
10-14 09:44 DEBUG  WindowsBackend: keyboard_layout=us
10-14 09:44 DEBUG  WindowsBackend: keyboard_variant=
10-14 09:44 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-14 09:44 DEBUG  CommonBackend: locale=en_US.UTF-8
10-14 09:44 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
10-14 09:44 DEBUG  CommonBackend: Searching ISOs on USB devices
10-14 09:44 DEBUG  CommonBackend: Searching for local CDs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 INFO   root: Already installed, running the uninstaller...
10-14 09:44 INFO   root: Running the uninstaller...
10-14 09:44 INFO   CommonBackend: This is the uninstaller running
10-14 09:44 DEBUG  WindowsFrontend: __init__...
10-14 09:44 DEBUG  WindowsFrontend: on_init...
10-14 09:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\translations, languages=['en_US', 'en']
10-14 09:44 INFO   root: Received settings
10-14 09:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\translations, languages=['en_US', 'en']
10-14 09:44 DEBUG  TaskList: # Running tasklist...
10-14 09:44 DEBUG  TaskList: ## Running Remove bootloader entry...
10-14 09:44 DEBUG  WindowsBackend: Removing bcd entry {59d97309-8679-11df-acea-00038a000015}
10-14 09:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
10-14 09:44 DEBUG  WindowsBackend: undo_bootini C:
10-14 09:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 51785.1210938 mb free ntfs)
10-14 09:44 DEBUG  WindowsBackend: undo_bootini D:
10-14 09:44 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 38882.9609375 mb free ntfs)
10-14 09:44 DEBUG  WindowsBackend: undo_bootini E:
10-14 09:44 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 17600.0507813 mb free ntfs)
10-14 09:44 DEBUG  WindowsBackend: undo_bootini K:
10-14 09:44 DEBUG  WindowsBackend: undo_configsys Drive(K: removable 0.0 mb free )
10-14 09:44 DEBUG  TaskList: ## Finished Remove bootloader entry
10-14 09:44 DEBUG  TaskList: ## Running Remove target dir...
10-14 09:44 DEBUG  CommonBackend: Deleting D:\ubuntu
10-14 09:44 DEBUG  TaskList: ## Finished Remove target dir
10-14 09:44 DEBUG  TaskList: ## Running Remove registry key...
10-14 09:44 DEBUG  TaskList: ## Finished Remove registry key
10-14 09:44 DEBUG  TaskList: # Finished tasklist
10-14 09:44 INFO   root: Almost finished uninstalling
10-14 09:44 INFO   root: Finished uninstallation
10-14 09:44 DEBUG  CommonBackend: Fetching basic info...
10-14 09:44 DEBUG  CommonBackend: original_exe=C:\Users\Karim\Downloads\wubi.exe
10-14 09:44 DEBUG  CommonBackend: platform=win32
10-14 09:44 DEBUG  CommonBackend: osname=nt
10-14 09:44 DEBUG  WindowsBackend: arch=amd64
10-14 09:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\data\isolist.ini
10-14 09:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-14 09:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-14 09:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-14 09:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-14 09:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-14 09:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-14 09:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-14 09:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-14 09:44 DEBUG  WindowsBackend: Fetching host info...
10-14 09:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-14 09:44 DEBUG  WindowsBackend: windows version=vista
10-14 09:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-14 09:44 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-14 09:44 DEBUG  WindowsBackend: windows_build=7601
10-14 09:44 DEBUG  WindowsBackend: gmt=2
10-14 09:44 DEBUG  WindowsBackend: country=US
10-14 09:44 DEBUG  WindowsBackend: timezone=America/New_York
10-14 09:44 DEBUG  WindowsBackend: windows_username=Karim
10-14 09:44 DEBUG  WindowsBackend: user_full_name=Karim
10-14 09:44 DEBUG  WindowsBackend: user_directory=C:\Users\Karim
10-14 09:44 DEBUG  WindowsBackend: windows_language_code=1033
10-14 09:44 DEBUG  WindowsBackend: windows_language=English
10-14 09:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz
10-14 09:44 DEBUG  WindowsBackend: bootloader=vista
10-14 09:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 51784.1328125 mb free ntfs)
10-14 09:44 DEBUG  WindowsBackend: drive=Drive(C: hd 51784.1328125 mb free ntfs)
10-14 09:44 DEBUG  WindowsBackend: drive=Drive(D: hd 41969.5664063 mb free ntfs)
10-14 09:44 DEBUG  WindowsBackend: drive=Drive(E: hd 17600.1796875 mb free ntfs)
10-14 09:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
10-14 09:44 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
10-14 09:44 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
10-14 09:44 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free cdfs)
10-14 09:44 DEBUG  WindowsBackend: uninstaller_path=None
10-14 09:44 DEBUG  WindowsBackend: previous_target_dir=None
10-14 09:44 DEBUG  WindowsBackend: previous_distro_name=None
10-14 09:44 DEBUG  WindowsBackend: keyboard_id=67699721
10-14 09:44 DEBUG  WindowsBackend: keyboard_layout=us
10-14 09:44 DEBUG  WindowsBackend: keyboard_variant=
10-14 09:44 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
10-14 09:44 DEBUG  CommonBackend: Searching ISOs on USB devices
10-14 09:44 DEBUG  CommonBackend: Searching for local CDs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 INFO   root: Running the installer...
10-14 09:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\translations, languages=['en_US', 'en']
10-14 09:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\translations, languages=['en_US', 'en']
10-14 09:44 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=karim
10-14 09:44 INFO   root: Received settings
10-14 09:44 DEBUG  CommonBackend: Searching for local CD
10-14 09:44 DEBUG  Distro:   checking whether C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-14 09:44 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
10-14 09:44 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
10-14 09:44 DEBUG  CommonBackend: Searching for local ISO
10-14 09:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\translations, languages=['en_US', 'en']
10-14 09:44 DEBUG  TaskList: # Running tasklist...
10-14 09:44 DEBUG  TaskList: ## Running select_target_dir...
10-14 09:44 INFO   WindowsBackend: Installing into D:\ubuntu
10-14 09:44 DEBUG  TaskList: ## Finished select_target_dir
10-14 09:44 DEBUG  TaskList: ## Running create_dir_structure...
10-14 09:44 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-14 09:44 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-14 09:44 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-14 09:44 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-14 09:44 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-14 09:44 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-14 09:44 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-14 09:44 DEBUG  TaskList: ## Finished create_dir_structure
10-14 09:44 DEBUG  TaskList: ## Running create_uninstaller...
10-14 09:44 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Karim\Downloads\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-14 09:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-14 09:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-14 09:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-14 09:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-14 09:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
10-14 09:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-14 09:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-14 09:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-14 09:44 DEBUG  TaskList: ## Finished create_uninstaller
10-14 09:44 DEBUG  TaskList: ## Running create_preseed_diskimage...
10-14 09:44 DEBUG  TaskList: ## Finished create_preseed_diskimage
10-14 09:44 DEBUG  TaskList: ## Running get_diskimage...
10-14 09:44 DEBUG  TaskList: New task download
10-14 09:44 DEBUG  TaskList: ### Running download...
10-14 09:44 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > D:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
10-14 09:44 DEBUG  downloader: Download start filename=D:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
10-14 10:32 DEBUG  TaskList: ### Finished download
10-14 10:32 DEBUG  downloader: download finished (read 507143012 bytes)
10-14 10:32 DEBUG  TaskList: ## Finished get_diskimage
10-14 10:32 DEBUG  TaskList: ## Running extract_diskimage...
10-14 10:34 DEBUG  TaskList: ## Finished extract_diskimage
10-14 10:34 DEBUG  TaskList: ## Running choose_disk_sizes...
10-14 10:34 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
10-14 10:34 DEBUG  TaskList: ## Finished choose_disk_sizes
10-14 10:34 DEBUG  TaskList: ## Running expand_diskimage...
10-14 10:38 DEBUG  TaskList: ## Finished expand_diskimage
10-14 10:38 DEBUG  TaskList: ## Running create_swap_diskimage...
10-14 10:38 DEBUG  TaskList: ## Finished create_swap_diskimage
10-14 10:38 DEBUG  TaskList: ## Running modify_bootloader...
10-14 10:38 DEBUG  TaskList: New task modify_bcd
10-14 10:38 DEBUG  TaskList: ### Running modify_bcd...
10-14 10:38 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 51784.1328125 mb free ntfs)
10-14 10:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {59d9730a-8679-11df-acea-00038a000015}
10-14 10:38 DEBUG  TaskList: ### Finished modify_bcd
10-14 10:38 DEBUG  TaskList: New task modify_bcd
10-14 10:38 DEBUG  TaskList: ### Running modify_bcd...
10-14 10:38 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 41969.5664063 mb free ntfs)
10-14 10:38 DEBUG  WindowsBackend: BCD has already been modified
10-14 10:38 DEBUG  TaskList: ### Finished modify_bcd
10-14 10:38 DEBUG  TaskList: New task modify_bcd
10-14 10:38 DEBUG  TaskList: ### Running modify_bcd...
10-14 10:38 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 17600.1796875 mb free ntfs)
10-14 10:38 DEBUG  WindowsBackend: BCD has already been modified
10-14 10:38 DEBUG  TaskList: ### Finished modify_bcd
10-14 10:38 DEBUG  TaskList: New task modify_bcd
10-14 10:38 DEBUG  TaskList: ### Running modify_bcd...
10-14 10:38 DEBUG  WindowsBackend: modify_bcd Drive(K: removable 0.0 mb free )
10-14 10:38 DEBUG  WindowsBackend: BCD has already been modified
10-14 10:38 DEBUG  TaskList: ### Finished modify_bcd
10-14 10:38 DEBUG  TaskList: ## Finished modify_bootloader
10-14 10:38 DEBUG  TaskList: ## Running diskimage_bootloader...
10-14 10:38 DEBUG  WindowsBackend: Copying C:\Users\Karim\AppData\Local\Temp\pylAF63.tmp\winboot -> D:\ubuntu\winboot
10-14 10:38 ERROR  TaskList: [Errno 2] No such file or directory: 'K:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'K:\\wubildr'
10-14 10:38 DEBUG  TaskList: # Cancelling tasklist
10-14 10:38 DEBUG  TaskList: # Finished tasklist
10-14 10:38 ERROR  root: [Errno 2] No such file or directory: 'K:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'K:\\wubildr'


Please help!!

---

### Post by tiyatromat on 2011-11-18
I had the same problem. Have solved this problem or anybody can say why it happens?

---

### Post by bcbc on 2011-11-18
See bug [lpbug]862003[/lpbug]. In the logfile from the original poster the install is successful. However, "permission denied" can also be issued in cases where the install is not successful so you have to check the log to make sure that this bug applies. Or rebooting into Ubuntu will show you as well.

---

