---
title: "Need help installing ubuntu! First timer!"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by carega on 2011-02-27
Hello, I'm new to this forum and new to ubuntu as well. I have been trying all afternoon to install ubuntu through wubi but I always get the following message halfway through the installation:

"Permission denied

Para más información vea el archivo de registro:

C:\Users\Pedro Elí\AppData\Local\Temp\wubi-10.10-rev197.log"

In English: "For more información see the registry file"

So I went and took a look at the file and have no idea what went wrong. It's the first time I'm installing ubuntu and I do not know anyone who can help me so please be kind and guide me step by step as there are many things I do not know.

Here's the copy of the file:

02-27 15:59 INFO   root: === wubi 10.10 rev197 ===
02-27 15:59 DEBUG  root: Logfile is c:\users\pedroe~1\appdata\local\temp\wubi-10.10-rev197.log
02-27 15:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
02-27 15:59 DEBUG  CommonBackend: data_dir=C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp\data
02-27 15:59 DEBUG  WindowsBackend: 7z=C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp\bin\7z.exe
02-27 15:59 DEBUG  CommonBackend: Fetching basic info...
02-27 15:59 DEBUG  CommonBackend: original_exe=G:\wubi.exe
02-27 15:59 DEBUG  CommonBackend: platform=win32
02-27 15:59 DEBUG  CommonBackend: osname=nt
02-27 15:59 DEBUG  CommonBackend: language=es_SV
02-27 15:59 DEBUG  CommonBackend: encoding=cp1252
02-27 15:59 DEBUG  WindowsBackend: arch=amd64
02-27 15:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp\data\isolist.ini
02-27 15:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-27 15:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-27 15:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-27 15:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-27 15:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-27 15:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-27 15:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-27 15:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-27 15:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-27 15:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
02-27 15:59 DEBUG  WindowsBackend: Fetching host info...
02-27 15:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-27 15:59 DEBUG  WindowsBackend: windows version=vista
02-27 15:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
02-27 15:59 DEBUG  WindowsBackend: windows_sp=None
02-27 15:59 DEBUG  WindowsBackend: windows_build=7600
02-27 15:59 DEBUG  WindowsBackend: gmt=-6
02-27 15:59 DEBUG  WindowsBackend: country=SV
02-27 15:59 DEBUG  WindowsBackend: timezone=America/El_Salvador
02-27 15:59 DEBUG  WindowsBackend: windows_username=Pedro El
02-27 15:59 DEBUG  WindowsBackend: user_full_name=Pedro El
02-27 15:59 DEBUG  WindowsBackend: user_directory=C:\Users\Pedro El
02-27 15:59 DEBUG  WindowsBackend: windows_language_code=1034
02-27 15:59 DEBUG  WindowsBackend: windows_language=Spanish
02-27 15:59 DEBUG  WindowsBackend: processor_name=AMD Sempron(tm) SI-42
02-27 15:59 DEBUG  WindowsBackend: bootloader=vista
02-27 15:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 85618.9648438 mb free ntfs)
02-27 15:59 DEBUG  WindowsBackend: drive=Drive(C: hd 85618.9648438 mb free ntfs)
02-27 15:59 DEBUG  WindowsBackend: drive=Drive(D: hd 1746.7890625 mb free ntfs)
02-27 15:59 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-27 15:59 DEBUG  WindowsBackend: drive=Drive(G: removable 1874.03125 mb free fat)
02-27 15:59 DEBUG  WindowsBackend: uninstaller_path=None
02-27 15:59 DEBUG  WindowsBackend: previous_target_dir=None
02-27 15:59 DEBUG  WindowsBackend: previous_distro_name=None
02-27 15:59 DEBUG  WindowsBackend: keyboard_id=134890506
02-27 15:59 DEBUG  WindowsBackend: keyboard_layout=latam
02-27 15:59 DEBUG  WindowsBackend: keyboard_variant=
02-27 15:59 DEBUG  CommonBackend: python locale=('es_SV', 'cp1252')
02-27 15:59 DEBUG  CommonBackend: locale=es_SV.UTF-8
02-27 15:59 DEBUG  WindowsBackend: total_memory_mb=1789.83203125
02-27 15:59 DEBUG  CommonBackend: Searching ISOs on USB devices
02-27 15:59 DEBUG  CommonBackend: Searching for local CDs
02-27 15:59 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp is a valid Ubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp is a valid Ubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp is a valid Ubuntu Netbook CD
02-27 15:59 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp is a valid Kubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp is a valid Kubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp is a valid Kubuntu Netbook CD
02-27 15:59 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp is a valid Xubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp is a valid Xubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp is a valid Mythbuntu CD
02-27 15:59 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp is a valid Mythbuntu CD
02-27 15:59 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
02-27 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-27 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 15:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
02-27 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-27 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 15:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
02-27 15:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
02-27 15:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-27 15:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-27 15:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 15:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-27 15:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 15:59 INFO   root: Running the installer...
02-27 15:59 DEBUG  WindowsFrontend: __init__...
02-27 15:59 DEBUG  WindowsFrontend: on_init...
02-27 15:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp\translations, languages=['es_SV', 'es']
02-27 15:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pylE39B.tmp\translations, languages=['es_SV', 'es']
02-27 16:07 INFO   WindowsFrontend: Operation cancelled
02-27 16:07 DEBUG  WindowsFrontend: frontend.quit
02-27 16:07 DEBUG  WindowsFrontend: frontend.on_quit
02-27 16:07 DEBUG  root: application.on_quit
02-27 16:07 INFO   root: sys.exit
02-27 16:20 INFO   root: === wubi 10.10 rev197 ===
02-27 16:20 DEBUG  root: Logfile is c:\users\pedroe~1\appdata\local\temp\wubi-10.10-rev197.log
02-27 16:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Pedro El\xed\\Downloads\\wubi.exe"']
02-27 16:20 DEBUG  CommonBackend: data_dir=C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\data
02-27 16:20 DEBUG  WindowsBackend: 7z=C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\bin\7z.exe
02-27 16:20 DEBUG  CommonBackend: Fetching basic info...
02-27 16:20 DEBUG  CommonBackend: original_exe=C:\Users\Pedro Elí\Downloads\wubi.exe
02-27 16:20 DEBUG  CommonBackend: platform=win32
02-27 16:20 DEBUG  CommonBackend: osname=nt
02-27 16:20 DEBUG  CommonBackend: language=es_SV
02-27 16:20 DEBUG  CommonBackend: encoding=cp1252
02-27 16:20 DEBUG  WindowsBackend: arch=amd64
02-27 16:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\data\isolist.ini
02-27 16:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-27 16:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-27 16:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-27 16:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-27 16:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-27 16:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-27 16:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-27 16:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-27 16:20 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-27 16:20 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
02-27 16:20 DEBUG  WindowsBackend: Fetching host info...
02-27 16:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-27 16:20 DEBUG  WindowsBackend: windows version=vista
02-27 16:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
02-27 16:20 DEBUG  WindowsBackend: windows_sp=None
02-27 16:20 DEBUG  WindowsBackend: windows_build=7600
02-27 16:20 DEBUG  WindowsBackend: gmt=-6
02-27 16:20 DEBUG  WindowsBackend: country=SV
02-27 16:20 DEBUG  WindowsBackend: timezone=America/El_Salvador
02-27 16:20 DEBUG  WindowsBackend: windows_username=Pedro El
02-27 16:20 DEBUG  WindowsBackend: user_full_name=Pedro El
02-27 16:20 DEBUG  WindowsBackend: user_directory=C:\Users\Pedro El
02-27 16:20 DEBUG  WindowsBackend: windows_language_code=1034
02-27 16:20 DEBUG  WindowsBackend: windows_language=Spanish
02-27 16:20 DEBUG  WindowsBackend: processor_name=AMD Sempron(tm) SI-42
02-27 16:20 DEBUG  WindowsBackend: bootloader=vista
02-27 16:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 85551.4140625 mb free ntfs)
02-27 16:20 DEBUG  WindowsBackend: drive=Drive(C: hd 85551.4140625 mb free ntfs)
02-27 16:20 DEBUG  WindowsBackend: drive=Drive(D: hd 1746.7890625 mb free ntfs)
02-27 16:20 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-27 16:20 DEBUG  WindowsBackend: drive=Drive(G: removable 1874.03125 mb free fat)
02-27 16:20 DEBUG  WindowsBackend: uninstaller_path=None
02-27 16:20 DEBUG  WindowsBackend: previous_target_dir=None
02-27 16:20 DEBUG  WindowsBackend: previous_distro_name=None
02-27 16:20 DEBUG  WindowsBackend: keyboard_id=134890506
02-27 16:20 DEBUG  WindowsBackend: keyboard_layout=latam
02-27 16:20 DEBUG  WindowsBackend: keyboard_variant=
02-27 16:20 DEBUG  CommonBackend: python locale=('es_SV', 'cp1252')
02-27 16:20 DEBUG  CommonBackend: locale=es_SV.UTF-8
02-27 16:20 DEBUG  WindowsBackend: total_memory_mb=1789.83203125
02-27 16:20 DEBUG  CommonBackend: Searching ISOs on USB devices
02-27 16:20 DEBUG  CommonBackend: Searching for local CDs
02-27 16:20 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp is a valid Ubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp is a valid Ubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp is a valid Ubuntu Netbook CD
02-27 16:20 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp is a valid Kubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp is a valid Kubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp is a valid Kubuntu Netbook CD
02-27 16:20 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp is a valid Xubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp is a valid Xubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp is a valid Mythbuntu CD
02-27 16:20 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp is a valid Mythbuntu CD
02-27 16:20 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
02-27 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-27 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 16:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
02-27 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-27 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 16:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
02-27 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
02-27 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-27 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-27 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 16:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-27 16:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 16:20 INFO   root: Running the installer...
02-27 16:20 DEBUG  WindowsFrontend: __init__...
02-27 16:20 DEBUG  WindowsFrontend: on_init...
02-27 16:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\translations, languages=['es_SV', 'es']
02-27 16:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\translations, languages=['es_SV', 'es']
02-27 16:28 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=es_ES, locale=es_ES.UTF-8, username=pedroeli
02-27 16:28 INFO   root: Received settings
02-27 16:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\translations, languages=['es_ES', 'es']
02-27 16:28 DEBUG  TaskList: # Running tasklist...
02-27 16:28 DEBUG  TaskList: ## Running select_target_dir...
02-27 16:28 INFO   WindowsBackend: Installing into C:\ubuntu
02-27 16:28 DEBUG  TaskList: ## Finished select_target_dir
02-27 16:28 DEBUG  TaskList: ## Running create_dir_structure...
02-27 16:28 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-27 16:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-27 16:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-27 16:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-27 16:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-27 16:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-27 16:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-27 16:28 DEBUG  TaskList: ## Finished create_dir_structure
02-27 16:28 DEBUG  TaskList: ## Running uncompress_target_dir...
02-27 16:28 DEBUG  TaskList: ## Finished uncompress_target_dir
02-27 16:28 DEBUG  TaskList: ## Running create_uninstaller...
02-27 16:28 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Pedro Elí\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-27 16:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-27 16:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-27 16:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-27 16:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-27 16:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
02-27 16:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-27 16:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-27 16:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-27 16:28 DEBUG  TaskList: ## Finished create_uninstaller
02-27 16:28 DEBUG  TaskList: ## Running copy_installation_files...
02-27 16:28 DEBUG  WindowsBackend: Copying C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-27 16:28 DEBUG  WindowsBackend: Copying C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\winboot -> C:\ubuntu\winboot
02-27 16:28 DEBUG  WindowsBackend: Copying C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
02-27 16:28 DEBUG  TaskList: ## Finished copy_installation_files
02-27 16:28 DEBUG  TaskList: ## Running get_iso...
02-27 16:28 DEBUG  CommonBackend: Searching for local CD
02-27 16:28 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp is a valid Ubuntu CD
02-27 16:28 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl80C.tmp\casper\filesystem.squashfs
02-27 16:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 16:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 16:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 16:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 16:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 16:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 16:28 DEBUG  CommonBackend: Searching for local ISO
02-27 16:28 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
02-27 16:28 DEBUG  TaskList: New task get_metalink
02-27 16:28 DEBUG  TaskList: ### Running get_metalink...
02-27 16:28 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink) > C:\ubuntu\install
02-27 16:28 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink, basename=ubuntu-10.10-desktop-amd64.metalink, length=9135, text=None
02-27 16:28 DEBUG  downloader: download finished (read 9135 bytes)
02-27 16:28 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink](http://releases.ubuntu.com/10.10/MD5SUMS-metalink) > C:\ubuntu\install
02-27 16:28 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
02-27 16:28 DEBUG  downloader: download finished (read 488 bytes)
02-27 16:28 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
02-27 16:28 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
02-27 16:28 DEBUG  downloader: download finished (read 198 bytes)
02-27 16:28 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
02-27 16:28 INFO   saplog: Checking block bindings..
02-27 16:28 INFO   saplog: Key verified successfully.
02-27 16:28 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

02-27 16:28 DEBUG  TaskList: ### Finished get_metalink
02-27 16:28 DEBUG  TaskList: New task download
02-27 16:28 DEBUG  TaskList: ### Running download...
02-27 16:28 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
02-27 17:28 ERROR  TaskList: Traceback (most recent call last):
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


02-27 17:28 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
02-27 17:28 DEBUG  TaskList: ### Finished download
02-27 17:28 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
02-27 17:28 DEBUG  TaskList: # Cancelling tasklist
02-27 17:28 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
02-27 17:28 DEBUG  TaskList: # Finished tasklist
02-27 17:50 INFO   root: === wubi 10.10 rev197 ===
02-27 17:50 DEBUG  root: Logfile is c:\users\pedroe~1\appdata\local\temp\wubi-10.10-rev197.log
02-27 17:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
02-27 17:50 DEBUG  CommonBackend: data_dir=C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp\data
02-27 17:50 DEBUG  WindowsBackend: 7z=C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp\bin\7z.exe
02-27 17:50 DEBUG  CommonBackend: Fetching basic info...
02-27 17:50 DEBUG  CommonBackend: original_exe=G:\wubi.exe
02-27 17:50 DEBUG  CommonBackend: platform=win32
02-27 17:50 DEBUG  CommonBackend: osname=nt
02-27 17:50 DEBUG  CommonBackend: language=es_SV
02-27 17:50 DEBUG  CommonBackend: encoding=cp1252
02-27 17:50 DEBUG  WindowsBackend: arch=amd64
02-27 17:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp\data\isolist.ini
02-27 17:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-27 17:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-27 17:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-27 17:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-27 17:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-27 17:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-27 17:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-27 17:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-27 17:50 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-27 17:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
02-27 17:50 DEBUG  WindowsBackend: Fetching host info...
02-27 17:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-27 17:50 DEBUG  WindowsBackend: windows version=vista
02-27 17:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
02-27 17:50 DEBUG  WindowsBackend: windows_sp=None
02-27 17:50 DEBUG  WindowsBackend: windows_build=7600
02-27 17:50 DEBUG  WindowsBackend: gmt=-6
02-27 17:50 DEBUG  WindowsBackend: country=SV
02-27 17:50 DEBUG  WindowsBackend: timezone=America/El_Salvador
02-27 17:50 DEBUG  WindowsBackend: windows_username=Pedro El
02-27 17:50 DEBUG  WindowsBackend: user_full_name=Pedro El
02-27 17:50 DEBUG  WindowsBackend: user_directory=C:\Users\Pedro El
02-27 17:50 DEBUG  WindowsBackend: windows_language_code=1034
02-27 17:50 DEBUG  WindowsBackend: windows_language=Spanish
02-27 17:50 DEBUG  WindowsBackend: processor_name=AMD Sempron(tm) SI-42
02-27 17:50 DEBUG  WindowsBackend: bootloader=vista
02-27 17:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 85128.1210938 mb free ntfs)
02-27 17:50 DEBUG  WindowsBackend: drive=Drive(C: hd 85128.1210938 mb free ntfs)
02-27 17:50 DEBUG  WindowsBackend: drive=Drive(D: hd 1746.7890625 mb free ntfs)
02-27 17:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-27 17:50 DEBUG  WindowsBackend: drive=Drive(G: removable 1874.03125 mb free fat)
02-27 17:50 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-27 17:50 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-27 17:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-27 17:50 DEBUG  WindowsBackend: keyboard_id=134890506
02-27 17:50 DEBUG  WindowsBackend: keyboard_layout=latam
02-27 17:50 DEBUG  WindowsBackend: keyboard_variant=
02-27 17:50 DEBUG  CommonBackend: python locale=('es_SV', 'cp1252')
02-27 17:50 DEBUG  CommonBackend: locale=es_SV.UTF-8
02-27 17:50 DEBUG  WindowsBackend: total_memory_mb=1789.83203125
02-27 17:50 DEBUG  CommonBackend: Searching ISOs on USB devices
02-27 17:50 DEBUG  CommonBackend: Searching for local CDs
02-27 17:50 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp is a valid Ubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp is a valid Ubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp is a valid Ubuntu Netbook CD
02-27 17:50 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp is a valid Kubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp is a valid Kubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp is a valid Kubuntu Netbook CD
02-27 17:50 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp is a valid Xubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp is a valid Xubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp is a valid Mythbuntu CD
02-27 17:50 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp is a valid Mythbuntu CD
02-27 17:50 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
02-27 17:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-27 17:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 17:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 17:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
02-27 17:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-27 17:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 17:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 17:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
02-27 17:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
02-27 17:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-27 17:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-27 17:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 17:50 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-27 17:50 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 17:50 INFO   root: Already installed, running the uninstaller...
02-27 17:50 INFO   root: Running the uninstaller...
02-27 17:50 INFO   CommonBackend: This is the uninstaller running
02-27 17:50 DEBUG  WindowsFrontend: __init__...
02-27 17:50 DEBUG  WindowsFrontend: on_init...
02-27 17:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pyl10E4.tmp\translations, languages=['es_SV', 'es']
02-27 17:50 INFO   WindowsFrontend: Operation cancelled
02-27 17:50 DEBUG  WindowsFrontend: frontend.quit
02-27 17:50 DEBUG  WindowsFrontend: frontend.on_quit
02-27 17:50 DEBUG  root: application.on_quit
02-27 17:50 INFO   root: sys.exit
02-27 18:02 INFO   root: === wubi 10.10 rev197 ===
02-27 18:02 DEBUG  root: Logfile is c:\users\pedroe~1\appdata\local\temp\wubi-10.10-rev197.log
02-27 18:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Pedro El\xed\\Downloads\\wubi.exe"']
02-27 18:02 DEBUG  CommonBackend: data_dir=C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\data
02-27 18:02 DEBUG  WindowsBackend: 7z=C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\bin\7z.exe
02-27 18:02 DEBUG  CommonBackend: Fetching basic info...
02-27 18:02 DEBUG  CommonBackend: original_exe=C:\Users\Pedro Elí\Downloads\wubi.exe
02-27 18:02 DEBUG  CommonBackend: platform=win32
02-27 18:02 DEBUG  CommonBackend: osname=nt
02-27 18:02 DEBUG  CommonBackend: language=es_SV
02-27 18:02 DEBUG  CommonBackend: encoding=cp1252
02-27 18:02 DEBUG  WindowsBackend: arch=amd64
02-27 18:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\data\isolist.ini
02-27 18:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-27 18:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-27 18:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-27 18:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-27 18:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-27 18:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-27 18:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-27 18:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-27 18:02 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-27 18:02 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
02-27 18:02 DEBUG  WindowsBackend: Fetching host info...
02-27 18:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-27 18:02 DEBUG  WindowsBackend: windows version=vista
02-27 18:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
02-27 18:02 DEBUG  WindowsBackend: windows_sp=None
02-27 18:02 DEBUG  WindowsBackend: windows_build=7600
02-27 18:02 DEBUG  WindowsBackend: gmt=-6
02-27 18:02 DEBUG  WindowsBackend: country=SV
02-27 18:02 DEBUG  WindowsBackend: timezone=America/El_Salvador
02-27 18:02 DEBUG  WindowsBackend: windows_username=Pedro El
02-27 18:02 DEBUG  WindowsBackend: user_full_name=Pedro El
02-27 18:02 DEBUG  WindowsBackend: user_directory=C:\Users\Pedro El
02-27 18:02 DEBUG  WindowsBackend: windows_language_code=1034
02-27 18:02 DEBUG  WindowsBackend: windows_language=Spanish
02-27 18:02 DEBUG  WindowsBackend: processor_name=AMD Sempron(tm) SI-42
02-27 18:02 DEBUG  WindowsBackend: bootloader=vista
02-27 18:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 85238.9609375 mb free ntfs)
02-27 18:02 DEBUG  WindowsBackend: drive=Drive(C: hd 85238.9609375 mb free ntfs)
02-27 18:02 DEBUG  WindowsBackend: drive=Drive(D: hd 1746.7890625 mb free ntfs)
02-27 18:02 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-27 18:02 DEBUG  WindowsBackend: drive=Drive(G: removable 1874.03125 mb free fat)
02-27 18:02 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-27 18:02 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-27 18:02 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-27 18:02 DEBUG  WindowsBackend: keyboard_id=134890506
02-27 18:02 DEBUG  WindowsBackend: keyboard_layout=latam
02-27 18:02 DEBUG  WindowsBackend: keyboard_variant=
02-27 18:02 DEBUG  CommonBackend: python locale=('es_SV', 'cp1252')
02-27 18:02 DEBUG  CommonBackend: locale=es_SV.UTF-8
02-27 18:02 DEBUG  WindowsBackend: total_memory_mb=1789.83203125
02-27 18:02 DEBUG  CommonBackend: Searching ISOs on USB devices
02-27 18:02 DEBUG  CommonBackend: Searching for local CDs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Ubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Kubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 INFO   root: Already installed, running the uninstaller...
02-27 18:02 INFO   root: Running the uninstaller...
02-27 18:02 INFO   CommonBackend: This is the uninstaller running
02-27 18:02 DEBUG  WindowsFrontend: __init__...
02-27 18:02 DEBUG  WindowsFrontend: on_init...
02-27 18:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\translations, languages=['es_SV', 'es']
02-27 18:02 INFO   root: Received settings
02-27 18:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\translations, languages=['es_SV', 'es']
02-27 18:02 DEBUG  TaskList: # Running tasklist...
02-27 18:02 DEBUG  TaskList: ## Running Hacer una copia de la ISO...
02-27 18:02 DEBUG  TaskList: ## Finished Hacer una copia de la ISO
02-27 18:02 DEBUG  TaskList: ## Running Quitar entrada del cargador de arranque...
02-27 18:02 DEBUG  WindowsBackend: Could not find bcd id
02-27 18:02 DEBUG  WindowsBackend: undo_bootini C:
02-27 18:02 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 85238.9609375 mb free ntfs)
02-27 18:02 DEBUG  WindowsBackend: undo_bootini D:
02-27 18:02 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1746.7890625 mb free ntfs)
02-27 18:02 DEBUG  WindowsBackend: undo_bootini G:
02-27 18:02 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 1874.03125 mb free fat)
02-27 18:02 DEBUG  TaskList: ## Finished Quitar entrada del cargador de arranque
02-27 18:02 DEBUG  TaskList: ## Running Borrar el directorio de destino...
02-27 18:02 DEBUG  CommonBackend: Deleting C:\ubuntu
02-27 18:02 DEBUG  TaskList: ## Finished Borrar el directorio de destino
02-27 18:02 DEBUG  TaskList: ## Running Borrar clave del registro...
02-27 18:02 DEBUG  TaskList: ## Finished Borrar clave del registro
02-27 18:02 DEBUG  TaskList: # Finished tasklist
02-27 18:02 INFO   root: Almost finished uninstalling
02-27 18:02 INFO   root: Finished uninstallation
02-27 18:02 DEBUG  CommonBackend: Fetching basic info...
02-27 18:02 DEBUG  CommonBackend: original_exe=C:\Users\Pedro Elí\Downloads\wubi.exe
02-27 18:02 DEBUG  CommonBackend: platform=win32
02-27 18:02 DEBUG  CommonBackend: osname=nt
02-27 18:02 DEBUG  WindowsBackend: arch=amd64
02-27 18:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\data\isolist.ini
02-27 18:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-27 18:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-27 18:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-27 18:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-27 18:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-27 18:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-27 18:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-27 18:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-27 18:02 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-27 18:02 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
02-27 18:02 DEBUG  WindowsBackend: Fetching host info...
02-27 18:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-27 18:02 DEBUG  WindowsBackend: windows version=vista
02-27 18:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
02-27 18:02 DEBUG  WindowsBackend: windows_sp=None
02-27 18:02 DEBUG  WindowsBackend: windows_build=7600
02-27 18:02 DEBUG  WindowsBackend: gmt=-6
02-27 18:02 DEBUG  WindowsBackend: country=SV
02-27 18:02 DEBUG  WindowsBackend: timezone=America/El_Salvador
02-27 18:02 DEBUG  WindowsBackend: windows_username=Pedro El
02-27 18:02 DEBUG  WindowsBackend: user_full_name=Pedro El
02-27 18:02 DEBUG  WindowsBackend: user_directory=C:\Users\Pedro El
02-27 18:02 DEBUG  WindowsBackend: windows_language_code=1034
02-27 18:02 DEBUG  WindowsBackend: windows_language=Spanish
02-27 18:02 DEBUG  WindowsBackend: processor_name=AMD Sempron(tm) SI-42
02-27 18:02 DEBUG  WindowsBackend: bootloader=vista
02-27 18:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 85606.3632813 mb free ntfs)
02-27 18:02 DEBUG  WindowsBackend: drive=Drive(C: hd 85606.3632813 mb free ntfs)
02-27 18:02 DEBUG  WindowsBackend: drive=Drive(D: hd 1746.7890625 mb free ntfs)
02-27 18:02 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-27 18:02 DEBUG  WindowsBackend: drive=Drive(G: removable 1874.03125 mb free fat)
02-27 18:02 DEBUG  WindowsBackend: uninstaller_path=None
02-27 18:02 DEBUG  WindowsBackend: previous_target_dir=None
02-27 18:02 DEBUG  WindowsBackend: previous_distro_name=None
02-27 18:02 DEBUG  WindowsBackend: keyboard_id=134890506
02-27 18:02 DEBUG  WindowsBackend: keyboard_layout=latam
02-27 18:02 DEBUG  WindowsBackend: keyboard_variant=
02-27 18:02 DEBUG  WindowsBackend: total_memory_mb=1789.83203125
02-27 18:02 DEBUG  CommonBackend: Searching ISOs on USB devices
02-27 18:02 DEBUG  CommonBackend: Searching for local CDs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Ubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Kubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-27 18:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:02 INFO   root: Running the installer...
02-27 18:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\translations, languages=['es_SV', 'es']
02-27 18:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\translations, languages=['es_SV', 'es']
02-27 18:03 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=es_ES, locale=es_ES.UTF-8, username=pedroel
02-27 18:03 INFO   root: Received settings
02-27 18:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\translations, languages=['es_ES', 'es']
02-27 18:03 DEBUG  TaskList: # Running tasklist...
02-27 18:03 DEBUG  TaskList: ## Running select_target_dir...
02-27 18:03 INFO   WindowsBackend: Installing into C:\ubuntu
02-27 18:03 DEBUG  TaskList: ## Finished select_target_dir
02-27 18:03 DEBUG  TaskList: ## Running create_dir_structure...
02-27 18:03 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-27 18:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-27 18:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-27 18:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-27 18:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-27 18:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-27 18:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-27 18:03 DEBUG  TaskList: ## Finished create_dir_structure
02-27 18:03 DEBUG  TaskList: ## Running uncompress_target_dir...
02-27 18:03 DEBUG  TaskList: ## Finished uncompress_target_dir
02-27 18:03 DEBUG  TaskList: ## Running create_uninstaller...
02-27 18:03 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Pedro Elí\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-27 18:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-27 18:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-27 18:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-27 18:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-27 18:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
02-27 18:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-27 18:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-27 18:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-27 18:03 DEBUG  TaskList: ## Finished create_uninstaller
02-27 18:03 DEBUG  TaskList: ## Running copy_installation_files...
02-27 18:03 DEBUG  WindowsBackend: Copying C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-27 18:03 DEBUG  WindowsBackend: Copying C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\winboot -> C:\ubuntu\winboot
02-27 18:03 DEBUG  WindowsBackend: Copying C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
02-27 18:03 DEBUG  TaskList: ## Finished copy_installation_files
02-27 18:03 DEBUG  TaskList: ## Running get_iso...
02-27 18:03 DEBUG  CommonBackend: Searching for local CD
02-27 18:03 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp is a valid Ubuntu CD
02-27 18:03 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylC956.tmp\casper\filesystem.squashfs
02-27 18:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 18:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 18:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 18:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 18:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 18:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 18:03 DEBUG  CommonBackend: Searching for local ISO
02-27 18:03 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
02-27 18:03 DEBUG  TaskList: New task get_metalink
02-27 18:03 DEBUG  TaskList: ### Running get_metalink...
02-27 18:03 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink) > C:\ubuntu\install
02-27 18:03 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink, basename=ubuntu-10.10-desktop-amd64.metalink, length=9135, text=None
02-27 18:03 DEBUG  downloader: download finished (read 9135 bytes)
02-27 18:03 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink](http://releases.ubuntu.com/10.10/MD5SUMS-metalink) > C:\ubuntu\install
02-27 18:03 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
02-27 18:03 DEBUG  downloader: download finished (read 488 bytes)
02-27 18:03 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
02-27 18:03 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
02-27 18:03 DEBUG  downloader: download finished (read 198 bytes)
02-27 18:03 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
02-27 18:03 INFO   saplog: Checking block bindings..
02-27 18:03 INFO   saplog: Key verified successfully.
02-27 18:03 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

02-27 18:03 DEBUG  TaskList: ### Finished get_metalink
02-27 18:03 DEBUG  TaskList: New task download
02-27 18:03 DEBUG  TaskList: ### Running download...
02-27 18:03 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
02-27 19:03 ERROR  TaskList: Traceback (most recent call last):
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


02-27 19:03 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
02-27 19:03 DEBUG  TaskList: ### Finished download
02-27 19:03 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
02-27 19:03 DEBUG  TaskList: # Cancelling tasklist
02-27 19:03 DEBUG  TaskList: # Finished tasklist
02-27 19:03 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
02-27 19:17 INFO   root: === wubi 10.10 rev197 ===
02-27 19:17 DEBUG  root: Logfile is c:\users\pedroe~1\appdata\local\temp\wubi-10.10-rev197.log
02-27 19:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Pedro El\xed\\Downloads\\wubi.exe"']
02-27 19:17 DEBUG  CommonBackend: data_dir=C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\data
02-27 19:17 DEBUG  WindowsBackend: 7z=C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\bin\7z.exe
02-27 19:17 DEBUG  CommonBackend: Fetching basic info...
02-27 19:17 DEBUG  CommonBackend: original_exe=C:\Users\Pedro Elí\Downloads\wubi.exe
02-27 19:17 DEBUG  CommonBackend: platform=win32
02-27 19:17 DEBUG  CommonBackend: osname=nt
02-27 19:17 DEBUG  CommonBackend: language=es_SV
02-27 19:17 DEBUG  CommonBackend: encoding=cp1252
02-27 19:17 DEBUG  WindowsBackend: arch=amd64
02-27 19:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\data\isolist.ini
02-27 19:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-27 19:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-27 19:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-27 19:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-27 19:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-27 19:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-27 19:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-27 19:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-27 19:17 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-27 19:17 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
02-27 19:17 DEBUG  WindowsBackend: Fetching host info...
02-27 19:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-27 19:17 DEBUG  WindowsBackend: windows version=vista
02-27 19:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
02-27 19:17 DEBUG  WindowsBackend: windows_sp=None
02-27 19:17 DEBUG  WindowsBackend: windows_build=7600
02-27 19:17 DEBUG  WindowsBackend: gmt=-6
02-27 19:17 DEBUG  WindowsBackend: country=SV
02-27 19:17 DEBUG  WindowsBackend: timezone=America/El_Salvador
02-27 19:17 DEBUG  WindowsBackend: windows_username=Pedro El
02-27 19:17 DEBUG  WindowsBackend: user_full_name=Pedro El
02-27 19:17 DEBUG  WindowsBackend: user_directory=C:\Users\Pedro El
02-27 19:17 DEBUG  WindowsBackend: windows_language_code=1034
02-27 19:17 DEBUG  WindowsBackend: windows_language=Spanish
02-27 19:17 DEBUG  WindowsBackend: processor_name=AMD Sempron(tm) SI-42
02-27 19:17 DEBUG  WindowsBackend: bootloader=vista
02-27 19:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 85248.4414063 mb free ntfs)
02-27 19:17 DEBUG  WindowsBackend: drive=Drive(C: hd 85248.4414063 mb free ntfs)
02-27 19:17 DEBUG  WindowsBackend: drive=Drive(D: hd 1746.7890625 mb free ntfs)
02-27 19:17 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-27 19:17 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-27 19:17 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-27 19:17 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-27 19:17 DEBUG  WindowsBackend: keyboard_id=134890506
02-27 19:17 DEBUG  WindowsBackend: keyboard_layout=latam
02-27 19:17 DEBUG  WindowsBackend: keyboard_variant=
02-27 19:17 DEBUG  CommonBackend: python locale=('es_SV', 'cp1252')
02-27 19:17 DEBUG  CommonBackend: locale=es_SV.UTF-8
02-27 19:17 DEBUG  WindowsBackend: total_memory_mb=1789.83203125
02-27 19:17 DEBUG  CommonBackend: Searching ISOs on USB devices
02-27 19:17 DEBUG  CommonBackend: Searching for local CDs
02-27 19:17 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Ubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Ubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Ubuntu Netbook CD
02-27 19:17 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Kubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Kubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Kubuntu Netbook CD
02-27 19:17 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Xubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Xubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Mythbuntu CD
02-27 19:17 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Mythbuntu CD
02-27 19:17 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
02-27 19:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-27 19:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 19:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 19:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
02-27 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-27 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 19:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:17 INFO   root: Already installed, running the uninstaller...
02-27 19:17 INFO   root: Running the uninstaller...
02-27 19:17 INFO   CommonBackend: This is the uninstaller running
02-27 19:17 DEBUG  WindowsFrontend: __init__...
02-27 19:17 DEBUG  WindowsFrontend: on_init...
02-27 19:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\translations, languages=['es_SV', 'es']
02-27 19:17 INFO   root: Received settings
02-27 19:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\translations, languages=['es_SV', 'es']
02-27 19:17 DEBUG  TaskList: # Running tasklist...
02-27 19:17 DEBUG  TaskList: ## Running Hacer una copia de la ISO...
02-27 19:17 DEBUG  TaskList: ## Finished Hacer una copia de la ISO
02-27 19:17 DEBUG  TaskList: ## Running Quitar entrada del cargador de arranque...
02-27 19:17 DEBUG  WindowsBackend: Could not find bcd id
02-27 19:17 DEBUG  WindowsBackend: undo_bootini C:
02-27 19:17 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 85248.4414063 mb free ntfs)
02-27 19:17 DEBUG  WindowsBackend: undo_bootini D:
02-27 19:17 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1746.7890625 mb free ntfs)
02-27 19:17 DEBUG  TaskList: ## Finished Quitar entrada del cargador de arranque
02-27 19:17 DEBUG  TaskList: ## Running Borrar el directorio de destino...
02-27 19:17 DEBUG  CommonBackend: Deleting C:\ubuntu
02-27 19:18 DEBUG  TaskList: ## Finished Borrar el directorio de destino
02-27 19:18 DEBUG  TaskList: ## Running Borrar clave del registro...
02-27 19:18 DEBUG  TaskList: ## Finished Borrar clave del registro
02-27 19:18 DEBUG  TaskList: # Finished tasklist
02-27 19:18 INFO   root: Almost finished uninstalling
02-27 19:18 INFO   root: Finished uninstallation
02-27 19:18 DEBUG  CommonBackend: Fetching basic info...
02-27 19:18 DEBUG  CommonBackend: original_exe=C:\Users\Pedro Elí\Downloads\wubi.exe
02-27 19:18 DEBUG  CommonBackend: platform=win32
02-27 19:18 DEBUG  CommonBackend: osname=nt
02-27 19:18 DEBUG  WindowsBackend: arch=amd64
02-27 19:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\data\isolist.ini
02-27 19:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-27 19:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-27 19:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-27 19:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-27 19:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-27 19:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-27 19:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-27 19:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-27 19:18 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-27 19:18 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
02-27 19:18 DEBUG  WindowsBackend: Fetching host info...
02-27 19:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-27 19:18 DEBUG  WindowsBackend: windows version=vista
02-27 19:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
02-27 19:18 DEBUG  WindowsBackend: windows_sp=None
02-27 19:18 DEBUG  WindowsBackend: windows_build=7600
02-27 19:18 DEBUG  WindowsBackend: gmt=-6
02-27 19:18 DEBUG  WindowsBackend: country=SV
02-27 19:18 DEBUG  WindowsBackend: timezone=America/El_Salvador
02-27 19:18 DEBUG  WindowsBackend: windows_username=Pedro El
02-27 19:18 DEBUG  WindowsBackend: user_full_name=Pedro El
02-27 19:18 DEBUG  WindowsBackend: user_directory=C:\Users\Pedro El
02-27 19:18 DEBUG  WindowsBackend: windows_language_code=1034
02-27 19:18 DEBUG  WindowsBackend: windows_language=Spanish
02-27 19:18 DEBUG  WindowsBackend: processor_name=AMD Sempron(tm) SI-42
02-27 19:18 DEBUG  WindowsBackend: bootloader=vista
02-27 19:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 85608.515625 mb free ntfs)
02-27 19:18 DEBUG  WindowsBackend: drive=Drive(C: hd 85608.4921875 mb free ntfs)
02-27 19:18 DEBUG  WindowsBackend: drive=Drive(D: hd 1746.7890625 mb free ntfs)
02-27 19:18 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-27 19:18 DEBUG  WindowsBackend: uninstaller_path=None
02-27 19:18 DEBUG  WindowsBackend: previous_target_dir=None
02-27 19:18 DEBUG  WindowsBackend: previous_distro_name=None
02-27 19:18 DEBUG  WindowsBackend: keyboard_id=134890506
02-27 19:18 DEBUG  WindowsBackend: keyboard_layout=latam
02-27 19:18 DEBUG  WindowsBackend: keyboard_variant=
02-27 19:18 DEBUG  WindowsBackend: total_memory_mb=1789.83203125
02-27 19:18 DEBUG  CommonBackend: Searching ISOs on USB devices
02-27 19:18 DEBUG  CommonBackend: Searching for local CDs
02-27 19:18 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Ubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Ubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Ubuntu Netbook CD
02-27 19:18 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Kubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Kubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Kubuntu Netbook CD
02-27 19:18 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Xubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Xubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Mythbuntu CD
02-27 19:18 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Mythbuntu CD
02-27 19:18 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
02-27 19:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-27 19:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 19:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 19:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
02-27 19:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-27 19:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 19:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 19:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:18 INFO   root: Running the installer...
02-27 19:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\translations, languages=['es_SV', 'es']
02-27 19:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\translations, languages=['es_SV', 'es']
02-27 19:18 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=es_ES, locale=es_ES.UTF-8, username=carega
02-27 19:18 INFO   root: Received settings
02-27 19:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\translations, languages=['es_ES', 'es']
02-27 19:18 DEBUG  TaskList: # Running tasklist...
02-27 19:18 DEBUG  TaskList: ## Running select_target_dir...
02-27 19:18 INFO   WindowsBackend: Installing into C:\ubuntu
02-27 19:18 DEBUG  TaskList: ## Finished select_target_dir
02-27 19:18 DEBUG  TaskList: ## Running create_dir_structure...
02-27 19:18 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-27 19:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-27 19:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-27 19:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-27 19:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-27 19:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-27 19:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-27 19:18 DEBUG  TaskList: ## Finished create_dir_structure
02-27 19:18 DEBUG  TaskList: ## Running uncompress_target_dir...
02-27 19:18 DEBUG  TaskList: ## Finished uncompress_target_dir
02-27 19:18 DEBUG  TaskList: ## Running create_uninstaller...
02-27 19:18 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Pedro Elí\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-27 19:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-27 19:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-27 19:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-27 19:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-27 19:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
02-27 19:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-27 19:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-27 19:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-27 19:18 DEBUG  TaskList: ## Finished create_uninstaller
02-27 19:18 DEBUG  TaskList: ## Running copy_installation_files...
02-27 19:18 DEBUG  WindowsBackend: Copying C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-27 19:18 DEBUG  WindowsBackend: Copying C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\winboot -> C:\ubuntu\winboot
02-27 19:18 DEBUG  WindowsBackend: Copying C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
02-27 19:18 DEBUG  TaskList: ## Finished copy_installation_files
02-27 19:18 DEBUG  TaskList: ## Running get_iso...
02-27 19:18 DEBUG  CommonBackend: Searching for local CD
02-27 19:18 DEBUG  Distro:   checking whether C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp is a valid Ubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain C:\Users\PEDROE~1\AppData\Local\Temp\pylF6BE.tmp\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 19:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 19:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 19:18 DEBUG  CommonBackend: Searching for local ISO
02-27 19:18 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
02-27 19:18 DEBUG  TaskList: New task get_metalink
02-27 19:18 DEBUG  TaskList: ### Running get_metalink...
02-27 19:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink) > C:\ubuntu\install
02-27 19:18 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink, basename=ubuntu-10.10-desktop-amd64.metalink, length=9135, text=None
02-27 19:18 DEBUG  downloader: download finished (read 9135 bytes)
02-27 19:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink](http://releases.ubuntu.com/10.10/MD5SUMS-metalink) > C:\ubuntu\install
02-27 19:18 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
02-27 19:18 DEBUG  downloader: download finished (read 488 bytes)
02-27 19:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
02-27 19:18 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
02-27 19:18 DEBUG  downloader: download finished (read 198 bytes)
02-27 19:18 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
02-27 19:18 INFO   saplog: Checking block bindings..
02-27 19:18 INFO   saplog: Key verified successfully.
02-27 19:18 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

02-27 19:18 DEBUG  TaskList: ### Finished get_metalink
02-27 19:18 DEBUG  TaskList: New task download
02-27 19:18 DEBUG  TaskList: ### Running download...
02-27 19:18 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
02-27 20:18 ERROR  TaskList: Traceback (most recent call last):
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


02-27 20:18 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
02-27 20:18 DEBUG  TaskList: ### Finished download
02-27 20:18 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
02-27 20:18 DEBUG  TaskList: # Cancelling tasklist
02-27 20:18 DEBUG  TaskList: # Finished tasklist
02-27 20:18 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'

Help! I don't want to use windows anymore but installing ubuntu is harder than it seems!

Thank you!

---

### Post by mörgæs on 2011-02-28
Hi, welcome to the fora. 

If you want to quit Windows completely Wubi is not the way to go. The safest and easiest is to install only Ubuntu on the machine.

However, if you want to keep Windows and use Wubi, a good beginning is reading this thread:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by Rubi1200 on 2011-02-28
Try putting the wubi.exe and downloaded ISO image in the same folder and then run wubi.exe again.

Oh, and welcome to the forums :-)

---

### Post by yusof125 on 2011-02-28
Make it easy!.
1. Must Have the Bootable CD or DVD within Ubuntu-10.10-desktop-i386
2. Mount that DVD or CD into Drive.
3. In your windows (XP or Vista or 7), try to run wubi.exe
4. Please, choose Install Ubuntu Beside Windows or Install Ubuntu Within Windows or something like that. (Sorry, :P I'M forgot the button name). This mean, you install Ubuntu without format or destroy your windows, so you can choose later, to login into windows or Ubuntu at boot screen.
5. Just follow the screen instructions, choose the recommended choice, fill in the blank with your details, try to choose a simple password and one character only, like: q or z or 1 or anything but one. [ignore the weak password warning]- I've found someone get annoying with his own password.
6. When installation is done, you must quickly choose Ubuntu at boot time, use your down arrow at your keyboard. The default boot is your Windows.
7. Let it working till next restart.
8. Always remember to choose Ubuntu at booting time.
9. Ho ho ho...you have done!.
Note: 
. Please check for update to keep your Ubuntu OS up-to-date.
. Download the codec before you play any audio or video (mp3,avi,dat,ect.) 
. Choose the preferred software, try or explore it first, uninstall it when you're not used or get annoying with it.

End For Now!, Keep Up-To-Date, Any Feedback for this note?
by yusof125

---

### Post by Mark Phelps on 2011-02-28
Despite what others have told you, choosing the Install alongside option and allowing the Ubuntu installer to shrink the Vista OS partition is asking for trouble.  In some cases, that has corrupted the Vista install and rendered it unbootable.

Better to use the Vista Disk Management utility and shrink the Vista partition to make room.

Also, you're trying to install the 64-bit version.  Are you sure your PC supports a 64-bit version?

---

### Post by bcbc on 2011-02-28
From the log file... you are running Wubi from G:, a removable USB key? It doesn't find a valid Ubuntu image on G: (this normally fails anyway if the partition is > 800MB). So then it tries to download the Ubuntu image using a bittorrent client. This is being blocked, perhaps by your firewall - in which case you have to give pyrun.exe access permission. 

As Rubi1200 said, downloading the desktop CD image yourself and placing wubi.exe in the same folder, is the easiest way to install.

Wubi is great to try out Ubuntu safely, just lock the grub-* packages as described in the Wubi megathread linked to above. And make sure you keep important data backed up separately.

If you intend to use it permanently, then it is best to do a proper dual boot install. Or of course you can replace Windows if you wish.

---

### Post by carega on 2011-02-28
Ok, so I figured out the problem was the ISO (though i don't know what an ISO is...) Wubi was downloading and 64-bit ISO and my system supports 32-bit. So problem solved.

I have ANOTHER problem though. And this is a big one. On another computer I tried ubuntu through a cd (I did the whole installing ubuntu from dvd thing on ubuntu.com) and everything was working fine. Then I decided to reboot the machine and work on windows vista. After I rebooted the computer froze on the lenovo screen. I shut it down and after trying to boot again the screen won't even light itself.

I tried with the ubuntu dvd again but nothing's starting, the same with vista cds. The computer just turns on but doesn't do absolutely anything else. Any help here, please?

I have a lenovo 3000 n200, does that help?

---

### Post by bcbc on 2011-02-28
I don't think that's correct. You have a 64-bit chip. (You can run either 64-bit or 32-bit Ubuntu).
> 02-27 16:20 DEBUG WindowsBackend: arch=amd64
02-27 16:20 DEBUG WindowsBackend: processor_name=AMD Sempron(tm) SI-42

Regarding the other computer... no idea. But it's unusual that a computer will boot from a CD/DVD one time, but then suddenly stop the next time. Make sure you are getting the BIOS to boot the DVD directly.
If you don't even see the BIOS splash you might want to unplug it, remove the battery and leave it for a few minutes.
Sometimes when you boot windows, some software can overwrite parts of the boot track used by Grub2. So if it's a regular dual boot, that could be the issue. Boot from an Ubuntu live CD and reinstall Grub2 to fix. [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by carega on 2011-02-28
If I have a 64-chip, how come my windows 7 version is 32-bit? Then how come i wouldn't work with that iso and it did when i downloaded the 32-bit one? It's strange. Or was it a problem with the file download and not the installation?

If I support 64-bit, is it better for me to install that one? Or will I have more problems later?

About the other computer, unplugging the battery worked just fine. It booted as if nothing ever happened.

Thanks!

---

### Post by geoffmcc on 2011-02-28
> If I have a 64-chip, how come my windows 7 version is 32-bit?

OEM wanted to save some money.

---

### Post by bcbc on 2011-02-28
Yeah... many 64-bit computers came with 32-bit OSes. Some software wasn't available or stable with 64-bit, so I guess it was a safer option to go with a 32-bit OS (or at least it used to be).
Or, yes, perhaps to save money :)

Regarding your wubi problem, the problem was with Wubi's bittorrent client getting access to your firewall. It had nothing to do with the fact that it was a 64-bit Ubuntu ISO (which was never even downloaded).

Anyway - glad you got the other laptop fixed - and I'm sure you'll be fine with 32-bit Ubuntu - although since you've just installed you can reinstall with 64-bit if you want. I have no idea which is better as I've never run a 64-bit OS.

---

### Post by geoffmcc on 2011-03-01
> **bcbc said:**
> 
Anyway - glad you got the other laptop fixed - and I'm sure you'll be fine with 32-bit Ubuntu - although since you've just installed you can reinstall with 64-bit if you want. I have no idea which is better as I've never run a 64-bit OS.


Most common problem with 64bit Ubuntu is flash. But i believe if you install browser in a 32bit chroot it would work. 

Just be sure to install ia32-libs for any 32 bit programs you want to run, or again, run them in a 32bit chroot enviroment

[http://ubuntuforums.org/showthread.php?t=24575]("http://ubuntuforums.org/showthread.php?t=24575")

---

### Post by carega on 2011-03-01
Ok, everything has turned out just fine. I burned a dvd and installed linux that way, i find it better than wubi. Thanks for your help and the fast responses!

---

