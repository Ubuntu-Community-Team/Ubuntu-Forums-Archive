---
title: "Try(hd0, 0): ntfs5: error: &quot;prefix is not set&quot; after installing Xubuntu 10.04 V. 2"
date: 2012-03-31
forum: Installation &amp; Upgrades
---

### Post by Seantum on 2012-03-31
Hi folks,

I have many times tried to install xubuntu 10.04 via wubi on my laptop (Acer Travelmate 292LCi).
But so far always the same error occured (see topic-title) when I tried to start xubuntu. Installation went smoothly each time, but I have so far never been able to start xubuntu...

I have the boot log for you here:

> 03-18 14:26 INFO   root: === wubi 10.04.2 rev191 ===
03-18 14:26 DEBUG  root: Logfile is c:\dokume~1\thomas\lokale~1\temp\wubi-10.04.2-rev191.log
03-18 14:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
03-18 14:26 DEBUG  CommonBackend: data_dir=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp\data
03-18 14:26 DEBUG  WindowsBackend: 7z=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp\bin\7z.exe
03-18 14:26 DEBUG  CommonBackend: Fetching basic info...
03-18 14:26 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-18 14:26 DEBUG  CommonBackend: platform=win32
03-18 14:26 DEBUG  CommonBackend: osname=nt
03-18 14:26 DEBUG  CommonBackend: language=de_AT
03-18 14:26 DEBUG  CommonBackend: encoding=cp1252
03-18 14:26 DEBUG  WindowsBackend: arch=i386
03-18 14:26 DEBUG  CommonBackend: Parsing isolist=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp\data\isolist.ini
03-18 14:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-18 14:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-18 14:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-18 14:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-18 14:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-18 14:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-18 14:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-18 14:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-18 14:26 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-18 14:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-18 14:26 DEBUG  WindowsBackend: Fetching host info...
03-18 14:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-18 14:26 DEBUG  WindowsBackend: windows version=xp
03-18 14:26 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-18 14:26 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-18 14:26 DEBUG  WindowsBackend: windows_build=2600
03-18 14:26 DEBUG  WindowsBackend: gmt=1
03-18 14:26 DEBUG  WindowsBackend: country=AT
03-18 14:26 DEBUG  WindowsBackend: timezone=Europe/Vienna
03-18 14:26 DEBUG  WindowsBackend: windows_username=Thomas
03-18 14:26 DEBUG  WindowsBackend: user_full_name=Thomas
03-18 14:26 DEBUG  WindowsBackend: user_directory=C:\Dokumente und Einstellungen\Thomas
03-18 14:26 DEBUG  WindowsBackend: windows_language_code=1031
03-18 14:26 DEBUG  WindowsBackend: windows_language=German
03-18 14:26 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1500MHz
03-18 14:26 DEBUG  WindowsBackend: bootloader=xp
03-18 14:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 21823.8125 mb free ntfs)
03-18 14:26 DEBUG  WindowsBackend: drive=Drive(C: hd 21823.8125 mb free ntfs)
03-18 14:26 DEBUG  WindowsBackend: drive=Drive(D: hd 78438.8671875 mb free ntfs)
03-18 14:26 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-18 14:26 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-18 14:26 DEBUG  WindowsBackend: uninstaller_path=None
03-18 14:26 DEBUG  WindowsBackend: previous_target_dir=None
03-18 14:26 DEBUG  WindowsBackend: previous_distro_name=None
03-18 14:26 DEBUG  WindowsBackend: keyboard_id=67570695
03-18 14:26 DEBUG  WindowsBackend: keyboard_layout=de
03-18 14:26 DEBUG  WindowsBackend: keyboard_variant=
03-18 14:26 DEBUG  CommonBackend: python locale=('de_AT', 'cp1252')
03-18 14:26 DEBUG  CommonBackend: locale=de_AT.UTF-8
03-18 14:26 DEBUG  WindowsBackend: total_memory_mb=495.484375
03-18 14:26 DEBUG  CommonBackend: Searching ISOs on USB devices
03-18 14:26 DEBUG  CommonBackend: Searching for local CDs
03-18 14:26 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp is a valid Ubuntu CD
03-18 14:26 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp is a valid Ubuntu CD
03-18 14:26 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp is a valid Ubuntu Netbook CD
03-18 14:26 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp is a valid Kubuntu CD
03-18 14:26 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp is a valid Kubuntu CD
03-18 14:26 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp is a valid Kubuntu Netbook CD
03-18 14:26 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp is a valid Xubuntu CD
03-18 14:26 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp is a valid Xubuntu CD
03-18 14:26 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp is a valid Mythbuntu CD
03-18 14:26 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp is a valid Mythbuntu CD
03-18 14:26 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-18 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-18 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-18 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-18 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-18 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-18 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-18 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-18 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-18 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-18 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-18 14:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-18 14:26 DEBUG  Distro:   parsing info from str=Xubuntu 10.04.2 "Lucid Lynx" - Release i386 (20110214.1)
03-18 14:26 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110214.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
03-18 14:26 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
03-18 14:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-18 14:26 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
03-18 14:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-18 14:26 DEBUG  Distro: wrong name: Xubuntu != Ubuntu Netbook
03-18 14:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-18 14:26 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
03-18 14:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-18 14:26 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
03-18 14:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-18 14:26 DEBUG  Distro: wrong name: Xubuntu != Kubuntu Netbook
03-18 14:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-18 14:26 INFO   Distro: Found a valid CD for Xubuntu: E:\
03-18 14:26 INFO   root: Running the CD menu...
03-18 14:26 DEBUG  WindowsFrontend: __init__...
03-18 14:26 DEBUG  WindowsFrontend: on_init...
03-18 14:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp\translations, languages=['de_AT', 'de']
03-18 14:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1F.tmp\translations, languages=['de_AT', 'de']
03-18 14:30 INFO   WindowsFrontend: Operation cancelled
03-18 14:30 DEBUG  WindowsFrontend: frontend.quit
03-18 14:30 DEBUG  WindowsFrontend: frontend.on_quit
03-18 14:30 DEBUG  root: application.on_quit
03-18 14:30 INFO   root: sys.exit
03-31 13:06 INFO   root: === wubi 10.04.2 rev191 ===
03-31 13:06 DEBUG  root: Logfile is c:\dokume~1\thomas\lokale~1\temp\wubi-10.04.2-rev191.log
03-31 13:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
03-31 13:06 DEBUG  CommonBackend: data_dir=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp\data
03-31 13:06 DEBUG  WindowsBackend: 7z=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp\bin\7z.exe
03-31 13:06 DEBUG  CommonBackend: Fetching basic info...
03-31 13:06 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-31 13:06 DEBUG  CommonBackend: platform=win32
03-31 13:06 DEBUG  CommonBackend: osname=nt
03-31 13:06 DEBUG  CommonBackend: language=de_AT
03-31 13:06 DEBUG  CommonBackend: encoding=cp1252
03-31 13:06 INFO   root: === wubi 10.04.2 rev191 ===
03-31 13:06 DEBUG  root: Logfile is c:\dokume~1\thomas\lokale~1\temp\wubi-10.04.2-rev191.log
03-31 13:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
03-31 13:06 DEBUG  CommonBackend: data_dir=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\data
03-31 13:06 DEBUG  WindowsBackend: 7z=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\bin\7z.exe
03-31 13:06 DEBUG  CommonBackend: Fetching basic info...
03-31 13:06 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-31 13:06 DEBUG  CommonBackend: platform=win32
03-31 13:06 DEBUG  CommonBackend: osname=nt
03-31 13:06 DEBUG  CommonBackend: language=de_AT
03-31 13:06 DEBUG  CommonBackend: encoding=cp1252
03-31 13:06 DEBUG  WindowsBackend: arch=i386
03-31 13:06 DEBUG  CommonBackend: Parsing isolist=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp\data\isolist.ini
03-31 13:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-31 13:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-31 13:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-31 13:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-31 13:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-31 13:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-31 13:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-31 13:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-31 13:06 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-31 13:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-31 13:06 DEBUG  WindowsBackend: Fetching host info...
03-31 13:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-31 13:06 DEBUG  WindowsBackend: windows version=xp
03-31 13:06 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-31 13:06 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-31 13:06 DEBUG  WindowsBackend: windows_build=2600
03-31 13:06 DEBUG  WindowsBackend: gmt=1
03-31 13:06 DEBUG  WindowsBackend: country=AT
03-31 13:06 DEBUG  WindowsBackend: timezone=Europe/Vienna
03-31 13:06 DEBUG  WindowsBackend: arch=i386
03-31 13:06 DEBUG  CommonBackend: Parsing isolist=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\data\isolist.ini
03-31 13:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-31 13:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-31 13:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
 13:06 DEBUG  WindowsBackend: user_full_name=Thomas
03-31 13:06 DEBUG  WindowsBackend: user_directory=C:\Dokumente und Einstellungen\Thomas
03-31 13:06 DEBUG  WindowsBackend: windows_language_code=1031
03-31 13:06 DEBUG  WindowsBackend: windows_language=German
03-31 13:06 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1500MHz
03-31 13:06 DEBUG  WindowsBackend: bootloader=xp
03-31 13:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-31 13:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-31 13:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-31 13:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-31 13:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-31 13:06 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-31 13:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-31 13:06 DEBUG  WindowsBackend: Fetching host info...
03-31 13:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-31 13:06 DEBUG  WindowsBackend: windows version=xp
03-31 13:06 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
03-31 13:06 DEBUG  WindowsBackend: windows_sp=Service Pack 3
03-31 13:06 DEBUG  WindowsBackend: windows_build=2600
03-31 13:06 DEBUG  WindowsBackend: gmt=1
03-31 13:06 DEBUG  WindowsBackend: country=AT
03-31 13:06 DEBUG  WindowsBackend: timezone=Europe/Vienna
03-31 13:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 18202.3242188 mb free ntfs)
03-31 13:06 DEBUG  WindowsBackend: drive=Drive(C: hd 18202.3242188 mb free ntfs)
03-31 13:06 DEBUG  WindowsBackend: drive=Drive(D: hd 74989.5625 mb free ntfs)
03-31 13:06 DEBUG  WindowsBackend: windows_username=Thomas
03-31 13:06 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-31 13:06 DEBUG  WindowsBackend: user_full_name=Thomas
03-31 13:06 DEBUG  WindowsBackend: user_directory=C:\Dokumente und Einstellungen\Thomas
03-31 13:06 DEBUG  WindowsBackend: windows_language_code=1031
03-31 13:06 DEBUG  WindowsBackend: windows_language=German
03-31 13:06 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1500MHz
03-31 13:06 DEBUG  WindowsBackend: bootloader=xp
03-31 13:06 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-31 13:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 18202.3242188 mb free ntfs)
03-31 13:06 DEBUG  WindowsBackend: drive=Drive(G: hd 21552.8125 mb free fat32)
03-31 13:06 DEBUG  WindowsBackend: uninstaller_path=None
03-31 13:06 DEBUG  WindowsBackend: previous_target_dir=None
03-31 13:06 DEBUG  WindowsBackend: previous_distro_name=None
03-31 13:06 DEBUG  WindowsBackend: keyboard_id=67570695
03-31 13:06 DEBUG  WindowsBackend: keyboard_layout=de
03-31 13:06 DEBUG  WindowsBackend: keyboard_variant=
03-31 13:06 DEBUG  CommonBackend: python locale=('de_AT', 'cp1252')
03-31 13:06 DEBUG  CommonBackend: locale=de_AT.UTF-8
03-31 13:06 DEBUG  WindowsBackend: total_memory_mb=495.484375
03-31 13:06 DEBUG  CommonBackend: Searching ISOs on USB devices
03-31 13:06 DEBUG  WindowsBackend: drive=Drive(C: hd 18202.3242188 mb free ntfs)
03-31 13:06 DEBUG  CommonBackend: Searching for local CDs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp is a valid Ubuntu CD
03-31 13:06 DEBUG  WindowsBackend: drive=Drive(D: hd 74989.5625 mb free ntfs)
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp is a valid Ubuntu CD
03-31 13:06 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-31 13:06 DEBUG  WindowsBackend: drive=Drive(G: hd 21552.8125 mb free fat32)
03-31 13:06 DEBUG  WindowsBackend: uninstaller_path=None
03-31 13:06 DEBUG  WindowsBackend: previous_target_dir=None
03-31 13:06 DEBUG  WindowsBackend: previous_distro_name=None
03-31 13:06 DEBUG  WindowsBackend: keyboard_id=67570695
03-31 13:06 DEBUG  WindowsBackend: keyboard_layout=de
03-31 13:06 DEBUG  WindowsBackend: keyboard_variant=
03-31 13:06 DEBUG  CommonBackend: python locale=('de_AT', 'cp1252')
03-31 13:06 DEBUG  CommonBackend: locale=de_AT.UTF-8
03-31 13:06 DEBUG  WindowsBackend: total_memory_mb=495.484375
03-31 13:06 DEBUG  CommonBackend: Searching ISOs on USB devices
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp is a valid Ubuntu Netbook CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp is a valid Kubuntu CD
03-31 13:06 DEBUG  CommonBackend: Searching for local CDs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp is a valid Ubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp is a valid Kubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp is a valid Ubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp is a valid Xubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp is a valid Kubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp is a valid Xubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp is a valid Kubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp is a valid Mythbuntu CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp is a valid Mythbuntu CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp is a valid Xubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp is a valid Xubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp is a valid Mythbuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp is a valid Mythbuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-31 13:06 DEBUG  Distro:     does not contain C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-31 13:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-31 13:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-31 13:06 DEBUG  Distro:   parsing info from str=Xubuntu 10.04.2 "Lucid Lynx" - Release i386 (20110214.1)
03-31 13:06 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110214.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
03-31 13:06 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
03-31 13:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-31 13:06 DEBUG  Distro:   parsing info from str=Xubuntu 10.04.2 "Lucid Lynx" - Release i386 (20110214.1)
03-31 13:06 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110214.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
03-31 13:06 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
03-31 13:06 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
03-31 13:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-31 13:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-31 13:06 DEBUG  Distro: wrong name: Xubuntu != Ubuntu Netbook
03-31 13:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-31 13:06 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
03-31 13:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-31 13:06 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
03-31 13:06 DEBUG  Distro: wrong name: Xubuntu != Ubuntu Netbook
03-31 13:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-31 13:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-31 13:06 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
03-31 13:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-31 13:06 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
03-31 13:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-31 13:06 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
03-31 13:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-31 13:06 DEBUG  Distro: wrong name: Xubuntu != Kubuntu Netbook
03-31 13:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-31 13:06 DEBUG  Distro: wrong name: Xubuntu != Kubuntu Netbook
03-31 13:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-31 13:06 INFO   Distro: Found a valid CD for Xubuntu: E:\
03-31 13:06 INFO   Distro: Found a valid CD for Xubuntu: E:\
03-31 13:06 INFO   root: Running the CD menu...
03-31 13:06 DEBUG  WindowsFrontend: __init__...
03-31 13:06 INFO   root: Running the CD menu...
03-31 13:06 DEBUG  WindowsFrontend: __init__...
03-31 13:06 DEBUG  WindowsFrontend: on_init...
03-31 13:06 INFO   WinuiPage: appname=wubi, localedir=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp\translations, languages=['de_AT', 'de']
03-31 13:06 DEBUG  WindowsFrontend: on_init...
03-31 13:06 INFO   WinuiPage: appname=wubi, localedir=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\translations, languages=['de_AT', 'de']
03-31 13:06 INFO   WinuiPage: appname=wubi, localedir=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl2.tmp\translations, languages=['de_AT', 'de']
03-31 13:06 INFO   WinuiPage: appname=wubi, localedir=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\translations, languages=['de_AT', 'de']
03-31 13:06 INFO   WindowsFrontend: Operation cancelled
03-31 13:06 DEBUG  WindowsFrontend: frontend.quit
03-31 13:06 DEBUG  WindowsFrontend: frontend.on_quit
03-31 13:06 DEBUG  root: application.on_quit
03-31 13:06 INFO   root: sys.exit
03-31 13:06 INFO   root: CD menu finished
03-31 13:06 INFO   root: Running the installer...
03-31 13:06 INFO   WinuiPage: appname=wubi, localedir=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\translations, languages=['de_AT', 'de']
03-31 13:06 INFO   WinuiPage: appname=wubi, localedir=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\translations, languages=['de_AT', 'de']
03-31 13:07 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=15000MB, distro_name=Xubuntu, language=de_DE, locale=de_DE.UTF-8, username=thomas
03-31 13:07 INFO   root: Received settings
03-31 13:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\translations, languages=['de_DE', 'de']
03-31 13:07 DEBUG  TaskList: # Running tasklist...
03-31 13:07 DEBUG  TaskList: ## Running select_target_dir...
03-31 13:07 INFO   WindowsBackend: Installing into G:\ubuntu
03-31 13:07 DEBUG  TaskList: ## Finished select_target_dir
03-31 13:07 DEBUG  TaskList: ## Running create_dir_structure...
03-31 13:07 DEBUG  CommonBackend: Creating dir G:\ubuntu
03-31 13:07 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
03-31 13:07 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
03-31 13:07 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
03-31 13:07 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
03-31 13:07 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
03-31 13:07 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
03-31 13:07 DEBUG  TaskList: ## Finished create_dir_structure
03-31 13:07 DEBUG  TaskList: ## Running uncompress_target_dir...
03-31 13:07 DEBUG  TaskList: ## Finished uncompress_target_dir
03-31 13:07 DEBUG  TaskList: ## Running create_uninstaller...
03-31 13:07 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
03-31 13:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
03-31 13:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
03-31 13:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Xubuntu
03-31 13:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Xubuntu.ico
03-31 13:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.2-rev191
03-31 13:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Xubuntu
03-31 13:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.xubuntu.org](http://www.xubuntu.org)
03-31 13:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-31 13:07 DEBUG  TaskList: ## Finished create_uninstaller
03-31 13:07 DEBUG  TaskList: ## Running copy_installation_files...
03-31 13:07 DEBUG  WindowsBackend: Copying C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
03-31 13:07 DEBUG  WindowsBackend: Copying C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\winboot -> G:\ubuntu\winboot
03-31 13:07 DEBUG  WindowsBackend: Copying C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\data\images\Xubuntu.ico -> G:\ubuntu\Xubuntu.ico
03-31 13:07 DEBUG  TaskList: ## Finished copy_installation_files
03-31 13:07 DEBUG  TaskList: ## Running get_iso...
03-31 13:07 DEBUG  TaskList: New task copy_file
03-31 13:07 DEBUG  TaskList: ### Running copy_file...
03-31 13:12 DEBUG  TaskList: ### Finished copy_file
03-31 13:12 DEBUG  TaskList: New task check_iso
03-31 13:12 DEBUG  TaskList: ### Running check_iso...
03-31 13:12 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
03-31 13:12 DEBUG  Distro:   checking Xubuntu ISO G:\ubuntu\install\installation.iso
03-31 13:13 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
03-31 13:13 DEBUG  Distro:   parsing info from str=Xubuntu 10.04.2 "Lucid Lynx" - Release i386 (20110214.1)
03-31 13:13 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110214.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
03-31 13:13 INFO   Distro: Found a valid iso for Xubuntu: G:\ubuntu\install\installation.iso
03-31 13:13 DEBUG  TaskList: New task get_metalink
03-31 13:13 DEBUG  TaskList: #### Running get_metalink...
03-31 13:13 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-i386.metalink) > G:\ubuntu\install
03-31 13:13 ERROR  CommonBackend: Cannot download metalink file [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10054, 'Connection reset by peer')>
03-31 13:13 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/daily-live/current/lucid-desktop-i386.metalink) > G:\ubuntu\install
03-31 13:13 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/xubuntu/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/xubuntu/daily-live/current/lucid-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10054, 'Connection reset by peer')>
03-31 13:13 DEBUG  TaskList: #### Finished get_metalink
03-31 13:13 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for G:\ubuntu\install\installation.iso, ignoring
03-31 13:13 DEBUG  TaskList: ### Finished check_iso
03-31 13:13 DEBUG  TaskList: ## Finished get_iso
03-31 13:13 DEBUG  TaskList: ## Running extract_kernel...
03-31 13:13 DEBUG  CommonBackend: Copying files from CD E:\
03-31 13:13 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-31 13:13 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
03-31 13:13 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 440f9dbacedaf7b58d1e82c295679675 == 440f9dbacedaf7b58d1e82c295679675
03-31 13:13 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
03-31 13:13 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = cde7abcc43314a8d6d5b2c0718b85db9 == cde7abcc43314a8d6d5b2c0718b85db9
03-31 13:13 DEBUG  TaskList: ## Finished extract_kernel
03-31 13:13 DEBUG  TaskList: ## Running choose_disk_sizes...
03-31 13:13 DEBUG  WindowsBackend: total size=15000
  root=4000
  swap=256
  home=4000
  usr=4000
03-31 13:13 DEBUG  TaskList: ## Finished choose_disk_sizes
03-31 13:13 DEBUG  TaskList: ## Running create_preseed...
03-31 13:13 DEBUG  TaskList: ## Finished create_preseed
03-31 13:13 DEBUG  TaskList: ## Running modify_bootloader...
03-31 13:13 DEBUG  TaskList: New task modify_bootini
03-31 13:13 DEBUG  TaskList: ### Running modify_bootini...
03-31 13:13 DEBUG  WindowsBackend: modify_bootini C:
03-31 13:13 DEBUG  TaskList: ### Finished modify_bootini
03-31 13:13 DEBUG  TaskList: New task modify_bootini
03-31 13:13 DEBUG  TaskList: ### Running modify_bootini...
03-31 13:13 DEBUG  WindowsBackend: modify_bootini D:
03-31 13:13 DEBUG  WindowsBackend: Could not find boot.ini D:\boot.ini
03-31 13:13 DEBUG  TaskList: ### Finished modify_bootini
03-31 13:13 DEBUG  TaskList: New task modify_bootini
03-31 13:13 DEBUG  TaskList: ### Running modify_bootini...
03-31 13:13 DEBUG  WindowsBackend: modify_bootini G:
03-31 13:13 DEBUG  WindowsBackend: Could not find boot.ini G:\boot.ini
03-31 13:13 DEBUG  TaskList: ### Finished modify_bootini
03-31 13:13 DEBUG  TaskList: ## Finished modify_bootloader
03-31 13:13 DEBUG  TaskList: ## Running modify_grub_configuration...
03-31 13:13 DEBUG  TaskList: ## Finished modify_grub_configuration
03-31 13:13 DEBUG  TaskList: ## Running create_virtual_disks...
03-31 13:13 DEBUG  Virtualdisk:  Creating virtual disk G:\ubuntu\disks\root.disk of 4000MB
03-31 13:22 DEBUG  Virtualdisk:  Creating virtual disk G:\ubuntu\disks\home.disk of 4000MB
03-31 13:29 DEBUG  Virtualdisk:  Creating virtual disk G:\ubuntu\disks\usr.disk of 4000MB
03-31 13:36 DEBUG  Virtualdisk:  Creating virtual disk G:\ubuntu\disks\swap.disk of 256MB
03-31 13:36 DEBUG  TaskList: ## Finished create_virtual_disks
03-31 13:36 DEBUG  TaskList: ## Running uncompress_files...
03-31 13:36 DEBUG  TaskList: ## Finished uncompress_files
03-31 13:36 DEBUG  TaskList: ## Running eject_cd...
03-31 13:36 DEBUG  TaskList: ## Finished eject_cd
03-31 13:36 DEBUG  TaskList: # Finished tasklist
03-31 13:36 INFO   root: Almost finished installing
03-31 13:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOKUME~1\Thomas\LOKALE~1\Temp\pyl1.tmp\translations, languages=['de_DE', 'de']
03-31 13:36 INFO   root: Finished installation
03-31 13:36 DEBUG  root: application.quit
03-31 13:36 DEBUG  WindowsFrontend: frontend.quit
03-31 13:36 DEBUG  WindowsFrontend: frontend.on_quit
03-31 13:36 DEBUG  root: application.on_quit
03-31 13:36 INFO   root: sys.exit
Where is the mistake and how can I fix it?

Any help is appreciated. 'Though I am fairly new at linux, I think I can follow your advices.

Best wishes and thank you in advance,
Seantum

---

