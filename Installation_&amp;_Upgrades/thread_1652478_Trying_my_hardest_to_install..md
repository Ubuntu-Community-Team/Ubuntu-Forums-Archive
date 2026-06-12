---
title: "Trying my hardest to install."
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by zebra690 on 2010-12-24
Here's my situation..

I have a dinosaur, it's a really old Dell with 512mb RAM and 80g HDD, the BIOS doesn't have a USB boot option, and it has no CD nor a floppy disk drive. My only option is USB, but again, I have no boot from USB option. I want to use ONLY Ubuntu, I want nothing to do with windows anymore.

I really don't want to use wubi, because it depends on windows, and the only way to put it on it's own partition is to use a CD, which I have no CD drive. I tried the "CD boot helper" to see if it would add a "Boot from usb" option to my BIOS, but I get the following error log:


"12-24 21:11 INFO   root: === wubi 10.10 rev197 ===
12-24 21:11 DEBUG  root: Logfile is c:\docume~1\gray\locals~1\temp\wubi-10.10-rev197.log
12-24 21:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
12-24 21:11 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp\data
12-24 21:11 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
12-24 21:11 DEBUG  CommonBackend: Fetching basic info...
12-24 21:11 DEBUG  CommonBackend: original_exe=D:\wubi.exe
12-24 21:11 DEBUG  CommonBackend: platform=win32
12-24 21:11 DEBUG  CommonBackend: osname=nt
12-24 21:11 DEBUG  CommonBackend: language=en_US
12-24 21:11 DEBUG  CommonBackend: encoding=cp1252
12-24 21:11 DEBUG  WindowsBackend: arch=i386
12-24 21:11 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
12-24 21:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-24 21:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-24 21:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-24 21:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-24 21:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-24 21:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-24 21:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-24 21:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-24 21:11 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-24 21:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-24 21:11 DEBUG  WindowsBackend: Fetching host info...
12-24 21:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-24 21:11 DEBUG  WindowsBackend: windows version=xp
12-24 21:11 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-24 21:11 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-24 21:11 DEBUG  WindowsBackend: windows_build=2600
12-24 21:11 DEBUG  WindowsBackend: gmt=-5
12-24 21:11 DEBUG  WindowsBackend: country=US
12-24 21:11 DEBUG  WindowsBackend: timezone=America/New_York
12-24 21:11 DEBUG  WindowsBackend: windows_username=Gray
12-24 21:11 DEBUG  WindowsBackend: user_full_name=Gray
12-24 21:11 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Gray
12-24 21:11 DEBUG  WindowsBackend: windows_language_code=1033
12-24 21:11 DEBUG  WindowsBackend: windows_language=English
12-24 21:11 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.80GHz
12-24 21:11 DEBUG  WindowsBackend: bootloader=xp
12-24 21:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8525.16796875 mb free ntfs)
12-24 21:11 DEBUG  WindowsBackend: drive=Drive(C: hd 8525.16796875 mb free ntfs)
12-24 21:11 DEBUG  WindowsBackend: drive=Drive(D: removable 6814.484375 mb free fat32)
12-24 21:11 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-24 21:11 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-24 21:11 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-24 21:11 DEBUG  WindowsBackend: keyboard_id=67699721
12-24 21:11 DEBUG  WindowsBackend: keyboard_layout=us
12-24 21:11 DEBUG  WindowsBackend: keyboard_variant=
12-24 21:11 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-24 21:11 DEBUG  CommonBackend: locale=en_US.UTF-8
12-24 21:11 DEBUG  WindowsBackend: total_memory_mb=510.484375
12-24 21:11 DEBUG  CommonBackend: Searching ISOs on USB devices
12-24 21:11 DEBUG  CommonBackend: Searching for local CDs
12-24 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
12-24 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
12-24 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
12-24 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
12-24 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
12-24 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
12-24 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
12-24 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
12-24 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
12-24 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
12-24 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 21:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 21:11 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
12-24 21:11 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
12-24 21:11 DEBUG  Distro: wrong arch: i386 != amd64
12-24 21:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 21:11 INFO   Distro: Found a valid CD for Ubuntu: D:\
12-24 21:11 INFO   root: Running the CD menu...
12-24 21:11 DEBUG  WindowsFrontend: __init__...
12-24 21:11 DEBUG  WindowsFrontend: on_init...
12-24 21:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
12-24 21:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
12-24 21:11 INFO   root: CD menu finished
12-24 21:11 INFO   root: Already installed, running the uninstaller...
12-24 21:11 INFO   root: Running the uninstaller...
12-24 21:11 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
12-24 21:11 DEBUG  root: application.quit
12-24 21:11 DEBUG  WindowsFrontend: frontend.quit
12-24 21:11 DEBUG  WindowsFrontend: frontend.on_quit
12-24 21:11 DEBUG  root: application.on_quit
12-24 21:11 INFO   root: sys.exit
12-24 21:24 INFO   root: === wubi 10.10 rev197 ===
12-24 21:24 DEBUG  root: Logfile is c:\docume~1\gray\locals~1\temp\wubi-10.10-rev197.log
12-24 21:24 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
12-24 21:24 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp\data
12-24 21:24 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp\bin\7z.exe
12-24 21:24 DEBUG  CommonBackend: Fetching basic info...
12-24 21:24 DEBUG  CommonBackend: original_exe=D:\wubi.exe
12-24 21:24 DEBUG  CommonBackend: platform=win32
12-24 21:24 DEBUG  CommonBackend: osname=nt
12-24 21:24 DEBUG  CommonBackend: language=en_US
12-24 21:24 DEBUG  CommonBackend: encoding=cp1252
12-24 21:24 DEBUG  WindowsBackend: arch=i386
12-24 21:24 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp\data\isolist.ini
12-24 21:24 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-24 21:24 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-24 21:24 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-24 21:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-24 21:24 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-24 21:24 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-24 21:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-24 21:24 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-24 21:24 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-24 21:24 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-24 21:24 DEBUG  WindowsBackend: Fetching host info...
12-24 21:24 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-24 21:24 DEBUG  WindowsBackend: windows version=xp
12-24 21:24 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-24 21:24 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-24 21:24 DEBUG  WindowsBackend: windows_build=2600
12-24 21:24 DEBUG  WindowsBackend: gmt=-5
12-24 21:24 DEBUG  WindowsBackend: country=US
12-24 21:24 DEBUG  WindowsBackend: timezone=America/New_York
12-24 21:24 DEBUG  WindowsBackend: windows_username=Gray
12-24 21:24 DEBUG  WindowsBackend: user_full_name=Gray
12-24 21:24 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Gray
12-24 21:24 DEBUG  WindowsBackend: windows_language_code=1033
12-24 21:24 DEBUG  WindowsBackend: windows_language=English
12-24 21:24 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.80GHz
12-24 21:24 DEBUG  WindowsBackend: bootloader=xp
12-24 21:24 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8491.140625 mb free ntfs)
12-24 21:24 DEBUG  WindowsBackend: drive=Drive(C: hd 8491.140625 mb free ntfs)
12-24 21:24 DEBUG  WindowsBackend: drive=Drive(D: removable 6814.484375 mb free fat32)
12-24 21:24 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-24 21:24 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-24 21:24 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-24 21:24 DEBUG  WindowsBackend: keyboard_id=67699721
12-24 21:24 DEBUG  WindowsBackend: keyboard_layout=us
12-24 21:24 DEBUG  WindowsBackend: keyboard_variant=
12-24 21:24 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-24 21:24 DEBUG  CommonBackend: locale=en_US.UTF-8
12-24 21:24 DEBUG  WindowsBackend: total_memory_mb=510.484375
12-24 21:24 DEBUG  CommonBackend: Searching ISOs on USB devices
12-24 21:24 DEBUG  CommonBackend: Searching for local CDs
12-24 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
12-24 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
12-24 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
12-24 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
12-24 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Netbook CD
12-24 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
12-24 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
12-24 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
12-24 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
12-24 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
12-24 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
12-24 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
12-24 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
12-24 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
12-24 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
12-24 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
12-24 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
12-24 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
12-24 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
12-24 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
12-24 21:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 21:24 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
12-24 21:24 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
12-24 21:24 DEBUG  Distro: wrong arch: i386 != amd64
12-24 21:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 21:24 INFO   Distro: Found a valid CD for Ubuntu: D:\
12-24 21:24 INFO   root: Running the CD menu...
12-24 21:24 DEBUG  WindowsFrontend: __init__...
12-24 21:24 DEBUG  WindowsFrontend: on_init...
12-24 21:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
12-24 21:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
12-24 21:24 INFO   root: CD menu finished
12-24 21:24 INFO   root: Already installed, running the uninstaller...
12-24 21:24 INFO   root: Running the uninstaller...
12-24 21:24 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
12-24 21:25 DEBUG  root: application.quit
12-24 21:25 DEBUG  WindowsFrontend: frontend.quit
12-24 21:25 DEBUG  WindowsFrontend: frontend.on_quit
12-24 21:25 DEBUG  root: application.on_quit
12-24 21:25 INFO   root: sys.exit
12-24 21:25 INFO   root: === wubi 10.10 rev197 ===
12-24 21:25 DEBUG  root: Logfile is c:\docume~1\gray\locals~1\temp\wubi-10.10-rev197.log
12-24 21:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
12-24 21:25 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\data
12-24 21:25 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\bin\7z.exe
12-24 21:25 DEBUG  CommonBackend: Fetching basic info...
12-24 21:25 DEBUG  CommonBackend: original_exe=D:\wubi.exe
12-24 21:25 DEBUG  CommonBackend: platform=win32
12-24 21:25 DEBUG  CommonBackend: osname=nt
12-24 21:25 DEBUG  CommonBackend: language=en_US
12-24 21:25 DEBUG  CommonBackend: encoding=cp1252
12-24 21:25 DEBUG  WindowsBackend: arch=i386
12-24 21:25 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\data\isolist.ini
12-24 21:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-24 21:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-24 21:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-24 21:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-24 21:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-24 21:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-24 21:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-24 21:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-24 21:25 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-24 21:25 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-24 21:25 DEBUG  WindowsBackend: Fetching host info...
12-24 21:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-24 21:25 DEBUG  WindowsBackend: windows version=xp
12-24 21:25 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-24 21:25 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-24 21:25 DEBUG  WindowsBackend: windows_build=2600
12-24 21:25 DEBUG  WindowsBackend: gmt=-5
12-24 21:25 DEBUG  WindowsBackend: country=US
12-24 21:25 DEBUG  WindowsBackend: timezone=America/New_York
12-24 21:25 DEBUG  WindowsBackend: windows_username=Gray
12-24 21:25 DEBUG  WindowsBackend: user_full_name=Gray
12-24 21:25 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Gray
12-24 21:25 DEBUG  WindowsBackend: windows_language_code=1033
12-24 21:25 DEBUG  WindowsBackend: windows_language=English
12-24 21:25 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.80GHz
12-24 21:25 DEBUG  WindowsBackend: bootloader=xp
12-24 21:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9154.125 mb free ntfs)
12-24 21:25 DEBUG  WindowsBackend: drive=Drive(C: hd 9154.125 mb free ntfs)
12-24 21:25 DEBUG  WindowsBackend: drive=Drive(D: removable 6814.484375 mb free fat32)
12-24 21:25 DEBUG  WindowsBackend: uninstaller_path=None
12-24 21:25 DEBUG  WindowsBackend: previous_target_dir=None
12-24 21:25 DEBUG  WindowsBackend: previous_distro_name=None
12-24 21:25 DEBUG  WindowsBackend: keyboard_id=67699721
12-24 21:25 DEBUG  WindowsBackend: keyboard_layout=us
12-24 21:25 DEBUG  WindowsBackend: keyboard_variant=
12-24 21:25 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-24 21:25 DEBUG  CommonBackend: locale=en_US.UTF-8
12-24 21:25 DEBUG  WindowsBackend: total_memory_mb=510.484375
12-24 21:25 DEBUG  CommonBackend: Searching ISOs on USB devices
12-24 21:25 DEBUG  CommonBackend: Searching for local CDs
12-24 21:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
12-24 21:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
12-24 21:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
12-24 21:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
12-24 21:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu Netbook CD
12-24 21:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
12-24 21:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
12-24 21:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
12-24 21:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
12-24 21:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
12-24 21:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu Netbook CD
12-24 21:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
12-24 21:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
12-24 21:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
12-24 21:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
12-24 21:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
12-24 21:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
12-24 21:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
12-24 21:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
12-24 21:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
12-24 21:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 21:25 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
12-24 21:25 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
12-24 21:25 DEBUG  Distro: wrong arch: i386 != amd64
12-24 21:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 21:25 INFO   Distro: Found a valid CD for Ubuntu: D:\
12-24 21:25 INFO   root: Running the CD menu...
12-24 21:25 DEBUG  WindowsFrontend: __init__...
12-24 21:25 DEBUG  WindowsFrontend: on_init...
12-24 21:25 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
12-24 21:25 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
12-24 21:25 INFO   root: CD menu finished
12-24 21:25 INFO   root: Running the CD boot helper...
12-24 21:25 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
12-24 21:25 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
12-24 21:26 INFO   root: CD boot helper confirmed
12-24 21:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
12-24 21:26 DEBUG  TaskList: # Running tasklist...
12-24 21:26 DEBUG  TaskList: ## Running select_target_dir...
12-24 21:26 INFO   WindowsBackend: Installing into C:\ubuntu
12-24 21:26 DEBUG  TaskList: ## Finished select_target_dir
12-24 21:26 DEBUG  TaskList: ## Running create_dir_structure...
12-24 21:26 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-24 21:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-24 21:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-24 21:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-24 21:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-24 21:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-24 21:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-24 21:26 DEBUG  TaskList: ## Finished create_dir_structure
12-24 21:26 DEBUG  TaskList: ## Running uncompress_target_dir...
12-24 21:26 DEBUG  TaskList: ## Finished uncompress_target_dir
12-24 21:26 DEBUG  TaskList: ## Running create_uninstaller...
12-24 21:26 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-24 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-24 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-24 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-24 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-24 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
12-24 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-24 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-24 21:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-24 21:26 DEBUG  TaskList: ## Finished create_uninstaller
12-24 21:26 DEBUG  TaskList: ## Running copy_installation_files...
12-24 21:26 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
12-24 21:26 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\winboot -> C:\ubuntu\winboot
12-24 21:26 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl4.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
12-24 21:26 DEBUG  TaskList: ## Finished copy_installation_files
12-24 21:26 DEBUG  TaskList: ## Running use_cd...
12-24 21:26 DEBUG  TaskList: New task copy_file
12-24 21:26 DEBUG  TaskList: ### Running copy_file...
12-24 21:41 DEBUG  TaskList: ### Finished copy_file
12-24 21:41 DEBUG  TaskList: New task check_iso
12-24 21:41 DEBUG  TaskList: ### Running check_iso...
12-24 21:41 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
12-24 21:41 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
12-24 21:41 DEBUG  Distro:     wrong size: 8022057984 > 900000000
12-24 21:41 DEBUG  TaskList: ### Finished check_iso
12-24 21:41 DEBUG  TaskList: ## Finished use_cd
12-24 21:41 DEBUG  TaskList: ## Running extract_kernel...
12-24 21:41 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
12-24 21:41 DEBUG  TaskList: # Cancelling tasklist
12-24 21:41 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
12-24 21:41 DEBUG  TaskList: # Finished tasklist
12-24 21:43 INFO   root: === wubi 10.10 rev197 ===
12-24 21:43 DEBUG  root: Logfile is c:\docume~1\gray\locals~1\temp\wubi-10.10-rev197.log
12-24 21:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
12-24 21:43 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\data
12-24 21:43 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\bin\7z.exe
12-24 21:43 DEBUG  CommonBackend: Fetching basic info...
12-24 21:43 DEBUG  CommonBackend: original_exe=D:\wubi.exe
12-24 21:43 DEBUG  CommonBackend: platform=win32
12-24 21:43 DEBUG  CommonBackend: osname=nt
12-24 21:43 DEBUG  CommonBackend: language=en_US
12-24 21:43 DEBUG  CommonBackend: encoding=cp1252
12-24 21:43 DEBUG  WindowsBackend: arch=i386
12-24 21:43 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\data\isolist.ini
12-24 21:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-24 21:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-24 21:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-24 21:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-24 21:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-24 21:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-24 21:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-24 21:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-24 21:43 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-24 21:43 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-24 21:43 DEBUG  WindowsBackend: Fetching host info...
12-24 21:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-24 21:43 DEBUG  WindowsBackend: windows version=xp
12-24 21:43 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-24 21:43 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-24 21:43 DEBUG  WindowsBackend: windows_build=2600
12-24 21:43 DEBUG  WindowsBackend: gmt=-5
12-24 21:43 DEBUG  WindowsBackend: country=US
12-24 21:43 DEBUG  WindowsBackend: timezone=America/New_York
12-24 21:43 DEBUG  WindowsBackend: windows_username=Gray
12-24 21:43 DEBUG  WindowsBackend: user_full_name=Gray
12-24 21:43 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Gray
12-24 21:43 DEBUG  WindowsBackend: windows_language_code=1033
12-24 21:43 DEBUG  WindowsBackend: windows_language=English
12-24 21:43 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.80GHz
12-24 21:43 DEBUG  WindowsBackend: bootloader=xp
12-24 21:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 1494.48046875 mb free ntfs)
12-24 21:43 DEBUG  WindowsBackend: drive=Drive(C: hd 1494.48046875 mb free ntfs)
12-24 21:43 DEBUG  WindowsBackend: drive=Drive(D: removable 6814.484375 mb free fat32)
12-24 21:43 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-24 21:43 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-24 21:43 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-24 21:43 DEBUG  WindowsBackend: keyboard_id=67699721
12-24 21:43 DEBUG  WindowsBackend: keyboard_layout=us
12-24 21:43 DEBUG  WindowsBackend: keyboard_variant=
12-24 21:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-24 21:43 DEBUG  CommonBackend: locale=en_US.UTF-8
12-24 21:43 DEBUG  WindowsBackend: total_memory_mb=510.484375
12-24 21:43 DEBUG  CommonBackend: Searching ISOs on USB devices
12-24 21:43 DEBUG  CommonBackend: Searching for local CDs
12-24 21:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Ubuntu CD
12-24 21:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Ubuntu CD
12-24 21:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Ubuntu Netbook CD
12-24 21:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Kubuntu CD
12-24 21:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Kubuntu CD
12-24 21:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Kubuntu Netbook CD
12-24 21:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Xubuntu CD
12-24 21:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Xubuntu CD
12-24 21:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Mythbuntu CD
12-24 21:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:43 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Mythbuntu CD
12-24 21:43 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 21:43 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
12-24 21:43 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
12-24 21:43 DEBUG  Distro: wrong arch: i386 != amd64
12-24 21:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 21:43 INFO   Distro: Found a valid CD for Ubuntu: D:\
12-24 21:43 INFO   root: Running the CD menu...
12-24 21:43 DEBUG  WindowsFrontend: __init__...
12-24 21:43 DEBUG  WindowsFrontend: on_init...
12-24 21:43 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\translations, languages=['en_US', 'en']
12-24 21:44 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\translations, languages=['en_US', 'en']
12-24 21:44 INFO   root: CD menu finished
12-24 21:44 INFO   root: Already installed, running the uninstaller...
12-24 21:44 INFO   root: Running the uninstaller...
12-24 21:44 INFO   CommonBackend: This is the uninstaller running
12-24 21:44 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\translations, languages=['en_US', 'en']
12-24 21:44 INFO   root: Received settings
12-24 21:44 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\translations, languages=['en_US', 'en']
12-24 21:44 DEBUG  TaskList: # Running tasklist...
12-24 21:44 DEBUG  TaskList: ## Running Backup ISO...
12-24 21:44 DEBUG  TaskList: ## Finished Backup ISO
12-24 21:44 DEBUG  TaskList: ## Running Remove bootloader entry...
12-24 21:44 ERROR  WindowsBackend: Cannot find bcdedit
12-24 21:44 DEBUG  WindowsBackend: undo_bootini C:
12-24 21:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 1494.48046875 mb free ntfs)
12-24 21:44 DEBUG  WindowsBackend: undo_bootini D:
12-24 21:44 DEBUG  WindowsBackend: undo_configsys Drive(D: removable 6814.484375 mb free fat32)
12-24 21:44 DEBUG  TaskList: ## Finished Remove bootloader entry
12-24 21:44 DEBUG  TaskList: ## Running Remove target dir...
12-24 21:44 DEBUG  CommonBackend: Deleting C:\ubuntu
12-24 21:44 DEBUG  TaskList: ## Finished Remove target dir
12-24 21:44 DEBUG  TaskList: ## Running Remove registry key...
12-24 21:44 DEBUG  TaskList: ## Finished Remove registry key
12-24 21:44 DEBUG  TaskList: # Finished tasklist
12-24 21:44 INFO   root: Almost finished uninstalling
12-24 21:44 INFO   root: Finished uninstallation
12-24 21:44 DEBUG  CommonBackend: Fetching basic info...
12-24 21:44 DEBUG  CommonBackend: original_exe=D:\wubi.exe
12-24 21:44 DEBUG  CommonBackend: platform=win32
12-24 21:44 DEBUG  CommonBackend: osname=nt
12-24 21:44 DEBUG  WindowsBackend: arch=i386
12-24 21:44 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\data\isolist.ini
12-24 21:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-24 21:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-24 21:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-24 21:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-24 21:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-24 21:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-24 21:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-24 21:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-24 21:44 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-24 21:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-24 21:44 DEBUG  WindowsBackend: Fetching host info...
12-24 21:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-24 21:44 DEBUG  WindowsBackend: windows version=xp
12-24 21:44 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-24 21:44 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-24 21:44 DEBUG  WindowsBackend: windows_build=2600
12-24 21:44 DEBUG  WindowsBackend: gmt=-5
12-24 21:44 DEBUG  WindowsBackend: country=US
12-24 21:44 DEBUG  WindowsBackend: timezone=America/New_York
12-24 21:44 DEBUG  WindowsBackend: windows_username=Gray
12-24 21:44 DEBUG  WindowsBackend: user_full_name=Gray
12-24 21:44 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Gray
12-24 21:44 DEBUG  WindowsBackend: windows_language_code=1033
12-24 21:44 DEBUG  WindowsBackend: windows_language=English
12-24 21:44 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.80GHz
12-24 21:44 DEBUG  WindowsBackend: bootloader=xp
12-24 21:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9146.5 mb free ntfs)
12-24 21:44 DEBUG  WindowsBackend: drive=Drive(C: hd 9146.5 mb free ntfs)
12-24 21:44 DEBUG  WindowsBackend: drive=Drive(D: removable 6814.484375 mb free fat32)
12-24 21:44 DEBUG  WindowsBackend: uninstaller_path=None
12-24 21:44 DEBUG  WindowsBackend: previous_target_dir=None
12-24 21:44 DEBUG  WindowsBackend: previous_distro_name=None
12-24 21:44 DEBUG  WindowsBackend: keyboard_id=67699721
12-24 21:44 DEBUG  WindowsBackend: keyboard_layout=us
12-24 21:44 DEBUG  WindowsBackend: keyboard_variant=
12-24 21:44 DEBUG  WindowsBackend: total_memory_mb=510.484375
12-24 21:44 DEBUG  CommonBackend: Searching ISOs on USB devices
12-24 21:44 DEBUG  CommonBackend: Searching for local CDs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Ubuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Ubuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Ubuntu Netbook CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Kubuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Kubuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Kubuntu Netbook CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Xubuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Xubuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Mythbuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp is a valid Mythbuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 21:44 DEBUG  Distro: wrong arch: i386 != amd64
12-24 21:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 21:44 INFO   Distro: Found a valid CD for Ubuntu: D:\
12-24 21:44 INFO   root: Running the CD boot helper...
12-24 21:44 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\translations, languages=['en_US', 'en']
12-24 21:44 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pylA.tmp\translations, languages=['en_US', 'en']
12-24 21:44 INFO   WindowsFrontend: Operation cancelled
12-24 21:44 DEBUG  WindowsFrontend: frontend.quit
12-24 21:44 DEBUG  WindowsFrontend: frontend.on_quit
12-24 21:44 DEBUG  root: application.on_quit
12-24 21:44 INFO   root: sys.exit
12-24 21:44 INFO   root: === wubi 10.10 rev197 ===
12-24 21:44 DEBUG  root: Logfile is c:\docume~1\gray\locals~1\temp\wubi-10.10-rev197.log
12-24 21:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
12-24 21:44 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp\data
12-24 21:44 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp\bin\7z.exe
12-24 21:44 DEBUG  CommonBackend: Fetching basic info...
12-24 21:44 DEBUG  CommonBackend: original_exe=D:\wubi.exe
12-24 21:44 DEBUG  CommonBackend: platform=win32
12-24 21:44 DEBUG  CommonBackend: osname=nt
12-24 21:44 DEBUG  CommonBackend: language=en_US
12-24 21:44 DEBUG  CommonBackend: encoding=cp1252
12-24 21:44 DEBUG  WindowsBackend: arch=i386
12-24 21:44 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp\data\isolist.ini
12-24 21:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-24 21:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-24 21:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-24 21:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-24 21:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-24 21:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-24 21:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-24 21:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-24 21:44 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-24 21:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-24 21:44 DEBUG  WindowsBackend: Fetching host info...
12-24 21:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-24 21:44 DEBUG  WindowsBackend: windows version=xp
12-24 21:44 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-24 21:44 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-24 21:44 DEBUG  WindowsBackend: windows_build=2600
12-24 21:44 DEBUG  WindowsBackend: gmt=-5
12-24 21:44 DEBUG  WindowsBackend: country=US
12-24 21:44 DEBUG  WindowsBackend: timezone=America/New_York
12-24 21:44 DEBUG  WindowsBackend: windows_username=Gray
12-24 21:44 DEBUG  WindowsBackend: user_full_name=Gray
12-24 21:44 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Gray
12-24 21:44 DEBUG  WindowsBackend: windows_language_code=1033
12-24 21:44 DEBUG  WindowsBackend: windows_language=English
12-24 21:44 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.80GHz
12-24 21:44 DEBUG  WindowsBackend: bootloader=xp
12-24 21:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9146.6796875 mb free ntfs)
12-24 21:44 DEBUG  WindowsBackend: drive=Drive(C: hd 9146.6796875 mb free ntfs)
12-24 21:44 DEBUG  WindowsBackend: drive=Drive(D: removable 6814.484375 mb free fat32)
12-24 21:44 DEBUG  WindowsBackend: uninstaller_path=None
12-24 21:44 DEBUG  WindowsBackend: previous_target_dir=None
12-24 21:44 DEBUG  WindowsBackend: previous_distro_name=None
12-24 21:44 DEBUG  WindowsBackend: keyboard_id=67699721
12-24 21:44 DEBUG  WindowsBackend: keyboard_layout=us
12-24 21:44 DEBUG  WindowsBackend: keyboard_variant=
12-24 21:44 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-24 21:44 DEBUG  CommonBackend: locale=en_US.UTF-8
12-24 21:44 DEBUG  WindowsBackend: total_memory_mb=510.484375
12-24 21:44 DEBUG  CommonBackend: Searching ISOs on USB devices
12-24 21:44 DEBUG  CommonBackend: Searching for local CDs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp is a valid Ubuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp is a valid Ubuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp is a valid Ubuntu Netbook CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp is a valid Kubuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp is a valid Kubuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp is a valid Kubuntu Netbook CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp is a valid Xubuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp is a valid Xubuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp is a valid Mythbuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp is a valid Mythbuntu CD
12-24 21:44 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
12-24 21:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 21:44 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
12-24 21:44 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
12-24 21:44 DEBUG  Distro: wrong arch: i386 != amd64
12-24 21:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 21:44 INFO   Distro: Found a valid CD for Ubuntu: D:\
12-24 21:44 INFO   root: Running the CD menu...
12-24 21:44 DEBUG  WindowsFrontend: __init__...
12-24 21:44 DEBUG  WindowsFrontend: on_init...
12-24 21:44 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp\translations, languages=['en_US', 'en']
12-24 21:44 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pylC.tmp\translations, languages=['en_US', 'en']
12-24 21:44 INFO   root: CD menu finished
12-24 21:44 INFO   root: Rebooting
12-24 21:44 DEBUG  TaskList: # Running tasklist...
12-24 21:44 DEBUG  TaskList: ## Running reboot...
12-24 21:44 DEBUG  TaskList: ## Finished reboot
12-24 21:44 DEBUG  TaskList: # Finished tasklist
12-24 21:44 DEBUG  root: application.quit
12-24 21:44 DEBUG  WindowsFrontend: frontend.quit
12-24 21:44 DEBUG  WindowsFrontend: frontend.on_quit
12-24 21:44 DEBUG  root: application.on_quit
12-24 21:44 INFO   root: sys.exit
12-24 21:58 INFO   root: === wubi 10.10 rev197 ===
12-24 21:58 DEBUG  root: Logfile is c:\docume~1\gray\locals~1\temp\wubi-10.10-rev197.log
12-24 21:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
12-24 21:58 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\data
12-24 21:58 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\bin\7z.exe
12-24 21:58 DEBUG  CommonBackend: Fetching basic info...
12-24 21:58 DEBUG  CommonBackend: original_exe=D:\wubi.exe
12-24 21:58 DEBUG  CommonBackend: platform=win32
12-24 21:58 DEBUG  CommonBackend: osname=nt
12-24 21:58 DEBUG  CommonBackend: language=en_US
12-24 21:58 DEBUG  CommonBackend: encoding=cp1252
12-24 21:58 DEBUG  WindowsBackend: arch=i386
12-24 21:58 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\data\isolist.ini
12-24 21:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-24 21:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-24 21:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-24 21:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-24 21:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-24 21:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-24 21:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-24 21:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-24 21:58 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-24 21:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-24 21:58 DEBUG  WindowsBackend: Fetching host info...
12-24 21:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-24 21:58 DEBUG  WindowsBackend: windows version=xp
12-24 21:58 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-24 21:58 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-24 21:58 DEBUG  WindowsBackend: windows_build=2600
12-24 21:58 DEBUG  WindowsBackend: gmt=-5
12-24 21:58 DEBUG  WindowsBackend: country=US
12-24 21:58 DEBUG  WindowsBackend: timezone=America/New_York
12-24 21:58 DEBUG  WindowsBackend: windows_username=Gray
12-24 21:58 DEBUG  WindowsBackend: user_full_name=Gray
12-24 21:58 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Gray
12-24 21:58 DEBUG  WindowsBackend: windows_language_code=1033
12-24 21:58 DEBUG  WindowsBackend: windows_language=English
12-24 21:58 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.80GHz
12-24 21:58 DEBUG  WindowsBackend: bootloader=xp
12-24 21:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9142.015625 mb free ntfs)
12-24 21:58 DEBUG  WindowsBackend: drive=Drive(C: hd 9142.015625 mb free ntfs)
12-24 21:58 DEBUG  WindowsBackend: drive=Drive(D: removable 6814.484375 mb free fat32)
12-24 21:58 DEBUG  WindowsBackend: uninstaller_path=None
12-24 21:58 DEBUG  WindowsBackend: previous_target_dir=None
12-24 21:58 DEBUG  WindowsBackend: previous_distro_name=None
12-24 21:58 DEBUG  WindowsBackend: keyboard_id=67699721
12-24 21:58 DEBUG  WindowsBackend: keyboard_layout=us
12-24 21:58 DEBUG  WindowsBackend: keyboard_variant=
12-24 21:58 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-24 21:58 DEBUG  CommonBackend: locale=en_US.UTF-8
12-24 21:58 DEBUG  WindowsBackend: total_memory_mb=510.484375
12-24 21:58 DEBUG  CommonBackend: Searching ISOs on USB devices
12-24 21:58 DEBUG  CommonBackend: Searching for local CDs
12-24 21:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
12-24 21:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
12-24 21:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
12-24 21:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
12-24 21:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu Netbook CD
12-24 21:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
12-24 21:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
12-24 21:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
12-24 21:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
12-24 21:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
12-24 21:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu Netbook CD
12-24 21:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
12-24 21:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
12-24 21:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
12-24 21:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
12-24 21:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
12-24 21:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
12-24 21:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
12-24 21:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
12-24 21:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
12-24 21:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 21:58 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
12-24 21:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
12-24 21:58 DEBUG  Distro: wrong arch: i386 != amd64
12-24 21:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 21:58 INFO   Distro: Found a valid CD for Ubuntu: D:\
12-24 21:58 INFO   root: Running the CD menu...
12-24 21:58 DEBUG  WindowsFrontend: __init__...
12-24 21:58 DEBUG  WindowsFrontend: on_init...
12-24 21:58 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
12-24 21:58 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
12-24 21:59 INFO   root: CD menu finished
12-24 21:59 INFO   root: Running the installer...
12-24 21:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
12-24 21:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
12-24 22:00 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=3000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=gray
12-24 22:00 INFO   root: Received settings
12-24 22:00 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
12-24 22:00 DEBUG  TaskList: # Running tasklist...
12-24 22:00 DEBUG  TaskList: ## Running select_target_dir...
12-24 22:00 INFO   WindowsBackend: Installing into C:\ubuntu
12-24 22:00 DEBUG  TaskList: ## Finished select_target_dir
12-24 22:00 DEBUG  TaskList: ## Running create_dir_structure...
12-24 22:00 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-24 22:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-24 22:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-24 22:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-24 22:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-24 22:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-24 22:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-24 22:00 DEBUG  TaskList: ## Finished create_dir_structure
12-24 22:00 DEBUG  TaskList: ## Running uncompress_target_dir...
12-24 22:00 DEBUG  TaskList: ## Finished uncompress_target_dir
12-24 22:00 DEBUG  TaskList: ## Running create_uninstaller...
12-24 22:00 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-24 22:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-24 22:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-24 22:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-24 22:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-24 22:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
12-24 22:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-24 22:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-24 22:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-24 22:00 DEBUG  TaskList: ## Finished create_uninstaller
12-24 22:00 DEBUG  TaskList: ## Running copy_installation_files...
12-24 22:00 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
12-24 22:00 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\winboot -> C:\ubuntu\winboot
12-24 22:00 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl3.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
12-24 22:00 DEBUG  TaskList: ## Finished copy_installation_files
12-24 22:00 DEBUG  TaskList: ## Running get_iso...
12-24 22:00 DEBUG  TaskList: New task copy_file
12-24 22:00 DEBUG  TaskList: ### Running copy_file...
12-24 22:04 INFO   WindowsFrontend: Operation cancelled
12-24 22:04 DEBUG  WindowsFrontend: frontend.quit
12-24 22:04 DEBUG  WindowsFrontend: frontend.on_quit
12-24 22:04 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
12-24 22:04 DEBUG  TaskList: # Cancelling tasklist
12-24 22:04 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
12-24 22:04 DEBUG  root: application.on_quit
12-24 22:04 DEBUG  root: Forceful exit
12-24 22:04 INFO   root: sys.exit
12-24 22:06 INFO   root: === wubi 10.10 rev197 ===
12-24 22:06 DEBUG  root: Logfile is c:\docume~1\gray\locals~1\temp\wubi-10.10-rev197.log
12-24 22:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
12-24 22:06 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\data
12-24 22:06 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\bin\7z.exe
12-24 22:06 DEBUG  CommonBackend: Fetching basic info...
12-24 22:06 DEBUG  CommonBackend: original_exe=D:\wubi.exe
12-24 22:06 DEBUG  CommonBackend: platform=win32
12-24 22:06 DEBUG  CommonBackend: osname=nt
12-24 22:06 DEBUG  CommonBackend: language=en_US
12-24 22:06 DEBUG  CommonBackend: encoding=cp1252
12-24 22:06 DEBUG  WindowsBackend: arch=i386
12-24 22:06 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\data\isolist.ini
12-24 22:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-24 22:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-24 22:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-24 22:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-24 22:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-24 22:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-24 22:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-24 22:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-24 22:06 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-24 22:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-24 22:06 DEBUG  WindowsBackend: Fetching host info...
12-24 22:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-24 22:06 DEBUG  WindowsBackend: windows version=xp
12-24 22:06 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-24 22:06 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-24 22:06 DEBUG  WindowsBackend: windows_build=2600
12-24 22:06 DEBUG  WindowsBackend: gmt=-5
12-24 22:06 DEBUG  WindowsBackend: country=US
12-24 22:06 DEBUG  WindowsBackend: timezone=America/New_York
12-24 22:06 DEBUG  WindowsBackend: windows_username=Gray
12-24 22:06 DEBUG  WindowsBackend: user_full_name=Gray
12-24 22:06 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Gray
12-24 22:06 DEBUG  WindowsBackend: windows_language_code=1033
12-24 22:06 DEBUG  WindowsBackend: windows_language=English
12-24 22:06 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.80GHz
12-24 22:06 DEBUG  WindowsBackend: bootloader=xp
12-24 22:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 7039.1953125 mb free ntfs)
12-24 22:06 DEBUG  WindowsBackend: drive=Drive(C: hd 7039.19140625 mb free ntfs)
12-24 22:06 DEBUG  WindowsBackend: drive=Drive(D: removable 6814.484375 mb free fat32)
12-24 22:06 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-24 22:06 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-24 22:06 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-24 22:06 DEBUG  WindowsBackend: keyboard_id=67699721
12-24 22:06 DEBUG  WindowsBackend: keyboard_layout=us
12-24 22:06 DEBUG  WindowsBackend: keyboard_variant=
12-24 22:06 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-24 22:06 DEBUG  CommonBackend: locale=en_US.UTF-8
12-24 22:06 DEBUG  WindowsBackend: total_memory_mb=510.484375
12-24 22:06 DEBUG  CommonBackend: Searching ISOs on USB devices
12-24 22:06 DEBUG  CommonBackend: Searching for local CDs
12-24 22:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
12-24 22:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
12-24 22:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu Netbook CD
12-24 22:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
12-24 22:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
12-24 22:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu Netbook CD
12-24 22:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
12-24 22:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
12-24 22:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
12-24 22:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
12-24 22:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 22:06 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
12-24 22:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
12-24 22:06 DEBUG  Distro: wrong arch: i386 != amd64
12-24 22:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 22:06 INFO   Distro: Found a valid CD for Ubuntu: D:\
12-24 22:06 INFO   root: Running the CD menu...
12-24 22:06 DEBUG  WindowsFrontend: __init__...
12-24 22:06 DEBUG  WindowsFrontend: on_init...
12-24 22:06 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
12-24 22:06 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
12-24 22:07 INFO   root: CD menu finished
12-24 22:07 INFO   root: Already installed, running the uninstaller...
12-24 22:07 INFO   root: Running the uninstaller...
12-24 22:07 INFO   CommonBackend: This is the uninstaller running
12-24 22:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
12-24 22:07 INFO   root: Received settings
12-24 22:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
12-24 22:07 DEBUG  TaskList: # Running tasklist...
12-24 22:07 DEBUG  TaskList: ## Running Backup ISO...
12-24 22:07 DEBUG  TaskList: ## Finished Backup ISO
12-24 22:07 DEBUG  TaskList: ## Running Remove bootloader entry...
12-24 22:07 ERROR  WindowsBackend: Cannot find bcdedit
12-24 22:07 DEBUG  WindowsBackend: undo_bootini C:
12-24 22:07 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 7039.19140625 mb free ntfs)
12-24 22:07 DEBUG  WindowsBackend: undo_bootini D:
12-24 22:07 DEBUG  WindowsBackend: undo_configsys Drive(D: removable 6814.484375 mb free fat32)
12-24 22:07 DEBUG  TaskList: ## Finished Remove bootloader entry
12-24 22:07 DEBUG  TaskList: ## Running Remove target dir...
12-24 22:07 DEBUG  CommonBackend: Deleting C:\ubuntu
12-24 22:07 DEBUG  TaskList: ## Finished Remove target dir
12-24 22:07 DEBUG  TaskList: ## Running Remove registry key...
12-24 22:07 DEBUG  TaskList: ## Finished Remove registry key
12-24 22:07 DEBUG  TaskList: # Finished tasklist
12-24 22:07 INFO   root: Almost finished uninstalling
12-24 22:07 INFO   root: Finished uninstallation
12-24 22:07 DEBUG  CommonBackend: Fetching basic info...
12-24 22:07 DEBUG  CommonBackend: original_exe=D:\wubi.exe
12-24 22:07 DEBUG  CommonBackend: platform=win32
12-24 22:07 DEBUG  CommonBackend: osname=nt
12-24 22:07 DEBUG  WindowsBackend: arch=i386
12-24 22:07 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\data\isolist.ini
12-24 22:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-24 22:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-24 22:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-24 22:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-24 22:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-24 22:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-24 22:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-24 22:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-24 22:07 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-24 22:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-24 22:07 DEBUG  WindowsBackend: Fetching host info...
12-24 22:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-24 22:07 DEBUG  WindowsBackend: windows version=xp
12-24 22:07 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-24 22:07 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-24 22:07 DEBUG  WindowsBackend: windows_build=2600
12-24 22:07 DEBUG  WindowsBackend: gmt=-5
12-24 22:07 DEBUG  WindowsBackend: country=US
12-24 22:07 DEBUG  WindowsBackend: timezone=America/New_York
12-24 22:07 DEBUG  WindowsBackend: windows_username=Gray
12-24 22:07 DEBUG  WindowsBackend: user_full_name=Gray
12-24 22:07 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Gray
12-24 22:07 DEBUG  WindowsBackend: windows_language_code=1033
12-24 22:07 DEBUG  WindowsBackend: windows_language=English
12-24 22:07 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.80GHz
12-24 22:07 DEBUG  WindowsBackend: bootloader=xp
12-24 22:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9139.640625 mb free ntfs)
12-24 22:07 DEBUG  WindowsBackend: drive=Drive(C: hd 9139.640625 mb free ntfs)
12-24 22:07 DEBUG  WindowsBackend: drive=Drive(D: removable 6814.484375 mb free fat32)
12-24 22:07 DEBUG  WindowsBackend: uninstaller_path=None
12-24 22:07 DEBUG  WindowsBackend: previous_target_dir=None
12-24 22:07 DEBUG  WindowsBackend: previous_distro_name=None
12-24 22:07 DEBUG  WindowsBackend: keyboard_id=67699721
12-24 22:07 DEBUG  WindowsBackend: keyboard_layout=us
12-24 22:07 DEBUG  WindowsBackend: keyboard_variant=
12-24 22:07 DEBUG  WindowsBackend: total_memory_mb=510.484375
12-24 22:07 DEBUG  CommonBackend: Searching ISOs on USB devices
12-24 22:07 DEBUG  CommonBackend: Searching for local CDs
12-24 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
12-24 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
12-24 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu Netbook CD
12-24 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
12-24 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
12-24 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu Netbook CD
12-24 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
12-24 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
12-24 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
12-24 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
12-24 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
12-24 22:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 22:07 DEBUG  Distro: wrong arch: i386 != amd64
12-24 22:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-24 22:07 INFO   Distro: Found a valid CD for Ubuntu: D:\
12-24 22:07 INFO   root: Running the CD boot helper...
12-24 22:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
12-24 22:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
12-24 22:07 INFO   root: CD boot helper confirmed
12-24 22:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
12-24 22:07 DEBUG  TaskList: # Running tasklist...
12-24 22:07 DEBUG  TaskList: ## Running select_target_dir...
12-24 22:07 INFO   WindowsBackend: Installing into C:\ubuntu
12-24 22:07 DEBUG  TaskList: ## Finished select_target_dir
12-24 22:07 DEBUG  TaskList: ## Running create_dir_structure...
12-24 22:07 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-24 22:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-24 22:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-24 22:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-24 22:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-24 22:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-24 22:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-24 22:07 DEBUG  TaskList: ## Finished create_dir_structure
12-24 22:07 DEBUG  TaskList: ## Running uncompress_target_dir...
12-24 22:07 DEBUG  TaskList: ## Finished uncompress_target_dir
12-24 22:07 DEBUG  TaskList: ## Running create_uninstaller...
12-24 22:07 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-24 22:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-24 22:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-24 22:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-24 22:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-24 22:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
12-24 22:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-24 22:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-24 22:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-24 22:07 DEBUG  TaskList: ## Finished create_uninstaller
12-24 22:07 DEBUG  TaskList: ## Running copy_installation_files...
12-24 22:07 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
12-24 22:07 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\winboot -> C:\ubuntu\winboot
12-24 22:07 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Gray\LOCALS~1\Temp\pyl6.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
12-24 22:07 DEBUG  TaskList: ## Finished copy_installation_files
12-24 22:07 DEBUG  TaskList: ## Running use_cd...
12-24 22:07 DEBUG  TaskList: New task copy_file
12-24 22:07 DEBUG  TaskList: ### Running copy_file...
12-24 22:39 DEBUG  TaskList: ### Finished copy_file
12-24 22:39 DEBUG  TaskList: New task check_iso
12-24 22:39 DEBUG  TaskList: ### Running check_iso...
12-24 22:39 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
12-24 22:39 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
12-24 22:39 DEBUG  Distro:     wrong size: 8022057984 > 900000000
12-24 22:39 DEBUG  TaskList: ### Finished check_iso
12-24 22:39 DEBUG  TaskList: ## Finished use_cd
12-24 22:39 DEBUG  TaskList: ## Running extract_kernel...
12-24 22:39 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
12-24 22:39 DEBUG  TaskList: # Cancelling tasklist
12-24 22:39 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
12-24 22:39 DEBUG  TaskList: # Finished tasklist"

---

### Post by tommcd on 2010-12-24
What model number Dell is this that has no cdrom drive or no floppy drive?

Suggestion:
Can you remove the hard drive from the Dell and install it as a second hard drive in another computer? Or put the Dell hard drive in an external hard drive enclosure that you can connect via usb to another computer?
If you can do this, then you can install Ubuntu onto the Dell hard drive from another computer, then stick the hard drive back in the Dell. When you boot up the Dell Ubuntu *should* boot up just fine.

And welcome to the Ubuntu forums!

---

### Post by bcbc on 2010-12-24
It looks like you've expanded the .iso to a USB. The wubi installer's complaining that it's too big.

Copy that wubi.exe and the downloaded .iso into a local folder and run wubi.exe from there. You can then [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") it to a direct install right after installing. 

Or removing the hard drive is another option.

---

