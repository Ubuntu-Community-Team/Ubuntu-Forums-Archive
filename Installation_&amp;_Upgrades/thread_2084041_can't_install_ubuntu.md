---
title: "can't install ubuntu"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by simokey on 2012-11-14
```

11-13 20:10 INFO   root: === wubi 12.04 rev269 ===
11-13 20:10 DEBUG  root: Logfile is c:\users\mrsimo~1\appdata\local\temp\wubi-12.04-rev269.log
11-13 20:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ProgramData\\Microsoft\\Windows\\Start Menu\\Programs\\Startup\\wubi.exe"']
11-13 20:10 DEBUG  CommonBackend: data_dir=C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\data
11-13 20:10 DEBUG  WindowsBackend: 7z=C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\bin\7z.exe
11-13 20:10 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-13 20:10 DEBUG  CommonBackend: Fetching basic info...
11-13 20:10 DEBUG  CommonBackend: original_exe=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup\wubi.exe
11-13 20:10 DEBUG  CommonBackend: platform=win32
11-13 20:10 DEBUG  CommonBackend: osname=nt
11-13 20:10 DEBUG  CommonBackend: language=fr_FR
11-13 20:10 DEBUG  CommonBackend: encoding=cp1256
11-13 20:10 DEBUG  WindowsBackend: arch=amd64
11-13 20:10 DEBUG  CommonBackend: Parsing isolist=C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\data\isolist.ini
11-13 20:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-13 20:10 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-13 20:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-13 20:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-13 20:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-13 20:10 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-13 20:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-13 20:10 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-13 20:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-13 20:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-13 20:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-13 20:10 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-13 20:10 DEBUG  WindowsBackend: Fetching host info...
11-13 20:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-13 20:10 DEBUG  WindowsBackend: windows version=vista
11-13 20:10 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-13 20:10 DEBUG  WindowsBackend: windows_sp=Service Pack 1
11-13 20:10 DEBUG  WindowsBackend: windows_build=7601
11-13 20:10 DEBUG  WindowsBackend: gmt=0
11-13 20:10 DEBUG  WindowsBackend: country=FR
11-13 20:10 DEBUG  WindowsBackend: timezone=Europe/Paris
11-13 20:10 DEBUG  WindowsBackend: windows_username=Mr Simo
11-13 20:10 DEBUG  WindowsBackend: user_full_name=Mr Simo
11-13 20:10 DEBUG  WindowsBackend: user_directory=C:\Users\Mr Simo
11-13 20:10 DEBUG  WindowsBackend: windows_language_code=1036
11-13 20:10 DEBUG  WindowsBackend: windows_language=French
11-13 20:10 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
11-13 20:10 DEBUG  WindowsBackend: bootloader=vista
11-13 20:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 170032.359375 mb free ntfs)
11-13 20:10 DEBUG  WindowsBackend: drive=Drive(C: hd 170032.359375 mb free ntfs)
11-13 20:10 DEBUG  WindowsBackend: drive=Drive(D: hd 91543.1953125 mb free ntfs)
11-13 20:10 DEBUG  WindowsBackend: drive=Drive(E: hd 74927.8085938 mb free ntfs)
11-13 20:10 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-13 20:10 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
11-13 20:10 DEBUG  WindowsBackend: drive=Drive(H: hd 76744.8984375 mb free ntfs)
11-13 20:10 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
11-13 20:10 DEBUG  WindowsBackend: uninstaller_path=None
11-13 20:10 DEBUG  WindowsBackend: previous_target_dir=None
11-13 20:10 DEBUG  WindowsBackend: previous_distro_name=None
11-13 20:10 DEBUG  WindowsBackend: keyboard_id=67896332
11-13 20:10 DEBUG  WindowsBackend: keyboard_layout=fr
11-13 20:10 DEBUG  WindowsBackend: keyboard_variant=
11-13 20:10 DEBUG  CommonBackend: python locale=('fr_FR', 'cp1256')
11-13 20:10 DEBUG  CommonBackend: locale=fr_FR.UTF-8
11-13 20:10 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
11-13 20:10 DEBUG  CommonBackend: Searching ISOs on USB devices
11-13 20:10 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.04.1-desktop-i386.iso
11-13 20:10 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.04.1-desktop-i386.iso
11-13 20:10 DEBUG  Distro:   parsing info from str=Ubuntu 12.04.1 LTS "Precise Pangolin" - Release i386 (20120817.3)
11-13 20:10 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04.1', 'build': '20120817.3', 'codename': 'Precise Pangolin', 'arch': 'i386'}
11-13 20:10 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.04.1-desktop-i386.iso
11-13 20:10 DEBUG  CommonBackend: Searching for local CDs
11-13 20:10 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp is a valid Ubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp is a valid Ubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp is a valid Kubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp is a valid Kubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp is a valid Xubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp is a valid Xubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp is a valid Mythbuntu CD
11-13 20:10 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp is a valid Mythbuntu CD
11-13 20:10 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp is a valid Edubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp is a valid Edubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp is a valid Lubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp is a valid Lubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-13 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-13 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-13 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-13 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-13 20:10 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
11-13 20:10 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
11-13 20:10 DEBUG  Distro: wrong version: 11.04 != 12.04.1
11-13 20:10 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-13 20:10 DEBUG  Distro: wrong version: 11.04 != 12.04.1
11-13 20:10 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-13 20:10 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
11-13 20:10 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-13 20:10 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
11-13 20:10 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-13 20:10 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
11-13 20:10 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-13 20:10 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
11-13 20:10 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-13 20:10 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
11-13 20:10 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-13 20:10 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
11-13 20:10 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
11-13 20:10 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
11-13 20:10 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
11-13 20:10 DEBUG  Distro: wrong name: Ubuntu != Edubuntu
11-13 20:10 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
11-13 20:10 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
11-13 20:10 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
11-13 20:10 DEBUG  Distro: wrong name: Ubuntu != Lubuntu
11-13 20:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-13 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-13 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-13 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-13 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-13 20:10 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
11-13 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-13 20:10 INFO   root: Running the installer...
11-13 20:10 DEBUG  WindowsFrontend: __init__...
11-13 20:10 DEBUG  WindowsFrontend: on_init...
11-13 20:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\translations, languages=['fr_FR', 'fr']
11-13 20:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MRSIMO~1\AppData\Local\Temp\pylCE84.tmp\translations, languages=['fr_FR', 'fr']
11-13 20:11 DEBUG  WindowsFrontend: frontend.on_quit
11-13 20:11 DEBUG  root: application.on_quit
11-13 20:11 INFO   root: sys.exit
11-13 20:36 INFO   root: === wubi 12.04 rev269 ===
11-13 20:36 DEBUG  root: Logfile is c:\users\mrsimo~1\appdata\local\temp\wubi-12.04-rev269.log
11-13 20:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
11-13 20:36 DEBUG  CommonBackend: data_dir=C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\data
11-13 20:36 DEBUG  WindowsBackend: 7z=C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\bin\7z.exe
11-13 20:36 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-13 20:36 DEBUG  CommonBackend: Fetching basic info...
11-13 20:36 DEBUG  CommonBackend: original_exe=F:\wubi.exe
11-13 20:36 DEBUG  CommonBackend: platform=win32
11-13 20:36 DEBUG  CommonBackend: osname=nt
11-13 20:36 DEBUG  CommonBackend: language=fr_FR
11-13 20:36 DEBUG  CommonBackend: encoding=cp1256
11-13 20:36 DEBUG  WindowsBackend: arch=amd64
11-13 20:36 DEBUG  CommonBackend: Parsing isolist=C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\data\isolist.ini
11-13 20:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-13 20:36 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-13 20:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-13 20:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-13 20:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-13 20:36 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-13 20:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-13 20:36 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-13 20:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-13 20:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-13 20:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-13 20:36 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-13 20:36 DEBUG  WindowsBackend: Fetching host info...
11-13 20:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-13 20:36 DEBUG  WindowsBackend: windows version=vista
11-13 20:36 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-13 20:36 DEBUG  WindowsBackend: windows_sp=Service Pack 1
11-13 20:36 DEBUG  WindowsBackend: windows_build=7601
11-13 20:36 DEBUG  WindowsBackend: gmt=0
11-13 20:36 DEBUG  WindowsBackend: country=FR
11-13 20:36 DEBUG  WindowsBackend: timezone=Europe/Paris
11-13 20:36 DEBUG  WindowsBackend: windows_username=Mr Simo
11-13 20:36 DEBUG  WindowsBackend: user_full_name=Mr Simo
11-13 20:36 DEBUG  WindowsBackend: user_directory=C:\Users\Mr Simo
11-13 20:36 DEBUG  WindowsBackend: windows_language_code=1036
11-13 20:36 DEBUG  WindowsBackend: windows_language=French
11-13 20:36 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
11-13 20:36 DEBUG  WindowsBackend: bootloader=vista
11-13 20:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 169945.484375 mb free ntfs)
11-13 20:36 DEBUG  WindowsBackend: drive=Drive(C: hd 169945.484375 mb free ntfs)
11-13 20:36 DEBUG  WindowsBackend: drive=Drive(D: hd 99902.8164063 mb free ntfs)
11-13 20:36 DEBUG  WindowsBackend: drive=Drive(E: hd 74927.8085938 mb free ntfs)
11-13 20:36 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
11-13 20:36 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
11-13 20:36 DEBUG  WindowsBackend: drive=Drive(H: hd 68380.9101563 mb free ntfs)
11-13 20:36 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
11-13 20:36 DEBUG  WindowsBackend: uninstaller_path=None
11-13 20:36 DEBUG  WindowsBackend: previous_target_dir=None
11-13 20:36 DEBUG  WindowsBackend: previous_distro_name=None
11-13 20:36 DEBUG  WindowsBackend: keyboard_id=67896332
11-13 20:36 DEBUG  WindowsBackend: keyboard_layout=fr
11-13 20:36 DEBUG  WindowsBackend: keyboard_variant=
11-13 20:36 DEBUG  CommonBackend: python locale=('fr_FR', 'cp1256')
11-13 20:36 DEBUG  CommonBackend: locale=fr_FR.UTF-8
11-13 20:36 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
11-13 20:36 DEBUG  CommonBackend: Searching ISOs on USB devices
11-13 20:36 DEBUG  Distro:   checking Ubuntu ISO H:\ubuntu-12.04.1-desktop-i386.iso
11-13 20:36 DEBUG  WindowsBackend:   extracting .disk\info from H:\ubuntu-12.04.1-desktop-i386.iso
11-13 20:36 DEBUG  Distro:   parsing info from str=Ubuntu 12.04.1 LTS "Precise Pangolin" - Release i386 (20120817.3)
11-13 20:36 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04.1', 'build': '20120817.3', 'codename': 'Precise Pangolin', 'arch': 'i386'}
11-13 20:36 INFO   Distro: Found a valid iso for Ubuntu: H:\ubuntu-12.04.1-desktop-i386.iso
11-13 20:36 DEBUG  CommonBackend: Searching for local CDs
11-13 20:36 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp is a valid Ubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp is a valid Ubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp is a valid Kubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp is a valid Kubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp is a valid Xubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp is a valid Xubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp is a valid Mythbuntu CD
11-13 20:36 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp is a valid Mythbuntu CD
11-13 20:36 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp is a valid Edubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp is a valid Edubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp is a valid Lubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp is a valid Lubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-13 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-13 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-13 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 20:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-13 20:36 DEBUG  Distro:   parsing info from str=Ubuntu 12.04.1 LTS "Precise Pangolin" - Release i386 (20120817.3)
11-13 20:36 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04.1', 'build': '20120817.3', 'codename': 'Precise Pangolin', 'arch': 'i386'}
11-13 20:36 INFO   Distro: Found a valid CD for Ubuntu: F:\
11-13 20:36 INFO   root: Running the CD menu...
11-13 20:36 DEBUG  WindowsFrontend: __init__...
11-13 20:36 DEBUG  WindowsFrontend: on_init...
11-13 20:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\translations, languages=['fr_FR', 'fr']
11-13 20:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\MRSIMO~1\AppData\Local\Temp\pyl7E91.tmp\translations, languages=['fr_FR', 'fr']
11-13 20:36 INFO   root: CD menu finished
11-13 20:36 INFO   root: Rebooting
11-13 20:36 DEBUG  TaskList: # Running tasklist...
11-13 20:36 DEBUG  TaskList: ## Running reboot...
11-13 20:36 DEBUG  TaskList: ## Finished reboot
11-13 20:36 DEBUG  TaskList: # Finished tasklist
11-13 20:36 DEBUG  root: application.quit
11-13 20:36 DEBUG  WindowsFrontend: frontend.quit
11-13 20:36 DEBUG  WindowsFrontend: frontend.on_quit
11-13 20:36 DEBUG  root: application.on_quit
11-13 20:36 INFO   root: sys.exit


```

---

### Post by grahammechanical on 2012-11-14
You clearly have not read this:

[http://ubuntuforums.org/showthread.php?t=1422475]("http://ubuntuforums.org/showthread.php?t=1422475")

You might also benefit from reading this:

[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

---

