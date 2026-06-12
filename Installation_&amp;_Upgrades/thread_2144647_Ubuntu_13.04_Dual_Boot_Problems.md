---
title: "Ubuntu 13.04 Dual Boot Problems"
date: 2013-05-13
forum: Installation &amp; Upgrades
---

### Post by mkodaimati on 2013-05-13
Hey, I am trying to dual boot Ubuntu 13.04 alongside windows 7 and when I go through the installer it isn't recognizing the disk I partitioned. Help would be greatly appreciated I'm new here spent a few hours trying to figure out what's wrong but no luck :p
[[IMG]http://img10.imageshack.us/img10/8782/screenshot006sx.png[/IMG]]("http://img10.imageshack.us/i/screenshot006sx.png/")
I have an HP Pavillion dv6 laptop and installing from a flash drive if that matters and pretty nooby. Also when I go through the wubi installer off my flash drive on windows instead of booting from the flash drive, I get an error:

05-12 21:52 INFO   root: === wubi 13.04 rev279 ===
05-12 21:52 DEBUG  root: Logfile is c:\users\moh\appdata\local\temp\wubi-13.04-rev279.log
05-12 21:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
05-12 21:52 DEBUG  CommonBackend: data_dir=C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\data
05-12 21:52 DEBUG  WindowsBackend: 7z=C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\bin\7z.exe
05-12 21:52 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-12 21:52 DEBUG  CommonBackend: Fetching basic info...
05-12 21:52 DEBUG  CommonBackend: original_exe=G:\wubi.exe
05-12 21:52 DEBUG  CommonBackend: platform=win32
05-12 21:52 DEBUG  CommonBackend: osname=nt
05-12 21:52 DEBUG  CommonBackend: language=en_US
05-12 21:52 DEBUG  CommonBackend: encoding=cp1252
05-12 21:52 DEBUG  WindowsBackend: arch=amd64
05-12 21:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\data\isolist.ini
05-12 21:52 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-12 21:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-12 21:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-12 21:52 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-12 21:52 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
05-12 21:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-12 21:52 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-12 21:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-12 21:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-12 21:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-12 21:52 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
05-12 21:52 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-12 21:52 DEBUG  WindowsBackend: Fetching host info...
05-12 21:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-12 21:52 DEBUG  WindowsBackend: windows version=vista
05-12 21:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-12 21:52 DEBUG  WindowsBackend: windows_sp=None
05-12 21:52 DEBUG  WindowsBackend: windows_build=7601
05-12 21:52 DEBUG  WindowsBackend: gmt=-5
05-12 21:52 DEBUG  WindowsBackend: country=US
05-12 21:52 DEBUG  WindowsBackend: timezone=America/New_York
05-12 21:52 DEBUG  WindowsBackend: windows_username=MOH
05-12 21:52 DEBUG  WindowsBackend: user_full_name=MOH
05-12 21:52 DEBUG  WindowsBackend: user_directory=C:\Users\MOH
05-12 21:52 DEBUG  WindowsBackend: windows_language_code=1033
05-12 21:52 DEBUG  WindowsBackend: windows_language=English
05-12 21:52 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
05-12 21:52 DEBUG  WindowsBackend: bootloader=vista
05-12 21:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 797526.820313 mb free ntfs)
05-12 21:52 DEBUG  WindowsBackend: drive=Drive(C: hd 797526.820313 mb free ntfs)
05-12 21:52 DEBUG  WindowsBackend: drive=Drive(D: hd 2238.4296875 mb free ntfs)
05-12 21:52 DEBUG  WindowsBackend: drive=Drive(E: hd 1.10546875 mb free fat32)
05-12 21:52 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-12 21:52 DEBUG  WindowsBackend: drive=Drive(G: removable 2342.5390625 mb free fat32)
05-12 21:52 DEBUG  WindowsBackend: uninstaller_path=None
05-12 21:52 DEBUG  WindowsBackend: previous_target_dir=None
05-12 21:52 DEBUG  WindowsBackend: previous_distro_name=None
05-12 21:52 DEBUG  WindowsBackend: keyboard_id=67699721
05-12 21:52 DEBUG  WindowsBackend: keyboard_layout=us
05-12 21:52 DEBUG  WindowsBackend: keyboard_variant=
05-12 21:52 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-12 21:52 DEBUG  CommonBackend: locale=en_US.UTF-8
05-12 21:52 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-12 21:52 DEBUG  CommonBackend: Searching ISOs on USB devices
05-12 21:52 DEBUG  CommonBackend: Searching for local CDs
05-12 21:52 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp is a valid Ubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp is a valid Ubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp is a valid Kubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp is a valid Kubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp is a valid Mythbuntu CD
05-12 21:52 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp is a valid Mythbuntu CD
05-12 21:52 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp is a valid Edubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp is a valid Edubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp is a valid Lubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp is a valid Lubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp is a valid Ubuntu Studio CD
05-12 21:52 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp is a valid Ubuntu Studio CD
05-12 21:52 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-12 21:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-12 21:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-12 21:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-12 21:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-12 21:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-12 21:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-12 21:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-12 21:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-12 21:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-12 21:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-12 21:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-12 21:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-12 21:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 21:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-12 21:52 DEBUG  Distro:   parsing info from str=Ubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
05-12 21:52 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
05-12 21:52 INFO   Distro: Found a valid CD for Ubuntu: G:\
05-12 21:52 INFO   root: Running the CD menu...
05-12 21:52 DEBUG  WindowsFrontend: __init__...
05-12 21:52 DEBUG  WindowsFrontend: on_init...
05-12 21:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\translations, languages=['en_US', 'en']
05-12 21:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pylDDE1.tmp\translations, languages=['en_US', 'en']
05-12 21:52 DEBUG  WindowsFrontend: frontend.on_quit
05-12 21:52 DEBUG  root: application.on_quit
05-12 21:52 INFO   root: sys.exit
05-12 22:40 INFO   root: === wubi 13.04 rev279 ===
05-12 22:40 DEBUG  root: Logfile is c:\users\moh\appdata\local\temp\wubi-13.04-rev279.log
05-12 22:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ProgramData\\Microsoft\\Windows\\Start Menu\\Programs\\Startup\\wubi.exe"']
05-12 22:40 DEBUG  CommonBackend: data_dir=C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\data
05-12 22:40 DEBUG  WindowsBackend: 7z=C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\bin\7z.exe
05-12 22:40 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-12 22:40 DEBUG  CommonBackend: Fetching basic info...
05-12 22:40 DEBUG  CommonBackend: original_exe=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup\wubi.exe
05-12 22:40 DEBUG  CommonBackend: platform=win32
05-12 22:40 DEBUG  CommonBackend: osname=nt
05-12 22:40 DEBUG  CommonBackend: language=en_US
05-12 22:40 DEBUG  CommonBackend: encoding=cp1252
05-12 22:40 DEBUG  WindowsBackend: arch=amd64
05-12 22:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\data\isolist.ini
05-12 22:40 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-12 22:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-12 22:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-12 22:40 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-12 22:40 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
05-12 22:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-12 22:40 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-12 22:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-12 22:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-12 22:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-12 22:40 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
05-12 22:40 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-12 22:40 DEBUG  WindowsBackend: Fetching host info...
05-12 22:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-12 22:40 DEBUG  WindowsBackend: windows version=vista
05-12 22:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-12 22:40 DEBUG  WindowsBackend: windows_sp=None
05-12 22:40 DEBUG  WindowsBackend: windows_build=7601
05-12 22:40 DEBUG  WindowsBackend: gmt=-5
05-12 22:40 DEBUG  WindowsBackend: country=US
05-12 22:40 DEBUG  WindowsBackend: timezone=America/New_York
05-12 22:40 DEBUG  WindowsBackend: windows_username=MOH
05-12 22:40 DEBUG  WindowsBackend: user_full_name=MOH
05-12 22:40 DEBUG  WindowsBackend: user_directory=C:\Users\MOH
05-12 22:40 DEBUG  WindowsBackend: windows_language_code=1033
05-12 22:40 DEBUG  WindowsBackend: windows_language=English
05-12 22:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
05-12 22:40 DEBUG  WindowsBackend: bootloader=vista
05-12 22:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 797522.085938 mb free ntfs)
05-12 22:40 DEBUG  WindowsBackend: drive=Drive(C: hd 797522.085938 mb free ntfs)
05-12 22:40 DEBUG  WindowsBackend: drive=Drive(D: hd 2238.4296875 mb free ntfs)
05-12 22:40 DEBUG  WindowsBackend: drive=Drive(E: hd 1.09765625 mb free fat32)
05-12 22:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-12 22:40 DEBUG  WindowsBackend: uninstaller_path=None
05-12 22:40 DEBUG  WindowsBackend: previous_target_dir=None
05-12 22:40 DEBUG  WindowsBackend: previous_distro_name=None
05-12 22:40 DEBUG  WindowsBackend: keyboard_id=67699721
05-12 22:40 DEBUG  WindowsBackend: keyboard_layout=us
05-12 22:40 DEBUG  WindowsBackend: keyboard_variant=
05-12 22:40 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-12 22:40 DEBUG  CommonBackend: locale=en_US.UTF-8
05-12 22:40 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-12 22:40 DEBUG  CommonBackend: Searching ISOs on USB devices
05-12 22:40 DEBUG  CommonBackend: Searching for local CDs
05-12 22:40 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC734.tmp is a valid Ubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC734.tmp is a valid Ubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC734.tmp is a valid Kubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC734.tmp is a valid Kubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC734.tmp is a valid Mythbuntu CD
05-12 22:40 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC734.tmp is a valid Mythbuntu CD
05-12 22:40 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC734.tmp is a valid Edubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC734.tmp is a valid Edubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC734.tmp is a valid Lubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC734.tmp is a valid Lubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC734.tmp is a valid Ubuntu Studio CD
05-12 22:40 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC734.tmp is a valid Ubuntu Studio CD
05-12 22:40 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-12 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-12 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-12 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-12 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-12 22:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-12 22:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-12 22:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-12 22:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-12 22:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-12 22:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-12 22:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-12 22:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 22:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-12 22:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 22:40 INFO   root: Running the installer...
05-12 22:40 DEBUG  WindowsFrontend: __init__...
05-12 22:40 DEBUG  WindowsFrontend: on_init...
05-12 22:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\translations, languages=['en_US', 'en']
05-12 22:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pylC734.tmp\translations, languages=['en_US', 'en']
05-12 22:40 DEBUG  WindowsFrontend: frontend.on_quit
05-12 22:40 DEBUG  root: application.on_quit
05-12 22:40 INFO   root: sys.exit
05-12 23:54 INFO   root: === wubi 13.04 rev279 ===
05-12 23:54 DEBUG  root: Logfile is c:\users\moh\appdata\local\temp\wubi-13.04-rev279.log
05-12 23:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
05-12 23:54 DEBUG  CommonBackend: data_dir=C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\data
05-12 23:54 DEBUG  WindowsBackend: 7z=C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\bin\7z.exe
05-12 23:54 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-12 23:54 DEBUG  CommonBackend: Fetching basic info...
05-12 23:54 DEBUG  CommonBackend: original_exe=G:\wubi.exe
05-12 23:54 DEBUG  CommonBackend: platform=win32
05-12 23:54 DEBUG  CommonBackend: osname=nt
05-12 23:54 DEBUG  CommonBackend: language=en_US
05-12 23:54 DEBUG  CommonBackend: encoding=cp1252
05-12 23:54 DEBUG  WindowsBackend: arch=amd64
05-12 23:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\data\isolist.ini
05-12 23:54 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-12 23:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-12 23:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-12 23:54 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-12 23:54 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
05-12 23:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-12 23:54 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-12 23:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-12 23:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-12 23:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-12 23:54 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
05-12 23:54 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-12 23:54 DEBUG  WindowsBackend: Fetching host info...
05-12 23:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-12 23:54 DEBUG  WindowsBackend: windows version=vista
05-12 23:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-12 23:54 DEBUG  WindowsBackend: windows_sp=None
05-12 23:54 DEBUG  WindowsBackend: windows_build=7601
05-12 23:54 DEBUG  WindowsBackend: gmt=-5
05-12 23:54 DEBUG  WindowsBackend: country=US
05-12 23:54 DEBUG  WindowsBackend: timezone=America/New_York
05-12 23:54 DEBUG  WindowsBackend: windows_username=MOH
05-12 23:54 DEBUG  WindowsBackend: user_full_name=MOH
05-12 23:54 DEBUG  WindowsBackend: user_directory=C:\Users\MOH
05-12 23:54 DEBUG  WindowsBackend: windows_language_code=1033
05-12 23:54 DEBUG  WindowsBackend: windows_language=English
05-12 23:54 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
05-12 23:54 DEBUG  WindowsBackend: bootloader=vista
05-12 23:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 697501.132813 mb free ntfs)
05-12 23:54 DEBUG  WindowsBackend: drive=Drive(C: hd 697501.132813 mb free ntfs)
05-12 23:54 DEBUG  WindowsBackend: drive=Drive(D: hd 2238.4296875 mb free ntfs)
05-12 23:54 DEBUG  WindowsBackend: drive=Drive(E: hd 1.09765625 mb free fat32)
05-12 23:54 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-12 23:54 DEBUG  WindowsBackend: drive=Drive(G: removable 2325.59375 mb free fat32)
05-12 23:54 DEBUG  WindowsBackend: drive=Drive(H: hd 95274.7578125 mb free ntfs)
05-12 23:54 DEBUG  WindowsBackend: uninstaller_path=None
05-12 23:54 DEBUG  WindowsBackend: previous_target_dir=None
05-12 23:54 DEBUG  WindowsBackend: previous_distro_name=None
05-12 23:54 DEBUG  WindowsBackend: keyboard_id=67699721
05-12 23:54 DEBUG  WindowsBackend: keyboard_layout=us
05-12 23:54 DEBUG  WindowsBackend: keyboard_variant=
05-12 23:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-12 23:54 DEBUG  CommonBackend: locale=en_US.UTF-8
05-12 23:54 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-12 23:54 DEBUG  CommonBackend: Searching ISOs on USB devices
05-12 23:54 DEBUG  CommonBackend: Searching for local CDs
05-12 23:54 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp is a valid Ubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp is a valid Ubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp is a valid Kubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp is a valid Kubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp is a valid Mythbuntu CD
05-12 23:54 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp is a valid Mythbuntu CD
05-12 23:54 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp is a valid Edubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp is a valid Edubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp is a valid Lubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp is a valid Lubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp is a valid Ubuntu Studio CD
05-12 23:54 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp is a valid Ubuntu Studio CD
05-12 23:54 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-12 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-12 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-12 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-12 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-12 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-12 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-12 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-12 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-12 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-12 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-12 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-12 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-12 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-12 23:54 DEBUG  Distro:   parsing info from str=Ubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
05-12 23:54 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
05-12 23:54 INFO   Distro: Found a valid CD for Ubuntu: G:\
05-12 23:54 INFO   root: Running the CD menu...
05-12 23:54 DEBUG  WindowsFrontend: __init__...
05-12 23:54 DEBUG  WindowsFrontend: on_init...
05-12 23:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\translations, languages=['en_US', 'en']
05-12 23:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\translations, languages=['en_US', 'en']
05-12 23:54 INFO   root: CD menu finished
05-12 23:54 INFO   root: Running the CD boot helper...
05-12 23:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\translations, languages=['en_US', 'en']
05-12 23:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\translations, languages=['en_US', 'en']
05-12 23:54 INFO   root: CD boot helper confirmed
05-12 23:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\translations, languages=['en_US', 'en']
05-12 23:54 DEBUG  TaskList: # Running tasklist...
05-12 23:54 DEBUG  TaskList: ## Running select_target_dir...
05-12 23:54 INFO   WindowsBackend: Installing into C:\ubuntu
05-12 23:54 DEBUG  TaskList: ## Finished select_target_dir
05-12 23:54 DEBUG  TaskList: ## Running create_dir_structure...
05-12 23:54 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-12 23:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-12 23:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-12 23:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-12 23:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-12 23:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-12 23:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-12 23:54 DEBUG  TaskList: ## Finished create_dir_structure
05-12 23:54 DEBUG  TaskList: ## Running uncompress_target_dir...
05-12 23:54 DEBUG  TaskList: ## Finished uncompress_target_dir
05-12 23:54 DEBUG  TaskList: ## Running create_uninstaller...
05-12 23:54 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-12 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-12 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-12 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-12 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-12 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 13.04-rev279
05-12 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-12 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-12 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-12 23:54 DEBUG  TaskList: ## Finished create_uninstaller
05-12 23:54 DEBUG  TaskList: ## Running copy_installation_files...
05-12 23:54 DEBUG  WindowsBackend: Copying C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-12 23:54 DEBUG  WindowsBackend: Copying C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\winboot -> C:\ubuntu\winboot
05-12 23:54 DEBUG  WindowsBackend: Copying C:\Users\MOH\AppData\Local\Temp\pyl7BA4.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-12 23:54 DEBUG  TaskList: ## Finished copy_installation_files
05-12 23:54 DEBUG  TaskList: ## Running use_cd...
05-12 23:54 DEBUG  TaskList: New task copy_file
05-12 23:54 DEBUG  TaskList: ### Running copy_file...
05-12 23:58 DEBUG  TaskList: ### Finished copy_file
05-12 23:58 DEBUG  TaskList: New task check_iso
05-12 23:58 DEBUG  TaskList: ### Running check_iso...
05-12 23:58 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
05-12 23:58 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
05-12 23:58 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
05-12 23:58 DEBUG  Distro:   parsing info from str=Ubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
05-12 23:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
05-12 23:58 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
05-12 23:58 DEBUG  TaskList: New task get_metalink
05-12 23:58 DEBUG  TaskList: #### Running get_metalink...
05-12 23:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.metalink](http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.metalink) > C:\ubuntu\install
05-12 23:58 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-13.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.metalink, basename=ubuntu-13.04-desktop-amd64.metalink, length=36499, text=None
05-12 23:58 DEBUG  downloader: download finished (read 36499 bytes)
05-12 23:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/13.04/MD5SUMS-metalink](http://releases.ubuntu.com/13.04/MD5SUMS-metalink) > C:\ubuntu\install
05-12 23:58 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/13.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=498, text=None
05-12 23:58 DEBUG  downloader: download finished (read 498 bytes)
05-12 23:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/13.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/13.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-12 23:58 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/13.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-12 23:58 DEBUG  downloader: download finished (read 198 bytes)
05-12 23:58 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-12 23:58 INFO   saplog: Checking block bindings..
05-12 23:58 INFO   saplog: Key verified successfully.
05-12 23:58 DEBUG  CommonBackend: metalink md5sums:
e578445ee73cc1641834fca2542a90ba *ubuntu-13.04-desktop-amd64+mac.metalink
6b2e76fe8853d019d66c34fb0bbaa574 *ubuntu-13.04-desktop-amd64.metalink
02c9c64dcd3359d5224612ed8097adcf *ubuntu-13.04-desktop-i386.metalink
eff9dda8b3a9d69c88f6703729d50174 *ubuntu-13.04-server-amd64+mac.metalink
afafb246cd2ef1ab04803cac3ec554ac *ubuntu-13.04-server-amd64.metalink
98f94e110e069b936fa5ed229136464b *ubuntu-13.04-server-armhf+omap4.metalink
9d09bf70b2a640e12ee8e510d64a553e *ubuntu-13.04-server-i386.metalink


05-12 23:58 ERROR  CommonBackend: The md5 of the metalink does match
05-12 23:58 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
05-12 23:58 DEBUG  TaskList: #### Finished get_metalink
05-12 23:58 DEBUG  TaskList: New task get_file_md5
05-12 23:58 DEBUG  TaskList: #### Running get_file_md5...
05-12 23:59 DEBUG  TaskList: #### Finished get_file_md5
05-12 23:59 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (8d72e2db7e72e13813731eab37a14d26 != 1e0842f3eaf25512b24c4b1045d4f7de)
None
05-12 23:59 DEBUG  TaskList: ### Finished check_iso
05-12 23:59 DEBUG  TaskList: ## Finished use_cd
05-12 23:59 DEBUG  TaskList: ## Running extract_kernel...
05-12 23:59 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 618, in extract_kernel
Exception: Could not retrieve the required installation files
05-12 23:59 DEBUG  TaskList: # Cancelling tasklist
05-12 23:59 DEBUG  TaskList: # Finished tasklist
05-12 23:59 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 228, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 618, in extract_kernel
Exception: Could not retrieve the required installation files
05-12 23:59 INFO   root: === wubi 13.04 rev279 ===
05-12 23:59 DEBUG  root: Logfile is c:\users\moh\appdata\local\temp\wubi-13.04-rev279.log
05-12 23:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
05-12 23:59 DEBUG  CommonBackend: data_dir=C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\data
05-12 23:59 DEBUG  WindowsBackend: 7z=C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\bin\7z.exe
05-12 23:59 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-12 23:59 DEBUG  CommonBackend: Fetching basic info...
05-12 23:59 DEBUG  CommonBackend: original_exe=G:\wubi.exe
05-12 23:59 DEBUG  CommonBackend: platform=win32
05-12 23:59 DEBUG  CommonBackend: osname=nt
05-12 23:59 DEBUG  CommonBackend: language=en_US
05-12 23:59 DEBUG  CommonBackend: encoding=cp1252
05-12 23:59 DEBUG  WindowsBackend: arch=amd64
05-12 23:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\data\isolist.ini
05-12 23:59 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-12 23:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-12 23:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-12 23:59 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-12 23:59 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
05-12 23:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-12 23:59 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-12 23:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-12 23:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-12 23:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-12 23:59 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
05-12 23:59 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-12 23:59 DEBUG  WindowsBackend: Fetching host info...
05-12 23:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-12 23:59 DEBUG  WindowsBackend: windows version=vista
05-12 23:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-12 23:59 DEBUG  WindowsBackend: windows_sp=None
05-12 23:59 DEBUG  WindowsBackend: windows_build=7601
05-12 23:59 DEBUG  WindowsBackend: gmt=-5
05-12 23:59 DEBUG  WindowsBackend: country=US
05-12 23:59 DEBUG  WindowsBackend: timezone=America/New_York
05-12 23:59 DEBUG  WindowsBackend: windows_username=MOH
05-12 23:59 DEBUG  WindowsBackend: user_full_name=MOH
05-12 23:59 DEBUG  WindowsBackend: user_directory=C:\Users\MOH
05-12 23:59 DEBUG  WindowsBackend: windows_language_code=1033
05-12 23:59 DEBUG  WindowsBackend: windows_language=English
05-12 23:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
05-12 23:59 DEBUG  WindowsBackend: bootloader=vista
05-12 23:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 693589.785156 mb free ntfs)
05-12 23:59 DEBUG  WindowsBackend: drive=Drive(C: hd 693589.785156 mb free ntfs)
05-12 23:59 DEBUG  WindowsBackend: drive=Drive(D: hd 2238.4296875 mb free ntfs)
05-12 23:59 DEBUG  WindowsBackend: drive=Drive(E: hd 1.09765625 mb free fat32)
05-12 23:59 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-12 23:59 DEBUG  WindowsBackend: drive=Drive(G: removable 2325.59375 mb free fat32)
05-12 23:59 DEBUG  WindowsBackend: drive=Drive(H: hd 95274.7578125 mb free ntfs)
05-12 23:59 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-12 23:59 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-12 23:59 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-12 23:59 DEBUG  WindowsBackend: keyboard_id=67699721
05-12 23:59 DEBUG  WindowsBackend: keyboard_layout=us
05-12 23:59 DEBUG  WindowsBackend: keyboard_variant=
05-12 23:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-12 23:59 DEBUG  CommonBackend: locale=en_US.UTF-8
05-12 23:59 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-12 23:59 DEBUG  CommonBackend: Searching ISOs on USB devices
05-12 23:59 DEBUG  CommonBackend: Searching for local CDs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:   parsing info from str=Ubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
05-12 23:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
05-12 23:59 INFO   Distro: Found a valid CD for Ubuntu: G:\
05-12 23:59 INFO   root: Running the CD menu...
05-12 23:59 DEBUG  WindowsFrontend: __init__...
05-12 23:59 DEBUG  WindowsFrontend: on_init...
05-12 23:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\translations, languages=['en_US', 'en']
05-12 23:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pyl7DD6.tmp\translations, languages=['en_US', 'en']
05-12 23:59 DEBUG  root: application.quit
05-12 23:59 DEBUG  WindowsFrontend: frontend.quit
05-12 23:59 DEBUG  WindowsFrontend: frontend.on_quit
05-12 23:59 DEBUG  root: application.on_quit
05-12 23:59 INFO   root: sys.exit
05-12 23:59 INFO   root: === wubi 13.04 rev279 ===
05-12 23:59 DEBUG  root: Logfile is c:\users\moh\appdata\local\temp\wubi-13.04-rev279.log
05-12 23:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"']
05-12 23:59 DEBUG  CommonBackend: data_dir=C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\data
05-12 23:59 DEBUG  WindowsBackend: 7z=C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\bin\7z.exe
05-12 23:59 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-12 23:59 DEBUG  CommonBackend: Fetching basic info...
05-12 23:59 DEBUG  CommonBackend: original_exe=G:\wubi.exe
05-12 23:59 DEBUG  CommonBackend: platform=win32
05-12 23:59 DEBUG  CommonBackend: osname=nt
05-12 23:59 DEBUG  CommonBackend: language=en_US
05-12 23:59 DEBUG  CommonBackend: encoding=cp1252
05-12 23:59 DEBUG  WindowsBackend: arch=amd64
05-12 23:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\data\isolist.ini
05-12 23:59 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-12 23:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-12 23:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-12 23:59 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-12 23:59 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
05-12 23:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-12 23:59 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-12 23:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-12 23:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-12 23:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-12 23:59 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
05-12 23:59 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-12 23:59 DEBUG  WindowsBackend: Fetching host info...
05-12 23:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-12 23:59 DEBUG  WindowsBackend: windows version=vista
05-12 23:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-12 23:59 DEBUG  WindowsBackend: windows_sp=None
05-12 23:59 DEBUG  WindowsBackend: windows_build=7601
05-12 23:59 DEBUG  WindowsBackend: gmt=-5
05-12 23:59 DEBUG  WindowsBackend: country=US
05-12 23:59 DEBUG  WindowsBackend: timezone=America/New_York
05-12 23:59 DEBUG  WindowsBackend: windows_username=MOH
05-12 23:59 DEBUG  WindowsBackend: user_full_name=MOH
05-12 23:59 DEBUG  WindowsBackend: user_directory=C:\Users\MOH
05-12 23:59 DEBUG  WindowsBackend: windows_language_code=1033
05-12 23:59 DEBUG  WindowsBackend: windows_language=English
05-12 23:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
05-12 23:59 DEBUG  WindowsBackend: bootloader=vista
05-12 23:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 693589.726563 mb free ntfs)
05-12 23:59 DEBUG  WindowsBackend: drive=Drive(C: hd 693589.726563 mb free ntfs)
05-12 23:59 DEBUG  WindowsBackend: drive=Drive(D: hd 2238.4296875 mb free ntfs)
05-12 23:59 DEBUG  WindowsBackend: drive=Drive(E: hd 1.09765625 mb free fat32)
05-12 23:59 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-12 23:59 DEBUG  WindowsBackend: drive=Drive(G: removable 2325.59375 mb free fat32)
05-12 23:59 DEBUG  WindowsBackend: drive=Drive(H: hd 95274.7578125 mb free ntfs)
05-12 23:59 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-12 23:59 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-12 23:59 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-12 23:59 DEBUG  WindowsBackend: keyboard_id=67699721
05-12 23:59 DEBUG  WindowsBackend: keyboard_layout=us
05-12 23:59 DEBUG  WindowsBackend: keyboard_variant=
05-12 23:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-12 23:59 DEBUG  CommonBackend: locale=en_US.UTF-8
05-12 23:59 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-12 23:59 DEBUG  CommonBackend: Searching ISOs on USB devices
05-12 23:59 DEBUG  CommonBackend: Searching for local CDs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-12 23:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-12 23:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-12 23:59 DEBUG  Distro:   parsing info from str=Ubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
05-12 23:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
05-12 23:59 INFO   Distro: Found a valid CD for Ubuntu: G:\
05-12 23:59 INFO   root: Running the CD menu...
05-12 23:59 DEBUG  WindowsFrontend: __init__...
05-12 23:59 DEBUG  WindowsFrontend: on_init...
05-12 23:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\translations, languages=['en_US', 'en']
05-12 23:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pylA5DF.tmp\translations, languages=['en_US', 'en']
05-13 00:08 INFO   root: CD menu finished
05-13 00:08 INFO   root: Rebooting
05-13 00:08 DEBUG  TaskList: # Running tasklist...
05-13 00:08 DEBUG  TaskList: ## Running reboot...
05-13 00:08 DEBUG  TaskList: ## Finished reboot
05-13 00:08 DEBUG  TaskList: # Finished tasklist
05-13 00:08 DEBUG  root: application.quit
05-13 00:08 DEBUG  WindowsFrontend: frontend.quit
05-13 00:08 DEBUG  WindowsFrontend: frontend.on_quit
05-13 00:08 DEBUG  root: application.on_quit
05-13 00:08 INFO   root: sys.exit
05-13 00:44 INFO   root: === wubi 13.04 rev279 ===
05-13 00:44 DEBUG  root: Logfile is c:\users\moh\appdata\local\temp\wubi-13.04-rev279.log
05-13 00:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ProgramData\\Microsoft\\Windows\\Start Menu\\Programs\\Startup\\wubi.exe"']
05-13 00:44 DEBUG  CommonBackend: data_dir=C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\data
05-13 00:44 DEBUG  WindowsBackend: 7z=C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\bin\7z.exe
05-13 00:44 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-13 00:44 DEBUG  CommonBackend: Fetching basic info...
05-13 00:44 DEBUG  CommonBackend: original_exe=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup\wubi.exe
05-13 00:44 DEBUG  CommonBackend: platform=win32
05-13 00:44 DEBUG  CommonBackend: osname=nt
05-13 00:44 DEBUG  CommonBackend: language=en_US
05-13 00:44 DEBUG  CommonBackend: encoding=cp1252
05-13 00:44 DEBUG  WindowsBackend: arch=amd64
05-13 00:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\data\isolist.ini
05-13 00:44 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-13 00:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-13 00:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-13 00:44 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-13 00:44 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
05-13 00:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-13 00:44 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-13 00:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-13 00:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-13 00:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-13 00:44 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
05-13 00:44 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-13 00:44 DEBUG  WindowsBackend: Fetching host info...
05-13 00:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-13 00:44 DEBUG  WindowsBackend: windows version=vista
05-13 00:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-13 00:44 DEBUG  WindowsBackend: windows_sp=None
05-13 00:44 DEBUG  WindowsBackend: windows_build=7601
05-13 00:44 DEBUG  WindowsBackend: gmt=-5
05-13 00:44 DEBUG  WindowsBackend: country=US
05-13 00:44 DEBUG  WindowsBackend: timezone=America/New_York
05-13 00:44 DEBUG  WindowsBackend: windows_username=MOH
05-13 00:44 DEBUG  WindowsBackend: user_full_name=MOH
05-13 00:44 DEBUG  WindowsBackend: user_directory=C:\Users\MOH
05-13 00:44 DEBUG  WindowsBackend: windows_language_code=1033
05-13 00:44 DEBUG  WindowsBackend: windows_language=English
05-13 00:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
05-13 00:44 DEBUG  WindowsBackend: bootloader=vista
05-13 00:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 693587.863281 mb free ntfs)
05-13 00:44 DEBUG  WindowsBackend: drive=Drive(C: hd 693587.863281 mb free ntfs)
05-13 00:44 DEBUG  WindowsBackend: drive=Drive(D: hd 2238.4296875 mb free ntfs)
05-13 00:44 DEBUG  WindowsBackend: drive=Drive(E: hd 1.09765625 mb free fat32)
05-13 00:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-13 00:44 DEBUG  WindowsBackend: drive=Drive(H: hd 95274.7578125 mb free ntfs)
05-13 00:44 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-13 00:44 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-13 00:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-13 00:44 DEBUG  WindowsBackend: keyboard_id=67699721
05-13 00:44 DEBUG  WindowsBackend: keyboard_layout=us
05-13 00:44 DEBUG  WindowsBackend: keyboard_variant=
05-13 00:44 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-13 00:44 DEBUG  CommonBackend: locale=en_US.UTF-8
05-13 00:44 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-13 00:44 DEBUG  CommonBackend: Searching ISOs on USB devices
05-13 00:44 DEBUG  CommonBackend: Searching for local CDs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 INFO   root: Already installed, running the uninstaller...
05-13 00:44 INFO   root: Running the uninstaller...
05-13 00:44 INFO   CommonBackend: This is the uninstaller running
05-13 00:44 DEBUG  WindowsFrontend: __init__...
05-13 00:44 DEBUG  WindowsFrontend: on_init...
05-13 00:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\translations, languages=['en_US', 'en']
05-13 00:44 INFO   root: Received settings
05-13 00:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\translations, languages=['en_US', 'en']
05-13 00:44 DEBUG  TaskList: # Running tasklist...
05-13 00:44 DEBUG  TaskList: ## Running Remove bootloader entry...
05-13 00:44 DEBUG  WindowsBackend: Could not find bcd id
05-13 00:44 DEBUG  WindowsBackend: undo_bootini C:
05-13 00:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 693587.863281 mb free ntfs)
05-13 00:44 DEBUG  WindowsBackend: undo_bootini D:
05-13 00:44 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2238.4296875 mb free ntfs)
05-13 00:44 DEBUG  WindowsBackend: undo_bootini E:
05-13 00:44 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 1.09765625 mb free fat32)
05-13 00:44 DEBUG  WindowsBackend: undo_bootini H:
05-13 00:44 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 95274.7578125 mb free ntfs)
05-13 00:44 DEBUG  TaskList: ## Finished Remove bootloader entry
05-13 00:44 DEBUG  TaskList: ## Running Remove target dir...
05-13 00:44 DEBUG  CommonBackend: Deleting C:\ubuntu
05-13 00:44 DEBUG  TaskList: ## Finished Remove target dir
05-13 00:44 DEBUG  TaskList: ## Running Remove registry key...
05-13 00:44 DEBUG  TaskList: ## Finished Remove registry key
05-13 00:44 DEBUG  TaskList: # Finished tasklist
05-13 00:44 INFO   root: Almost finished uninstalling
05-13 00:44 INFO   root: Finished uninstallation
05-13 00:44 DEBUG  CommonBackend: Fetching basic info...
05-13 00:44 DEBUG  CommonBackend: original_exe=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup\wubi.exe
05-13 00:44 DEBUG  CommonBackend: platform=win32
05-13 00:44 DEBUG  CommonBackend: osname=nt
05-13 00:44 DEBUG  WindowsBackend: arch=amd64
05-13 00:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\data\isolist.ini
05-13 00:44 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-13 00:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-13 00:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-13 00:44 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-13 00:44 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
05-13 00:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-13 00:44 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-13 00:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-13 00:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-13 00:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-13 00:44 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
05-13 00:44 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-13 00:44 DEBUG  WindowsBackend: Fetching host info...
05-13 00:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-13 00:44 DEBUG  WindowsBackend: windows version=vista
05-13 00:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-13 00:44 DEBUG  WindowsBackend: windows_sp=None
05-13 00:44 DEBUG  WindowsBackend: windows_build=7601
05-13 00:44 DEBUG  WindowsBackend: gmt=-5
05-13 00:44 DEBUG  WindowsBackend: country=US
05-13 00:44 DEBUG  WindowsBackend: timezone=America/New_York
05-13 00:44 DEBUG  WindowsBackend: windows_username=MOH
05-13 00:44 DEBUG  WindowsBackend: user_full_name=MOH
05-13 00:44 DEBUG  WindowsBackend: user_directory=C:\Users\MOH
05-13 00:44 DEBUG  WindowsBackend: windows_language_code=1033
05-13 00:44 DEBUG  WindowsBackend: windows_language=English
05-13 00:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
05-13 00:44 DEBUG  WindowsBackend: bootloader=vista
05-13 00:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 697504.871094 mb free ntfs)
05-13 00:44 DEBUG  WindowsBackend: drive=Drive(C: hd 697504.871094 mb free ntfs)
05-13 00:44 DEBUG  WindowsBackend: drive=Drive(D: hd 2238.4296875 mb free ntfs)
05-13 00:44 DEBUG  WindowsBackend: drive=Drive(E: hd 1.09765625 mb free fat32)
05-13 00:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-13 00:44 DEBUG  WindowsBackend: drive=Drive(H: hd 95274.7578125 mb free ntfs)
05-13 00:44 DEBUG  WindowsBackend: uninstaller_path=None
05-13 00:44 DEBUG  WindowsBackend: previous_target_dir=None
05-13 00:44 DEBUG  WindowsBackend: previous_distro_name=None
05-13 00:44 DEBUG  WindowsBackend: keyboard_id=67699721
05-13 00:44 DEBUG  WindowsBackend: keyboard_layout=us
05-13 00:44 DEBUG  WindowsBackend: keyboard_variant=
05-13 00:44 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-13 00:44 DEBUG  CommonBackend: Searching ISOs on USB devices
05-13 00:44 DEBUG  CommonBackend: Searching for local CDs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Studio CD
05-13 00:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:44 INFO   root: Running the installer...
05-13 00:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\translations, languages=['en_US', 'en']
05-13 00:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\translations, languages=['en_US', 'en']
05-13 00:45 DEBUG  WinuiInstallationPage: target_drive=H:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=moh
05-13 00:45 INFO   root: Received settings
05-13 00:45 DEBUG  CommonBackend: Searching for local CD
05-13 00:45 DEBUG  Distro:   checking whether C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp is a valid Ubuntu CD
05-13 00:45 DEBUG  Distro:     does not contain C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\casper\filesystem.squashfs
05-13 00:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-13 00:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-13 00:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-13 00:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-13 00:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-13 00:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-13 00:45 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-13 00:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-13 00:45 DEBUG  CommonBackend: Searching for local ISO
05-13 00:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\translations, languages=['en_US', 'en']
05-13 00:45 DEBUG  TaskList: # Running tasklist...
05-13 00:45 DEBUG  TaskList: ## Running select_target_dir...
05-13 00:45 INFO   WindowsBackend: Installing into H:\ubuntu
05-13 00:45 DEBUG  TaskList: ## Finished select_target_dir
05-13 00:45 DEBUG  TaskList: ## Running create_dir_structure...
05-13 00:45 DEBUG  CommonBackend: Creating dir H:\ubuntu
05-13 00:45 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks
05-13 00:45 DEBUG  CommonBackend: Creating dir H:\ubuntu\install
05-13 00:45 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot
05-13 00:45 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot
05-13 00:45 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot\grub
05-13 00:45 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot\grub
05-13 00:45 DEBUG  TaskList: ## Finished create_dir_structure
05-13 00:45 DEBUG  TaskList: ## Running uncompress_target_dir...
05-13 00:45 DEBUG  TaskList: ## Finished uncompress_target_dir
05-13 00:45 DEBUG  TaskList: ## Running create_uninstaller...
05-13 00:45 DEBUG  WindowsBackend: Copying uninstaller C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup\wubi.exe -> H:\ubuntu\uninstall-wubi.exe
05-13 00:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString H:\ubuntu\uninstall-wubi.exe
05-13 00:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir H:\ubuntu
05-13 00:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-13 00:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon H:\ubuntu\Ubuntu.ico
05-13 00:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 13.04-rev279
05-13 00:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-13 00:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-13 00:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-13 00:45 DEBUG  TaskList: ## Finished create_uninstaller
05-13 00:45 DEBUG  TaskList: ## Running copy_installation_files...
05-13 00:45 DEBUG  WindowsBackend: Copying C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\data\custom-installation -> H:\ubuntu\install\custom-installation
05-13 00:45 DEBUG  WindowsBackend: Copying C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\winboot -> H:\ubuntu\winboot
05-13 00:45 DEBUG  WindowsBackend: Copying C:\Users\MOH\AppData\Local\Temp\pylC0ED.tmp\data\images\Ubuntu.ico -> H:\ubuntu\Ubuntu.ico
05-13 00:45 DEBUG  TaskList: ## Finished copy_installation_files
05-13 00:45 DEBUG  TaskList: ## Running get_iso...
05-13 00:45 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-13 00:45 DEBUG  TaskList: New task get_metalink
05-13 00:45 DEBUG  TaskList: ### Running get_metalink...
05-13 00:45 DEBUG  downloader: downloading [http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.metalink](http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.metalink) > H:\ubuntu\install
05-13 00:45 DEBUG  downloader: Download start filename=H:\ubuntu\install\ubuntu-13.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.metalink, basename=ubuntu-13.04-desktop-amd64.metalink, length=36499, text=None
05-13 00:45 DEBUG  downloader: download finished (read 36499 bytes)
05-13 00:45 DEBUG  downloader: downloading [http://releases.ubuntu.com/13.04/MD5SUMS-metalink](http://releases.ubuntu.com/13.04/MD5SUMS-metalink) > H:\ubuntu\install
05-13 00:45 DEBUG  downloader: Download start filename=H:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/13.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=498, text=None
05-13 00:45 DEBUG  downloader: download finished (read 498 bytes)
05-13 00:45 DEBUG  downloader: downloading [http://releases.ubuntu.com/13.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/13.04/MD5SUMS-metalink.gpg) > H:\ubuntu\install
05-13 00:45 DEBUG  downloader: Download start filename=H:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/13.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-13 00:45 DEBUG  downloader: download finished (read 198 bytes)
05-13 00:45 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-13 00:45 INFO   saplog: Checking block bindings..
05-13 00:45 INFO   saplog: Key verified successfully.
05-13 00:45 DEBUG  CommonBackend: metalink md5sums:
e578445ee73cc1641834fca2542a90ba *ubuntu-13.04-desktop-amd64+mac.metalink
6b2e76fe8853d019d66c34fb0bbaa574 *ubuntu-13.04-desktop-amd64.metalink
02c9c64dcd3359d5224612ed8097adcf *ubuntu-13.04-desktop-i386.metalink
eff9dda8b3a9d69c88f6703729d50174 *ubuntu-13.04-server-amd64+mac.metalink
afafb246cd2ef1ab04803cac3ec554ac *ubuntu-13.04-server-amd64.metalink
98f94e110e069b936fa5ed229136464b *ubuntu-13.04-server-armhf+omap4.metalink
9d09bf70b2a640e12ee8e510d64a553e *ubuntu-13.04-server-i386.metalink


05-13 00:45 ERROR  CommonBackend: The md5 of the metalink does match
05-13 00:45 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
05-13 00:45 DEBUG  TaskList: ### Finished get_metalink
05-13 00:45 DEBUG  TaskList: New task download
05-13 00:45 DEBUG  TaskList: ### Running download...
05-13 00:45 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.iso.torrent) > H:\ubuntu\install\ubuntu-13.04-desktop-amd64.iso
05-13 00:55 DEBUG  TaskList: ### Finished download
05-13 00:55 DEBUG  TaskList: New task check_iso
05-13 00:55 DEBUG  TaskList: ### Running check_iso...
05-13 00:55 DEBUG  CommonBackend: Checking H:\ubuntu\install\ubuntu-13.04-desktop-amd64.iso
05-13 00:55 DEBUG  Distro:   checking Ubuntu ISO H:\ubuntu\install\ubuntu-13.04-desktop-amd64.iso
05-13 00:55 DEBUG  WindowsBackend:   extracting .disk\info from H:\ubuntu\install\ubuntu-13.04-desktop-amd64.iso
05-13 00:55 DEBUG  Distro:   parsing info from str=Ubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
05-13 00:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
05-13 00:55 INFO   Distro: Found a valid iso for Ubuntu: H:\ubuntu\install\ubuntu-13.04-desktop-amd64.iso
05-13 00:55 DEBUG  TaskList: New task get_file_md5
05-13 00:55 DEBUG  TaskList: #### Running get_file_md5...
05-13 00:55 DEBUG  TaskList: #### Finished get_file_md5
05-13 00:55 DEBUG  TaskList: ### Finished check_iso
05-13 00:55 DEBUG  TaskList: ## Finished get_iso
05-13 00:55 DEBUG  TaskList: ## Running extract_kernel...
05-13 00:55 DEBUG  CommonBackend: Extracting files from ISO H:\ubuntu\install\ubuntu-13.04-desktop-amd64.iso
05-13 00:55 DEBUG  WindowsBackend:   extracting md5sum.txt from H:\ubuntu\install\ubuntu-13.04-desktop-amd64.iso
05-13 00:55 DEBUG  WindowsBackend:   extracting casper\vmlinuz.efi from H:\ubuntu\install\ubuntu-13.04-desktop-amd64.iso
05-13 00:55 DEBUG  WindowsBackend:   extracting casper\initrd.lz from H:\ubuntu\install\ubuntu-13.04-desktop-amd64.iso
05-13 00:55 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
05-13 00:55 DEBUG  CommonBackend:   checking H:\ubuntu\install\boot\vmlinuz.efi
05-13 00:55 DEBUG  CommonBackend:   H:\ubuntu\install\boot\vmlinuz.efi md5 = 1919b5acd184538ecb978f6361f98bf1 == 1919b5acd184538ecb978f6361f98bf1
05-13 00:55 DEBUG  CommonBackend:   checking H:\ubuntu\install\boot\initrd.lz
05-13 00:55 DEBUG  CommonBackend:   H:\ubuntu\install\boot\initrd.lz md5 = 1a2c7a01a1d5e6b788bf8266ab55bac9 == 1a2c7a01a1d5e6b788bf8266ab55bac9
05-13 00:55 DEBUG  TaskList: ## Finished extract_kernel
05-13 00:55 DEBUG  TaskList: ## Running choose_disk_sizes...
05-13 00:55 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
05-13 00:55 DEBUG  TaskList: ## Finished choose_disk_sizes
05-13 00:55 DEBUG  TaskList: ## Running create_preseed...
05-13 00:55 DEBUG  TaskList: ## Finished create_preseed
05-13 00:55 DEBUG  TaskList: ## Running modify_bootloader...
05-13 00:55 DEBUG  TaskList: New task modify_bcd
05-13 00:55 DEBUG  TaskList: ### Running modify_bcd...
05-13 00:55 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 697504.871094 mb free ntfs)
05-13 00:55 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {f112dc57-7ca6-11e2-8ab4-a6a97f72b79d} device partition=H:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {f112dc57-7ca6-11e2-8ab4-a6a97f72b79d} device partition=H:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
05-13 00:55 DEBUG  TaskList: # Cancelling tasklist
05-13 00:55 DEBUG  TaskList: New task modify_bcd
05-13 00:55 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {f112dc57-7ca6-11e2-8ab4-a6a97f72b79d} device partition=H:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {f112dc57-7ca6-11e2-8ab4-a6a97f72b79d} device partition=H:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
05-13 00:55 DEBUG  TaskList: New task modify_bcd
05-13 00:55 DEBUG  TaskList: New task modify_bcd
05-13 00:55 DEBUG  TaskList: ## Finished modify_bootloader
05-13 00:55 DEBUG  TaskList: # Finished tasklist

---

### Post by bcbc on 2013-05-13
Dynamic drives aren't supported by linux/ubuntu. The error you're getting is from Windows, but even if it allowed the request, it wouldn't work because Ubuntu can't see that partition: [http://askubuntu.com/q/179215/14916](http://askubuntu.com/q/179215/14916)

---

### Post by mkodaimati on 2013-05-13
Switched Dynamic drives to basic smoothly dual booted. Thanks!

---

