---
title: "Cant install, log posted"
date: 2014-06-03
forum: Installation &amp; Upgrades
---

### Post by bertil2 on 2014-06-03
Package: installation-reports

Boot method: ISO mirror
Image version: [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.iso](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.iso)
Date: 02/05/2014 GMT+1  16.00 

Machine: Toshiba SATTELITE A200-1ML
Processor: Genuine Intel CPU T2080 @ 1.73GHz 1.73GHz 
Memory: 1.5 GB RAM
Partitions: <dont know what this means>

Output of lspci -knn (or lspci -nn): dont know what this means

Base System Installation Checklist:
[O] = OK, [E] = Error (please elaborate below), [ ] = didn't try it

Initial boot:           [ ]
Detect network card:    [ ]
Configure network:      [ ]
Detect CD:              [ ]
Load installer modules: [ ]
Detect hard drives:     [ ]
Partition hard drives:  [ ]
Install base system:    [ ]
Clock/timezone setup:   [ ]
User/password setup:    [ ]
Install tasks:          [ ]
Install boot loader:    [ ]
Overall install:        [E]

Comments/Problems: When trying to install UBUNTU with the wubi executable in windows, 
the installation asks me to restart my computer. When I do, nothing happens, so I choose
the third option. When the installation is almost done, I get an error during "Installing
cd-boothelper" (My install is in danish, so it's a rough translation.     
The pop-up says there is an invalid argument, and it displays the location for the log-file
displayed below.

06-03 15:35 INFO   root: === wubi 14.04 rev286 ===
06-03 15:35 DEBUG  root: Logfile is c:\users\mor\appdata\local\temp\wubi-14.04-rev286.log
06-03 15:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
06-03 15:35 DEBUG  CommonBackend: data_dir=C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\data
06-03 15:35 DEBUG  WindowsBackend: 7z=C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\bin\7z.exe
06-03 15:35 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-03 15:35 DEBUG  CommonBackend: Fetching basic info...
06-03 15:35 DEBUG  CommonBackend: original_exe=H:\wubi.exe
06-03 15:35 DEBUG  CommonBackend: platform=win32
06-03 15:35 DEBUG  CommonBackend: osname=nt
06-03 15:35 DEBUG  CommonBackend: language=da_DK
06-03 15:35 DEBUG  CommonBackend: encoding=cp1252
06-03 15:35 DEBUG  WindowsBackend: arch=i386
06-03 15:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\data\isolist.ini
06-03 15:35 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
06-03 15:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-03 15:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-03 15:35 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
06-03 15:35 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
06-03 15:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-03 15:35 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
06-03 15:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-03 15:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-03 15:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-03 15:35 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
06-03 15:35 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
06-03 15:35 DEBUG  WindowsBackend: Fetching host info...
06-03 15:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-03 15:35 DEBUG  WindowsBackend: windows version=vista
06-03 15:35 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
06-03 15:35 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-03 15:35 DEBUG  WindowsBackend: windows_build=6002
06-03 15:35 DEBUG  WindowsBackend: gmt=1
06-03 15:35 DEBUG  WindowsBackend: country=DK
06-03 15:35 DEBUG  WindowsBackend: timezone=Europe/Copenhagen
06-03 15:35 DEBUG  WindowsBackend: windows_username=Mor
06-03 15:35 DEBUG  WindowsBackend: user_full_name=Mor
06-03 15:35 DEBUG  WindowsBackend: user_directory=C:\Users\Mor
06-03 15:35 DEBUG  WindowsBackend: windows_language_code=1030
06-03 15:35 DEBUG  WindowsBackend: windows_language=Danish
06-03 15:35 DEBUG  WindowsBackend: processor_name=Genuine Intel(R) CPU           T2080  @ 1.73GHz
06-03 15:35 DEBUG  WindowsBackend: bootloader=vista
06-03 15:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8095.1640625 mb free ntfs)
06-03 15:35 DEBUG  WindowsBackend: drive=Drive(C: hd 8095.1640625 mb free ntfs)
06-03 15:35 DEBUG  WindowsBackend: drive=Drive(D: removable 1876.96875 mb free fat)
06-03 15:35 DEBUG  WindowsBackend: drive=Drive(E: hd 55640.9179688 mb free ntfs)
06-03 15:35 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
06-03 15:35 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
06-03 15:35 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
06-03 15:35 DEBUG  WindowsBackend: uninstaller_path=None
06-03 15:35 DEBUG  WindowsBackend: previous_target_dir=None
06-03 15:35 DEBUG  WindowsBackend: previous_distro_name=None
06-03 15:35 DEBUG  WindowsBackend: keyboard_id=67503110
06-03 15:35 DEBUG  WindowsBackend: keyboard_layout=dk
06-03 15:35 DEBUG  WindowsBackend: keyboard_variant=
06-03 15:35 DEBUG  CommonBackend: python locale=('da_DK', 'cp1252')
06-03 15:35 DEBUG  CommonBackend: locale=da_DK.UTF-8
06-03 15:35 DEBUG  WindowsBackend: total_memory_mb=1525.37890625
06-03 15:35 DEBUG  CommonBackend: Searching ISOs on USB devices
06-03 15:35 DEBUG  CommonBackend: Searching for local CDs
06-03 15:35 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp is a valid Ubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp is a valid Ubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp is a valid Kubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp is a valid Kubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp is a valid Mythbuntu CD
06-03 15:35 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp is a valid Mythbuntu CD
06-03 15:35 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp is a valid Edubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp is a valid Edubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp is a valid Lubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp is a valid Lubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp is a valid Ubuntu Studio CD
06-03 15:35 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp is a valid Ubuntu Studio CD
06-03 15:35 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-03 15:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-03 15:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
06-03 15:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
06-03 15:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-03 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-03 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
06-03 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
06-03 15:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-03 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-03 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
06-03 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
06-03 15:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-03 15:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-03 15:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
06-03 15:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
06-03 15:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:35 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-03 15:35 DEBUG  Distro:     does not contain H:\casper\vmlinuz.efi
06-03 15:35 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-03 15:35 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release i386 (20140417)
06-03 15:35 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'i386'}
06-03 15:35 INFO   Distro: Found a valid CD for Ubuntu: H:\
06-03 15:35 INFO   root: Running the CD menu...
06-03 15:35 DEBUG  WindowsFrontend: __init__...
06-03 15:35 DEBUG  WindowsFrontend: on_init...
06-03 15:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\translations, languages=['da_DK', 'da']
06-03 15:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mor\AppData\Local\Temp\pylCD50.tmp\translations, languages=['da_DK', 'da']
06-03 15:35 INFO   root: CD menu finished
06-03 15:35 INFO   root: Rebooting
06-03 15:35 DEBUG  TaskList: # Running tasklist...
06-03 15:35 DEBUG  TaskList: ## Running reboot...
06-03 15:35 DEBUG  TaskList: ## Finished reboot
06-03 15:35 DEBUG  TaskList: # Finished tasklist
06-03 15:35 DEBUG  root: application.quit
06-03 15:35 DEBUG  WindowsFrontend: frontend.quit
06-03 15:35 DEBUG  WindowsFrontend: frontend.on_quit
06-03 15:35 DEBUG  root: application.on_quit
06-03 15:35 INFO   root: sys.exit
06-03 15:45 INFO   root: === wubi 14.04 rev286 ===
06-03 15:45 DEBUG  root: Logfile is c:\users\mor\appdata\local\temp\wubi-14.04-rev286.log
06-03 15:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
06-03 15:45 DEBUG  CommonBackend: data_dir=C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\data
06-03 15:45 DEBUG  WindowsBackend: 7z=C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\bin\7z.exe
06-03 15:45 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-03 15:45 DEBUG  CommonBackend: Fetching basic info...
06-03 15:45 DEBUG  CommonBackend: original_exe=H:\wubi.exe
06-03 15:45 DEBUG  CommonBackend: platform=win32
06-03 15:45 DEBUG  CommonBackend: osname=nt
06-03 15:45 DEBUG  CommonBackend: language=da_DK
06-03 15:45 DEBUG  CommonBackend: encoding=cp1252
06-03 15:45 DEBUG  WindowsBackend: arch=i386
06-03 15:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\data\isolist.ini
06-03 15:45 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
06-03 15:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-03 15:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-03 15:45 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
06-03 15:45 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
06-03 15:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-03 15:45 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
06-03 15:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-03 15:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-03 15:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-03 15:45 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
06-03 15:45 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
06-03 15:45 DEBUG  WindowsBackend: Fetching host info...
06-03 15:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-03 15:45 DEBUG  WindowsBackend: windows version=vista
06-03 15:45 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
06-03 15:45 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-03 15:45 DEBUG  WindowsBackend: windows_build=6002
06-03 15:45 DEBUG  WindowsBackend: gmt=1
06-03 15:45 DEBUG  WindowsBackend: country=DK
06-03 15:45 DEBUG  WindowsBackend: timezone=Europe/Copenhagen
06-03 15:45 DEBUG  WindowsBackend: windows_username=Mor
06-03 15:45 DEBUG  WindowsBackend: user_full_name=Mor
06-03 15:45 DEBUG  WindowsBackend: user_directory=C:\Users\Mor
06-03 15:45 DEBUG  WindowsBackend: windows_language_code=1030
06-03 15:45 DEBUG  WindowsBackend: windows_language=Danish
06-03 15:45 DEBUG  WindowsBackend: processor_name=Genuine Intel(R) CPU           T2080  @ 1.73GHz
06-03 15:45 DEBUG  WindowsBackend: bootloader=vista
06-03 15:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8078.90625 mb free ntfs)
06-03 15:45 DEBUG  WindowsBackend: drive=Drive(C: hd 8078.90625 mb free ntfs)
06-03 15:45 DEBUG  WindowsBackend: drive=Drive(D: removable 1876.96875 mb free fat)
06-03 15:45 DEBUG  WindowsBackend: drive=Drive(E: hd 55640.9179688 mb free ntfs)
06-03 15:45 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
06-03 15:45 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
06-03 15:45 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
06-03 15:45 DEBUG  WindowsBackend: uninstaller_path=None
06-03 15:45 DEBUG  WindowsBackend: previous_target_dir=None
06-03 15:45 DEBUG  WindowsBackend: previous_distro_name=None
06-03 15:45 DEBUG  WindowsBackend: keyboard_id=67503110
06-03 15:45 DEBUG  WindowsBackend: keyboard_layout=dk
06-03 15:45 DEBUG  WindowsBackend: keyboard_variant=
06-03 15:45 DEBUG  CommonBackend: python locale=('da_DK', 'cp1252')
06-03 15:45 DEBUG  CommonBackend: locale=da_DK.UTF-8
06-03 15:45 DEBUG  WindowsBackend: total_memory_mb=1525.37890625
06-03 15:45 DEBUG  CommonBackend: Searching ISOs on USB devices
06-03 15:45 DEBUG  CommonBackend: Searching for local CDs
06-03 15:45 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp is a valid Ubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp is a valid Ubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp is a valid Kubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp is a valid Kubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp is a valid Mythbuntu CD
06-03 15:45 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp is a valid Mythbuntu CD
06-03 15:45 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp is a valid Edubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp is a valid Edubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp is a valid Lubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp is a valid Lubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp is a valid Ubuntu Studio CD
06-03 15:45 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp is a valid Ubuntu Studio CD
06-03 15:45 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-03 15:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-03 15:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
06-03 15:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
06-03 15:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-03 15:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-03 15:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
06-03 15:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
06-03 15:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-03 15:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-03 15:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
06-03 15:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
06-03 15:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-03 15:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-03 15:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
06-03 15:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
06-03 15:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:45 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-03 15:45 DEBUG  Distro:     does not contain H:\casper\vmlinuz.efi
06-03 15:45 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-03 15:45 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release i386 (20140417)
06-03 15:45 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'i386'}
06-03 15:45 INFO   Distro: Found a valid CD for Ubuntu: H:\
06-03 15:45 INFO   root: Running the CD menu...
06-03 15:45 DEBUG  WindowsFrontend: __init__...
06-03 15:45 DEBUG  WindowsFrontend: on_init...
06-03 15:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\translations, languages=['da_DK', 'da']
06-03 15:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\translations, languages=['da_DK', 'da']
06-03 15:45 INFO   root: CD menu finished
06-03 15:45 INFO   root: Running the CD boot helper...
06-03 15:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\translations, languages=['da_DK', 'da']
06-03 15:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\translations, languages=['da_DK', 'da']
06-03 15:46 INFO   root: CD boot helper confirmed
06-03 15:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\translations, languages=['da_DK', 'da']
06-03 15:46 DEBUG  TaskList: # Running tasklist...
06-03 15:46 DEBUG  TaskList: ## Running select_target_dir...
06-03 15:46 INFO   WindowsBackend: Installing into C:\ubuntu
06-03 15:46 DEBUG  TaskList: ## Finished select_target_dir
06-03 15:46 DEBUG  TaskList: ## Running create_dir_structure...
06-03 15:46 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-03 15:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-03 15:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-03 15:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-03 15:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-03 15:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-03 15:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-03 15:46 DEBUG  TaskList: ## Finished create_dir_structure
06-03 15:46 DEBUG  TaskList: ## Running uncompress_target_dir...
06-03 15:46 DEBUG  TaskList: ## Finished uncompress_target_dir
06-03 15:46 DEBUG  TaskList: ## Running create_uninstaller...
06-03 15:46 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-03 15:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
06-03 15:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
06-03 15:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-03 15:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
06-03 15:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
06-03 15:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-03 15:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-03 15:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-03 15:46 DEBUG  TaskList: ## Finished create_uninstaller
06-03 15:46 DEBUG  TaskList: ## Running copy_installation_files...
06-03 15:46 DEBUG  WindowsBackend: Copying C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
06-03 15:46 DEBUG  WindowsBackend: Copying C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\winboot -> C:\ubuntu\winboot
06-03 15:46 DEBUG  WindowsBackend: Copying C:\Users\Mor\AppData\Local\Temp\pylD42F.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
06-03 15:46 DEBUG  TaskList: ## Finished copy_installation_files
06-03 15:46 DEBUG  TaskList: ## Running use_cd...
06-03 15:46 DEBUG  TaskList: New task copy_file
06-03 15:46 DEBUG  TaskList: ### Running copy_file...
06-03 15:52 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 202, in copy_file
IOError: [Errno 22] Invalid argument
06-03 15:52 DEBUG  TaskList: # Cancelling tasklist
06-03 15:52 DEBUG  TaskList: New task check_iso
06-03 15:52 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 228, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 202, in copy_file
IOError: [Errno 22] Invalid argument
06-03 15:52 DEBUG  TaskList: ## Finished use_cd
06-03 15:52 DEBUG  TaskList: # Finished tasklist
06-03 15:55 INFO   root: === wubi 14.04 rev286 ===
06-03 15:55 DEBUG  root: Logfile is c:\users\mor\appdata\local\temp\wubi-14.04-rev286.log
06-03 15:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
06-03 15:55 DEBUG  CommonBackend: data_dir=C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\data
06-03 15:55 DEBUG  WindowsBackend: 7z=C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\bin\7z.exe
06-03 15:55 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-03 15:55 DEBUG  CommonBackend: Fetching basic info...
06-03 15:55 DEBUG  CommonBackend: original_exe=H:\wubi.exe
06-03 15:55 DEBUG  CommonBackend: platform=win32
06-03 15:55 DEBUG  CommonBackend: osname=nt
06-03 15:55 DEBUG  CommonBackend: language=da_DK
06-03 15:55 DEBUG  CommonBackend: encoding=cp1252
06-03 15:55 DEBUG  WindowsBackend: arch=i386
06-03 15:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\data\isolist.ini
06-03 15:55 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
06-03 15:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-03 15:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-03 15:55 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
06-03 15:55 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
06-03 15:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-03 15:55 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
06-03 15:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-03 15:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-03 15:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-03 15:55 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
06-03 15:55 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
06-03 15:55 DEBUG  WindowsBackend: Fetching host info...
06-03 15:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-03 15:55 DEBUG  WindowsBackend: windows version=vista
06-03 15:55 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
06-03 15:55 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-03 15:55 DEBUG  WindowsBackend: windows_build=6002
06-03 15:55 DEBUG  WindowsBackend: gmt=1
06-03 15:55 DEBUG  WindowsBackend: country=DK
06-03 15:55 DEBUG  WindowsBackend: timezone=Europe/Copenhagen
06-03 15:55 DEBUG  WindowsBackend: windows_username=Mor
06-03 15:55 DEBUG  WindowsBackend: user_full_name=Mor
06-03 15:55 DEBUG  WindowsBackend: user_directory=C:\Users\Mor
06-03 15:55 DEBUG  WindowsBackend: windows_language_code=1030
06-03 15:55 DEBUG  WindowsBackend: windows_language=Danish
06-03 15:55 DEBUG  WindowsBackend: processor_name=Genuine Intel(R) CPU           T2080  @ 1.73GHz
06-03 15:55 DEBUG  WindowsBackend: bootloader=vista
06-03 15:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 7075.35546875 mb free ntfs)
06-03 15:55 DEBUG  WindowsBackend: drive=Drive(C: hd 7075.35546875 mb free ntfs)
06-03 15:55 DEBUG  WindowsBackend: drive=Drive(D: removable 1876.96875 mb free fat)
06-03 15:55 DEBUG  WindowsBackend: drive=Drive(E: hd 55640.9179688 mb free ntfs)
06-03 15:55 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
06-03 15:55 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
06-03 15:55 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
06-03 15:55 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-03 15:55 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-03 15:55 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-03 15:55 DEBUG  WindowsBackend: keyboard_id=67503110
06-03 15:55 DEBUG  WindowsBackend: keyboard_layout=dk
06-03 15:55 DEBUG  WindowsBackend: keyboard_variant=
06-03 15:55 DEBUG  CommonBackend: python locale=('da_DK', 'cp1252')
06-03 15:55 DEBUG  CommonBackend: locale=da_DK.UTF-8
06-03 15:55 DEBUG  WindowsBackend: total_memory_mb=1525.37890625
06-03 15:55 DEBUG  CommonBackend: Searching ISOs on USB devices
06-03 15:55 DEBUG  CommonBackend: Searching for local CDs
06-03 15:55 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Ubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Ubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Kubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Kubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Mythbuntu CD
06-03 15:55 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Mythbuntu CD
06-03 15:55 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Edubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Edubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Lubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Lubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Ubuntu Studio CD
06-03 15:55 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Ubuntu Studio CD
06-03 15:55 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-03 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-03 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
06-03 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
06-03 15:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-03 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-03 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
06-03 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
06-03 15:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-03 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-03 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
06-03 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
06-03 15:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-03 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-03 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
06-03 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
06-03 15:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 15:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-03 15:55 DEBUG  Distro:     does not contain H:\casper\vmlinuz.efi
06-03 15:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-03 15:55 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release i386 (20140417)
06-03 15:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'i386'}
06-03 15:55 INFO   Distro: Found a valid CD for Ubuntu: H:\
06-03 15:55 INFO   root: Running the CD menu...
06-03 15:55 DEBUG  WindowsFrontend: __init__...
06-03 15:55 DEBUG  WindowsFrontend: on_init...
06-03 15:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\translations, languages=['da_DK', 'da']
06-03 15:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\translations, languages=['da_DK', 'da']
06-03 16:11 INFO   root: CD menu finished
06-03 16:11 INFO   root: Already installed, running the uninstaller...
06-03 16:11 INFO   root: Running the uninstaller...
06-03 16:11 INFO   CommonBackend: This is the uninstaller running
06-03 16:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\translations, languages=['da_DK', 'da']
06-03 16:11 INFO   root: Received settings
06-03 16:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\translations, languages=['da_DK', 'da']
06-03 16:11 DEBUG  TaskList: # Running tasklist...
06-03 16:11 DEBUG  TaskList: ## Running Fjern indgang fra opstartsindlæser...
06-03 16:11 DEBUG  WindowsBackend: Could not find bcd id
06-03 16:11 DEBUG  WindowsBackend: undo_bootini C:
06-03 16:11 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 7075.35546875 mb free ntfs)
06-03 16:11 DEBUG  WindowsBackend: undo_bootini D:
06-03 16:11 DEBUG  WindowsBackend: undo_configsys Drive(D: removable 1876.96875 mb free fat)
06-03 16:11 DEBUG  WindowsBackend: undo_bootini E:
06-03 16:11 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 55640.9179688 mb free ntfs)
06-03 16:11 DEBUG  TaskList: ## Finished Fjern indgang fra opstartsindlæser
06-03 16:11 DEBUG  TaskList: ## Running Fjern destinationsmappe...
06-03 16:11 DEBUG  CommonBackend: Deleting C:\ubuntu
06-03 16:11 DEBUG  TaskList: ## Finished Fjern destinationsmappe
06-03 16:11 DEBUG  TaskList: ## Running Fjern registreringsnøglen...
06-03 16:11 DEBUG  TaskList: ## Finished Fjern registreringsnøglen
06-03 16:11 DEBUG  TaskList: # Finished tasklist
06-03 16:11 INFO   root: Almost finished uninstalling
06-03 16:11 INFO   root: Finished uninstallation
06-03 16:11 DEBUG  CommonBackend: Fetching basic info...
06-03 16:11 DEBUG  CommonBackend: original_exe=H:\wubi.exe
06-03 16:11 DEBUG  CommonBackend: platform=win32
06-03 16:11 DEBUG  CommonBackend: osname=nt
06-03 16:11 DEBUG  WindowsBackend: arch=i386
06-03 16:11 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\data\isolist.ini
06-03 16:11 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
06-03 16:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-03 16:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-03 16:11 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
06-03 16:11 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
06-03 16:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-03 16:11 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
06-03 16:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-03 16:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-03 16:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-03 16:11 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
06-03 16:11 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
06-03 16:11 DEBUG  WindowsBackend: Fetching host info...
06-03 16:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-03 16:11 DEBUG  WindowsBackend: windows version=vista
06-03 16:11 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
06-03 16:11 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-03 16:11 DEBUG  WindowsBackend: windows_build=6002
06-03 16:11 DEBUG  WindowsBackend: gmt=1
06-03 16:11 DEBUG  WindowsBackend: country=DK
06-03 16:11 DEBUG  WindowsBackend: timezone=Europe/Copenhagen
06-03 16:11 DEBUG  WindowsBackend: windows_username=Mor
06-03 16:11 DEBUG  WindowsBackend: user_full_name=Mor
06-03 16:11 DEBUG  WindowsBackend: user_directory=C:\Users\Mor
06-03 16:11 DEBUG  WindowsBackend: windows_language_code=1030
06-03 16:11 DEBUG  WindowsBackend: windows_language=Danish
06-03 16:11 DEBUG  WindowsBackend: processor_name=Genuine Intel(R) CPU           T2080  @ 1.73GHz
06-03 16:11 DEBUG  WindowsBackend: bootloader=vista
06-03 16:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 7948.421875 mb free ntfs)
06-03 16:11 DEBUG  WindowsBackend: drive=Drive(C: hd 7948.421875 mb free ntfs)
06-03 16:11 DEBUG  WindowsBackend: drive=Drive(D: removable 1876.96875 mb free fat)
06-03 16:11 DEBUG  WindowsBackend: drive=Drive(E: hd 55640.9179688 mb free ntfs)
06-03 16:11 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
06-03 16:11 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
06-03 16:11 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
06-03 16:11 DEBUG  WindowsBackend: uninstaller_path=None
06-03 16:11 DEBUG  WindowsBackend: previous_target_dir=None
06-03 16:11 DEBUG  WindowsBackend: previous_distro_name=None
06-03 16:11 DEBUG  WindowsBackend: keyboard_id=67503110
06-03 16:11 DEBUG  WindowsBackend: keyboard_layout=dk
06-03 16:11 DEBUG  WindowsBackend: keyboard_variant=
06-03 16:11 DEBUG  WindowsBackend: total_memory_mb=1525.37890625
06-03 16:11 DEBUG  CommonBackend: Searching ISOs on USB devices
06-03 16:11 DEBUG  CommonBackend: Searching for local CDs
06-03 16:11 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Ubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Ubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Kubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Kubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Mythbuntu CD
06-03 16:11 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Mythbuntu CD
06-03 16:11 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Edubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Edubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Lubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Lubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Ubuntu Studio CD
06-03 16:11 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp is a valid Ubuntu Studio CD
06-03 16:11 DEBUG  Distro:     does not contain C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-03 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-03 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
06-03 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
06-03 16:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-03 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-03 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
06-03 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
06-03 16:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-03 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-03 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
06-03 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
06-03 16:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-03 16:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-03 16:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
06-03 16:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
06-03 16:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-03 16:11 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-03 16:11 DEBUG  Distro:     does not contain H:\casper\vmlinuz.efi
06-03 16:11 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
06-03 16:11 INFO   Distro: Found a valid CD for Ubuntu: H:\
06-03 16:11 INFO   root: Running the CD boot helper...
06-03 16:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\translations, languages=['da_DK', 'da']
06-03 16:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\translations, languages=['da_DK', 'da']
06-03 16:11 INFO   root: CD boot helper confirmed
06-03 16:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\translations, languages=['da_DK', 'da']
06-03 16:11 DEBUG  TaskList: # Running tasklist...
06-03 16:11 DEBUG  TaskList: ## Running select_target_dir...
06-03 16:11 INFO   WindowsBackend: Installing into C:\ubuntu
06-03 16:11 DEBUG  TaskList: ## Finished select_target_dir
06-03 16:11 DEBUG  TaskList: ## Running create_dir_structure...
06-03 16:11 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-03 16:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-03 16:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-03 16:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-03 16:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-03 16:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-03 16:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-03 16:11 DEBUG  TaskList: ## Finished create_dir_structure
06-03 16:11 DEBUG  TaskList: ## Running uncompress_target_dir...
06-03 16:11 DEBUG  TaskList: ## Finished uncompress_target_dir
06-03 16:11 DEBUG  TaskList: ## Running create_uninstaller...
06-03 16:11 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-03 16:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
06-03 16:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
06-03 16:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-03 16:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
06-03 16:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
06-03 16:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-03 16:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-03 16:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-03 16:11 DEBUG  TaskList: ## Finished create_uninstaller
06-03 16:11 DEBUG  TaskList: ## Running copy_installation_files...
06-03 16:11 DEBUG  WindowsBackend: Copying C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
06-03 16:11 DEBUG  WindowsBackend: Copying C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\winboot -> C:\ubuntu\winboot
06-03 16:11 DEBUG  WindowsBackend: Copying C:\Users\Mor\AppData\Local\Temp\pyl1110.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
06-03 16:11 DEBUG  TaskList: ## Finished copy_installation_files
06-03 16:11 DEBUG  TaskList: ## Running use_cd...
06-03 16:11 DEBUG  TaskList: New task copy_file
06-03 16:11 DEBUG  TaskList: ### Running copy_file...
06-03 16:14 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 202, in copy_file
IOError: [Errno 22] Invalid argument
06-03 16:14 DEBUG  TaskList: # Cancelling tasklist
06-03 16:14 DEBUG  TaskList: New task check_iso
06-03 16:14 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 228, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 202, in copy_file
IOError: [Errno 22] Invalid argument
06-03 16:14 DEBUG  TaskList: ## Finished use_cd
06-03 16:14 DEBUG  TaskList: # Finished tasklist

---

