---
title: "Installing Ubuntu with Windows 8"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by Exp3rt on 2013-02-07
Hello all,
I wanna install Ubuntu with my Windows 8, but there is a few error. 
[[IMG]http://download.overclockproject.net/images/hd4mdrwt0jwlwirypof.jpg[/IMG]]("http://download.overclockproject.net/")
 
The error log:
```

02-07 14:08 INFO   root: === wubi 12.04 rev269 ===
02-07 14:08 DEBUG  root: Logfile is c:\users\expert\appdata\local\temp\wubi-12.04-rev269.log
02-07 14:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
02-07 14:08 DEBUG  CommonBackend: data_dir=C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\data
02-07 14:08 DEBUG  WindowsBackend: 7z=C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\bin\7z.exe
02-07 14:08 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-07 14:08 DEBUG  CommonBackend: Fetching basic info...
02-07 14:08 DEBUG  CommonBackend: original_exe=G:\wubi.exe
02-07 14:08 DEBUG  CommonBackend: platform=win32
02-07 14:08 DEBUG  CommonBackend: osname=nt
02-07 14:08 DEBUG  CommonBackend: language=en_US
02-07 14:08 DEBUG  CommonBackend: encoding=cp1252
02-07 14:08 DEBUG  WindowsBackend: arch=amd64
02-07 14:08 DEBUG  CommonBackend: Parsing isolist=C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\data\isolist.ini
02-07 14:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-07 14:08 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
02-07 14:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-07 14:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-07 14:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-07 14:08 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
02-07 14:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-07 14:08 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
02-07 14:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-07 14:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-07 14:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-07 14:08 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
02-07 14:08 DEBUG  WindowsBackend: Fetching host info...
02-07 14:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-07 14:08 DEBUG  WindowsBackend: windows version=vista
02-07 14:08 DEBUG  WindowsBackend: windows_version2=Windows 8 Enterprise N
02-07 14:08 DEBUG  WindowsBackend: windows_sp=None
02-07 14:08 DEBUG  WindowsBackend: windows_build=9200
02-07 14:08 DEBUG  WindowsBackend: gmt=4
02-07 14:08 DEBUG  WindowsBackend: country=US
02-07 14:08 DEBUG  WindowsBackend: timezone=America/New_York
02-07 14:08 DEBUG  WindowsBackend: windows_username=Expert
02-07 14:08 DEBUG  WindowsBackend: user_full_name=Expert
02-07 14:08 DEBUG  WindowsBackend: user_directory=C:\Users\Expert
02-07 14:08 DEBUG  WindowsBackend: windows_language_code=1033
02-07 14:08 DEBUG  WindowsBackend: windows_language=English
02-07 14:08 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
02-07 14:08 DEBUG  WindowsBackend: bootloader=vista
02-07 14:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 87039.9140625 mb free ntfs)
02-07 14:08 DEBUG  WindowsBackend: drive=Drive(C: hd 87039.9140625 mb free ntfs)
02-07 14:08 DEBUG  WindowsBackend: drive=Drive(D: hd 15151.46875 mb free ntfs)
02-07 14:08 DEBUG  WindowsBackend: drive=Drive(E: hd 13896.3671875 mb free ntfs)
02-07 14:08 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
02-07 14:08 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
02-07 14:08 DEBUG  WindowsBackend: uninstaller_path=None
02-07 14:08 DEBUG  WindowsBackend: previous_target_dir=None
02-07 14:08 DEBUG  WindowsBackend: previous_distro_name=None
02-07 14:08 DEBUG  WindowsBackend: keyboard_id=67699721
02-07 14:08 DEBUG  WindowsBackend: keyboard_layout=us
02-07 14:08 DEBUG  WindowsBackend: keyboard_variant=
02-07 14:08 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-07 14:08 DEBUG  CommonBackend: locale=en_US.UTF-8
02-07 14:08 DEBUG  WindowsBackend: total_memory_mb=3894.68359375
02-07 14:08 DEBUG  CommonBackend: Searching ISOs on USB devices
02-07 14:08 DEBUG  CommonBackend: Searching for local CDs
02-07 14:08 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp is a valid Ubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp is a valid Ubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp is a valid Kubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp is a valid Kubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp is a valid Xubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp is a valid Xubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp is a valid Mythbuntu CD
02-07 14:08 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp is a valid Mythbuntu CD
02-07 14:08 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp is a valid Edubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp is a valid Edubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp is a valid Lubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp is a valid Lubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-07 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-07 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-07 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-07 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-07 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-07 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
02-07 14:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-07 14:08 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-07 14:08 DEBUG  Distro:   parsing info from str=Ubuntu 12.04.1 LTS "Precise Pangolin" - Release i386 (20120817.3)
02-07 14:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04.1', 'build': '20120817.3', 'codename': 'Precise Pangolin', 'arch': 'i386'}
02-07 14:08 INFO   Distro: Found a valid CD for Ubuntu: G:\
02-07 14:08 INFO   root: Running the CD menu...
02-07 14:08 DEBUG  WindowsFrontend: __init__...
02-07 14:08 DEBUG  WindowsFrontend: on_init...
02-07 14:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\translations, languages=['en_US', 'en']
02-07 14:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Expert\AppData\Local\Temp\pyl3135.tmp\translations, languages=['en_US', 'en']
02-07 14:09 INFO   WindowsFrontend: Operation cancelled
02-07 14:09 DEBUG  WindowsFrontend: frontend.quit
02-07 14:09 DEBUG  WindowsFrontend: frontend.on_quit
02-07 14:09 DEBUG  root: application.on_quit
02-07 14:09 INFO   root: sys.exit
02-08 03:24 INFO   root: === wubi 12.04 rev269 ===
02-08 03:24 DEBUG  root: Logfile is c:\users\expert\appdata\local\temp\wubi-12.04-rev269.log
02-08 03:24 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Expert\\AppData\\Local\\Temp\\MagicISO_01CE058602870D3C\\wubi.exe"']
02-08 03:24 DEBUG  CommonBackend: data_dir=C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\data
02-08 03:24 DEBUG  WindowsBackend: 7z=C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\bin\7z.exe
02-08 03:24 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-08 03:24 DEBUG  CommonBackend: Fetching basic info...
02-08 03:24 DEBUG  CommonBackend: original_exe=C:\Users\Expert\AppData\Local\Temp\MagicISO_01CE058602870D3C\wubi.exe
02-08 03:24 DEBUG  CommonBackend: platform=win32
02-08 03:24 DEBUG  CommonBackend: osname=nt
02-08 03:24 DEBUG  CommonBackend: language=en_US
02-08 03:24 DEBUG  CommonBackend: encoding=cp1252
02-08 03:24 DEBUG  WindowsBackend: arch=amd64
02-08 03:24 DEBUG  CommonBackend: Parsing isolist=C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\data\isolist.ini
02-08 03:24 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-08 03:24 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
02-08 03:24 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-08 03:24 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-08 03:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-08 03:24 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
02-08 03:24 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-08 03:24 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
02-08 03:24 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-08 03:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-08 03:24 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-08 03:24 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
02-08 03:24 DEBUG  WindowsBackend: Fetching host info...
02-08 03:24 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-08 03:24 DEBUG  WindowsBackend: windows version=vista
02-08 03:24 DEBUG  WindowsBackend: windows_version2=Windows 8 Enterprise N
02-08 03:24 DEBUG  WindowsBackend: windows_sp=None
02-08 03:24 DEBUG  WindowsBackend: windows_build=9200
02-08 03:24 DEBUG  WindowsBackend: gmt=4
02-08 03:24 DEBUG  WindowsBackend: country=US
02-08 03:24 DEBUG  WindowsBackend: timezone=America/New_York
02-08 03:24 DEBUG  WindowsBackend: windows_username=Expert
02-08 03:24 DEBUG  WindowsBackend: user_full_name=Expert
02-08 03:24 DEBUG  WindowsBackend: user_directory=C:\Users\Expert
02-08 03:24 DEBUG  WindowsBackend: windows_language_code=1033
02-08 03:24 DEBUG  WindowsBackend: windows_language=English
02-08 03:24 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
02-08 03:24 DEBUG  WindowsBackend: bootloader=vista
02-08 03:24 DEBUG  WindowsBackend: system_drive=Drive(C: hd 85645.6835938 mb free ntfs)
02-08 03:24 DEBUG  WindowsBackend: drive=Drive(C: hd 85645.6796875 mb free ntfs)
02-08 03:24 DEBUG  WindowsBackend: drive=Drive(D: hd 15151.46875 mb free ntfs)
02-08 03:24 DEBUG  WindowsBackend: drive=Drive(E: hd 13896.3359375 mb free ntfs)
02-08 03:24 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free udf)
02-08 03:24 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
02-08 03:24 DEBUG  WindowsBackend: uninstaller_path=None
02-08 03:24 DEBUG  WindowsBackend: previous_target_dir=None
02-08 03:24 DEBUG  WindowsBackend: previous_distro_name=None
02-08 03:24 DEBUG  WindowsBackend: keyboard_id=67699721
02-08 03:24 DEBUG  WindowsBackend: keyboard_layout=us
02-08 03:24 DEBUG  WindowsBackend: keyboard_variant=
02-08 03:24 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-08 03:24 DEBUG  CommonBackend: locale=en_US.UTF-8
02-08 03:24 DEBUG  WindowsBackend: total_memory_mb=3894.68359375
02-08 03:24 DEBUG  CommonBackend: Searching ISOs on USB devices
02-08 03:24 DEBUG  CommonBackend: Searching for local CDs
02-08 03:24 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp is a valid Ubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp is a valid Ubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp is a valid Kubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp is a valid Kubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp is a valid Xubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp is a valid Xubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp is a valid Mythbuntu CD
02-08 03:24 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp is a valid Mythbuntu CD
02-08 03:24 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp is a valid Edubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp is a valid Edubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp is a valid Lubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp is a valid Lubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-08 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-08 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-08 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-08 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-08 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-08 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-08 03:24 DEBUG  Distro:   parsing info from str=Ubuntu 12.04.1 LTS "Precise Pangolin" - Release i386 (20120817.3)
02-08 03:24 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04.1', 'build': '20120817.3', 'codename': 'Precise Pangolin', 'arch': 'i386'}
02-08 03:24 INFO   Distro: Found a valid CD for Ubuntu: G:\
02-08 03:24 INFO   root: Running the installer...
02-08 03:24 DEBUG  WindowsFrontend: __init__...
02-08 03:24 DEBUG  WindowsFrontend: on_init...
02-08 03:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\translations, languages=['en_US', 'en']
02-08 03:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\translations, languages=['en_US', 'en']
02-08 03:24 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=expert
02-08 03:24 INFO   root: Received settings
02-08 03:24 DEBUG  CommonBackend: Searching for local CD
02-08 03:24 DEBUG  Distro:   checking whether C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp is a valid Ubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-08 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-08 03:24 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-08 03:24 INFO   Distro: Found a valid CD for Ubuntu: G:\
02-08 03:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Expert\AppData\Local\Temp\pylE1A4.tmp\translations, languages=['en_US', 'en']
02-08 03:24 DEBUG  TaskList: # Running tasklist...
02-08 03:24 DEBUG  TaskList: ## Running select_target_dir...
02-08 03:24 INFO   WindowsBackend: Installing into C:\ubuntu
02-08 03:24 DEBUG  TaskList: ## Finished select_target_dir
02-08 03:24 DEBUG  TaskList: ## Running create_dir_structure...
02-08 03:24 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-08 03:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-08 03:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-08 03:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-08 03:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-08 03:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-08 03:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-08 03:24 DEBUG  TaskList: ## Finished create_dir_structure
02-08 03:24 DEBUG  TaskList: ## Running uncompress_target_dir...
02-08 03:24 DEBUG  TaskList: ## Finished uncompress_target_dir
02-08 03:24 DEBUG  TaskList: ## Running create_uninstaller...
02-08 03:24 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Expert\AppData\Local\Temp\MagicISO_01CE058602870D3C\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-08 03:24 ERROR  TaskList: [Errno 2] No such file or directory: 'C:\\Users\\Expert\\AppData\\Local\\Temp\\MagicISO_01CE058602870D3C\\wubi.exe'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 116, in create_uninstaller
  File "\lib\shutil.py", line 38, in copyfile
IOError: [Errno 2] No such file or directory: 'C:\\Users\\Expert\\AppData\\Local\\Temp\\MagicISO_01CE058602870D3C\\wubi.exe'
02-08 03:24 DEBUG  TaskList: # Cancelling tasklist
02-08 03:24 DEBUG  TaskList: # Finished tasklist
02-08 03:24 ERROR  root: [Errno 2] No such file or directory: 'C:\\Users\\Expert\\AppData\\Local\\Temp\\MagicISO_01CE058602870D3C\\wubi.exe'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 116, in create_uninstaller
  File "\lib\shutil.py", line 38, in copyfile
IOError: [Errno 2] No such file or directory: 'C:\\Users\\Expert\\AppData\\Local\\Temp\\MagicISO_01CE058602870D3C\\wubi.exe'

```
Thanks

---

### Post by Cheesemill on 2013-02-07
Wubi doesn't work with Windows 8.

It might do in the future but at the moment if you have Windows 8 your only option is a proper dual-boot setup.

---

### Post by Mark Phelps on 2013-02-07
Also, if you DO decide to go with a traditional dual-boot (with Ubuntu in its own Linux filesystem partitions), do NOT use the Ubuntu installer to shrink Win8.  Doing so risks corrupting Win8 and rendering it unbootable.  Instead, use the Disk Managment utility to do the shrinkage.

Also, you should look into using the Win8 feature to create Win8 Recovery Media.  This will come in handy later, should you need to repair Win8 from the dual-boot setup.

---

### Post by bcbc on 2013-02-07
> **Cheesemill said:**
> Wubi doesn't work with Windows 8.

It might do in the future but at the moment if you have Windows 8 your only option is a proper dual-boot setup.

It works with Windows 8 if the disk has a MBR partition table. Since the version of Windows 8 is 32bit (from the logfile) it's probably okay. Any computer that comes with Windows 8 pre-installed will not work.

My advice is not to mount the ISO using partition magic (or whatever you are using). Just place wubi.exe and the ISO in the same folder before running.

---

### Post by Damascushead on 2013-02-08
Don't know what kind of machine you are running but I would:

1.Go into windows 8 and change the size of the windows partition until you have enough "free space" for Ubuntu.

2. Get Ubuntu 12.10 (best for dual booting with windows 8) on a live USB or CD

3. Install in the traditional manner from said live device.

4. If you have problems after reboot, then run 'boot-repair' to fix grub.


Windows 8 has changed the dual boot process a bit so you will have to do a bit of reading first. I just finished dual booting mine today, and it took a bit of trial and error.

---

