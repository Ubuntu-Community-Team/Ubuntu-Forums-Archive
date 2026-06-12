---
title: "can't install on windows 7"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by jolieyeah on 2010-11-12
Hi, I am new here. I tried to install ubuntu 10.04.1 today, but I got an error. and here is the log:

---------------
11-12 20:31 INFO   root: === wubi 10.04.1 rev190 ===
11-12 20:31 DEBUG  root: Logfile is c:\users\user1\appdata\local\temp\wubi-10.04.1-rev190.log
11-12 20:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\user1\\Downloads\\wubi.exe"']
11-12 20:31 DEBUG  CommonBackend: data_dir=C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp\data
11-12 20:31 DEBUG  WindowsBackend: 7z=C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp\bin\7z.exe
11-12 20:31 DEBUG  CommonBackend: Fetching basic info...
11-12 20:31 DEBUG  CommonBackend: original_exe=C:\Users\user1\Downloads\wubi.exe
11-12 20:31 DEBUG  CommonBackend: platform=win32
11-12 20:31 DEBUG  CommonBackend: osname=nt
11-12 20:31 DEBUG  CommonBackend: language=en_US
11-12 20:31 DEBUG  CommonBackend: encoding=cp1252
11-12 20:31 DEBUG  WindowsBackend: arch=amd64
11-12 20:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp\data\isolist.ini
11-12 20:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-12 20:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-12 20:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-12 20:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-12 20:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-12 20:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-12 20:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-12 20:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-12 20:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-12 20:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-12 20:31 DEBUG  WindowsBackend: Fetching host info...
11-12 20:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-12 20:31 DEBUG  WindowsBackend: windows version=vista
11-12 20:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-12 20:31 DEBUG  WindowsBackend: windows_sp=None
11-12 20:31 DEBUG  WindowsBackend: windows_build=7600
11-12 20:31 DEBUG  WindowsBackend: gmt=-5
11-12 20:31 DEBUG  WindowsBackend: country=US
11-12 20:31 DEBUG  WindowsBackend: timezone=America/New_York
11-12 20:31 DEBUG  WindowsBackend: windows_username=user1
11-12 20:31 DEBUG  WindowsBackend: user_full_name=user1
11-12 20:31 DEBUG  WindowsBackend: user_directory=C:\Users\user1
11-12 20:31 DEBUG  WindowsBackend: windows_language_code=1033
11-12 20:31 DEBUG  WindowsBackend: windows_language=English
11-12 20:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU       M 620  @ 2.67GHz
11-12 20:31 DEBUG  WindowsBackend: bootloader=vista
11-12 20:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 109030.726563 mb free ntfs)
11-12 20:31 DEBUG  WindowsBackend: drive=Drive(C: hd 109030.726563 mb free ntfs)
11-12 20:31 DEBUG  WindowsBackend: drive=Drive(F: hd 1520.42578125 mb free fat32)
11-12 20:31 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free udf)
11-12 20:31 DEBUG  WindowsBackend: uninstaller_path=None
11-12 20:31 DEBUG  WindowsBackend: previous_target_dir=None
11-12 20:31 DEBUG  WindowsBackend: previous_distro_name=None
11-12 20:31 DEBUG  WindowsBackend: keyboard_id=67699721
11-12 20:31 DEBUG  WindowsBackend: keyboard_layout=us
11-12 20:31 DEBUG  WindowsBackend: keyboard_variant=
11-12 20:31 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-12 20:31 DEBUG  CommonBackend: locale=en_US.UTF-8
11-12 20:31 DEBUG  WindowsBackend: total_memory_mb=1903.4296875
11-12 20:31 DEBUG  CommonBackend: Searching ISOs on USB devices
11-12 20:31 DEBUG  CommonBackend: Searching for local CDs
11-12 20:31 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp is a valid Ubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp is a valid Ubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp is a valid Ubuntu Netbook CD
11-12 20:31 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp is a valid Kubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp is a valid Kubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp is a valid Kubuntu Netbook CD
11-12 20:31 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp is a valid Xubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp is a valid Xubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp is a valid Mythbuntu CD
11-12 20:31 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp is a valid Mythbuntu CD
11-12 20:31 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
11-12 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
11-12 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
11-12 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
11-12 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:31 INFO   root: Running the installer...
11-12 20:31 DEBUG  WindowsFrontend: __init__...
11-12 20:31 DEBUG  WindowsFrontend: on_init...
11-12 20:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp\translations, languages=['en_US', 'en']
11-12 20:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\user1\AppData\Local\Temp\pylA8DC.tmp\translations, languages=['en_US', 'en']
11-12 20:37 INFO   WindowsFrontend: Operation cancelled
11-12 20:37 DEBUG  WindowsFrontend: frontend.quit
11-12 20:37 DEBUG  WindowsFrontend: frontend.on_quit
11-12 20:37 DEBUG  root: application.on_quit
11-12 20:37 INFO   root: sys.exit
11-12 20:37 INFO   root: === wubi 10.04.1 rev190 ===
11-12 20:37 DEBUG  root: Logfile is c:\users\user1\appdata\local\temp\wubi-10.04.1-rev190.log
11-12 20:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\user1\\Downloads\\wubi.exe"']
11-12 20:37 DEBUG  CommonBackend: data_dir=C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\data
11-12 20:37 DEBUG  WindowsBackend: 7z=C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\bin\7z.exe
11-12 20:37 DEBUG  CommonBackend: Fetching basic info...
11-12 20:37 DEBUG  CommonBackend: original_exe=C:\Users\user1\Downloads\wubi.exe
11-12 20:37 DEBUG  CommonBackend: platform=win32
11-12 20:37 DEBUG  CommonBackend: osname=nt
11-12 20:37 DEBUG  CommonBackend: language=en_US
11-12 20:37 DEBUG  CommonBackend: encoding=cp1252
11-12 20:37 DEBUG  WindowsBackend: arch=amd64
11-12 20:37 DEBUG  CommonBackend: Parsing isolist=C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\data\isolist.ini
11-12 20:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-12 20:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-12 20:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-12 20:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-12 20:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-12 20:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-12 20:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-12 20:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-12 20:37 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-12 20:37 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-12 20:37 DEBUG  WindowsBackend: Fetching host info...
11-12 20:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-12 20:37 DEBUG  WindowsBackend: windows version=vista
11-12 20:37 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-12 20:37 DEBUG  WindowsBackend: windows_sp=None
11-12 20:37 DEBUG  WindowsBackend: windows_build=7600
11-12 20:37 DEBUG  WindowsBackend: gmt=-5
11-12 20:37 DEBUG  WindowsBackend: country=US
11-12 20:37 DEBUG  WindowsBackend: timezone=America/New_York
11-12 20:37 DEBUG  WindowsBackend: windows_username=user1
11-12 20:37 DEBUG  WindowsBackend: user_full_name=user1
11-12 20:37 DEBUG  WindowsBackend: user_directory=C:\Users\user1
11-12 20:37 DEBUG  WindowsBackend: windows_language_code=1033
11-12 20:37 DEBUG  WindowsBackend: windows_language=English
11-12 20:37 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU       M 620  @ 2.67GHz
11-12 20:37 DEBUG  WindowsBackend: bootloader=vista
11-12 20:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 47434.3203125 mb free ntfs)
11-12 20:37 DEBUG  WindowsBackend: drive=Drive(C: hd 47434.3164063 mb free ntfs)
11-12 20:37 DEBUG  WindowsBackend: drive=Drive(D: hd 61497.3828125 mb free ntfs)
11-12 20:37 DEBUG  WindowsBackend: drive=Drive(F: hd 1520.42578125 mb free fat32)
11-12 20:37 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free udf)
11-12 20:37 DEBUG  WindowsBackend: uninstaller_path=None
11-12 20:37 DEBUG  WindowsBackend: previous_target_dir=None
11-12 20:37 DEBUG  WindowsBackend: previous_distro_name=None
11-12 20:37 DEBUG  WindowsBackend: keyboard_id=67699721
11-12 20:37 DEBUG  WindowsBackend: keyboard_layout=us
11-12 20:37 DEBUG  WindowsBackend: keyboard_variant=
11-12 20:37 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-12 20:37 DEBUG  CommonBackend: locale=en_US.UTF-8
11-12 20:37 DEBUG  WindowsBackend: total_memory_mb=1903.4296875
11-12 20:37 DEBUG  CommonBackend: Searching ISOs on USB devices
11-12 20:37 DEBUG  CommonBackend: Searching for local CDs
11-12 20:37 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp is a valid Ubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp is a valid Ubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp is a valid Ubuntu Netbook CD
11-12 20:37 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp is a valid Kubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp is a valid Kubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp is a valid Kubuntu Netbook CD
11-12 20:37 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp is a valid Xubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp is a valid Xubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp is a valid Mythbuntu CD
11-12 20:37 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp is a valid Mythbuntu CD
11-12 20:37 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-12 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-12 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
11-12 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
11-12 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
11-12 20:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
11-12 20:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 20:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 20:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:37 INFO   root: Running the installer...
11-12 20:37 DEBUG  WindowsFrontend: __init__...
11-12 20:37 DEBUG  WindowsFrontend: on_init...
11-12 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\translations, languages=['en_US', 'en']
11-12 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\translations, languages=['en_US', 'en']
11-12 20:37 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=user1
11-12 20:37 INFO   root: Received settings
11-12 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\translations, languages=['en_US', 'en']
11-12 20:37 DEBUG  TaskList: # Running tasklist...
11-12 20:37 DEBUG  TaskList: ## Running select_target_dir...
11-12 20:37 INFO   WindowsBackend: Installing into D:\ubuntu
11-12 20:37 DEBUG  TaskList: ## Finished select_target_dir
11-12 20:37 DEBUG  TaskList: ## Running create_dir_structure...
11-12 20:37 DEBUG  CommonBackend: Creating dir D:\ubuntu
11-12 20:37 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
11-12 20:37 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
11-12 20:37 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
11-12 20:37 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
11-12 20:37 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
11-12 20:37 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
11-12 20:37 DEBUG  TaskList: ## Finished create_dir_structure
11-12 20:37 DEBUG  TaskList: ## Running uncompress_target_dir...
11-12 20:37 DEBUG  TaskList: ## Finished uncompress_target_dir
11-12 20:37 DEBUG  TaskList: ## Running create_uninstaller...
11-12 20:37 DEBUG  WindowsBackend: Copying uninstaller C:\Users\user1\Downloads\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
11-12 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
11-12 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
11-12 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-12 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
11-12 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
11-12 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-12 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-12 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-12 20:37 DEBUG  TaskList: ## Finished create_uninstaller
11-12 20:37 DEBUG  TaskList: ## Running copy_installation_files...
11-12 20:37 DEBUG  WindowsBackend: Copying C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
11-12 20:37 DEBUG  WindowsBackend: Copying C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\winboot -> D:\ubuntu\winboot
11-12 20:37 DEBUG  WindowsBackend: Copying C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
11-12 20:37 DEBUG  TaskList: ## Finished copy_installation_files
11-12 20:37 DEBUG  TaskList: ## Running get_iso...
11-12 20:37 DEBUG  CommonBackend: Searching for local CD
11-12 20:37 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp is a valid Ubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pylFE4B.tmp\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 20:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:37 DEBUG  CommonBackend: Searching for local ISO
11-12 20:37 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-12 20:37 DEBUG  TaskList: New task get_metalink
11-12 20:37 DEBUG  TaskList: ### Running get_metalink...
11-12 20:37 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink) > D:\ubuntu\install
11-12 20:37 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink, basename=ubuntu-10.04.1-desktop-amd64.metalink, length=36844, text=None
11-12 20:37 DEBUG  downloader: download finished (read 36844 bytes)
11-12 20:37 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink](http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink) > D:\ubuntu\install
11-12 20:37 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=651, text=None
11-12 20:37 DEBUG  downloader: download finished (read 651 bytes)
11-12 20:37 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink.gpg) > D:\ubuntu\install
11-12 20:37 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
11-12 20:37 DEBUG  downloader: download finished (read 189 bytes)
11-12 20:37 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
11-12 20:37 INFO   saplog: Checking block bindings..
11-12 20:37 INFO   saplog: Key verified successfully.
11-12 20:37 DEBUG  CommonBackend: metalink md5sums:
a293f05f7be5e61937b1c277c6a69262  ubuntu-10.04-netbook-armel+dove.metalink
dece0df9abb10efb1f590f759cccf340  ubuntu-10.04-netbook-armel+imx51.metalink
a3805816968bf7199e080ba653a19ac1  ubuntu-10.04-netbook-i386.metalink
94706d50d0375fe01b4b480a9c875a7f  ubuntu-10.04.1-alternate-amd64.metalink
7e94a4ebedb1dcfc4fe376f5a96c45aa  ubuntu-10.04.1-alternate-i386.metalink
974c01945586ebcbb672f11ce6df0e39  ubuntu-10.04.1-desktop-amd64.metalink
b3b2f75f70c5216d1325a5a02f3770ce  ubuntu-10.04.1-desktop-i386.metalink
8b0786e4978a123ce91e87181eb0f570  ubuntu-10.04.1-server-amd64.metalink
56dff8fca4d2612eb035a909092f5016  ubuntu-10.04.1-server-i386.metalink

11-12 20:37 DEBUG  TaskList: ### Finished get_metalink
11-12 20:37 DEBUG  TaskList: New task download
11-12 20:37 DEBUG  TaskList: ### Running download...
11-12 20:37 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.iso.torrent) > D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 20:59 DEBUG  TaskList: ### Finished download
11-12 20:59 DEBUG  TaskList: New task check_iso
11-12 20:59 DEBUG  TaskList: ### Running check_iso...
11-12 20:59 DEBUG  CommonBackend: Checking D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 20:59 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 20:59 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 20:59 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.1 LTS "Lucid Lynx" - Release amd64 (20100816.1)
11-12 20:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.1', 'build': '20100816.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
11-12 20:59 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 20:59 DEBUG  TaskList: New task get_file_md5
11-12 20:59 DEBUG  TaskList: #### Running get_file_md5...
11-12 20:59 DEBUG  TaskList: #### Finished get_file_md5
11-12 20:59 DEBUG  TaskList: ### Finished check_iso
11-12 20:59 DEBUG  TaskList: ## Finished get_iso
11-12 20:59 DEBUG  TaskList: ## Running extract_kernel...
11-12 20:59 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 20:59 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 20:59 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 20:59 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 20:59 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
11-12 20:59 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
11-12 20:59 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = 3c758a2db6d6909eac17cb173fe2fae7 == 3c758a2db6d6909eac17cb173fe2fae7
11-12 20:59 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
11-12 20:59 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = bbdb9403ed7050629dbb57085aa381dd == bbdb9403ed7050629dbb57085aa381dd
11-12 20:59 DEBUG  TaskList: ## Finished extract_kernel
11-12 20:59 DEBUG  TaskList: ## Running choose_disk_sizes...
11-12 20:59 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
11-12 20:59 DEBUG  TaskList: ## Finished choose_disk_sizes
11-12 20:59 DEBUG  TaskList: ## Running create_preseed...
11-12 20:59 DEBUG  TaskList: ## Finished create_preseed
11-12 20:59 DEBUG  TaskList: ## Running modify_bootloader...
11-12 20:59 DEBUG  TaskList: New task modify_bcd
11-12 20:59 DEBUG  TaskList: ### Running modify_bcd...
11-12 20:59 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 47434.3164063 mb free ntfs)
11-12 20:59 ERROR  TaskList: Error executing command
>>command=C:\windows\System32\bcdedit.exe /set {57a03f83-df52-11df-bdbe-c01d94a8b7f5} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\windows\System32\bcdedit.exe /set {57a03f83-df52-11df-bdbe-c01d94a8b7f5} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
11-12 20:59 DEBUG  TaskList: # Cancelling tasklist
11-12 20:59 DEBUG  TaskList: New task modify_bcd
11-12 20:59 ERROR  root: Error executing command
>>command=C:\windows\System32\bcdedit.exe /set {57a03f83-df52-11df-bdbe-c01d94a8b7f5} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\windows\System32\bcdedit.exe /set {57a03f83-df52-11df-bdbe-c01d94a8b7f5} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
11-12 20:59 DEBUG  TaskList: New task modify_bcd
11-12 20:59 DEBUG  TaskList: ## Finished modify_bootloader
11-12 20:59 DEBUG  TaskList: # Finished tasklist
11-12 20:59 INFO   root: === wubi 10.04.1 rev190 ===
11-12 20:59 DEBUG  root: Logfile is c:\users\user1\appdata\local\temp\wubi-10.04.1-rev190.log
11-12 20:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\user1\\Downloads\\wubi.exe"']
11-12 20:59 DEBUG  CommonBackend: data_dir=C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\data
11-12 20:59 DEBUG  WindowsBackend: 7z=C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\bin\7z.exe
11-12 20:59 DEBUG  CommonBackend: Fetching basic info...
11-12 20:59 DEBUG  CommonBackend: original_exe=C:\Users\user1\Downloads\wubi.exe
11-12 20:59 DEBUG  CommonBackend: platform=win32
11-12 20:59 DEBUG  CommonBackend: osname=nt
11-12 20:59 DEBUG  CommonBackend: language=en_US
11-12 20:59 DEBUG  CommonBackend: encoding=cp1252
11-12 20:59 DEBUG  WindowsBackend: arch=amd64
11-12 20:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\data\isolist.ini
11-12 20:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-12 20:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-12 20:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-12 20:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-12 20:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-12 20:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-12 20:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-12 20:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-12 20:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-12 20:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-12 20:59 DEBUG  WindowsBackend: Fetching host info...
11-12 20:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-12 20:59 DEBUG  WindowsBackend: windows version=vista
11-12 20:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-12 20:59 DEBUG  WindowsBackend: windows_sp=None
11-12 20:59 DEBUG  WindowsBackend: windows_build=7600
11-12 20:59 DEBUG  WindowsBackend: gmt=-5
11-12 20:59 DEBUG  WindowsBackend: country=US
11-12 20:59 DEBUG  WindowsBackend: timezone=America/New_York
11-12 20:59 DEBUG  WindowsBackend: windows_username=user1
11-12 20:59 DEBUG  WindowsBackend: user_full_name=user1
11-12 20:59 DEBUG  WindowsBackend: user_directory=C:\Users\user1
11-12 20:59 DEBUG  WindowsBackend: windows_language_code=1033
11-12 20:59 DEBUG  WindowsBackend: windows_language=English
11-12 20:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU       M 620  @ 2.67GHz
11-12 20:59 DEBUG  WindowsBackend: bootloader=vista
11-12 20:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 47433.3984375 mb free ntfs)
11-12 20:59 DEBUG  WindowsBackend: drive=Drive(C: hd 47433.3984375 mb free ntfs)
11-12 20:59 DEBUG  WindowsBackend: drive=Drive(D: hd 60796.421875 mb free ntfs)
11-12 20:59 DEBUG  WindowsBackend: drive=Drive(F: hd 1520.42578125 mb free fat32)
11-12 20:59 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free udf)
11-12 20:59 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
11-12 20:59 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
11-12 20:59 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-12 20:59 DEBUG  WindowsBackend: keyboard_id=67699721
11-12 20:59 DEBUG  WindowsBackend: keyboard_layout=us
11-12 20:59 DEBUG  WindowsBackend: keyboard_variant=
11-12 20:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-12 20:59 DEBUG  CommonBackend: locale=en_US.UTF-8
11-12 20:59 DEBUG  WindowsBackend: total_memory_mb=1903.4296875
11-12 20:59 DEBUG  CommonBackend: Searching ISOs on USB devices
11-12 20:59 DEBUG  CommonBackend: Searching for local CDs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Ubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Kubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 INFO   root: Already installed, running the uninstaller...
11-12 20:59 INFO   root: Running the uninstaller...
11-12 20:59 INFO   CommonBackend: This is the uninstaller running
11-12 20:59 DEBUG  WindowsFrontend: __init__...
11-12 20:59 DEBUG  WindowsFrontend: on_init...
11-12 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\translations, languages=['en_US', 'en']
11-12 20:59 INFO   root: Received settings
11-12 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\translations, languages=['en_US', 'en']
11-12 20:59 DEBUG  TaskList: # Running tasklist...
11-12 20:59 DEBUG  TaskList: ## Running Backup ISO...
11-12 20:59 DEBUG  TaskList: ## Finished Backup ISO
11-12 20:59 DEBUG  TaskList: ## Running Remove bootloader entry...
11-12 20:59 DEBUG  WindowsBackend: Could not find bcd id
11-12 20:59 DEBUG  WindowsBackend: undo_bootini C:
11-12 20:59 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 47433.3984375 mb free ntfs)
11-12 20:59 DEBUG  WindowsBackend: undo_bootini D:
11-12 20:59 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 60796.421875 mb free ntfs)
11-12 20:59 DEBUG  WindowsBackend: undo_bootini F:
11-12 20:59 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 1520.42578125 mb free fat32)
11-12 20:59 DEBUG  TaskList: ## Finished Remove bootloader entry
11-12 20:59 DEBUG  TaskList: ## Running Remove target dir...
11-12 20:59 DEBUG  CommonBackend: Deleting D:\ubuntu
11-12 20:59 DEBUG  TaskList: ## Finished Remove target dir
11-12 20:59 DEBUG  TaskList: ## Running Remove registry key...
11-12 20:59 DEBUG  TaskList: ## Finished Remove registry key
11-12 20:59 DEBUG  TaskList: # Finished tasklist
11-12 20:59 INFO   root: Almost finished uninstalling
11-12 20:59 INFO   root: Finished uninstallation
11-12 20:59 DEBUG  CommonBackend: Fetching basic info...
11-12 20:59 DEBUG  CommonBackend: original_exe=C:\Users\user1\Downloads\wubi.exe
11-12 20:59 DEBUG  CommonBackend: platform=win32
11-12 20:59 DEBUG  CommonBackend: osname=nt
11-12 20:59 DEBUG  WindowsBackend: arch=amd64
11-12 20:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\data\isolist.ini
11-12 20:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-12 20:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-12 20:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-12 20:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-12 20:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-12 20:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-12 20:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-12 20:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-12 20:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-12 20:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-12 20:59 DEBUG  WindowsBackend: Fetching host info...
11-12 20:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-12 20:59 DEBUG  WindowsBackend: windows version=vista
11-12 20:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-12 20:59 DEBUG  WindowsBackend: windows_sp=None
11-12 20:59 DEBUG  WindowsBackend: windows_build=7600
11-12 20:59 DEBUG  WindowsBackend: gmt=-5
11-12 20:59 DEBUG  WindowsBackend: country=US
11-12 20:59 DEBUG  WindowsBackend: timezone=America/New_York
11-12 20:59 DEBUG  WindowsBackend: windows_username=user1
11-12 20:59 DEBUG  WindowsBackend: user_full_name=user1
11-12 20:59 DEBUG  WindowsBackend: user_directory=C:\Users\user1
11-12 20:59 DEBUG  WindowsBackend: windows_language_code=1033
11-12 20:59 DEBUG  WindowsBackend: windows_language=English
11-12 20:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU       M 620  @ 2.67GHz
11-12 20:59 DEBUG  WindowsBackend: bootloader=vista
11-12 20:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 47433.4765625 mb free ntfs)
11-12 20:59 DEBUG  WindowsBackend: drive=Drive(C: hd 47433.4765625 mb free ntfs)
11-12 20:59 DEBUG  WindowsBackend: drive=Drive(D: hd 61497.3828125 mb free ntfs)
11-12 20:59 DEBUG  WindowsBackend: drive=Drive(F: hd 1520.42578125 mb free fat32)
11-12 20:59 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free udf)
11-12 20:59 DEBUG  WindowsBackend: uninstaller_path=None
11-12 20:59 DEBUG  WindowsBackend: previous_target_dir=None
11-12 20:59 DEBUG  WindowsBackend: previous_distro_name=None
11-12 20:59 DEBUG  WindowsBackend: keyboard_id=67699721
11-12 20:59 DEBUG  WindowsBackend: keyboard_layout=us
11-12 20:59 DEBUG  WindowsBackend: keyboard_variant=
11-12 20:59 DEBUG  WindowsBackend: total_memory_mb=1903.4296875
11-12 20:59 DEBUG  CommonBackend: Searching ISOs on USB devices
11-12 20:59 DEBUG  CommonBackend: Searching for local CDs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystefm.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Ubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Kubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 20:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 20:59 INFO   root: Running the installer...
11-12 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\translations, languages=['en_US', 'en']
11-12 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\translations, languages=['en_US', 'en']
11-12 21:00 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=user1
11-12 21:00 INFO   root: Received settings
11-12 21:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\translations, languages=['en_US', 'en']
11-12 21:00 DEBUG  TaskList: # Running tasklist...
11-12 21:00 DEBUG  TaskList: ## Running select_target_dir...
11-12 21:00 INFO   WindowsBackend: Installing into D:\ubuntu
11-12 21:00 DEBUG  TaskList: ## Finished select_target_dir
11-12 21:00 DEBUG  TaskList: ## Running create_dir_structure...
11-12 21:00 DEBUG  CommonBackend: Creating dir D:\ubuntu
11-12 21:00 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
11-12 21:00 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
11-12 21:00 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
11-12 21:00 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
11-12 21:00 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
11-12 21:00 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
11-12 21:00 DEBUG  TaskList: ## Finished create_dir_structure
11-12 21:00 DEBUG  TaskList: ## Running uncompress_target_dir...
11-12 21:00 DEBUG  TaskList: ## Finished uncompress_target_dir
11-12 21:00 DEBUG  TaskList: ## Running create_uninstaller...
11-12 21:00 DEBUG  WindowsBackend: Copying uninstaller C:\Users\user1\Downloads\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
11-12 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
11-12 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
11-12 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-12 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
11-12 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
11-12 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-12 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-12 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-12 21:00 DEBUG  TaskList: ## Finished create_uninstaller
11-12 21:00 DEBUG  TaskList: ## Running copy_installation_files...
11-12 21:00 DEBUG  WindowsBackend: Copying C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
11-12 21:00 DEBUG  WindowsBackend: Copying C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\winboot -> D:\ubuntu\winboot
11-12 21:00 DEBUG  WindowsBackend: Copying C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
11-12 21:00 DEBUG  TaskList: ## Finished copy_installation_files
11-12 21:00 DEBUG  TaskList: ## Running get_iso...
11-12 21:00 DEBUG  CommonBackend: Searching for local CD
11-12 21:00 DEBUG  Distro:   checking whether C:\Users\user1\AppData\Local\Temp\pyl5753.tmp is a valid Ubuntu CD
11-12 21:00 DEBUG  Distro:     does not contain C:\Users\user1\AppData\Local\Temp\pyl5753.tmp\casper\filesystem.squashfs
11-12 21:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 21:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 21:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 21:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 21:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 21:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 21:00 DEBUG  CommonBackend: Searching for local ISO
11-12 21:00 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-12 21:00 DEBUG  TaskList: New task get_metalink
11-12 21:00 DEBUG  TaskList: ### Running get_metalink...
11-12 21:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink) > D:\ubuntu\install
11-12 21:00 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink, basename=ubuntu-10.04.1-desktop-amd64.metalink, length=36844, text=None
11-12 21:00 DEBUG  downloader: download finished (read 36844 bytes)
11-12 21:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink](http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink) > D:\ubuntu\install
11-12 21:00 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=651, text=None
11-12 21:00 DEBUG  downloader: download finished (read 651 bytes)
11-12 21:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink.gpg) > D:\ubuntu\install
11-12 21:00 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
11-12 21:00 DEBUG  downloader: download finished (read 189 bytes)
11-12 21:00 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
11-12 21:00 INFO   saplog: Checking block bindings..
11-12 21:00 INFO   saplog: Key verified successfully.
11-12 21:00 DEBUG  CommonBackend: metalink md5sums:
a293f05f7be5e61937b1c277c6a69262  ubuntu-10.04-netbook-armel+dove.metalink
dece0df9abb10efb1f590f759cccf340  ubuntu-10.04-netbook-armel+imx51.metalink
a3805816968bf7199e080ba653a19ac1  ubuntu-10.04-netbook-i386.metalink
94706d50d0375fe01b4b480a9c875a7f  ubuntu-10.04.1-alternate-amd64.metalink
7e94a4ebedb1dcfc4fe376f5a96c45aa  ubuntu-10.04.1-alternate-i386.metalink
974c01945586ebcbb672f11ce6df0e39  ubuntu-10.04.1-desktop-amd64.metalink
b3b2f75f70c5216d1325a5a02f3770ce  ubuntu-10.04.1-desktop-i386.metalink
8b0786e4978a123ce91e87181eb0f570  ubuntu-10.04.1-server-amd64.metalink
56dff8fca4d2612eb035a909092f5016  ubuntu-10.04.1-server-i386.metalink

11-12 21:00 DEBUG  TaskList: ### Finished get_metalink
11-12 21:00 DEBUG  TaskList: New task download
11-12 21:00 DEBUG  TaskList: ### Running download...
11-12 21:00 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.iso.torrent) > D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 21:14 DEBUG  TaskList: ### Finished download
11-12 21:14 DEBUG  TaskList: New task check_iso
11-12 21:14 DEBUG  TaskList: ### Running check_iso...
11-12 21:14 DEBUG  CommonBackend: Checking D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 21:14 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 21:14 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 21:14 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.1 LTS "Lucid Lynx" - Release amd64 (20100816.1)
11-12 21:14 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.1', 'build': '20100816.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
11-12 21:14 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 21:14 DEBUG  TaskList: New task get_file_md5
11-12 21:14 DEBUG  TaskList: #### Running get_file_md5...
11-12 21:14 DEBUG  TaskList: #### Finished get_file_md5
11-12 21:14 DEBUG  TaskList: ### Finished check_iso
11-12 21:14 DEBUG  TaskList: ## Finished get_iso
11-12 21:14 DEBUG  TaskList: ## Running extract_kernel...
11-12 21:14 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 21:14 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 21:14 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 21:14 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\ubuntu-10.04.1-desktop-amd64.iso
11-12 21:14 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
11-12 21:14 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
11-12 21:14 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = 3c758a2db6d6909eac17cb173fe2fae7 == 3c758a2db6d6909eac17cb173fe2fae7
11-12 21:14 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
11-12 21:14 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = bbdb9403ed7050629dbb57085aa381dd == bbdb9403ed7050629dbb57085aa381dd
11-12 21:14 DEBUG  TaskList: ## Finished extract_kernel
11-12 21:14 DEBUG  TaskList: ## Running choose_disk_sizes...
11-12 21:14 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
11-12 21:14 DEBUG  TaskList: ## Finished choose_disk_sizes
11-12 21:14 DEBUG  TaskList: ## Running create_preseed...
11-12 21:14 DEBUG  TaskList: ## Finished create_preseed
11-12 21:14 DEBUG  TaskList: ## Running modify_bootloader...
11-12 21:14 DEBUG  TaskList: New task modify_bcd
11-12 21:14 DEBUG  TaskList: ### Running modify_bcd...
11-12 21:14 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 47433.4765625 mb free ntfs)
11-12 21:14 ERROR  TaskList: Error executing command
>>command=C:\windows\System32\bcdedit.exe /set {57a03f84-df52-11df-bdbe-c01d94a8b7f5} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\windows\System32\bcdedit.exe /set {57a03f84-df52-11df-bdbe-c01d94a8b7f5} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
11-12 21:14 DEBUG  TaskList: # Cancelling tasklist
11-12 21:14 DEBUG  TaskList: New task modify_bcd
11-12 21:14 ERROR  root: Error executing command
>>command=C:\windows\System32\bcdedit.exe /set {57a03f84-df52-11df-bdbe-c01d94a8b7f5} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\windows\System32\bcdedit.exe /set {57a03f84-df52-11df-bdbe-c01d94a8b7f5} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
11-12 21:14 DEBUG  TaskList: New task modify_bcd
11-12 21:14 DEBUG  TaskList: ## Finished modify_bootloader
11-12 21:14 DEBUG  TaskList: # Finished tasklist
--------------
please help!!

Thanks.

---

### Post by rcayea on 2010-11-12
I am not sure what the issue is, but I do know one thing, we need more information. 

Did you try to install Ubuntu alongside Windows or did you try to install windows after Ubuntu or Ubuntu after Windows was already installed?

What was your situation when you installed Ubuntu?

---

### Post by bcbc on 2010-11-12
You're installing to drive D: 
If this is a dynamic drive (created within windows 7) then it won't work. Try instead to install to C:

---

### Post by jolieyeah on 2010-11-13
Thank you all!!
I installed win7 first and then installed ubuntu, I want to have dual OS...

and  D is dynamic. 

Let me try to install it on the C drive.


Thanks again~~

---

### Post by jolieyeah on 2010-11-13
Hi, everyone, I got it .

Thanks again!!

---

