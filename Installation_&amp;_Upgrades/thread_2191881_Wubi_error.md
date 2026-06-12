---
title: "Wubi error"
date: 2013-12-04
forum: Installation &amp; Upgrades
---

### Post by numerelle on 2013-12-04
Hey guys, new to the whole ubuntu/linux thing, i would like some help . I ran wubi, picked lubuntu started going to it's process.. it *looked *like it was torrenting the iso twice. Then it gave me an error, "Could not retrieve the required installation files..." All default settings except i put the installation size at 12gb instead of 18gb

Installing lubuntu on windows xp
Below is the log

```
12-04 15:06 INFO   root: === wubi 12.04.3 rev279 ===12-04 15:06 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-12.04.3-rev279.log
12-04 15:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Owner\\Desktop\\wubi.exe"']
12-04 15:06 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\data
12-04 15:06 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\bin\7z.exe
12-04 15:06 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
12-04 15:06 DEBUG  CommonBackend: Fetching basic info...
12-04 15:06 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\Desktop\wubi.exe
12-04 15:06 DEBUG  CommonBackend: platform=win32
12-04 15:06 DEBUG  CommonBackend: osname=nt
12-04 15:06 DEBUG  CommonBackend: language=en_US
12-04 15:06 DEBUG  CommonBackend: encoding=cp1252
12-04 15:06 DEBUG  WindowsBackend: arch=i386
12-04 15:06 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\data\isolist.ini
12-04 15:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-04 15:06 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-04 15:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-04 15:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-04 15:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-04 15:06 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-04 15:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-04 15:06 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-04 15:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-04 15:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-04 15:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-04 15:06 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-04 15:06 DEBUG  WindowsBackend: Fetching host info...
12-04 15:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-04 15:06 DEBUG  WindowsBackend: windows version=xp
12-04 15:06 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-04 15:06 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-04 15:06 DEBUG  WindowsBackend: windows_build=2600
12-04 15:06 DEBUG  WindowsBackend: gmt=-8
12-04 15:06 DEBUG  WindowsBackend: country=US
12-04 15:06 DEBUG  WindowsBackend: timezone=America/Los_Angeles
12-04 15:06 DEBUG  WindowsBackend: windows_username=Owner
12-04 15:06 DEBUG  WindowsBackend: user_full_name=Owner
12-04 15:06 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
12-04 15:06 DEBUG  WindowsBackend: windows_language_code=1033
12-04 15:06 DEBUG  WindowsBackend: windows_language=English
12-04 15:06 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.60GHz
12-04 15:06 DEBUG  WindowsBackend: bootloader=xp
12-04 15:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33850.75 mb free ntfs)
12-04 15:06 DEBUG  WindowsBackend: drive=Drive(C: hd 33850.75 mb free ntfs)
12-04 15:06 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
12-04 15:06 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-04 15:06 DEBUG  WindowsBackend: uninstaller_path=None
12-04 15:06 DEBUG  WindowsBackend: previous_target_dir=None
12-04 15:06 DEBUG  WindowsBackend: previous_distro_name=None
12-04 15:06 DEBUG  WindowsBackend: keyboard_id=67699721
12-04 15:06 DEBUG  WindowsBackend: keyboard_layout=us
12-04 15:06 DEBUG  WindowsBackend: keyboard_variant=
12-04 15:06 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-04 15:06 DEBUG  CommonBackend: locale=en_US.UTF-8
12-04 15:06 DEBUG  WindowsBackend: total_memory_mb=383.53125
12-04 15:06 DEBUG  CommonBackend: Searching ISOs on USB devices
12-04 15:06 DEBUG  CommonBackend: Searching for local CDs
12-04 15:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp is a valid Ubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp is a valid Ubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp is a valid Kubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp is a valid Kubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp is a valid Xubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp is a valid Xubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp is a valid Mythbuntu CD
12-04 15:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp is a valid Mythbuntu CD
12-04 15:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp is a valid Edubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp is a valid Edubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp is a valid Lubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp is a valid Lubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-04 15:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-04 15:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-04 15:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:06 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 INFO   root: Running the installer...
12-04 15:07 DEBUG  WindowsFrontend: __init__...
12-04 15:07 DEBUG  WindowsFrontend: on_init...
12-04 15:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\translations, languages=['en_US', 'en']
12-04 15:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2C.tmp\translations, languages=['en_US', 'en']
12-04 15:07 INFO   WindowsFrontend: Operation cancelled
12-04 15:07 DEBUG  WindowsFrontend: frontend.quit
12-04 15:07 DEBUG  WindowsFrontend: frontend.on_quit
12-04 15:07 DEBUG  root: application.on_quit
12-04 15:07 INFO   root: sys.exit
12-04 15:07 INFO   root: === wubi 12.04.3 rev279 ===
12-04 15:07 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-12.04.3-rev279.log
12-04 15:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Owner\\Desktop\\wubi.exe"']
12-04 15:07 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\data
12-04 15:07 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\bin\7z.exe
12-04 15:07 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
12-04 15:07 DEBUG  CommonBackend: Fetching basic info...
12-04 15:07 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\Desktop\wubi.exe
12-04 15:07 DEBUG  CommonBackend: platform=win32
12-04 15:07 DEBUG  CommonBackend: osname=nt
12-04 15:07 DEBUG  CommonBackend: language=en_US
12-04 15:07 DEBUG  CommonBackend: encoding=cp1252
12-04 15:07 DEBUG  WindowsBackend: arch=i386
12-04 15:07 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\data\isolist.ini
12-04 15:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-04 15:07 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-04 15:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-04 15:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-04 15:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-04 15:07 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-04 15:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-04 15:07 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-04 15:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-04 15:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-04 15:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-04 15:07 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-04 15:07 DEBUG  WindowsBackend: Fetching host info...
12-04 15:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-04 15:07 DEBUG  WindowsBackend: windows version=xp
12-04 15:07 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-04 15:07 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-04 15:07 DEBUG  WindowsBackend: windows_build=2600
12-04 15:07 DEBUG  WindowsBackend: gmt=-8
12-04 15:07 DEBUG  WindowsBackend: country=US
12-04 15:07 DEBUG  WindowsBackend: timezone=America/Los_Angeles
12-04 15:07 DEBUG  WindowsBackend: windows_username=Owner
12-04 15:07 DEBUG  WindowsBackend: user_full_name=Owner
12-04 15:07 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
12-04 15:07 DEBUG  WindowsBackend: windows_language_code=1033
12-04 15:07 DEBUG  WindowsBackend: windows_language=English
12-04 15:07 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.60GHz
12-04 15:07 DEBUG  WindowsBackend: bootloader=xp
12-04 15:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33850.4101563 mb free ntfs)
12-04 15:07 DEBUG  WindowsBackend: drive=Drive(C: hd 33850.4101563 mb free ntfs)
12-04 15:07 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
12-04 15:07 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-04 15:07 DEBUG  WindowsBackend: uninstaller_path=None
12-04 15:07 DEBUG  WindowsBackend: previous_target_dir=None
12-04 15:07 DEBUG  WindowsBackend: previous_distro_name=None
12-04 15:07 DEBUG  WindowsBackend: keyboard_id=67699721
12-04 15:07 DEBUG  WindowsBackend: keyboard_layout=us
12-04 15:07 DEBUG  WindowsBackend: keyboard_variant=
12-04 15:07 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-04 15:07 DEBUG  CommonBackend: locale=en_US.UTF-8
12-04 15:07 DEBUG  WindowsBackend: total_memory_mb=383.53125
12-04 15:07 DEBUG  CommonBackend: Searching ISOs on USB devices
12-04 15:07 DEBUG  CommonBackend: Searching for local CDs
12-04 15:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp is a valid Ubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp is a valid Ubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp is a valid Kubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp is a valid Kubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp is a valid Xubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp is a valid Xubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp is a valid Mythbuntu CD
12-04 15:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp is a valid Mythbuntu CD
12-04 15:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp is a valid Edubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp is a valid Edubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp is a valid Lubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp is a valid Lubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-04 15:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-04 15:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-04 15:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:07 INFO   root: Running the installer...
12-04 15:07 DEBUG  WindowsFrontend: __init__...
12-04 15:07 DEBUG  WindowsFrontend: on_init...
12-04 15:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\translations, languages=['en_US', 'en']
12-04 15:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\translations, languages=['en_US', 'en']
12-04 15:08 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Lubuntu, language=en_US, locale=en_US.UTF-8, username=owner
12-04 15:08 INFO   root: Received settings
12-04 15:08 DEBUG  CommonBackend: Searching for local CD
12-04 15:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp is a valid Lubuntu CD
12-04 15:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\casper\filesystem.squashfs
12-04 15:08 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-04 15:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:08 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-04 15:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:08 DEBUG  CommonBackend: Searching for local ISO
12-04 15:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\translations, languages=['en_US', 'en']
12-04 15:08 DEBUG  TaskList: # Running tasklist...
12-04 15:08 DEBUG  TaskList: ## Running select_target_dir...
12-04 15:08 INFO   WindowsBackend: Installing into C:\ubuntu
12-04 15:08 DEBUG  TaskList: ## Finished select_target_dir
12-04 15:08 DEBUG  TaskList: ## Running create_dir_structure...
12-04 15:08 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-04 15:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-04 15:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-04 15:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-04 15:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-04 15:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-04 15:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-04 15:08 DEBUG  TaskList: ## Finished create_dir_structure
12-04 15:08 DEBUG  TaskList: ## Running uncompress_target_dir...
12-04 15:08 DEBUG  TaskList: ## Finished uncompress_target_dir
12-04 15:08 DEBUG  TaskList: ## Running create_uninstaller...
12-04 15:08 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Owner\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-04 15:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-04 15:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-04 15:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Lubuntu
12-04 15:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Lubuntu.ico
12-04 15:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04.3-rev279
12-04 15:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Lubuntu
12-04 15:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://lubuntu.net](http://lubuntu.net)
12-04 15:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-04 15:08 DEBUG  TaskList: ## Finished create_uninstaller
12-04 15:08 DEBUG  TaskList: ## Running copy_installation_files...
12-04 15:08 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
12-04 15:08 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\winboot -> C:\ubuntu\winboot
12-04 15:08 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2E.tmp\data\images\Lubuntu.ico -> C:\ubuntu\Lubuntu.ico
12-04 15:08 DEBUG  TaskList: ## Finished copy_installation_files
12-04 15:08 DEBUG  TaskList: ## Running get_iso...
12-04 15:08 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-04 15:08 DEBUG  TaskList: New task get_metalink
12-04 15:08 DEBUG  TaskList: ### Running get_metalink...
12-04 15:08 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.metalink](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.metalink) > C:\ubuntu\install
12-04 15:08 DEBUG  downloader: Download start filename=C:\ubuntu\install\lubuntu-12.04-desktop-i386.metalink, url=http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.metalink, basename=lubuntu-12.04-desktop-i386.metalink, length=1037, text=None
12-04 15:08 DEBUG  downloader: download finished (read 1037 bytes)
12-04 15:08 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink) > C:\ubuntu\install
12-04 15:08 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=586, text=None
12-04 15:08 DEBUG  downloader: download finished (read 586 bytes)
12-04 15:08 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink.gpg) > C:\ubuntu\install
12-04 15:08 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
12-04 15:08 DEBUG  downloader: download finished (read 198 bytes)
12-04 15:08 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
12-04 15:08 INFO   saplog: Checking block bindings..
12-04 15:08 INFO   saplog: Key verified successfully.
12-04 15:08 DEBUG  CommonBackend: metalink md5sums:
60979d07b6355e829b4468b29de1a40e  lubuntu-12.04-alternate-amd64+mac.metalink
9b28d0044548685aa6a44d7ff535dae9  lubuntu-12.04-alternate-amd64.metalink
1cdd6d6e020ea49496d90e490f2dedae  lubuntu-12.04-alternate-i386.metalink
1dc9aac7ea1b0b5f59818a6f0c7a3ff1  lubuntu-12.04-alternate-powerpc.metalink
c330d7adc56433a7625a604a92bd13f9  lubuntu-12.04-desktop-amd64+mac.metalink
6d31cbcbd249d1b5cfabc79a99058cc3  lubuntu-12.04-desktop-amd64.metalink
5051a1b9d698a5393f499908478ddae1  lubuntu-12.04-desktop-i386.metalink
a2aeb48a97620a0acd78ea260e5f4534  lubuntu-12.04-desktop-powerpc.metalink


12-04 15:08 DEBUG  TaskList: ### Finished get_metalink
12-04 15:08 DEBUG  TaskList: New task download
12-04 15:08 DEBUG  TaskList: ### Running download...
12-04 15:08 DEBUG  btdownloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso.torrent](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso.torrent) > C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-04 15:32 DEBUG  TaskList: ### Finished download
12-04 15:32 DEBUG  TaskList: New task check_iso
12-04 15:32 DEBUG  TaskList: ### Running check_iso...
12-04 15:32 DEBUG  CommonBackend: Checking C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-04 15:32 DEBUG  Distro:   checking Lubuntu ISO C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-04 15:32 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-04 15:32 DEBUG  Distro:   parsing info from str=Lubuntu 12.04 "Precise Pangolin" - Release i386 (20120423)
12-04 15:32 DEBUG  Distro:   parsed info={'name': 'Lubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
12-04 15:32 DEBUG  Distro: wrong version: 12.04 != 12.04.3
12-04 15:32 DEBUG  TaskList: ### Finished check_iso
12-04 15:32 DEBUG  TaskList: New task download
12-04 15:32 DEBUG  TaskList: ### Running download...
12-04 15:32 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso) > C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-04 15:32 DEBUG  downloader: Download start filename=C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso, url=http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso, basename=lubuntu-12.04-desktop-i386.iso, length=721727488, text=None
12-04 15:50 DEBUG  TaskList: ### Finished download
12-04 15:50 DEBUG  downloader: download finished (read 721727488 bytes)
12-04 15:50 DEBUG  TaskList: New task check_iso
12-04 15:50 DEBUG  TaskList: ### Running check_iso...
12-04 15:50 DEBUG  CommonBackend: Checking C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-04 15:50 DEBUG  Distro:   checking Lubuntu ISO C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-04 15:50 DEBUG  Distro: wrong version: 12.04 != 12.04.3
12-04 15:50 DEBUG  TaskList: ### Finished check_iso
12-04 15:50 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 600, in get_iso
Exception: Could not retrieve the required installation files
12-04 15:50 DEBUG  TaskList: # Cancelling tasklist
12-04 15:50 DEBUG  TaskList: # Finished tasklist
12-04 15:50 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 600, in get_iso
Exception: Could not retrieve the required installation files
12-04 15:51 INFO   root: === wubi 12.04.3 rev279 ===
12-04 15:51 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-12.04.3-rev279.log
12-04 15:51 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Owner\\Desktop\\wubi.exe"']
12-04 15:51 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\data
12-04 15:51 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\bin\7z.exe
12-04 15:51 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
12-04 15:51 DEBUG  CommonBackend: Fetching basic info...
12-04 15:51 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\Desktop\wubi.exe
12-04 15:51 DEBUG  CommonBackend: platform=win32
12-04 15:51 DEBUG  CommonBackend: osname=nt
12-04 15:51 DEBUG  CommonBackend: language=en_US
12-04 15:51 DEBUG  CommonBackend: encoding=cp1252
12-04 15:51 DEBUG  WindowsBackend: arch=i386
12-04 15:51 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\data\isolist.ini
12-04 15:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-04 15:51 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-04 15:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-04 15:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-04 15:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-04 15:51 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-04 15:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-04 15:51 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-04 15:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-04 15:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-04 15:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-04 15:51 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-04 15:51 DEBUG  WindowsBackend: Fetching host info...
12-04 15:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-04 15:51 DEBUG  WindowsBackend: windows version=xp
12-04 15:51 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-04 15:51 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-04 15:51 DEBUG  WindowsBackend: windows_build=2600
12-04 15:51 DEBUG  WindowsBackend: gmt=-8
12-04 15:51 DEBUG  WindowsBackend: country=US
12-04 15:51 DEBUG  WindowsBackend: timezone=America/Los_Angeles
12-04 15:51 DEBUG  WindowsBackend: windows_username=Owner
12-04 15:51 DEBUG  WindowsBackend: user_full_name=Owner
12-04 15:51 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
12-04 15:51 DEBUG  WindowsBackend: windows_language_code=1033
12-04 15:51 DEBUG  WindowsBackend: windows_language=English
12-04 15:51 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.60GHz
12-04 15:51 DEBUG  WindowsBackend: bootloader=xp
12-04 15:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33847.1914063 mb free ntfs)
12-04 15:51 DEBUG  WindowsBackend: drive=Drive(C: hd 33847.1914063 mb free ntfs)
12-04 15:51 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
12-04 15:51 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-04 15:51 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-04 15:51 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-04 15:51 DEBUG  WindowsBackend: previous_distro_name=Lubuntu
12-04 15:51 DEBUG  WindowsBackend: keyboard_id=67699721
12-04 15:51 DEBUG  WindowsBackend: keyboard_layout=us
12-04 15:51 DEBUG  WindowsBackend: keyboard_variant=
12-04 15:51 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-04 15:51 DEBUG  CommonBackend: locale=en_US.UTF-8
12-04 15:51 DEBUG  WindowsBackend: total_memory_mb=383.53125
12-04 15:51 DEBUG  CommonBackend: Searching ISOs on USB devices
12-04 15:51 DEBUG  CommonBackend: Searching for local CDs
12-04 15:51 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Ubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Ubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Kubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Kubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Xubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Xubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Mythbuntu CD
12-04 15:51 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Mythbuntu CD
12-04 15:51 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Edubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Edubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Lubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Lubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-04 15:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-04 15:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-04 15:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-04 15:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:51 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-04 15:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:51 INFO   root: Already installed, running the uninstaller...
12-04 15:51 INFO   root: Running the uninstaller...
12-04 15:52 INFO   CommonBackend: This is the uninstaller running
12-04 15:52 DEBUG  WindowsFrontend: __init__...
12-04 15:52 DEBUG  WindowsFrontend: on_init...
12-04 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\translations, languages=['en_US', 'en']
12-04 15:52 INFO   root: Received settings
12-04 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\translations, languages=['en_US', 'en']
12-04 15:52 DEBUG  TaskList: # Running tasklist...
12-04 15:52 DEBUG  TaskList: ## Running Remove bootloader entry...
12-04 15:52 ERROR  WindowsBackend: Cannot find bcdedit
12-04 15:52 DEBUG  WindowsBackend: undo_bootini C:
12-04 15:52 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 33847.1914063 mb free ntfs)
12-04 15:52 DEBUG  TaskList: ## Finished Remove bootloader entry
12-04 15:52 DEBUG  TaskList: ## Running Remove target dir...
12-04 15:52 DEBUG  CommonBackend: Deleting C:\ubuntu
12-04 15:52 DEBUG  TaskList: ## Finished Remove target dir
12-04 15:52 DEBUG  TaskList: ## Running Remove registry key...
12-04 15:52 DEBUG  TaskList: ## Finished Remove registry key
12-04 15:52 DEBUG  TaskList: # Finished tasklist
12-04 15:52 INFO   root: Almost finished uninstalling
12-04 15:52 INFO   root: Finished uninstallation
12-04 15:52 DEBUG  CommonBackend: Fetching basic info...
12-04 15:52 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Owner\Desktop\wubi.exe
12-04 15:52 DEBUG  CommonBackend: platform=win32
12-04 15:52 DEBUG  CommonBackend: osname=nt
12-04 15:52 DEBUG  WindowsBackend: arch=i386
12-04 15:52 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\data\isolist.ini
12-04 15:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-04 15:52 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-04 15:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-04 15:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-04 15:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-04 15:52 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-04 15:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-04 15:52 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-04 15:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-04 15:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-04 15:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-04 15:52 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-04 15:52 DEBUG  WindowsBackend: Fetching host info...
12-04 15:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-04 15:52 DEBUG  WindowsBackend: windows version=xp
12-04 15:52 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-04 15:52 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-04 15:52 DEBUG  WindowsBackend: windows_build=2600
12-04 15:52 DEBUG  WindowsBackend: gmt=-8
12-04 15:52 DEBUG  WindowsBackend: country=US
12-04 15:52 DEBUG  WindowsBackend: timezone=America/Los_Angeles
12-04 15:52 DEBUG  WindowsBackend: windows_username=Owner
12-04 15:52 DEBUG  WindowsBackend: user_full_name=Owner
12-04 15:52 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
12-04 15:52 DEBUG  WindowsBackend: windows_language_code=1033
12-04 15:52 DEBUG  WindowsBackend: windows_language=English
12-04 15:52 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 1.60GHz
12-04 15:52 DEBUG  WindowsBackend: bootloader=xp
12-04 15:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33849.8007813 mb free ntfs)
12-04 15:52 DEBUG  WindowsBackend: drive=Drive(C: hd 33849.8007813 mb free ntfs)
12-04 15:52 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
12-04 15:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-04 15:52 DEBUG  WindowsBackend: uninstaller_path=None
12-04 15:52 DEBUG  WindowsBackend: previous_target_dir=None
12-04 15:52 DEBUG  WindowsBackend: previous_distro_name=None
12-04 15:52 DEBUG  WindowsBackend: keyboard_id=67699721
12-04 15:52 DEBUG  WindowsBackend: keyboard_layout=us
12-04 15:52 DEBUG  WindowsBackend: keyboard_variant=
12-04 15:52 DEBUG  WindowsBackend: total_memory_mb=383.53125
12-04 15:52 DEBUG  CommonBackend: Searching ISOs on USB devices
12-04 15:52 DEBUG  CommonBackend: Searching for local CDs
12-04 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Ubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Ubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Kubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Kubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Xubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Xubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Mythbuntu CD
12-04 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Mythbuntu CD
12-04 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Edubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Edubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Lubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Lubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-04 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-04 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-04 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-04 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:52 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-04 15:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:52 INFO   root: Running the installer...
12-04 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\translations, languages=['en_US', 'en']
12-04 15:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\translations, languages=['en_US', 'en']
12-04 15:56 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=12000MB, distro_name=Lubuntu, language=en_US, locale=en_US.UTF-8, username=owner
12-04 15:56 INFO   root: Received settings
12-04 15:56 DEBUG  CommonBackend: Searching for local CD
12-04 15:56 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp is a valid Lubuntu CD
12-04 15:56 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\casper\filesystem.squashfs
12-04 15:56 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-04 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-04 15:56 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-04 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-04 15:56 DEBUG  CommonBackend: Searching for local ISO
12-04 15:56 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\translations, languages=['en_US', 'en']
12-04 15:56 DEBUG  TaskList: # Running tasklist...
12-04 15:56 DEBUG  TaskList: ## Running select_target_dir...
12-04 15:56 INFO   WindowsBackend: Installing into C:\ubuntu
12-04 15:56 DEBUG  TaskList: ## Finished select_target_dir
12-04 15:56 DEBUG  TaskList: ## Running create_dir_structure...
12-04 15:56 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-04 15:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-04 15:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-04 15:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-04 15:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-04 15:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-04 15:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-04 15:56 DEBUG  TaskList: ## Finished create_dir_structure
12-04 15:56 DEBUG  TaskList: ## Running uncompress_target_dir...
12-04 15:56 DEBUG  TaskList: ## Finished uncompress_target_dir
12-04 15:56 DEBUG  TaskList: ## Running create_uninstaller...
12-04 15:56 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Owner\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-04 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-04 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-04 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Lubuntu
12-04 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Lubuntu.ico
12-04 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04.3-rev279
12-04 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Lubuntu
12-04 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://lubuntu.net](http://lubuntu.net)
12-04 15:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-04 15:56 DEBUG  TaskList: ## Finished create_uninstaller
12-04 15:56 DEBUG  TaskList: ## Running copy_installation_files...
12-04 15:56 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
12-04 15:56 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\winboot -> C:\ubuntu\winboot
12-04 15:56 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl32.tmp\data\images\Lubuntu.ico -> C:\ubuntu\Lubuntu.ico
12-04 15:56 DEBUG  TaskList: ## Finished copy_installation_files
12-04 15:56 DEBUG  TaskList: ## Running get_iso...
12-04 15:56 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-04 15:56 DEBUG  TaskList: New task get_metalink
12-04 15:56 DEBUG  TaskList: ### Running get_metalink...
12-04 15:56 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.metalink](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.metalink) > C:\ubuntu\install
12-04 15:56 DEBUG  downloader: Download start filename=C:\ubuntu\install\lubuntu-12.04-desktop-i386.metalink, url=http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.metalink, basename=lubuntu-12.04-desktop-i386.metalink, length=1037, text=None
12-04 15:56 DEBUG  downloader: download finished (read 1037 bytes)
12-04 15:56 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink) > C:\ubuntu\install
12-04 15:56 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=586, text=None
12-04 15:56 DEBUG  downloader: download finished (read 586 bytes)
12-04 15:56 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink.gpg) > C:\ubuntu\install
12-04 15:56 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
12-04 15:56 DEBUG  downloader: download finished (read 198 bytes)
12-04 15:56 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
12-04 15:56 INFO   saplog: Checking block bindings..
12-04 15:56 INFO   saplog: Key verified successfully.
12-04 15:56 DEBUG  CommonBackend: metalink md5sums:
60979d07b6355e829b4468b29de1a40e  lubuntu-12.04-alternate-amd64+mac.metalink
9b28d0044548685aa6a44d7ff535dae9  lubuntu-12.04-alternate-amd64.metalink
1cdd6d6e020ea49496d90e490f2dedae  lubuntu-12.04-alternate-i386.metalink
1dc9aac7ea1b0b5f59818a6f0c7a3ff1  lubuntu-12.04-alternate-powerpc.metalink
c330d7adc56433a7625a604a92bd13f9  lubuntu-12.04-desktop-amd64+mac.metalink
6d31cbcbd249d1b5cfabc79a99058cc3  lubuntu-12.04-desktop-amd64.metalink
5051a1b9d698a5393f499908478ddae1  lubuntu-12.04-desktop-i386.metalink
a2aeb48a97620a0acd78ea260e5f4534  lubuntu-12.04-desktop-powerpc.metalink


12-04 15:56 DEBUG  TaskList: ### Finished get_metalink
12-04 15:56 DEBUG  TaskList: New task download
12-04 15:56 DEBUG  TaskList: ### Running download...
12-04 15:56 DEBUG  btdownloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso.torrent](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso.torrent) > C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-04 16:11 DEBUG  TaskList: ### Finished download
12-04 16:11 DEBUG  TaskList: New task check_iso
12-04 16:11 DEBUG  TaskList: ### Running check_iso...
12-04 16:11 DEBUG  CommonBackend: Checking C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-04 16:11 DEBUG  Distro:   checking Lubuntu ISO C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-04 16:12 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-04 16:12 DEBUG  Distro:   parsing info from str=Lubuntu 12.04 "Precise Pangolin" - Release i386 (20120423)
12-04 16:12 DEBUG  Distro:   parsed info={'name': 'Lubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
12-04 16:12 DEBUG  Distro: wrong version: 12.04 != 12.04.3
12-04 16:12 DEBUG  TaskList: ### Finished check_iso
12-04 16:12 DEBUG  TaskList: New task download
12-04 16:12 DEBUG  TaskList: ### Running download...
12-04 16:12 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso) > C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-04 16:12 DEBUG  downloader: Download start filename=C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso, url=http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso, basename=lubuntu-12.04-desktop-i386.iso, length=721727488, text=None
12-04 16:31 DEBUG  TaskList: ### Finished download
12-04 16:31 DEBUG  downloader: download finished (read 721727488 bytes)
12-04 16:31 DEBUG  TaskList: New task check_iso
12-04 16:31 DEBUG  TaskList: ### Running check_iso...
12-04 16:31 DEBUG  CommonBackend: Checking C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-04 16:31 DEBUG  Distro:   checking Lubuntu ISO C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-04 16:31 DEBUG  Distro: wrong version: 12.04 != 12.04.3
12-04 16:31 DEBUG  TaskList: ### Finished check_iso
12-04 16:31 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 600, in get_iso
Exception: Could not retrieve the required installation files
12-04 16:31 DEBUG  TaskList: # Cancelling tasklist
12-04 16:31 DEBUG  TaskList: # Finished tasklist
12-04 16:31 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 600, in get_iso
Exception: Could not retrieve the required installation files



```

---

### Post by QIII on 2013-12-05
Hello!

Which version of Lubuntu are you trying to install?

Wubi was used to "try before you buy", so to speak.  It is no longer recommended for recent versions of Ubuntu.

---

### Post by numerelle on 2013-12-05
I'm using the defaults, i'm guessing it's 12.04? I dont know, the log says [COLOR=#000000][FONT=Ubuntu Mono]Distro: wrong version: 12.04 != 12.04.3[/FONT][/COLOR]
Is that the problem?


Well, I just wanted to *try* lubuntu; the computer is too old to boot from USB so I just wanted to try wubi instead

---

### Post by bcbc on 2013-12-07
You have to use the 12.04 wubi.exe (12.04.0) for lubuntu. Get it from here: [http://old-releases.ubuntu.com/releases/12.04.0/wubi-12.04.exe](http://old-releases.ubuntu.com/releases/12.04.0/wubi-12.04.exe)

Note: if you still have the iso it downloaded [COLOR=#000000][FONT=Ubuntu Mono] C:\ubuntu\install\lubuntu-12.04-desktop-i386.iso (or [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] C:\ubuntu\install\installation.iso). First MOVE that out of there and place in the same directory as the wubi.exe you download. Then it will skip downloading it again.[/FONT][/COLOR]

---

