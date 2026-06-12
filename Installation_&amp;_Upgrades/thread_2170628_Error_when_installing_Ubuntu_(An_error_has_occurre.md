---
title: "Error when installing Ubuntu (An error has occurred setting the element data.)"
date: 2013-08-27
forum: Installation &amp; Upgrades
---

### Post by marudits on 2013-08-27
Hi, I have a problem when trying to install Ubuntu on Windows 8 (for dual-boot) by using ISO file (image file). I run wubi.exe from drive DVD_ROM and drive D (Local Disk) but it still same.
This is the error log :


```
08-23 11:13 INFO   root: === wubi 12.10 rev273 ===
08-23 11:13 DEBUG  root: Logfile is c:\users\marudi~1\appdata\local\temp\wubi-12.10-rev273.log
08-23 11:13 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"']
08-23 11:13 DEBUG  CommonBackend: data_dir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp\data
08-23 11:13 DEBUG  WindowsBackend: 7z=C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp\bin\7z.exe
08-23 11:13 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-23 11:13 DEBUG  CommonBackend: Fetching basic info...
08-23 11:13 DEBUG  CommonBackend: original_exe=J:\wubi.exe
08-23 11:13 DEBUG  CommonBackend: platform=win32
08-23 11:13 DEBUG  CommonBackend: osname=nt
08-23 11:13 DEBUG  CommonBackend: language=en_US
08-23 11:13 DEBUG  CommonBackend: encoding=cp1252
08-23 11:13 DEBUG  WindowsBackend: arch=amd64
08-23 11:13 DEBUG  CommonBackend: Parsing isolist=C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp\data\isolist.ini
08-23 11:13 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-23 11:13 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-23 11:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-23 11:13 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-23 11:13 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-23 11:13 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-23 11:13 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-23 11:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-23 11:13 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-23 11:13 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-23 11:13 DEBUG  WindowsBackend: Fetching host info...
08-23 11:13 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-23 11:13 DEBUG  WindowsBackend: windows version=vista
08-23 11:13 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
08-23 11:13 DEBUG  WindowsBackend: windows_sp=None
08-23 11:13 DEBUG  WindowsBackend: windows_build=9200
08-23 11:13 DEBUG  WindowsBackend: gmt=7
08-23 11:13 DEBUG  WindowsBackend: country=US
08-23 11:13 DEBUG  WindowsBackend: timezone=America/New_York
08-23 11:13 DEBUG  WindowsBackend: windows_username=MARUDI TRI S
08-23 11:13 DEBUG  WindowsBackend: user_full_name=MARUDI TRI S
08-23 11:13 DEBUG  WindowsBackend: user_directory=C:\Users\MARUDI TRI S
08-23 11:13 DEBUG  WindowsBackend: windows_language_code=1033
08-23 11:13 DEBUG  WindowsBackend: windows_language=English
08-23 11:13 DEBUG  WindowsBackend: processor_name=AMD A6-4400M APU with Radeon(tm) HD Graphics   
08-23 11:13 DEBUG  WindowsBackend: bootloader=vista
08-23 11:13 DEBUG  WindowsBackend: system_drive=Drive(C: hd 24077.984375 mb free ntfs)
08-23 11:13 DEBUG  WindowsBackend: drive=Drive(C: hd 24077.984375 mb free ntfs)
08-23 11:13 DEBUG  WindowsBackend: drive=Drive(D: hd 23311.78125 mb free ntfs)
08-23 11:13 DEBUG  WindowsBackend: drive=Drive(E: hd 15484.484375 mb free ntfs)
08-23 11:13 DEBUG  WindowsBackend: drive=Drive(F: hd 38329.359375 mb free ntfs)
08-23 11:13 DEBUG  WindowsBackend: drive=Drive(G: hd 21471.1601563 mb free ntfs)
08-23 11:13 DEBUG  WindowsBackend: drive=Drive(H: hd 54153.4492188 mb free ntfs)
08-23 11:13 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
08-23 11:13 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
08-23 11:13 DEBUG  WindowsBackend: uninstaller_path=None
08-23 11:13 DEBUG  WindowsBackend: previous_target_dir=None
08-23 11:13 DEBUG  WindowsBackend: previous_distro_name=None
08-23 11:13 DEBUG  WindowsBackend: keyboard_id=67699721
08-23 11:13 DEBUG  WindowsBackend: keyboard_layout=us
08-23 11:13 DEBUG  WindowsBackend: keyboard_variant=
08-23 11:13 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-23 11:13 DEBUG  CommonBackend: locale=en_US.UTF-8
08-23 11:13 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-23 11:13 DEBUG  CommonBackend: Searching ISOs on USB devices
08-23 11:13 DEBUG  CommonBackend: Searching for local CDs
08-23 11:13 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp is a valid Ubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp is a valid Ubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp is a valid Kubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp is a valid Kubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp is a valid Mythbuntu CD
08-23 11:13 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp is a valid Mythbuntu CD
08-23 11:13 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp is a valid Edubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp is a valid Edubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp is a valid Lubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp is a valid Lubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-23 11:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-23 11:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-23 11:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-23 11:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-23 11:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-23 11:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-23 11:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-23 11:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-23 11:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-23 11:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-23 11:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-23 11:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-23 11:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 11:13 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-23 11:13 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
08-23 11:13 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
08-23 11:13 INFO   Distro: Found a valid CD for Ubuntu: J:\
08-23 11:13 INFO   root: Running the CD menu...
08-23 11:13 DEBUG  WindowsFrontend: __init__...
08-23 11:13 DEBUG  WindowsFrontend: on_init...
08-23 11:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp\translations, languages=['en_US', 'en']
08-23 11:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl8285.tmp\translations, languages=['en_US', 'en']
08-23 11:14 INFO   WindowsFrontend: Operation cancelled
08-23 11:14 DEBUG  WindowsFrontend: frontend.quit
08-23 11:14 DEBUG  WindowsFrontend: frontend.on_quit
08-23 11:14 DEBUG  root: application.on_quit
08-23 11:14 INFO   root: sys.exit
08-23 13:35 INFO   root: === wubi 12.10 rev273 ===
08-23 13:35 DEBUG  root: Logfile is c:\users\marudi~1\appdata\local\temp\wubi-12.10-rev273.log
08-23 13:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"']
08-23 13:35 DEBUG  CommonBackend: data_dir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp\data
08-23 13:35 DEBUG  WindowsBackend: 7z=C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp\bin\7z.exe
08-23 13:35 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-23 13:35 DEBUG  CommonBackend: Fetching basic info...
08-23 13:35 DEBUG  CommonBackend: original_exe=J:\wubi.exe
08-23 13:35 DEBUG  CommonBackend: platform=win32
08-23 13:35 DEBUG  CommonBackend: osname=nt
08-23 13:35 DEBUG  CommonBackend: language=en_US
08-23 13:35 DEBUG  CommonBackend: encoding=cp1252
08-23 13:35 DEBUG  WindowsBackend: arch=amd64
08-23 13:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp\data\isolist.ini
08-23 13:35 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-23 13:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-23 13:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-23 13:35 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-23 13:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-23 13:35 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-23 13:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-23 13:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-23 13:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-23 13:35 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-23 13:35 DEBUG  WindowsBackend: Fetching host info...
08-23 13:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-23 13:35 DEBUG  WindowsBackend: windows version=vista
08-23 13:35 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
08-23 13:35 DEBUG  WindowsBackend: windows_sp=None
08-23 13:35 DEBUG  WindowsBackend: windows_build=9200
08-23 13:35 DEBUG  WindowsBackend: gmt=7
08-23 13:35 DEBUG  WindowsBackend: country=US
08-23 13:35 DEBUG  WindowsBackend: timezone=America/New_York
08-23 13:35 DEBUG  WindowsBackend: windows_username=MARUDI TRI S
08-23 13:35 DEBUG  WindowsBackend: user_full_name=MARUDI TRI S
08-23 13:35 DEBUG  WindowsBackend: user_directory=C:\Users\MARUDI TRI S
08-23 13:35 DEBUG  WindowsBackend: windows_language_code=1033
08-23 13:35 DEBUG  WindowsBackend: windows_language=English
08-23 13:35 DEBUG  WindowsBackend: processor_name=AMD A6-4400M APU with Radeon(tm) HD Graphics   
08-23 13:35 DEBUG  WindowsBackend: bootloader=vista
08-23 13:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 24242.15625 mb free ntfs)
08-23 13:35 DEBUG  WindowsBackend: drive=Drive(C: hd 24242.15625 mb free ntfs)
08-23 13:35 DEBUG  WindowsBackend: drive=Drive(D: hd 23311.78125 mb free ntfs)
08-23 13:35 DEBUG  WindowsBackend: drive=Drive(E: hd 15484.484375 mb free ntfs)
08-23 13:35 DEBUG  WindowsBackend: drive=Drive(F: hd 38329.359375 mb free ntfs)
08-23 13:35 DEBUG  WindowsBackend: drive=Drive(G: hd 21468.4257813 mb free ntfs)
08-23 13:35 DEBUG  WindowsBackend: drive=Drive(H: hd 54110.0507813 mb free ntfs)
08-23 13:35 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
08-23 13:35 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
08-23 13:35 DEBUG  WindowsBackend: uninstaller_path=None
08-23 13:35 DEBUG  WindowsBackend: previous_target_dir=None
08-23 13:35 DEBUG  WindowsBackend: previous_distro_name=None
08-23 13:35 DEBUG  WindowsBackend: keyboard_id=67699721
08-23 13:35 DEBUG  WindowsBackend: keyboard_layout=us
08-23 13:35 DEBUG  WindowsBackend: keyboard_variant=
08-23 13:35 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-23 13:35 DEBUG  CommonBackend: locale=en_US.UTF-8
08-23 13:35 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-23 13:35 DEBUG  CommonBackend: Searching ISOs on USB devices
08-23 13:35 DEBUG  CommonBackend: Searching for local CDs
08-23 13:35 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp is a valid Ubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp is a valid Ubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp is a valid Kubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp is a valid Kubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp is a valid Mythbuntu CD
08-23 13:35 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp is a valid Mythbuntu CD
08-23 13:35 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp is a valid Edubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp is a valid Edubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp is a valid Lubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp is a valid Lubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-23 13:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-23 13:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-23 13:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-23 13:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-23 13:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-23 13:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-23 13:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-23 13:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-23 13:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-23 13:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-23 13:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-23 13:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-23 13:35 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:35 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-23 13:35 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
08-23 13:35 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
08-23 13:35 INFO   Distro: Found a valid CD for Ubuntu: J:\
08-23 13:35 INFO   root: Running the CD menu...
08-23 13:35 DEBUG  WindowsFrontend: __init__...
08-23 13:35 DEBUG  WindowsFrontend: on_init...
08-23 13:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp\translations, languages=['en_US', 'en']
08-23 13:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl1A73.tmp\translations, languages=['en_US', 'en']
08-23 13:35 INFO   root: CD menu finished
08-23 13:35 INFO   root: Rebooting
08-23 13:35 DEBUG  TaskList: # Running tasklist...
08-23 13:35 DEBUG  TaskList: ## Running reboot...
08-23 13:35 DEBUG  TaskList: ## Finished reboot
08-23 13:35 DEBUG  TaskList: # Finished tasklist
08-23 13:35 DEBUG  root: application.quit
08-23 13:35 DEBUG  WindowsFrontend: frontend.quit
08-23 13:35 DEBUG  WindowsFrontend: frontend.on_quit
08-23 13:35 DEBUG  root: application.on_quit
08-23 13:35 INFO   root: sys.exit
08-23 13:43 INFO   root: === wubi 12.10 rev273 ===
08-23 13:43 DEBUG  root: Logfile is c:\users\marudi~1\appdata\local\temp\wubi-12.10-rev273.log
08-23 13:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"']
08-23 13:43 DEBUG  CommonBackend: data_dir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp\data
08-23 13:43 DEBUG  WindowsBackend: 7z=C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp\bin\7z.exe
08-23 13:43 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-23 13:43 DEBUG  CommonBackend: Fetching basic info...
08-23 13:43 DEBUG  CommonBackend: original_exe=J:\wubi.exe
08-23 13:43 DEBUG  CommonBackend: platform=win32
08-23 13:43 DEBUG  CommonBackend: osname=nt
08-23 13:43 DEBUG  CommonBackend: language=en_US
08-23 13:43 DEBUG  CommonBackend: encoding=cp1252
08-23 13:43 DEBUG  WindowsBackend: arch=amd64
08-23 13:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp\data\isolist.ini
08-23 13:43 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-23 13:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-23 13:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-23 13:43 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-23 13:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-23 13:43 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-23 13:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-23 13:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-23 13:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-23 13:43 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-23 13:43 DEBUG  WindowsBackend: Fetching host info...
08-23 13:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-23 13:43 DEBUG  WindowsBackend: windows version=vista
08-23 13:43 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
08-23 13:43 DEBUG  WindowsBackend: windows_sp=None
08-23 13:43 DEBUG  WindowsBackend: windows_build=9200
08-23 13:43 DEBUG  WindowsBackend: gmt=7
08-23 13:43 DEBUG  WindowsBackend: country=US
08-23 13:43 DEBUG  WindowsBackend: timezone=America/New_York
08-23 13:43 DEBUG  WindowsBackend: windows_username=MARUDI TRI S
08-23 13:43 DEBUG  WindowsBackend: user_full_name=MARUDI TRI S
08-23 13:43 DEBUG  WindowsBackend: user_directory=C:\Users\MARUDI TRI S
08-23 13:43 DEBUG  WindowsBackend: windows_language_code=1033
08-23 13:43 DEBUG  WindowsBackend: windows_language=English
08-23 13:43 DEBUG  WindowsBackend: processor_name=AMD A6-4400M APU with Radeon(tm) HD Graphics   
08-23 13:43 DEBUG  WindowsBackend: bootloader=vista
08-23 13:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 24292.8085938 mb free ntfs)
08-23 13:43 DEBUG  WindowsBackend: drive=Drive(C: hd 24292.8085938 mb free ntfs)
08-23 13:43 DEBUG  WindowsBackend: drive=Drive(D: hd 23312.2851563 mb free ntfs)
08-23 13:43 DEBUG  WindowsBackend: drive=Drive(E: hd 15484.484375 mb free ntfs)
08-23 13:43 DEBUG  WindowsBackend: drive=Drive(F: hd 38329.359375 mb free ntfs)
08-23 13:43 DEBUG  WindowsBackend: drive=Drive(G: hd 21468.4257813 mb free ntfs)
08-23 13:43 DEBUG  WindowsBackend: drive=Drive(H: hd 54111.0546875 mb free ntfs)
08-23 13:43 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
08-23 13:43 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
08-23 13:43 DEBUG  WindowsBackend: uninstaller_path=None
08-23 13:43 DEBUG  WindowsBackend: previous_target_dir=None
08-23 13:43 DEBUG  WindowsBackend: previous_distro_name=None
08-23 13:43 DEBUG  WindowsBackend: keyboard_id=67699721
08-23 13:43 DEBUG  WindowsBackend: keyboard_layout=us
08-23 13:43 DEBUG  WindowsBackend: keyboard_variant=
08-23 13:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-23 13:43 DEBUG  CommonBackend: locale=en_US.UTF-8
08-23 13:43 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-23 13:43 DEBUG  CommonBackend: Searching ISOs on USB devices
08-23 13:43 DEBUG  CommonBackend: Searching for local CDs
08-23 13:43 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp is a valid Ubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp is a valid Ubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp is a valid Kubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp is a valid Kubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp is a valid Mythbuntu CD
08-23 13:43 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp is a valid Mythbuntu CD
08-23 13:43 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp is a valid Edubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp is a valid Edubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp is a valid Lubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp is a valid Lubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-23 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-23 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-23 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-23 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-23 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-23 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-23 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-23 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-23 13:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-23 13:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-23 13:43 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-23 13:43 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-23 13:43 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:43 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-23 13:43 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
08-23 13:43 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
08-23 13:43 INFO   Distro: Found a valid CD for Ubuntu: J:\
08-23 13:43 INFO   root: Running the CD menu...
08-23 13:43 DEBUG  WindowsFrontend: __init__...
08-23 13:43 DEBUG  WindowsFrontend: on_init...
08-23 13:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp\translations, languages=['en_US', 'en']
08-23 13:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl643E.tmp\translations, languages=['en_US', 'en']
08-23 13:43 DEBUG  root: application.quit
08-23 13:43 DEBUG  WindowsFrontend: frontend.quit
08-23 13:43 DEBUG  WindowsFrontend: frontend.on_quit
08-23 13:43 DEBUG  root: application.on_quit
08-23 13:43 INFO   root: sys.exit
08-23 13:44 INFO   root: === wubi 12.10 rev273 ===
08-23 13:44 DEBUG  root: Logfile is c:\users\marudi~1\appdata\local\temp\wubi-12.10-rev273.log
08-23 13:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"']
08-23 13:44 DEBUG  CommonBackend: data_dir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp\data
08-23 13:44 DEBUG  WindowsBackend: 7z=C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp\bin\7z.exe
08-23 13:44 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-23 13:44 DEBUG  CommonBackend: Fetching basic info...
08-23 13:44 DEBUG  CommonBackend: original_exe=J:\wubi.exe
08-23 13:44 DEBUG  CommonBackend: platform=win32
08-23 13:44 DEBUG  CommonBackend: osname=nt
08-23 13:44 DEBUG  CommonBackend: language=en_US
08-23 13:44 DEBUG  CommonBackend: encoding=cp1252
08-23 13:44 DEBUG  WindowsBackend: arch=amd64
08-23 13:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp\data\isolist.ini
08-23 13:44 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-23 13:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-23 13:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-23 13:44 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-23 13:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-23 13:44 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-23 13:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-23 13:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-23 13:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-23 13:44 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-23 13:44 DEBUG  WindowsBackend: Fetching host info...
08-23 13:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-23 13:44 DEBUG  WindowsBackend: windows version=vista
08-23 13:44 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
08-23 13:44 DEBUG  WindowsBackend: windows_sp=None
08-23 13:44 DEBUG  WindowsBackend: windows_build=9200
08-23 13:44 DEBUG  WindowsBackend: gmt=7
08-23 13:44 DEBUG  WindowsBackend: country=US
08-23 13:44 DEBUG  WindowsBackend: timezone=America/New_York
08-23 13:44 DEBUG  WindowsBackend: windows_username=MARUDI TRI S
08-23 13:44 DEBUG  WindowsBackend: user_full_name=MARUDI TRI S
08-23 13:44 DEBUG  WindowsBackend: user_directory=C:\Users\MARUDI TRI S
08-23 13:44 DEBUG  WindowsBackend: windows_language_code=1033
08-23 13:44 DEBUG  WindowsBackend: windows_language=English
08-23 13:44 DEBUG  WindowsBackend: processor_name=AMD A6-4400M APU with Radeon(tm) HD Graphics   
08-23 13:44 DEBUG  WindowsBackend: bootloader=vista
08-23 13:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 24286.9882813 mb free ntfs)
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(C: hd 24286.9882813 mb free ntfs)
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(D: hd 23312.2851563 mb free ntfs)
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(E: hd 15484.484375 mb free ntfs)
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(F: hd 38329.359375 mb free ntfs)
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(G: hd 21468.4257813 mb free ntfs)
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(H: hd 54111.0546875 mb free ntfs)
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
08-23 13:44 DEBUG  WindowsBackend: uninstaller_path=None
08-23 13:44 DEBUG  WindowsBackend: previous_target_dir=None
08-23 13:44 DEBUG  WindowsBackend: previous_distro_name=None
08-23 13:44 DEBUG  WindowsBackend: keyboard_id=67699721
08-23 13:44 DEBUG  WindowsBackend: keyboard_layout=us
08-23 13:44 DEBUG  WindowsBackend: keyboard_variant=
08-23 13:44 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-23 13:44 DEBUG  CommonBackend: locale=en_US.UTF-8
08-23 13:44 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-23 13:44 DEBUG  CommonBackend: Searching ISOs on USB devices
08-23 13:44 DEBUG  CommonBackend: Searching for local CDs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
08-23 13:44 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
08-23 13:44 INFO   Distro: Found a valid CD for Ubuntu: J:\
08-23 13:44 INFO   root: Running the CD menu...
08-23 13:44 DEBUG  WindowsFrontend: __init__...
08-23 13:44 DEBUG  WindowsFrontend: on_init...
08-23 13:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp\translations, languages=['en_US', 'en']
08-23 13:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl4F38.tmp\translations, languages=['en_US', 'en']
08-23 13:44 DEBUG  root: application.quit
08-23 13:44 DEBUG  WindowsFrontend: frontend.quit
08-23 13:44 DEBUG  WindowsFrontend: frontend.on_quit
08-23 13:44 DEBUG  root: application.on_quit
08-23 13:44 INFO   root: sys.exit
08-23 13:44 INFO   root: === wubi 12.10 rev273 ===
08-23 13:44 DEBUG  root: Logfile is c:\users\marudi~1\appdata\local\temp\wubi-12.10-rev273.log
08-23 13:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"']
08-23 13:44 DEBUG  CommonBackend: data_dir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\data
08-23 13:44 DEBUG  WindowsBackend: 7z=C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\bin\7z.exe
08-23 13:44 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-23 13:44 DEBUG  CommonBackend: Fetching basic info...
08-23 13:44 DEBUG  CommonBackend: original_exe=J:\wubi.exe
08-23 13:44 DEBUG  CommonBackend: platform=win32
08-23 13:44 DEBUG  CommonBackend: osname=nt
08-23 13:44 DEBUG  CommonBackend: language=en_US
08-23 13:44 DEBUG  CommonBackend: encoding=cp1252
08-23 13:44 DEBUG  WindowsBackend: arch=amd64
08-23 13:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\data\isolist.ini
08-23 13:44 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-23 13:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-23 13:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-23 13:44 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-23 13:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-23 13:44 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-23 13:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-23 13:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-23 13:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-23 13:44 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-23 13:44 DEBUG  WindowsBackend: Fetching host info...
08-23 13:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-23 13:44 DEBUG  WindowsBackend: windows version=vista
08-23 13:44 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
08-23 13:44 DEBUG  WindowsBackend: windows_sp=None
08-23 13:44 DEBUG  WindowsBackend: windows_build=9200
08-23 13:44 DEBUG  WindowsBackend: gmt=7
08-23 13:44 DEBUG  WindowsBackend: country=US
08-23 13:44 DEBUG  WindowsBackend: timezone=America/New_York
08-23 13:44 DEBUG  WindowsBackend: windows_username=MARUDI TRI S
08-23 13:44 DEBUG  WindowsBackend: user_full_name=MARUDI TRI S
08-23 13:44 DEBUG  WindowsBackend: user_directory=C:\Users\MARUDI TRI S
08-23 13:44 DEBUG  WindowsBackend: windows_language_code=1033
08-23 13:44 DEBUG  WindowsBackend: windows_language=English
08-23 13:44 DEBUG  WindowsBackend: processor_name=AMD A6-4400M APU with Radeon(tm) HD Graphics   
08-23 13:44 DEBUG  WindowsBackend: bootloader=vista
08-23 13:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 24286.703125 mb free ntfs)
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(C: hd 24286.703125 mb free ntfs)
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(D: hd 23312.2851563 mb free ntfs)
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(E: hd 15484.484375 mb free ntfs)
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(F: hd 38329.359375 mb free ntfs)
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(G: hd 21468.4257813 mb free ntfs)
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(H: hd 54111.0546875 mb free ntfs)
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
08-23 13:44 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
08-23 13:44 DEBUG  WindowsBackend: uninstaller_path=None
08-23 13:44 DEBUG  WindowsBackend: previous_target_dir=None
08-23 13:44 DEBUG  WindowsBackend: previous_distro_name=None
08-23 13:44 DEBUG  WindowsBackend: keyboard_id=67699721
08-23 13:44 DEBUG  WindowsBackend: keyboard_layout=us
08-23 13:44 DEBUG  WindowsBackend: keyboard_variant=
08-23 13:44 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-23 13:44 DEBUG  CommonBackend: locale=en_US.UTF-8
08-23 13:44 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-23 13:44 DEBUG  CommonBackend: Searching ISOs on USB devices
08-23 13:44 DEBUG  CommonBackend: Searching for local CDs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-23 13:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-23 13:44 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-23 13:44 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
08-23 13:44 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
08-23 13:44 INFO   Distro: Found a valid CD for Ubuntu: J:\
08-23 13:44 INFO   root: Running the CD menu...
08-23 13:44 DEBUG  WindowsFrontend: __init__...
08-23 13:44 DEBUG  WindowsFrontend: on_init...
08-23 13:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\translations, languages=['en_US', 'en']
08-23 13:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\translations, languages=['en_US', 'en']
08-23 13:44 INFO   root: CD menu finished
08-23 13:44 INFO   root: Running the CD boot helper...
08-23 13:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\translations, languages=['en_US', 'en']
08-23 13:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\translations, languages=['en_US', 'en']
08-23 13:44 INFO   root: CD boot helper confirmed
08-23 13:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\translations, languages=['en_US', 'en']
08-23 13:44 DEBUG  TaskList: # Running tasklist...
08-23 13:44 DEBUG  TaskList: ## Running select_target_dir...
08-23 13:44 INFO   WindowsBackend: Installing into C:\ubuntu
08-23 13:44 DEBUG  TaskList: ## Finished select_target_dir
08-23 13:44 DEBUG  TaskList: ## Running create_dir_structure...
08-23 13:44 DEBUG  CommonBackend: Creating dir C:\ubuntu
08-23 13:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
08-23 13:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
08-23 13:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
08-23 13:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
08-23 13:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
08-23 13:44 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
08-23 13:44 DEBUG  TaskList: ## Finished create_dir_structure
08-23 13:44 DEBUG  TaskList: ## Running uncompress_target_dir...
08-23 13:44 DEBUG  TaskList: ## Finished uncompress_target_dir
08-23 13:44 DEBUG  TaskList: ## Running create_uninstaller...
08-23 13:44 DEBUG  WindowsBackend: Copying uninstaller J:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
08-23 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
08-23 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
08-23 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-23 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
08-23 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
08-23 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-23 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-23 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-23 13:44 DEBUG  TaskList: ## Finished create_uninstaller
08-23 13:44 DEBUG  TaskList: ## Running copy_installation_files...
08-23 13:44 DEBUG  WindowsBackend: Copying C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
08-23 13:44 DEBUG  WindowsBackend: Copying C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\winboot -> C:\ubuntu\winboot
08-23 13:44 DEBUG  WindowsBackend: Copying C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
08-23 13:44 DEBUG  TaskList: ## Finished copy_installation_files
08-23 13:44 DEBUG  TaskList: ## Running use_cd...
08-23 13:44 DEBUG  TaskList: New task copy_file
08-23 13:44 DEBUG  TaskList: ### Running copy_file...
08-23 13:45 DEBUG  TaskList: ### Finished copy_file
08-23 13:45 DEBUG  TaskList: New task check_iso
08-23 13:45 DEBUG  TaskList: ### Running check_iso...
08-23 13:45 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
08-23 13:45 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
08-23 13:45 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
08-23 13:45 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
08-23 13:45 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
08-23 13:45 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
08-23 13:45 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
08-23 13:45 DEBUG  TaskList: New task get_metalink
08-23 13:45 DEBUG  TaskList: #### Running get_metalink...
08-23 13:45 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) > C:\ubuntu\install
08-23 13:45 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) err=SSLFactory instance has no attribute 'get_https_connection'
08-23 13:45 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) > C:\ubuntu\install
08-23 13:45 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) err=SSLFactory instance has no attribute 'get_https_connection'
08-23 13:45 DEBUG  TaskList: #### Finished get_metalink
08-23 13:45 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for C:\ubuntu\install\installation.iso, ignoring
08-23 13:45 DEBUG  TaskList: ### Finished check_iso
08-23 13:45 DEBUG  TaskList: ## Finished use_cd
08-23 13:45 DEBUG  TaskList: ## Running extract_kernel...
08-23 13:45 DEBUG  CommonBackend: Copying files from CD J:\
08-23 13:45 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
08-23 13:45 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
08-23 13:45 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = dedeef44f082210eb0d605d21837feb5 == dedeef44f082210eb0d605d21837feb5
08-23 13:45 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
08-23 13:45 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = bf4099046c27293af1f7ec8c76baf1c7 == bf4099046c27293af1f7ec8c76baf1c7
08-23 13:45 DEBUG  TaskList: ## Finished extract_kernel
08-23 13:45 DEBUG  TaskList: ## Running create_preseed_cdboot...
08-23 13:45 DEBUG  TaskList: ## Finished create_preseed_cdboot
08-23 13:45 DEBUG  TaskList: ## Running modify_bootloader...
08-23 13:45 DEBUG  TaskList: New task modify_bcd
08-23 13:45 DEBUG  TaskList: ### Running modify_bcd...
08-23 13:45 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 24286.703125 mb free ntfs)
08-23 13:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {ab334397-0bbf-11e3-afee-50b7c3b19288}
08-23 13:46 DEBUG  TaskList: ### Finished modify_bcd
08-23 13:46 DEBUG  TaskList: New task modify_bcd
08-23 13:46 DEBUG  TaskList: ### Running modify_bcd...
08-23 13:46 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 23312.2851563 mb free ntfs)
08-23 13:46 DEBUG  WindowsBackend: BCD has already been modified
08-23 13:46 DEBUG  TaskList: ### Finished modify_bcd
08-23 13:46 DEBUG  TaskList: New task modify_bcd
08-23 13:46 DEBUG  TaskList: ### Running modify_bcd...
08-23 13:46 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 15484.484375 mb free ntfs)
08-23 13:46 DEBUG  WindowsBackend: BCD has already been modified
08-23 13:46 DEBUG  TaskList: ### Finished modify_bcd
08-23 13:46 DEBUG  TaskList: New task modify_bcd
08-23 13:46 DEBUG  TaskList: ### Running modify_bcd...
08-23 13:46 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 38329.359375 mb free ntfs)
08-23 13:46 DEBUG  WindowsBackend: BCD has already been modified
08-23 13:46 DEBUG  TaskList: ### Finished modify_bcd
08-23 13:46 DEBUG  TaskList: New task modify_bcd
08-23 13:46 DEBUG  TaskList: ### Running modify_bcd...
08-23 13:46 DEBUG  WindowsBackend: modify_bcd Drive(G: hd 21468.4257813 mb free ntfs)
08-23 13:46 DEBUG  WindowsBackend: BCD has already been modified
08-23 13:46 DEBUG  TaskList: ### Finished modify_bcd
08-23 13:46 DEBUG  TaskList: New task modify_bcd
08-23 13:46 DEBUG  TaskList: ### Running modify_bcd...
08-23 13:46 DEBUG  WindowsBackend: modify_bcd Drive(H: hd 54111.0546875 mb free ntfs)
08-23 13:46 DEBUG  WindowsBackend: BCD has already been modified
08-23 13:46 DEBUG  TaskList: ### Finished modify_bcd
08-23 13:46 DEBUG  TaskList: ## Finished modify_bootloader
08-23 13:46 DEBUG  TaskList: ## Running modify_grub_configuration...
08-23 13:46 DEBUG  TaskList: ## Finished modify_grub_configuration
08-23 13:46 DEBUG  TaskList: ## Running uncompress_files...
08-23 13:46 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
08-23 13:46 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
08-23 13:46 DEBUG  TaskList: ## Finished uncompress_files
08-23 13:46 DEBUG  TaskList: ## Running eject_cd...
08-23 13:46 DEBUG  TaskList: ## Finished eject_cd
08-23 13:46 DEBUG  TaskList: # Finished tasklist
08-23 13:46 INFO   root: Almost finished installing
08-23 13:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl9607.tmp\translations, languages=['en_US', 'en']
08-23 13:46 INFO   root: Finished installation
08-23 13:46 INFO   root: Rebooting
08-23 13:46 DEBUG  TaskList: # Running tasklist...
08-23 13:46 DEBUG  TaskList: ## Running reboot...
08-23 13:46 DEBUG  TaskList: ## Finished reboot
08-23 13:46 DEBUG  TaskList: # Finished tasklist
08-23 13:46 DEBUG  root: application.quit
08-23 13:46 DEBUG  WindowsFrontend: frontend.quit
08-23 13:46 DEBUG  WindowsFrontend: frontend.on_quit
08-23 13:46 DEBUG  root: application.on_quit
08-23 13:46 INFO   root: sys.exit
07-01 10:18 INFO   root: === wubi 12.10 rev273 ===
07-01 10:18 DEBUG  root: Logfile is c:\users\marudi~1\appdata\local\temp\wubi-12.10-rev273.log
07-01 10:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
07-01 10:18 DEBUG  CommonBackend: data_dir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\data
07-01 10:18 DEBUG  WindowsBackend: 7z=C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\bin\7z.exe
07-01 10:18 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-01 10:18 DEBUG  CommonBackend: Fetching basic info...
07-01 10:18 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
07-01 10:18 DEBUG  CommonBackend: platform=win32
07-01 10:18 DEBUG  CommonBackend: osname=nt
07-01 10:18 DEBUG  CommonBackend: language=en_US
07-01 10:18 DEBUG  CommonBackend: encoding=cp1252
07-01 10:18 DEBUG  WindowsBackend: arch=amd64
07-01 10:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\data\isolist.ini
07-01 10:18 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-01 10:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-01 10:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-01 10:18 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-01 10:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-01 10:18 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-01 10:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-01 10:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-01 10:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-01 10:18 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-01 10:18 DEBUG  WindowsBackend: Fetching host info...
07-01 10:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-01 10:18 DEBUG  WindowsBackend: windows version=vista
07-01 10:18 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
07-01 10:18 DEBUG  WindowsBackend: windows_sp=None
07-01 10:18 DEBUG  WindowsBackend: windows_build=9200
07-01 10:18 DEBUG  WindowsBackend: gmt=7
07-01 10:18 DEBUG  WindowsBackend: country=US
07-01 10:18 DEBUG  WindowsBackend: timezone=America/New_York
07-01 10:18 DEBUG  WindowsBackend: windows_username=MARUDI TRI S
07-01 10:18 DEBUG  WindowsBackend: user_full_name=MARUDI TRI S
07-01 10:18 DEBUG  WindowsBackend: user_directory=C:\Users\MARUDI TRI S
07-01 10:18 DEBUG  WindowsBackend: windows_language_code=1033
07-01 10:18 DEBUG  WindowsBackend: windows_language=English
07-01 10:18 DEBUG  WindowsBackend: processor_name=AMD A6-4400M APU with Radeon(tm) HD Graphics   
07-01 10:18 DEBUG  WindowsBackend: bootloader=vista
07-01 10:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 25901.2890625 mb free ntfs)
07-01 10:18 DEBUG  WindowsBackend: drive=Drive(C: hd 25901.2890625 mb free ntfs)
07-01 10:18 DEBUG  WindowsBackend: drive=Drive(D: hd 23312.2851563 mb free ntfs)
07-01 10:18 DEBUG  WindowsBackend: drive=Drive(E: hd 15484.484375 mb free ntfs)
07-01 10:18 DEBUG  WindowsBackend: drive=Drive(F: hd 38329.359375 mb free ntfs)
07-01 10:18 DEBUG  WindowsBackend: drive=Drive(G: hd 21468.09375 mb free ntfs)
07-01 10:18 DEBUG  WindowsBackend: drive=Drive(H: hd 52142.7695313 mb free ntfs)
07-01 10:18 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-01 10:18 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free udf)
07-01 10:18 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-01 10:18 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-01 10:18 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-01 10:18 DEBUG  WindowsBackend: keyboard_id=67699721
07-01 10:18 DEBUG  WindowsBackend: keyboard_layout=us
07-01 10:18 DEBUG  WindowsBackend: keyboard_variant=
07-01 10:18 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-01 10:18 DEBUG  CommonBackend: locale=en_US.UTF-8
07-01 10:18 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-01 10:18 DEBUG  CommonBackend: Searching ISOs on USB devices
07-01 10:18 DEBUG  CommonBackend: Searching for local CDs
07-01 10:18 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
07-01 10:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-01 10:18 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
07-01 10:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-01 10:18 INFO   root: Running the uninstaller...
07-01 10:18 INFO   CommonBackend: This is the uninstaller running
07-01 10:18 DEBUG  WindowsFrontend: __init__...
07-01 10:18 DEBUG  WindowsFrontend: on_init...
07-01 10:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\translations, languages=['en_US', 'en']
07-01 10:18 INFO   root: Received settings
07-01 10:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\translations, languages=['en_US', 'en']
07-01 10:18 DEBUG  TaskList: # Running tasklist...
07-01 10:18 DEBUG  TaskList: ## Running Remove bootloader entry...
07-01 10:18 DEBUG  WindowsBackend: Removing bcd entry {ab334397-0bbf-11e3-afee-50b7c3b19288}
07-01 10:18 ERROR  WindowsBackend: Error executing command
>>command=C:\WINDOWS\System32\bcdedit.exe /delete {ab334397-0bbf-11e3-afee-50b7c3b19288} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.


The system cannot find the file specified.




>>stdout=
07-01 10:18 DEBUG  WindowsBackend: undo_bootini C:
07-01 10:18 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 25901.2890625 mb free ntfs)
07-01 10:18 DEBUG  WindowsBackend: undo_bootini D:
07-01 10:18 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 23312.2851563 mb free ntfs)
07-01 10:18 DEBUG  WindowsBackend: undo_bootini E:
07-01 10:18 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 15484.484375 mb free ntfs)
07-01 10:18 DEBUG  WindowsBackend: undo_bootini F:
07-01 10:18 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 38329.359375 mb free ntfs)
07-01 10:18 DEBUG  WindowsBackend: undo_bootini G:
07-01 10:18 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 21468.09375 mb free ntfs)
07-01 10:18 DEBUG  WindowsBackend: undo_bootini H:
07-01 10:18 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 52142.7695313 mb free ntfs)
07-01 10:18 DEBUG  TaskList: ## Finished Remove bootloader entry
07-01 10:18 DEBUG  TaskList: ## Running Remove target dir...
07-01 10:18 DEBUG  CommonBackend: Deleting C:\ubuntu
07-01 10:18 DEBUG  TaskList: ## Finished Remove target dir
07-01 10:18 DEBUG  TaskList: ## Running Remove registry key...
07-01 10:18 DEBUG  TaskList: ## Finished Remove registry key
07-01 10:18 DEBUG  TaskList: # Finished tasklist
07-01 10:18 INFO   root: Almost finished uninstalling
07-01 10:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl156A.tmp\translations, languages=['en_US', 'en']
07-01 10:18 INFO   root: Finished uninstallation
07-01 10:18 DEBUG  root: application.quit
07-01 10:18 DEBUG  WindowsFrontend: frontend.quit
07-01 10:18 DEBUG  WindowsFrontend: frontend.on_quit
07-01 10:18 DEBUG  root: application.on_quit
07-01 10:18 INFO   root: sys.exit
08-27 10:53 INFO   root: === wubi 12.10 rev273 ===
08-27 10:53 DEBUG  root: Logfile is c:\users\marudi~1\appdata\local\temp\wubi-12.10-rev273.log
08-27 10:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"']
08-27 10:53 DEBUG  CommonBackend: data_dir=C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp\data
08-27 10:53 DEBUG  WindowsBackend: 7z=C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp\bin\7z.exe
08-27 10:53 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-27 10:53 DEBUG  CommonBackend: Fetching basic info...
08-27 10:53 DEBUG  CommonBackend: original_exe=J:\wubi.exe
08-27 10:53 DEBUG  CommonBackend: platform=win32
08-27 10:53 DEBUG  CommonBackend: osname=nt
08-27 10:53 DEBUG  CommonBackend: language=en_US
08-27 10:53 DEBUG  CommonBackend: encoding=cp1252
08-27 10:53 DEBUG  WindowsBackend: arch=amd64
08-27 10:53 DEBUG  CommonBackend: Parsing isolist=C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp\data\isolist.ini
08-27 10:53 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-27 10:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-27 10:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-27 10:53 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-27 10:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-27 10:53 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-27 10:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-27 10:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-27 10:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-27 10:53 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-27 10:53 DEBUG  WindowsBackend: Fetching host info...
08-27 10:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-27 10:53 DEBUG  WindowsBackend: windows version=vista
08-27 10:53 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
08-27 10:53 DEBUG  WindowsBackend: windows_sp=None
08-27 10:53 DEBUG  WindowsBackend: windows_build=9200
08-27 10:53 DEBUG  WindowsBackend: gmt=7
08-27 10:53 DEBUG  WindowsBackend: country=US
08-27 10:53 DEBUG  WindowsBackend: timezone=America/New_York
08-27 10:53 DEBUG  WindowsBackend: windows_username=MARUDI TRI S
08-27 10:53 DEBUG  WindowsBackend: user_full_name=MARUDI TRI S
08-27 10:53 DEBUG  WindowsBackend: user_directory=C:\Users\MARUDI TRI S
08-27 10:53 DEBUG  WindowsBackend: windows_language_code=1033
08-27 10:53 DEBUG  WindowsBackend: windows_language=English
08-27 10:53 DEBUG  WindowsBackend: processor_name=AMD A6-4400M APU with Radeon(tm) HD Graphics   
08-27 10:53 DEBUG  WindowsBackend: bootloader=vista
08-27 10:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 26727.8046875 mb free ntfs)
08-27 10:53 DEBUG  WindowsBackend: drive=Drive(C: hd 26727.8046875 mb free ntfs)
08-27 10:53 DEBUG  WindowsBackend: drive=Drive(D: hd 23313.1289063 mb free ntfs)
08-27 10:53 DEBUG  WindowsBackend: drive=Drive(E: hd 15484.484375 mb free ntfs)
08-27 10:53 DEBUG  WindowsBackend: drive=Drive(F: hd 38329.3515625 mb free ntfs)
08-27 10:53 DEBUG  WindowsBackend: drive=Drive(G: hd 21467.7578125 mb free ntfs)
08-27 10:53 DEBUG  WindowsBackend: drive=Drive(H: hd 51904.7148438 mb free ntfs)
08-27 10:53 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
08-27 10:53 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
08-27 10:53 DEBUG  WindowsBackend: uninstaller_path=None
08-27 10:53 DEBUG  WindowsBackend: previous_target_dir=None
08-27 10:53 DEBUG  WindowsBackend: previous_distro_name=None
08-27 10:53 DEBUG  WindowsBackend: keyboard_id=67699721
08-27 10:53 DEBUG  WindowsBackend: keyboard_layout=us
08-27 10:53 DEBUG  WindowsBackend: keyboard_variant=
08-27 10:53 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-27 10:53 DEBUG  CommonBackend: locale=en_US.UTF-8
08-27 10:53 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-27 10:53 DEBUG  CommonBackend: Searching ISOs on USB devices
08-27 10:53 DEBUG  CommonBackend: Searching for local CDs
08-27 10:53 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp is a valid Ubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp is a valid Ubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp is a valid Kubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp is a valid Kubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp is a valid Mythbuntu CD
08-27 10:53 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp is a valid Mythbuntu CD
08-27 10:53 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp is a valid Edubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp is a valid Edubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp is a valid Lubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp is a valid Lubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-27 10:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-27 10:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-27 10:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-27 10:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-27 10:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-27 10:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-27 10:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-27 10:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-27 10:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-27 10:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-27 10:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-27 10:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-27 10:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:53 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-27 10:53 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
08-27 10:53 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
08-27 10:53 INFO   Distro: Found a valid CD for Ubuntu: J:\
08-27 10:53 INFO   root: Running the CD menu...
08-27 10:53 DEBUG  WindowsFrontend: __init__...
08-27 10:53 DEBUG  WindowsFrontend: on_init...
08-27 10:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp\translations, languages=['en_US', 'en']
08-27 10:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pylB0C7.tmp\translations, languages=['en_US', 'en']
08-27 10:54 INFO   WindowsFrontend: Operation cancelled
08-27 10:54 DEBUG  WindowsFrontend: frontend.quit
08-27 10:54 DEBUG  WindowsFrontend: frontend.on_quit
08-27 10:54 DEBUG  root: application.on_quit
08-27 10:54 INFO   root: sys.exit
08-27 10:56 INFO   root: === wubi 12.10 rev273 ===
08-27 10:56 DEBUG  root: Logfile is c:\users\marudi~1\appdata\local\temp\wubi-12.10-rev273.log
08-27 10:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"', '--force-wubi']
08-27 10:56 DEBUG  CommonBackend: data_dir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\data
08-27 10:56 DEBUG  WindowsBackend: 7z=C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\bin\7z.exe
08-27 10:56 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-27 10:56 DEBUG  CommonBackend: Fetching basic info...
08-27 10:56 DEBUG  CommonBackend: original_exe=J:\wubi.exe
08-27 10:56 DEBUG  CommonBackend: platform=win32
08-27 10:56 DEBUG  CommonBackend: osname=nt
08-27 10:56 DEBUG  CommonBackend: language=en_US
08-27 10:56 DEBUG  CommonBackend: encoding=cp1252
08-27 10:56 DEBUG  WindowsBackend: arch=amd64
08-27 10:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\data\isolist.ini
08-27 10:56 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-27 10:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-27 10:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-27 10:56 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-27 10:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-27 10:56 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-27 10:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-27 10:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-27 10:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-27 10:56 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-27 10:56 DEBUG  WindowsBackend: Fetching host info...
08-27 10:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-27 10:56 DEBUG  WindowsBackend: windows version=vista
08-27 10:56 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
08-27 10:56 DEBUG  WindowsBackend: windows_sp=None
08-27 10:56 DEBUG  WindowsBackend: windows_build=9200
08-27 10:56 DEBUG  WindowsBackend: gmt=7
08-27 10:56 DEBUG  WindowsBackend: country=US
08-27 10:56 DEBUG  WindowsBackend: timezone=America/New_York
08-27 10:56 DEBUG  WindowsBackend: windows_username=MARUDI TRI S
08-27 10:56 DEBUG  WindowsBackend: user_full_name=MARUDI TRI S
08-27 10:56 DEBUG  WindowsBackend: user_directory=C:\Users\MARUDI TRI S
08-27 10:56 DEBUG  WindowsBackend: windows_language_code=1033
08-27 10:56 DEBUG  WindowsBackend: windows_language=English
08-27 10:56 DEBUG  WindowsBackend: processor_name=AMD A6-4400M APU with Radeon(tm) HD Graphics   
08-27 10:56 DEBUG  WindowsBackend: bootloader=vista
08-27 10:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 26550.9882813 mb free ntfs)
08-27 10:56 DEBUG  WindowsBackend: drive=Drive(C: hd 26550.9882813 mb free ntfs)
08-27 10:56 DEBUG  WindowsBackend: drive=Drive(D: hd 23313.1289063 mb free ntfs)
08-27 10:56 DEBUG  WindowsBackend: drive=Drive(E: hd 15484.484375 mb free ntfs)
08-27 10:56 DEBUG  WindowsBackend: drive=Drive(F: hd 38329.3515625 mb free ntfs)
08-27 10:56 DEBUG  WindowsBackend: drive=Drive(G: hd 21467.7578125 mb free ntfs)
08-27 10:56 DEBUG  WindowsBackend: drive=Drive(H: hd 51904.7148438 mb free ntfs)
08-27 10:56 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
08-27 10:56 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
08-27 10:56 DEBUG  WindowsBackend: uninstaller_path=None
08-27 10:56 DEBUG  WindowsBackend: previous_target_dir=None
08-27 10:56 DEBUG  WindowsBackend: previous_distro_name=None
08-27 10:56 DEBUG  WindowsBackend: keyboard_id=67699721
08-27 10:56 DEBUG  WindowsBackend: keyboard_layout=us
08-27 10:56 DEBUG  WindowsBackend: keyboard_variant=
08-27 10:56 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-27 10:56 DEBUG  CommonBackend: locale=en_US.UTF-8
08-27 10:56 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-27 10:56 DEBUG  CommonBackend: Searching ISOs on USB devices
08-27 10:56 DEBUG  CommonBackend: Searching for local CDs
08-27 10:56 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp is a valid Ubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp is a valid Ubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp is a valid Kubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp is a valid Kubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp is a valid Mythbuntu CD
08-27 10:56 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp is a valid Mythbuntu CD
08-27 10:56 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp is a valid Edubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp is a valid Edubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp is a valid Lubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp is a valid Lubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-27 10:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-27 10:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-27 10:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-27 10:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-27 10:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-27 10:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-27 10:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-27 10:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-27 10:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-27 10:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-27 10:56 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-27 10:56 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-27 10:56 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-27 10:56 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-27 10:56 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
08-27 10:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
08-27 10:56 INFO   Distro: Found a valid CD for Ubuntu: J:\
08-27 10:56 INFO   root: Running the CD menu...
08-27 10:56 DEBUG  WindowsFrontend: __init__...
08-27 10:56 DEBUG  WindowsFrontend: on_init...
08-27 10:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\translations, languages=['en_US', 'en']
08-27 10:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\translations, languages=['en_US', 'en']
08-27 10:56 INFO   root: CD menu finished
08-27 10:56 INFO   root: Running the installer...
08-27 10:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\translations, languages=['en_US', 'en']
08-27 10:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\translations, languages=['en_US', 'en']
08-27 10:57 DEBUG  WinuiInstallationPage: target_drive=H:, installation_size=25000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=marudits
08-27 10:57 INFO   root: Received settings
08-27 10:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\translations, languages=['en_US', 'en']
08-27 10:57 DEBUG  TaskList: # Running tasklist...
08-27 10:57 DEBUG  TaskList: ## Running select_target_dir...
08-27 10:57 INFO   WindowsBackend: Installing into H:\ubuntu
08-27 10:57 DEBUG  TaskList: ## Finished select_target_dir
08-27 10:57 DEBUG  TaskList: ## Running create_dir_structure...
08-27 10:57 DEBUG  CommonBackend: Creating dir H:\ubuntu
08-27 10:57 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks
08-27 10:57 DEBUG  CommonBackend: Creating dir H:\ubuntu\install
08-27 10:57 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot
08-27 10:57 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot
08-27 10:57 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot\grub
08-27 10:57 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot\grub
08-27 10:57 DEBUG  TaskList: ## Finished create_dir_structure
08-27 10:57 DEBUG  TaskList: ## Running uncompress_target_dir...
08-27 10:57 DEBUG  TaskList: ## Finished uncompress_target_dir
08-27 10:57 DEBUG  TaskList: ## Running create_uninstaller...
08-27 10:57 DEBUG  WindowsBackend: Copying uninstaller J:\wubi.exe -> H:\ubuntu\uninstall-wubi.exe
08-27 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString H:\ubuntu\uninstall-wubi.exe
08-27 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir H:\ubuntu
08-27 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-27 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon H:\ubuntu\Ubuntu.ico
08-27 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
08-27 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-27 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-27 10:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-27 10:57 DEBUG  TaskList: ## Finished create_uninstaller
08-27 10:57 DEBUG  TaskList: ## Running copy_installation_files...
08-27 10:57 DEBUG  WindowsBackend: Copying C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\data\custom-installation -> H:\ubuntu\install\custom-installation
08-27 10:57 DEBUG  WindowsBackend: Copying C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\winboot -> H:\ubuntu\winboot
08-27 10:57 DEBUG  WindowsBackend: Copying C:\Users\MARUDI~1\AppData\Local\Temp\pyl7FA9.tmp\data\images\Ubuntu.ico -> H:\ubuntu\Ubuntu.ico
08-27 10:57 DEBUG  TaskList: ## Finished copy_installation_files
08-27 10:57 DEBUG  TaskList: ## Running get_iso...
08-27 10:57 DEBUG  TaskList: New task copy_file
08-27 10:57 DEBUG  TaskList: ### Running copy_file...
08-27 10:57 DEBUG  TaskList: ### Finished copy_file
08-27 10:57 DEBUG  TaskList: New task check_iso
08-27 10:57 DEBUG  TaskList: ### Running check_iso...
08-27 10:57 DEBUG  CommonBackend: Checking H:\ubuntu\install\installation.iso
08-27 10:57 DEBUG  Distro:   checking Ubuntu ISO H:\ubuntu\install\installation.iso
08-27 10:58 DEBUG  WindowsBackend:   extracting .disk\info from H:\ubuntu\install\installation.iso
08-27 10:58 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
08-27 10:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
08-27 10:58 INFO   Distro: Found a valid iso for Ubuntu: H:\ubuntu\install\installation.iso
08-27 10:58 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
08-27 10:58 DEBUG  TaskList: New task get_metalink
08-27 10:58 DEBUG  TaskList: #### Running get_metalink...
08-27 10:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) > H:\ubuntu\install
08-27 10:58 DEBUG  downloader: Download start filename=H:\ubuntu\install\ubuntu-12.10-desktop-i386.metalink, url=http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink, basename=ubuntu-12.10-desktop-i386.metalink, length=31562, text=None
08-27 10:58 DEBUG  downloader: download finished (read 31562 bytes)
08-27 10:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/MD5SUMS-metalink](http://releases.ubuntu.com/12.10/MD5SUMS-metalink) > H:\ubuntu\install
08-27 10:58 DEBUG  downloader: Download start filename=H:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/12.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=1196, text=None
08-27 10:58 DEBUG  downloader: download finished (read 1196 bytes)
08-27 10:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/12.10/MD5SUMS-metalink.gpg) > H:\ubuntu\install
08-27 10:58 DEBUG  downloader: Download start filename=H:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/12.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
08-27 10:58 DEBUG  downloader: download finished (read 198 bytes)
08-27 10:58 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
08-27 10:58 INFO   saplog: Checking block bindings..
08-27 10:58 INFO   saplog: Key verified successfully.
08-27 10:58 DEBUG  CommonBackend: metalink md5sums:
1fdde0057923dc6c4bd69b657480a631 *ubuntu-12.10-beta2-desktop-amd64+mac.metalink
091d4adafcfe4eea08eb41771be3f3ba *ubuntu-12.10-beta2-desktop-amd64.metalink
940ab0bf82879435181f8c03304e7387 *ubuntu-12.10-beta2-desktop-armhf+omap4.metalink
9e0ad0a15414df437a27c66da938d3e3 *ubuntu-12.10-beta2-desktop-i386.metalink
4672b67404c84ba74bf104607bbec49a *ubuntu-12.10-beta2-server-amd64+mac.metalink
a8d35d8579f11579e802667bbcb7b0fb *ubuntu-12.10-beta2-server-amd64.metalink
fb6219893d9f4f329183fafaac258681 *ubuntu-12.10-beta2-server-armhf+omap4.metalink
12fbf5ccf3aedfd8fe31f1ab00ec8ddb *ubuntu-12.10-beta2-server-i386.metalink
e1a7672decc21eb6a65464b0a239a1db *ubuntu-12.10-desktop-amd64+mac.metalink
894437367bf791cf02902d6f5285af98 *ubuntu-12.10-desktop-amd64.metalink
57a58f151b50e218acc4724388d2f387 *ubuntu-12.10-desktop-armhf+omap4.metalink
11e206f0d5e147fe05b9e85d78f5f187 *ubuntu-12.10-desktop-i386.metalink
fc37a124ca1957d7549a296d59e3dd81 *ubuntu-12.10-server-amd64+mac.metalink
35afee005d732a9ad0361b4aae25e3c3 *ubuntu-12.10-server-amd64.metalink
68adfc9d71d5b3613a09c3e6c45f8ba5 *ubuntu-12.10-server-armhf+omap4.metalink
c4fd126394cf2e1bbd626b5f74b3e40b *ubuntu-12.10-server-i386.metalink


08-27 10:58 ERROR  CommonBackend: The md5 of the metalink does match
08-27 10:58 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
08-27 10:58 DEBUG  TaskList: #### Finished get_metalink
08-27 10:58 DEBUG  TaskList: New task get_file_md5
08-27 10:58 DEBUG  TaskList: #### Running get_file_md5...
08-27 10:58 DEBUG  TaskList: #### Finished get_file_md5
08-27 10:58 DEBUG  TaskList: ### Finished check_iso
08-27 10:58 DEBUG  TaskList: ## Finished get_iso
08-27 10:58 DEBUG  TaskList: ## Running extract_kernel...
08-27 10:58 DEBUG  CommonBackend: Copying files from CD J:\
08-27 10:58 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
08-27 10:58 DEBUG  CommonBackend:   checking H:\ubuntu\install\boot\vmlinuz
08-27 10:58 DEBUG  CommonBackend:   H:\ubuntu\install\boot\vmlinuz md5 = dedeef44f082210eb0d605d21837feb5 == dedeef44f082210eb0d605d21837feb5
08-27 10:58 DEBUG  CommonBackend:   checking H:\ubuntu\install\boot\initrd.lz
08-27 10:58 DEBUG  CommonBackend:   H:\ubuntu\install\boot\initrd.lz md5 = bf4099046c27293af1f7ec8c76baf1c7 == bf4099046c27293af1f7ec8c76baf1c7
08-27 10:58 DEBUG  TaskList: ## Finished extract_kernel
08-27 10:58 DEBUG  TaskList: ## Running choose_disk_sizes...
08-27 10:58 DEBUG  WindowsBackend: total size=25000
  root=24744
  swap=256
  home=0
  usr=0
08-27 10:58 DEBUG  TaskList: ## Finished choose_disk_sizes
08-27 10:58 DEBUG  TaskList: ## Running create_preseed...
08-27 10:58 DEBUG  TaskList: ## Finished create_preseed
08-27 10:58 DEBUG  TaskList: ## Running modify_bootloader...
08-27 10:58 DEBUG  TaskList: New task modify_bcd
08-27 10:58 DEBUG  TaskList: ### Running modify_bcd...
08-27 10:58 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 26550.9882813 mb free ntfs)
08-27 10:58 ERROR  TaskList: Error executing command
>>command=C:\WINDOWS\System32\bcdedit.exe /set {ab334399-0bbf-11e3-afee-50b7c3b19288} device partition=H:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\WINDOWS\System32\bcdedit.exe /set {ab334399-0bbf-11e3-afee-50b7c3b19288} device partition=H:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
08-27 10:58 DEBUG  TaskList: # Cancelling tasklist
08-27 10:58 ERROR  root: Error executing command
>>command=C:\WINDOWS\System32\bcdedit.exe /set {ab334399-0bbf-11e3-afee-50b7c3b19288} device partition=H:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\WINDOWS\System32\bcdedit.exe /set {ab334399-0bbf-11e3-afee-50b7c3b19288} device partition=H:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
08-27 10:58 DEBUG  TaskList: New task modify_bcd
08-27 10:58 DEBUG  TaskList: New task modify_bcd
08-27 10:58 DEBUG  TaskList: New task modify_bcd
08-27 10:58 DEBUG  TaskList: New task modify_bcd
08-27 10:58 DEBUG  TaskList: New task modify_bcd
08-27 10:58 DEBUG  TaskList: ## Finished modify_bootloader
08-27 10:58 DEBUG  TaskList: # Finished tasklist
```


Thanks for help.

---

### Post by grahammechanical on 2013-08-27
Windows 8 and wubi.exe are not compatible. That is the problem.

> Windows installer is not compatible with Windows 8 or UEFI firmware, and is not available for Ubuntu 13.04.


[http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows](http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows)

Regards.

---

