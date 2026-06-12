---
title: "Installation Error"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by sharants on 2010-03-07
I am trying to install ubuntu through Wubi and i am getting the below error for some reason. Please can some one help me resolve this. I got a log file and i am attaching the details of the log.

03-07 08:01 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-07 08:01 DEBUG  root: Logfile is c:\docume~1\sharan\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-07 08:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\softwares\\Wibi Ubuntu Installer\\wubi.exe"']
03-07 08:01 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp\data
03-07 08:01 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp\bin\7z.exe
03-07 08:01 DEBUG  CommonBackend: Fetching basic info...
03-07 08:01 DEBUG  CommonBackend: original_exe=E:\softwares\Wibi Ubuntu Installer\wubi.exe
03-07 08:01 DEBUG  CommonBackend: platform=win32
03-07 08:01 DEBUG  CommonBackend: osname=nt
03-07 08:01 DEBUG  CommonBackend: language=en_GB
03-07 08:01 DEBUG  CommonBackend: encoding=cp1252
03-07 08:01 DEBUG  WindowsBackend: arch=amd64
03-07 08:01 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp\data\isolist.ini
03-07 08:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-07 08:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-07 08:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-07 08:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-07 08:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-07 08:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-07 08:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-07 08:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-07 08:01 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-07 08:01 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-07 08:01 DEBUG  WindowsBackend: Fetching host info...
03-07 08:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-07 08:01 DEBUG  WindowsBackend: windows version=xp
03-07 08:01 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-07 08:01 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-07 08:01 DEBUG  WindowsBackend: windows_build=2600
03-07 08:01 DEBUG  WindowsBackend: gmt=5
03-07 08:01 DEBUG  WindowsBackend: country=GB
03-07 08:01 DEBUG  WindowsBackend: timezone=Europe/London
03-07 08:01 DEBUG  WindowsBackend: windows_username=Sharan
03-07 08:01 DEBUG  WindowsBackend: user_full_name=Sharan
03-07 08:01 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sharan
03-07 08:01 DEBUG  WindowsBackend: windows_language_code=1033
03-07 08:01 DEBUG  WindowsBackend: windows_language=English
03-07 08:01 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz
03-07 08:01 DEBUG  WindowsBackend: bootloader=xp
03-07 08:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 7517.515625 mb free fat32)
03-07 08:01 DEBUG  WindowsBackend: drive=Drive(C: hd 7517.515625 mb free fat32)
03-07 08:01 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
03-07 08:01 DEBUG  WindowsBackend: drive=Drive(E: hd 30934.7109375 mb free ntfs)
03-07 08:01 DEBUG  WindowsBackend: drive=Drive(F: hd 6446.44921875 mb free ntfs)
03-07 08:01 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
03-07 08:01 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-07 08:01 DEBUG  WindowsBackend: uninstaller_path=None
03-07 08:01 DEBUG  WindowsBackend: previous_target_dir=None
03-07 08:01 DEBUG  WindowsBackend: previous_distro_name=None
03-07 08:01 DEBUG  WindowsBackend: keyboard_id=67699721
03-07 08:01 DEBUG  WindowsBackend: keyboard_layout=gb
03-07 08:01 DEBUG  WindowsBackend: keyboard_variant=
03-07 08:01 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
03-07 08:01 DEBUG  CommonBackend: locale=en_GB.UTF-8
03-07 08:01 DEBUG  WindowsBackend: total_memory_mb=2039.35546875
03-07 08:01 DEBUG  CommonBackend: Searching ISOs on USB devices
03-07 08:01 DEBUG  CommonBackend: Searching for local CDs
03-07 08:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp is a valid Ubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp is a valid Ubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp is a valid Ubuntu Netbook Remix CD
03-07 08:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp is a valid Kubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp is a valid Kubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp is a valid Kubuntu Netbook CD
03-07 08:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp is a valid Xubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp is a valid Xubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp is a valid Mythbuntu CD
03-07 08:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp is a valid Mythbuntu CD
03-07 08:01 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-07 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-07 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-07 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-07 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-07 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-07 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-07 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-07 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-07 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-07 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-07 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-07 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
03-07 08:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-07 08:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-07 08:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-07 08:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook Remix CD
03-07 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-07 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-07 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-07 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:01 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-07 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:01 INFO   root: Running the installer...
03-07 08:01 DEBUG  WindowsFrontend: __init__...
03-07 08:01 DEBUG  WindowsFrontend: on_init...
03-07 08:01 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp\translations, 

languages=['en_GB', 'en']
03-07 08:01 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328A.tmp\translations, 

languages=['en_GB', 'en']
03-07 08:01 INFO   WindowsFrontend: Operation cancelled
03-07 08:01 DEBUG  WindowsFrontend: frontend.quit
03-07 08:01 DEBUG  WindowsFrontend: frontend.on_quit
03-07 08:01 DEBUG  root: application.on_quit
03-07 08:01 INFO   root: sys.exit
03-07 08:02 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-07 08:02 DEBUG  root: Logfile is c:\docume~1\sharan\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-07 08:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\softwares\\Wibi Ubuntu Installer\\wubi.exe"']
03-07 08:02 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\data
03-07 08:02 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\bin\7z.exe
03-07 08:02 DEBUG  CommonBackend: Fetching basic info...
03-07 08:02 DEBUG  CommonBackend: original_exe=E:\softwares\Wibi Ubuntu Installer\wubi.exe
03-07 08:02 DEBUG  CommonBackend: platform=win32
03-07 08:02 DEBUG  CommonBackend: osname=nt
03-07 08:02 DEBUG  CommonBackend: language=en_GB
03-07 08:02 DEBUG  CommonBackend: encoding=cp1252
03-07 08:02 DEBUG  WindowsBackend: arch=amd64
03-07 08:02 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\data\isolist.ini
03-07 08:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-07 08:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-07 08:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-07 08:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-07 08:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-07 08:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-07 08:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-07 08:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-07 08:02 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-07 08:02 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-07 08:02 DEBUG  WindowsBackend: Fetching host info...
03-07 08:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-07 08:02 DEBUG  WindowsBackend: windows version=xp
03-07 08:02 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-07 08:02 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-07 08:02 DEBUG  WindowsBackend: windows_build=2600
03-07 08:02 DEBUG  WindowsBackend: gmt=5
03-07 08:02 DEBUG  WindowsBackend: country=GB
03-07 08:02 DEBUG  WindowsBackend: timezone=Europe/London
03-07 08:02 DEBUG  WindowsBackend: windows_username=Sharan
03-07 08:02 DEBUG  WindowsBackend: user_full_name=Sharan
03-07 08:02 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sharan
03-07 08:02 DEBUG  WindowsBackend: windows_language_code=1033
03-07 08:02 DEBUG  WindowsBackend: windows_language=English
03-07 08:02 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz
03-07 08:02 DEBUG  WindowsBackend: bootloader=xp
03-07 08:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 7504.4375 mb free fat32)
03-07 08:02 DEBUG  WindowsBackend: drive=Drive(C: hd 7504.4375 mb free fat32)
03-07 08:02 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
03-07 08:02 DEBUG  WindowsBackend: drive=Drive(E: hd 30934.7109375 mb free ntfs)
03-07 08:02 DEBUG  WindowsBackend: drive=Drive(F: hd 6446.44921875 mb free ntfs)
03-07 08:02 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
03-07 08:02 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-07 08:02 DEBUG  WindowsBackend: uninstaller_path=None
03-07 08:02 DEBUG  WindowsBackend: previous_target_dir=None
03-07 08:02 DEBUG  WindowsBackend: previous_distro_name=None
03-07 08:02 DEBUG  WindowsBackend: keyboard_id=67699721
03-07 08:02 DEBUG  WindowsBackend: keyboard_layout=gb
03-07 08:02 DEBUG  WindowsBackend: keyboard_variant=
03-07 08:02 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
03-07 08:02 DEBUG  CommonBackend: locale=en_GB.UTF-8
03-07 08:02 DEBUG  WindowsBackend: total_memory_mb=2039.35546875
03-07 08:02 DEBUG  CommonBackend: Searching ISOs on USB devices
03-07 08:02 DEBUG  CommonBackend: Searching for local CDs
03-07 08:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp is a valid Ubuntu Netbook Remix CD
03-07 08:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp is a valid Kubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp is a valid Kubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp is a valid Kubuntu Netbook CD
03-07 08:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp is a valid Xubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp is a valid Xubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp is a valid Mythbuntu CD
03-07 08:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp is a valid Mythbuntu CD
03-07 08:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-07 08:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-07 08:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-07 08:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-07 08:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-07 08:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-07 08:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-07 08:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-07 08:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-07 08:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-07 08:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-07 08:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-07 08:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
03-07 08:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-07 08:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-07 08:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-07 08:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook Remix CD
03-07 08:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-07 08:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-07 08:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-07 08:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:02 INFO   root: Running the installer...
03-07 08:02 DEBUG  WindowsFrontend: __init__...
03-07 08:02 DEBUG  WindowsFrontend: on_init...
03-07 08:02 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\translations, 

languages=['en_GB', 'en']
03-07 08:02 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\translations, 

languages=['en_GB', 'en']
03-07 08:02 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=10000MB, distro_name=Ubuntu, language=en_GB, 

locale=en_GB.UTF-8, username=sharan
03-07 08:02 INFO   root: Received settings
03-07 08:02 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\translations, 

languages=['en_GB', 'en']
03-07 08:02 DEBUG  TaskList: # Running tasklist...
03-07 08:02 DEBUG  TaskList: ## Running select_target_dir...
03-07 08:02 INFO   WindowsBackend: Installing into E:\ubuntu
03-07 08:02 DEBUG  TaskList: ## Finished select_target_dir
03-07 08:02 DEBUG  TaskList: ## Running create_dir_structure...
03-07 08:02 DEBUG  CommonBackend: Creating dir E:\ubuntu
03-07 08:02 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
03-07 08:02 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
03-07 08:02 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
03-07 08:02 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
03-07 08:02 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
03-07 08:02 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
03-07 08:02 DEBUG  TaskList: ## Finished create_dir_structure
03-07 08:02 DEBUG  TaskList: ## Running uncompress_target_dir...
03-07 08:02 DEBUG  TaskList: ## Finished uncompress_target_dir
03-07 08:02 DEBUG  TaskList: ## Running create_uninstaller...
03-07 08:02 DEBUG  WindowsBackend: Copying uninstaller E:\softwares\Wibi Ubuntu Installer\wubi.exe -> 

E:\ubuntu\uninstall-wubi.exe
03-07 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

UninstallString E:\ubuntu\uninstall-wubi.exe
03-07 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

InstallationDir E:\ubuntu
03-07 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

DisplayName Ubuntu
03-07 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

DisplayIcon E:\ubuntu\Ubuntu.ico
03-07 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

DisplayVersion 9.10ubuntu1-rev160
03-07 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

Publisher Ubuntu
03-07 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-07 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-07 08:02 DEBUG  TaskList: ## Finished create_uninstaller
03-07 08:02 DEBUG  TaskList: ## Running copy_installation_files...
03-07 08:02 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\data\custom-installation -> 

E:\ubuntu\install\custom-installation
03-07 08:02 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\winboot -> E:\ubuntu\winboot
03-07 08:02 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\data\images\Ubuntu.ico -> 

E:\ubuntu\Ubuntu.ico
03-07 08:02 DEBUG  TaskList: ## Finished copy_installation_files
03-07 08:02 DEBUG  TaskList: ## Running get_iso...
03-07 08:02 DEBUG  CommonBackend: Searching for local CD
03-07 08:02 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl328B.tmp\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-07 08:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:02 DEBUG  CommonBackend: Searching for local ISO
03-07 08:02 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-07 08:02 DEBUG  TaskList: New task get_metalink
03-07 08:02 DEBUG  TaskList: ### Running get_metalink...
03-07 08:02 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink) > 

E:\ubuntu\install
03-07 08:02 DEBUG  downloader: Download start filename=E:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, 

url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, 

length=26651, text=None
03-07 08:02 DEBUG  downloader: download finished (read 26651 bytes)
03-07 08:02 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > E:\ubuntu\install
03-07 08:02 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink, 

url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
03-07 08:02 DEBUG  downloader: download finished (read 562 bytes)
03-07 08:02 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > E:\ubuntu\install
03-07 08:02 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink.gpg, 

url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
03-07 08:02 DEBUG  downloader: download finished (read 189 bytes)
03-07 08:02 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-07 08:02 INFO   saplog: Checking block bindings..
03-07 08:02 INFO   saplog: Key verified successfully.
03-07 08:02 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

03-07 08:02 DEBUG  TaskList: ### Finished get_metalink
03-07 08:02 DEBUG  TaskList: New task download
03-07 08:02 DEBUG  TaskList: ### Running download...
03-07 08:02 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent) > 

E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
03-07 08:04 INFO   WindowsFrontend: Operation cancelled
03-07 08:04 DEBUG  WindowsFrontend: frontend.quit
03-07 08:04 DEBUG  WindowsFrontend: frontend.on_quit
03-07 08:04 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
03-07 08:04 DEBUG  TaskList: # Cancelling tasklist
03-07 08:04 DEBUG  TaskList: ### Finished download
03-07 08:04 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
03-07 08:04 DEBUG  root: application.on_quit
03-07 08:04 DEBUG  root: Forceful exit
03-07 08:04 INFO   root: sys.exit
03-07 08:04 INFO   root: === wubi 9.10ubuntu1 rev160 ===
03-07 08:04 DEBUG  root: Logfile is c:\docume~1\sharan\locals~1\temp\wubi-9.10ubuntu1-rev160.log
03-07 08:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\softwares\\Wibi Ubuntu Installer\\wubi.exe"']
03-07 08:04 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\data
03-07 08:04 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\bin\7z.exe
03-07 08:04 DEBUG  CommonBackend: Fetching basic info...
03-07 08:04 DEBUG  CommonBackend: original_exe=E:\softwares\Wibi Ubuntu Installer\wubi.exe
03-07 08:04 DEBUG  CommonBackend: platform=win32
03-07 08:04 DEBUG  CommonBackend: osname=nt
03-07 08:04 DEBUG  CommonBackend: language=en_GB
03-07 08:04 DEBUG  CommonBackend: encoding=cp1252
03-07 08:04 DEBUG  WindowsBackend: arch=amd64
03-07 08:04 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\data\isolist.ini
03-07 08:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-07 08:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-07 08:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-07 08:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-07 08:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-07 08:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-07 08:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-07 08:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-07 08:04 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-07 08:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-07 08:04 DEBUG  WindowsBackend: Fetching host info...
03-07 08:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-07 08:04 DEBUG  WindowsBackend: windows version=xp
03-07 08:04 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-07 08:04 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-07 08:04 DEBUG  WindowsBackend: windows_build=2600
03-07 08:04 DEBUG  WindowsBackend: gmt=5
03-07 08:04 DEBUG  WindowsBackend: country=GB
03-07 08:04 DEBUG  WindowsBackend: timezone=Europe/London
03-07 08:04 DEBUG  WindowsBackend: windows_username=Sharan
03-07 08:04 DEBUG  WindowsBackend: user_full_name=Sharan
03-07 08:04 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sharan
03-07 08:04 DEBUG  WindowsBackend: windows_language_code=1033
03-07 08:04 DEBUG  WindowsBackend: windows_language=English
03-07 08:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz
03-07 08:04 DEBUG  WindowsBackend: bootloader=xp
03-07 08:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8211.4375 mb free fat32)
03-07 08:04 DEBUG  WindowsBackend: drive=Drive(C: hd 8211.4375 mb free fat32)
03-07 08:04 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
03-07 08:04 DEBUG  WindowsBackend: drive=Drive(E: hd 30235.1757813 mb free ntfs)
03-07 08:04 DEBUG  WindowsBackend: drive=Drive(F: hd 6446.44921875 mb free ntfs)
03-07 08:04 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
03-07 08:04 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-07 08:04 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
03-07 08:04 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
03-07 08:04 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-07 08:04 DEBUG  WindowsBackend: keyboard_id=67699721
03-07 08:04 DEBUG  WindowsBackend: keyboard_layout=gb
03-07 08:04 DEBUG  WindowsBackend: keyboard_variant=
03-07 08:04 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
03-07 08:04 DEBUG  CommonBackend: locale=en_GB.UTF-8
03-07 08:04 DEBUG  WindowsBackend: total_memory_mb=2039.35546875
03-07 08:04 DEBUG  CommonBackend: Searching ISOs on USB devices
03-07 08:04 DEBUG  CommonBackend: Searching for local CDs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Ubuntu Netbook Remix CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Kubuntu Netbook CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook Remix CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 INFO   root: Already installed, running the uninstaller...
03-07 08:04 INFO   root: Running the uninstaller...
03-07 08:04 INFO   CommonBackend: This is the uninstaller running
03-07 08:04 DEBUG  WindowsFrontend: __init__...
03-07 08:04 DEBUG  WindowsFrontend: on_init...
03-07 08:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\translations, 

languages=['en_GB', 'en']
03-07 08:04 INFO   root: Received settings
03-07 08:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\translations, 

languages=['en_GB', 'en']
03-07 08:04 DEBUG  TaskList: # Running tasklist...
03-07 08:04 DEBUG  TaskList: ## Running Backup ISO...
03-07 08:04 DEBUG  TaskList: ## Finished Backup ISO
03-07 08:04 DEBUG  TaskList: ## Running Remove bootloader entry...
03-07 08:04 ERROR  WindowsBackend: Cannot find bcdedit
03-07 08:04 DEBUG  WindowsBackend: undo_bootini C:
03-07 08:04 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 8211.4375 mb free fat32)
03-07 08:04 DEBUG  WindowsBackend: undo_bootini E:
03-07 08:04 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 30235.1757813 mb free ntfs)
03-07 08:04 DEBUG  WindowsBackend: undo_bootini F:
03-07 08:04 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 6446.44921875 mb free ntfs)
03-07 08:04 DEBUG  TaskList: ## Finished Remove bootloader entry
03-07 08:04 DEBUG  TaskList: ## Running Remove target dir...
03-07 08:04 DEBUG  CommonBackend: Deleting E:\ubuntu
03-07 08:04 DEBUG  TaskList: ## Finished Remove target dir
03-07 08:04 DEBUG  TaskList: ## Running Remove registry key...
03-07 08:04 DEBUG  TaskList: ## Finished Remove registry key
03-07 08:04 DEBUG  TaskList: # Finished tasklist
03-07 08:04 INFO   root: Almost finished uninstalling
03-07 08:04 INFO   root: Finished uninstallation
03-07 08:04 DEBUG  CommonBackend: Fetching basic info...
03-07 08:04 DEBUG  CommonBackend: original_exe=E:\softwares\Wibi Ubuntu Installer\wubi.exe
03-07 08:04 DEBUG  CommonBackend: platform=win32
03-07 08:04 DEBUG  CommonBackend: osname=nt
03-07 08:04 DEBUG  WindowsBackend: arch=amd64
03-07 08:04 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\data\isolist.ini
03-07 08:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-07 08:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-07 08:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-07 08:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-07 08:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-07 08:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-07 08:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-07 08:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-07 08:04 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-07 08:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
03-07 08:04 DEBUG  WindowsBackend: Fetching host info...
03-07 08:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-07 08:04 DEBUG  WindowsBackend: windows version=xp
03-07 08:04 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-07 08:04 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-07 08:04 DEBUG  WindowsBackend: windows_build=2600
03-07 08:04 DEBUG  WindowsBackend: gmt=5
03-07 08:04 DEBUG  WindowsBackend: country=GB
03-07 08:04 DEBUG  WindowsBackend: timezone=Europe/London
03-07 08:04 DEBUG  WindowsBackend: windows_username=Sharan
03-07 08:04 DEBUG  WindowsBackend: user_full_name=Sharan
03-07 08:04 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Sharan
03-07 08:04 DEBUG  WindowsBackend: windows_language_code=1033
03-07 08:04 DEBUG  WindowsBackend: windows_language=English
03-07 08:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz
03-07 08:04 DEBUG  WindowsBackend: bootloader=xp
03-07 08:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8210.9375 mb free fat32)
03-07 08:04 DEBUG  WindowsBackend: drive=Drive(C: hd 8210.9375 mb free fat32)
03-07 08:04 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
03-07 08:04 DEBUG  WindowsBackend: drive=Drive(E: hd 30244.7382813 mb free ntfs)
03-07 08:04 DEBUG  WindowsBackend: drive=Drive(F: hd 6446.44921875 mb free ntfs)
03-07 08:04 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
03-07 08:04 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-07 08:04 DEBUG  WindowsBackend: uninstaller_path=None
03-07 08:04 DEBUG  WindowsBackend: previous_target_dir=None
03-07 08:04 DEBUG  WindowsBackend: previous_distro_name=None
03-07 08:04 DEBUG  WindowsBackend: keyboard_id=67699721
03-07 08:04 DEBUG  WindowsBackend: keyboard_layout=gb
03-07 08:04 DEBUG  WindowsBackend: keyboard_variant=
03-07 08:04 DEBUG  WindowsBackend: total_memory_mb=2039.35546875
03-07 08:04 DEBUG  CommonBackend: Searching ISOs on USB devices
03-07 08:04 DEBUG  CommonBackend: Searching for local CDs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Ubuntu Netbook Remix CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Kubuntu Netbook CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook Remix CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-07 08:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:04 INFO   root: Running the installer...
03-07 08:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\translations, 

languages=['en_GB', 'en']
03-07 08:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\translations, 

languages=['en_GB', 'en']
03-07 08:04 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=10000MB, distro_name=Ubuntu, language=en_GB, 

locale=en_GB.UTF-8, username=sharan
03-07 08:04 INFO   root: Received settings
03-07 08:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\translations, 

languages=['en_GB', 'en']
03-07 08:04 DEBUG  TaskList: # Running tasklist...
03-07 08:04 DEBUG  TaskList: ## Running select_target_dir...
03-07 08:04 INFO   WindowsBackend: Installing into E:\ubuntu
03-07 08:04 DEBUG  TaskList: ## Finished select_target_dir
03-07 08:04 DEBUG  TaskList: ## Running create_dir_structure...
03-07 08:04 DEBUG  CommonBackend: Creating dir E:\ubuntu
03-07 08:04 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
03-07 08:04 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
03-07 08:04 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
03-07 08:04 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
03-07 08:04 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
03-07 08:04 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
03-07 08:04 DEBUG  TaskList: ## Finished create_dir_structure
03-07 08:04 DEBUG  TaskList: ## Running uncompress_target_dir...
03-07 08:04 DEBUG  TaskList: ## Finished uncompress_target_dir
03-07 08:04 DEBUG  TaskList: ## Running create_uninstaller...
03-07 08:04 DEBUG  WindowsBackend: Copying uninstaller E:\softwares\Wibi Ubuntu Installer\wubi.exe -> 

E:\ubuntu\uninstall-wubi.exe
03-07 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

UninstallString E:\ubuntu\uninstall-wubi.exe
03-07 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

InstallationDir E:\ubuntu
03-07 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

DisplayName Ubuntu
03-07 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

DisplayIcon E:\ubuntu\Ubuntu.ico
03-07 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

DisplayVersion 9.10ubuntu1-rev160
03-07 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

Publisher Ubuntu
03-07 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-07 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-07 08:05 DEBUG  TaskList: ## Finished create_uninstaller
03-07 08:05 DEBUG  TaskList: ## Running copy_installation_files...
03-07 08:05 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\data\custom-installation -> 

E:\ubuntu\install\custom-installation
03-07 08:05 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\winboot -> E:\ubuntu\winboot
03-07 08:05 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\data\images\Ubuntu.ico -> 

E:\ubuntu\Ubuntu.ico
03-07 08:05 DEBUG  TaskList: ## Finished copy_installation_files
03-07 08:05 DEBUG  TaskList: ## Running get_iso...
03-07 08:05 DEBUG  CommonBackend: Searching for local CD
03-07 08:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp is a valid Ubuntu CD
03-07 08:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Sharan\LOCALS~1\Temp\pyl3411.tmp\casper\filesystem.squashfs
03-07 08:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-07 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-07 08:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-07 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-07 08:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-07 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-07 08:05 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-07 08:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-07 08:05 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-07 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-07 08:05 DEBUG  CommonBackend: Searching for local ISO
03-07 08:05 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-07 08:05 DEBUG  TaskList: New task get_metalink
03-07 08:05 DEBUG  TaskList: ### Running get_metalink...
03-07 08:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink) > 

E:\ubuntu\install
03-07 08:05 DEBUG  downloader: Download start filename=E:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, 

url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, 

length=26651, text=None
03-07 08:05 DEBUG  downloader: download finished (read 26651 bytes)
03-07 08:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > E:\ubuntu\install
03-07 08:05 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink, 

url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
03-07 08:05 DEBUG  downloader: download finished (read 562 bytes)
03-07 08:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > E:\ubuntu\install
03-07 08:05 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink.gpg, 

url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
03-07 08:05 DEBUG  downloader: download finished (read 189 bytes)
03-07 08:05 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-07 08:05 INFO   saplog: Checking block bindings..
03-07 08:05 INFO   saplog: Key verified successfully.
03-07 08:05 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

03-07 08:05 DEBUG  TaskList: ### Finished get_metalink
03-07 08:05 DEBUG  TaskList: New task download
03-07 08:05 DEBUG  TaskList: ### Running download...
03-07 08:05 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent) > 

E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
03-07 11:25 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (7, 'getaddrinfo failed')>

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
DownloadError: Problem connecting to tracker - <urlopen error (7, 'getaddrinfo failed')>


03-07 11:25 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (7, 'getaddrinfo failed')>

 in task download
03-07 11:25 DEBUG  TaskList: ### Finished download
03-07 11:25 ERROR  TaskList: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'
03-07 11:25 DEBUG  TaskList: # Cancelling tasklist
03-07 11:25 DEBUG  TaskList: # Finished tasklist
03-07 11:25 ERROR  root: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'E:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'

---

### Post by webtechquery on 2010-03-07
Hi.

I suggest you to install Ubuntu directly, and not through Wubi. I've a bad experience of using Wubi. It made me installed Ubuntu, but after a while, it start giving errors of updating etc. So, if you have a CD of Ubuntu, then I would suggest you to format one of the partitions of your hard drive, and try installing Ubuntu with the CD. For that, you first have to restart your PC and boot your PC with the CD. 
Dont get worried. It will be simple to install Ubuntu, by not affecting your Windows (if you install Ubuntu with care).

Thanks.

---

