---
title: "Cant install ubuntu using wubi on win 7"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by girish.gp on 2011-03-16
i m not able 2 install ubuntu using wubi on windows 7...
the specifications r:-
file system :NTFS and 
64-bit x86 intel i3 processor

plz find the attachment to see the error that i received after installation.

when i went to the destination stated in the error, i got the text file which contained following data:-
"
12-30 21:27 INFO   root: === wubi 10.10 rev197 ===
12-30 21:27 DEBUG  root: Logfile is c:\users\girish\appdata\local\temp\wubi-10.10-rev197.log
12-30 21:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
12-30 21:27 DEBUG  CommonBackend: data_dir=C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp\data
12-30 21:27 DEBUG  WindowsBackend: 7z=C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp\bin\7z.exe
12-30 21:27 DEBUG  CommonBackend: Fetching basic info...
12-30 21:27 DEBUG  CommonBackend: original_exe=F:\wubi.exe
12-30 21:27 DEBUG  CommonBackend: platform=win32
12-30 21:27 DEBUG  CommonBackend: osname=nt
12-30 21:27 DEBUG  CommonBackend: language=en_IN
12-30 21:27 DEBUG  CommonBackend: encoding=cp1252
12-30 21:27 DEBUG  WindowsBackend: arch=amd64
12-30 21:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp\data\isolist.ini
12-30 21:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-30 21:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-30 21:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-30 21:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-30 21:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-30 21:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-30 21:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-30 21:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-30 21:27 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-30 21:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-30 21:27 DEBUG  WindowsBackend: Fetching host info...
12-30 21:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-30 21:27 DEBUG  WindowsBackend: windows version=vista
12-30 21:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-30 21:27 DEBUG  WindowsBackend: windows_sp=None
12-30 21:27 DEBUG  WindowsBackend: windows_build=7600
12-30 21:27 DEBUG  WindowsBackend: gmt=5
12-30 21:27 DEBUG  WindowsBackend: country=IN
12-30 21:27 DEBUG  WindowsBackend: timezone=Asia/Calcutta
12-30 21:27 DEBUG  WindowsBackend: windows_username=Girish
12-30 21:27 DEBUG  WindowsBackend: user_full_name=Girish
12-30 21:27 DEBUG  WindowsBackend: user_directory=C:\Users\Girish
12-30 21:27 DEBUG  WindowsBackend: windows_language_code=1033
12-30 21:27 DEBUG  WindowsBackend: windows_language=English
12-30 21:27 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
12-30 21:27 DEBUG  WindowsBackend: bootloader=vista
12-30 21:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 79957.0859375 mb free ntfs)
12-30 21:27 DEBUG  WindowsBackend: drive=Drive(C: hd 79957.0859375 mb free ntfs)
12-30 21:27 DEBUG  WindowsBackend: drive=Drive(D: hd 3260.40625 mb free ntfs)
12-30 21:27 DEBUG  WindowsBackend: drive=Drive(E: hd 90.2333984375 mb free fat32)
12-30 21:27 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
12-30 21:27 DEBUG  WindowsBackend: drive=Drive(G: hd 6464.44140625 mb free ntfs)
12-30 21:27 DEBUG  WindowsBackend: drive=Drive(H: hd 21028.0195313 mb free ntfs)
12-30 21:27 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
12-30 21:27 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-30 21:27 DEBUG  WindowsBackend: uninstaller_path=None
12-30 21:27 DEBUG  WindowsBackend: previous_target_dir=None
12-30 21:27 DEBUG  WindowsBackend: previous_distro_name=None
12-30 21:27 DEBUG  WindowsBackend: keyboard_id=67699721
12-30 21:27 DEBUG  WindowsBackend: keyboard_layout=us
12-30 21:27 DEBUG  WindowsBackend: keyboard_variant=
12-30 21:27 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
12-30 21:27 DEBUG  CommonBackend: locale=en_IN
12-30 21:27 DEBUG  WindowsBackend: total_memory_mb=2933.859375
12-30 21:27 DEBUG  CommonBackend: Searching ISOs on USB devices
12-30 21:27 DEBUG  CommonBackend: Searching for local CDs
12-30 21:27 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp is a valid Ubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp is a valid Ubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp is a valid Ubuntu Netbook CD
12-30 21:27 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp is a valid Kubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp is a valid Kubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp is a valid Kubuntu Netbook CD
12-30 21:27 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp is a valid Xubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp is a valid Xubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp is a valid Mythbuntu CD
12-30 21:27 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp is a valid Mythbuntu CD
12-30 21:27 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
12-30 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-30 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-30 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-30 21:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
12-30 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-30 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-30 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-30 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-30 21:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-30 21:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-30 21:27 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
12-30 21:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
12-30 21:27 INFO   Distro: Found a valid CD for Ubuntu: F:\
12-30 21:27 INFO   root: Running the CD menu...
12-30 21:27 DEBUG  WindowsFrontend: __init__...
12-30 21:27 DEBUG  WindowsFrontend: on_init...
12-30 21:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp\translations, languages=['en_IN', 'en']
12-30 21:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pyl4515.tmp\translations, languages=['en_IN', 'en']
12-30 21:27 INFO   WindowsFrontend: Operation cancelled
12-30 21:27 DEBUG  WindowsFrontend: frontend.quit
12-30 21:27 DEBUG  WindowsFrontend: frontend.on_quit
12-30 21:27 DEBUG  root: application.on_quit
12-30 21:27 INFO   root: sys.exit
03-16 17:49 INFO   root: === wubi 10.10 rev197 ===
03-16 17:49 DEBUG  root: Logfile is c:\users\girish\appdata\local\temp\wubi-10.10-rev197.log
03-16 17:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
03-16 17:49 DEBUG  CommonBackend: data_dir=C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp\data
03-16 17:49 DEBUG  WindowsBackend: 7z=C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp\bin\7z.exe
03-16 17:49 DEBUG  CommonBackend: Fetching basic info...
03-16 17:49 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-16 17:49 DEBUG  CommonBackend: platform=win32
03-16 17:49 DEBUG  CommonBackend: osname=nt
03-16 17:49 DEBUG  CommonBackend: language=en_IN
03-16 17:49 DEBUG  CommonBackend: encoding=cp1252
03-16 17:49 DEBUG  WindowsBackend: arch=amd64
03-16 17:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp\data\isolist.ini
03-16 17:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-16 17:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-16 17:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-16 17:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-16 17:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-16 17:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-16 17:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-16 17:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-16 17:49 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-16 17:49 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-16 17:49 DEBUG  WindowsBackend: Fetching host info...
03-16 17:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-16 17:49 DEBUG  WindowsBackend: windows version=vista
03-16 17:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-16 17:49 DEBUG  WindowsBackend: windows_sp=None
03-16 17:49 DEBUG  WindowsBackend: windows_build=7600
03-16 17:49 DEBUG  WindowsBackend: gmt=5
03-16 17:49 DEBUG  WindowsBackend: country=IN
03-16 17:49 DEBUG  WindowsBackend: timezone=Asia/Calcutta
03-16 17:49 DEBUG  WindowsBackend: windows_username=Girish
03-16 17:49 DEBUG  WindowsBackend: user_full_name=Girish
03-16 17:49 DEBUG  WindowsBackend: user_directory=C:\Users\Girish
03-16 17:49 DEBUG  WindowsBackend: windows_language_code=1033
03-16 17:49 DEBUG  WindowsBackend: windows_language=English
03-16 17:49 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
03-16 17:49 DEBUG  WindowsBackend: bootloader=vista
03-16 17:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 66772.3398438 mb free ntfs)
03-16 17:49 DEBUG  WindowsBackend: drive=Drive(C: hd 66772.3398438 mb free ntfs)
03-16 17:49 DEBUG  WindowsBackend: drive=Drive(D: hd 3260.40625 mb free ntfs)
03-16 17:49 DEBUG  WindowsBackend: drive=Drive(E: hd 90.2333984375 mb free fat32)
03-16 17:49 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-16 17:49 DEBUG  WindowsBackend: drive=Drive(G: hd 19370.0351563 mb free ntfs)
03-16 17:49 DEBUG  WindowsBackend: drive=Drive(H: hd 69454.2070313 mb free ntfs)
03-16 17:49 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
03-16 17:49 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
03-16 17:49 DEBUG  WindowsBackend: uninstaller_path=None
03-16 17:49 DEBUG  WindowsBackend: previous_target_dir=None
03-16 17:49 DEBUG  WindowsBackend: previous_distro_name=None
03-16 17:49 DEBUG  WindowsBackend: keyboard_id=67699721
03-16 17:49 DEBUG  WindowsBackend: keyboard_layout=us
03-16 17:49 DEBUG  WindowsBackend: keyboard_variant=
03-16 17:49 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
03-16 17:49 DEBUG  CommonBackend: locale=en_IN
03-16 17:49 DEBUG  WindowsBackend: total_memory_mb=2933.859375
03-16 17:49 DEBUG  CommonBackend: Searching ISOs on USB devices
03-16 17:49 DEBUG  CommonBackend: Searching for local CDs
03-16 17:49 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp is a valid Ubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp is a valid Ubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp is a valid Ubuntu Netbook CD
03-16 17:49 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp is a valid Kubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp is a valid Kubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp is a valid Kubuntu Netbook CD
03-16 17:49 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp is a valid Xubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp is a valid Xubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp is a valid Mythbuntu CD
03-16 17:49 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp is a valid Mythbuntu CD
03-16 17:49 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-16 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-16 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-16 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-16 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-16 17:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-16 17:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-16 17:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-16 17:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-16 17:49 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:49 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-16 17:49 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-16 17:49 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-16 17:49 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-16 17:49 INFO   root: Running the CD menu...
03-16 17:49 DEBUG  WindowsFrontend: __init__...
03-16 17:49 DEBUG  WindowsFrontend: on_init...
03-16 17:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp\translations, languages=['en_IN', 'en']
03-16 17:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pyl38BE.tmp\translations, languages=['en_IN', 'en']
03-16 17:50 INFO   root: CD menu finished
03-16 17:50 INFO   root: Rebooting
03-16 17:50 DEBUG  TaskList: # Running tasklist...
03-16 17:50 DEBUG  TaskList: ## Running reboot...
03-16 17:50 DEBUG  TaskList: ## Finished reboot
03-16 17:50 DEBUG  TaskList: # Finished tasklist
03-16 17:50 DEBUG  root: application.quit
03-16 17:50 DEBUG  WindowsFrontend: frontend.quit
03-16 17:50 DEBUG  WindowsFrontend: frontend.on_quit
03-16 17:50 DEBUG  root: application.on_quit
03-16 17:50 INFO   root: sys.exit
03-16 17:53 INFO   root: === wubi 10.10 rev197 ===
03-16 17:53 DEBUG  root: Logfile is c:\users\girish\appdata\local\temp\wubi-10.10-rev197.log
03-16 17:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-16 17:53 DEBUG  CommonBackend: data_dir=C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\data
03-16 17:53 DEBUG  WindowsBackend: 7z=C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\bin\7z.exe
03-16 17:53 DEBUG  CommonBackend: Fetching basic info...
03-16 17:53 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-16 17:53 DEBUG  CommonBackend: platform=win32
03-16 17:53 DEBUG  CommonBackend: osname=nt
03-16 17:53 DEBUG  CommonBackend: language=en_IN
03-16 17:53 DEBUG  CommonBackend: encoding=cp1252
03-16 17:53 DEBUG  WindowsBackend: arch=amd64
03-16 17:53 DEBUG  CommonBackend: Parsing isolist=C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\data\isolist.ini
03-16 17:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-16 17:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-16 17:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-16 17:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-16 17:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-16 17:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-16 17:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-16 17:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-16 17:53 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-16 17:53 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-16 17:53 DEBUG  WindowsBackend: Fetching host info...
03-16 17:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-16 17:53 DEBUG  WindowsBackend: windows version=vista
03-16 17:53 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-16 17:53 DEBUG  WindowsBackend: windows_sp=None
03-16 17:53 DEBUG  WindowsBackend: windows_build=7600
03-16 17:53 DEBUG  WindowsBackend: gmt=5
03-16 17:53 DEBUG  WindowsBackend: country=IN
03-16 17:53 DEBUG  WindowsBackend: timezone=Asia/Calcutta
03-16 17:53 DEBUG  WindowsBackend: windows_username=Girish
03-16 17:53 DEBUG  WindowsBackend: user_full_name=Girish
03-16 17:53 DEBUG  WindowsBackend: user_directory=C:\Users\Girish
03-16 17:53 DEBUG  WindowsBackend: windows_language_code=1033
03-16 17:53 DEBUG  WindowsBackend: windows_language=English
03-16 17:53 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
03-16 17:53 DEBUG  WindowsBackend: bootloader=vista
03-16 17:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 66786.1992188 mb free ntfs)
03-16 17:53 DEBUG  WindowsBackend: drive=Drive(C: hd 66786.1992188 mb free ntfs)
03-16 17:53 DEBUG  WindowsBackend: drive=Drive(D: hd 3260.40625 mb free ntfs)
03-16 17:53 DEBUG  WindowsBackend: drive=Drive(E: hd 90.2333984375 mb free fat32)
03-16 17:53 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-16 17:53 DEBUG  WindowsBackend: drive=Drive(G: hd 19370.328125 mb free ntfs)
03-16 17:53 DEBUG  WindowsBackend: drive=Drive(H: hd 69454.2070313 mb free ntfs)
03-16 17:53 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
03-16 17:53 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
03-16 17:53 DEBUG  WindowsBackend: uninstaller_path=None
03-16 17:53 DEBUG  WindowsBackend: previous_target_dir=None
03-16 17:53 DEBUG  WindowsBackend: previous_distro_name=None
03-16 17:53 DEBUG  WindowsBackend: keyboard_id=67699721
03-16 17:53 DEBUG  WindowsBackend: keyboard_layout=us
03-16 17:53 DEBUG  WindowsBackend: keyboard_variant=
03-16 17:53 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
03-16 17:53 DEBUG  CommonBackend: locale=en_IN
03-16 17:53 DEBUG  WindowsBackend: total_memory_mb=2933.859375
03-16 17:53 DEBUG  CommonBackend: Searching ISOs on USB devices
03-16 17:53 DEBUG  CommonBackend: Searching for local CDs
03-16 17:53 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp is a valid Ubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp is a valid Ubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp is a valid Ubuntu Netbook CD
03-16 17:53 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp is a valid Kubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp is a valid Kubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp is a valid Kubuntu Netbook CD
03-16 17:53 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp is a valid Xubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp is a valid Xubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp is a valid Mythbuntu CD
03-16 17:53 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp is a valid Mythbuntu CD
03-16 17:53 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-16 17:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-16 17:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-16 17:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-16 17:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-16 17:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-16 17:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-16 17:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-16 17:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-16 17:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 17:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-16 17:53 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-16 17:53 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-16 17:53 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-16 17:53 INFO   root: Running the CD menu...
03-16 17:53 DEBUG  WindowsFrontend: __init__...
03-16 17:53 DEBUG  WindowsFrontend: on_init...
03-16 17:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\translations, languages=['en_IN', 'en']
03-16 17:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\translations, languages=['en_IN', 'en']
03-16 17:53 INFO   root: CD menu finished
03-16 17:53 INFO   root: Running the installer...
03-16 17:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\translations, languages=['en_IN', 'en']
03-16 17:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\translations, languages=['en_IN', 'en']
03-16 17:54 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=girish
03-16 17:54 INFO   root: Received settings
03-16 17:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\translations, languages=['en_US', 'en']
03-16 17:54 DEBUG  TaskList: # Running tasklist...
03-16 17:54 DEBUG  TaskList: ## Running select_target_dir...
03-16 17:54 INFO   WindowsBackend: Installing into C:\ubuntu
03-16 17:54 DEBUG  TaskList: ## Finished select_target_dir
03-16 17:54 DEBUG  TaskList: ## Running create_dir_structure...
03-16 17:54 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-16 17:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-16 17:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-16 17:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-16 17:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-16 17:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-16 17:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-16 17:54 DEBUG  TaskList: ## Finished create_dir_structure
03-16 17:54 DEBUG  TaskList: ## Running uncompress_target_dir...
03-16 17:54 DEBUG  TaskList: ## Finished uncompress_target_dir
03-16 17:54 DEBUG  TaskList: ## Running create_uninstaller...
03-16 17:54 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-16 17:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-16 17:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-16 17:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-16 17:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-16 17:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-16 17:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-16 17:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-16 17:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-16 17:54 DEBUG  TaskList: ## Finished create_uninstaller
03-16 17:54 DEBUG  TaskList: ## Running copy_installation_files...
03-16 17:54 DEBUG  WindowsBackend: Copying C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-16 17:54 DEBUG  WindowsBackend: Copying C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\winboot -> C:\ubuntu\winboot
03-16 17:54 DEBUG  WindowsBackend: Copying C:\Users\Girish\AppData\Local\Temp\pyl79EF.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-16 17:54 DEBUG  TaskList: ## Finished copy_installation_files
03-16 17:54 DEBUG  TaskList: ## Running get_iso...
03-16 17:54 DEBUG  TaskList: New task copy_file
03-16 17:54 DEBUG  TaskList: ### Running copy_file...
03-16 17:58 DEBUG  TaskList: ### Finished copy_file
03-16 17:58 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-16 17:58 DEBUG  TaskList: # Cancelling tasklist
03-16 17:58 DEBUG  TaskList: New task check_iso
03-16 17:58 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-16 17:58 DEBUG  CommonBackend: Searching for local ISO
03-16 17:58 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-16 17:58 DEBUG  TaskList: New task get_metalink
03-16 17:58 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-16 17:58 DEBUG  TaskList: # Cancelling tasklist
03-16 17:58 DEBUG  TaskList: # Finished tasklist
03-16 18:03 INFO   root: === wubi 10.10 rev197 ===
03-16 18:03 DEBUG  root: Logfile is c:\users\girish\appdata\local\temp\wubi-10.10-rev197.log
03-16 18:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
03-16 18:03 DEBUG  CommonBackend: data_dir=C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\data
03-16 18:03 DEBUG  WindowsBackend: 7z=C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\bin\7z.exe
03-16 18:03 DEBUG  CommonBackend: Fetching basic info...
03-16 18:03 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
03-16 18:03 DEBUG  CommonBackend: platform=win32
03-16 18:03 DEBUG  CommonBackend: osname=nt
03-16 18:03 DEBUG  CommonBackend: language=en_IN
03-16 18:03 DEBUG  CommonBackend: encoding=cp1252
03-16 18:03 DEBUG  WindowsBackend: arch=amd64
03-16 18:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\data\isolist.ini
03-16 18:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-16 18:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-16 18:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-16 18:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-16 18:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-16 18:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-16 18:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-16 18:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-16 18:03 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-16 18:03 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-16 18:03 DEBUG  WindowsBackend: Fetching host info...
03-16 18:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-16 18:03 DEBUG  WindowsBackend: windows version=vista
03-16 18:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-16 18:03 DEBUG  WindowsBackend: windows_sp=None
03-16 18:03 DEBUG  WindowsBackend: windows_build=7600
03-16 18:03 DEBUG  WindowsBackend: gmt=5
03-16 18:03 DEBUG  WindowsBackend: country=IN
03-16 18:03 DEBUG  WindowsBackend: timezone=Asia/Calcutta
03-16 18:03 DEBUG  WindowsBackend: windows_username=Girish
03-16 18:03 DEBUG  WindowsBackend: user_full_name=Girish
03-16 18:03 DEBUG  WindowsBackend: user_directory=C:\Users\Girish
03-16 18:03 DEBUG  WindowsBackend: windows_language_code=1033
03-16 18:03 DEBUG  WindowsBackend: windows_language=English
03-16 18:03 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
03-16 18:03 DEBUG  WindowsBackend: bootloader=vista
03-16 18:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 66088.828125 mb free ntfs)
03-16 18:03 DEBUG  WindowsBackend: drive=Drive(C: hd 66088.828125 mb free ntfs)
03-16 18:03 DEBUG  WindowsBackend: drive=Drive(D: hd 3260.40625 mb free ntfs)
03-16 18:03 DEBUG  WindowsBackend: drive=Drive(E: hd 90.2333984375 mb free fat32)
03-16 18:03 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-16 18:03 DEBUG  WindowsBackend: drive=Drive(G: hd 19370.328125 mb free ntfs)
03-16 18:03 DEBUG  WindowsBackend: drive=Drive(H: hd 69454.2070313 mb free ntfs)
03-16 18:03 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
03-16 18:03 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
03-16 18:03 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-16 18:03 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-16 18:03 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-16 18:03 DEBUG  WindowsBackend: keyboard_id=67699721
03-16 18:03 DEBUG  WindowsBackend: keyboard_layout=us
03-16 18:03 DEBUG  WindowsBackend: keyboard_variant=
03-16 18:03 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
03-16 18:03 DEBUG  CommonBackend: locale=en_IN
03-16 18:03 DEBUG  WindowsBackend: total_memory_mb=2933.859375
03-16 18:03 DEBUG  CommonBackend: Searching ISOs on USB devices
03-16 18:03 DEBUG  CommonBackend: Searching for local CDs
03-16 18:03 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp is a valid Ubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp is a valid Ubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp is a valid Ubuntu Netbook CD
03-16 18:03 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp is a valid Kubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp is a valid Kubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp is a valid Kubuntu Netbook CD
03-16 18:03 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp is a valid Xubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp is a valid Xubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp is a valid Mythbuntu CD
03-16 18:03 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp is a valid Mythbuntu CD
03-16 18:03 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-16 18:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-16 18:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-16 18:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-16 18:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-16 18:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-16 18:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-16 18:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-16 18:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-16 18:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-16 18:03 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-16 18:03 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-16 18:03 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-16 18:03 INFO   root: Running the uninstaller...
03-16 18:03 INFO   CommonBackend: This is the uninstaller running
03-16 18:03 DEBUG  WindowsFrontend: __init__...
03-16 18:03 DEBUG  WindowsFrontend: on_init...
03-16 18:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\translations, languages=['en_IN', 'en']
03-16 18:03 INFO   root: Received settings
03-16 18:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\translations, languages=['en_IN', 'en']
03-16 18:03 DEBUG  TaskList: # Running tasklist...
03-16 18:03 DEBUG  TaskList: ## Running Backup ISO...
03-16 18:03 DEBUG  TaskList: ## Finished Backup ISO
03-16 18:03 DEBUG  TaskList: ## Running Remove bootloader entry...
03-16 18:03 DEBUG  WindowsBackend: Could not find bcd id
03-16 18:03 DEBUG  WindowsBackend: undo_bootini C:
03-16 18:03 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 66088.828125 mb free ntfs)
03-16 18:03 DEBUG  WindowsBackend: undo_bootini D:
03-16 18:03 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 3260.40625 mb free ntfs)
03-16 18:03 DEBUG  WindowsBackend: undo_bootini E:
03-16 18:03 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 90.2333984375 mb free fat32)
03-16 18:03 DEBUG  WindowsBackend: undo_bootini G:
03-16 18:03 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 19370.328125 mb free ntfs)
03-16 18:03 DEBUG  WindowsBackend: undo_bootini H:
03-16 18:03 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 69454.2070313 mb free ntfs)
03-16 18:03 DEBUG  WindowsBackend: undo_bootini Q:
03-16 18:03 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
03-16 18:03 DEBUG  TaskList: ## Finished Remove bootloader entry
03-16 18:03 DEBUG  TaskList: ## Running Remove target dir...
03-16 18:03 DEBUG  CommonBackend: Deleting C:\ubuntu
03-16 18:03 DEBUG  TaskList: ## Finished Remove target dir
03-16 18:03 DEBUG  TaskList: ## Running Remove registry key...
03-16 18:03 DEBUG  TaskList: ## Finished Remove registry key
03-16 18:03 DEBUG  TaskList: # Finished tasklist
03-16 18:03 INFO   root: Almost finished uninstalling
03-16 18:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pylA89D.tmp\translations, languages=['en_IN', 'en']
03-16 18:03 INFO   root: Finished uninstallation
03-16 18:03 DEBUG  root: application.quit
03-16 18:03 DEBUG  WindowsFrontend: frontend.quit
03-16 18:03 DEBUG  WindowsFrontend: frontend.on_quit
03-16 18:03 DEBUG  root: application.on_quit
03-16 18:03 INFO   root: sys.exit
03-16 18:06 INFO   root: === wubi 10.10 rev197 ===
03-16 18:06 DEBUG  root: Logfile is c:\users\girish\appdata\local\temp\wubi-10.10-rev197.log
03-16 18:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-16 18:06 DEBUG  CommonBackend: data_dir=C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\data
03-16 18:06 DEBUG  WindowsBackend: 7z=C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\bin\7z.exe
03-16 18:06 DEBUG  CommonBackend: Fetching basic info...
03-16 18:06 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-16 18:06 DEBUG  CommonBackend: platform=win32
03-16 18:06 DEBUG  CommonBackend: osname=nt
03-16 18:06 DEBUG  CommonBackend: language=en_IN
03-16 18:06 DEBUG  CommonBackend: encoding=cp1252
03-16 18:06 DEBUG  WindowsBackend: arch=amd64
03-16 18:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\data\isolist.ini
03-16 18:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-16 18:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-16 18:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-16 18:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-16 18:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-16 18:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-16 18:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-16 18:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-16 18:06 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-16 18:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-16 18:06 DEBUG  WindowsBackend: Fetching host info...
03-16 18:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-16 18:06 DEBUG  WindowsBackend: windows version=vista
03-16 18:06 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-16 18:06 DEBUG  WindowsBackend: windows_sp=None
03-16 18:06 DEBUG  WindowsBackend: windows_build=7600
03-16 18:06 DEBUG  WindowsBackend: gmt=5
03-16 18:06 DEBUG  WindowsBackend: country=IN
03-16 18:06 DEBUG  WindowsBackend: timezone=Asia/Calcutta
03-16 18:06 DEBUG  WindowsBackend: windows_username=Girish
03-16 18:06 DEBUG  WindowsBackend: user_full_name=Girish
03-16 18:06 DEBUG  WindowsBackend: user_directory=C:\Users\Girish
03-16 18:06 DEBUG  WindowsBackend: windows_language_code=1033
03-16 18:06 DEBUG  WindowsBackend: windows_language=English
03-16 18:06 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
03-16 18:06 DEBUG  WindowsBackend: bootloader=vista
03-16 18:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 66782.046875 mb free ntfs)
03-16 18:06 DEBUG  WindowsBackend: drive=Drive(C: hd 66782.046875 mb free ntfs)
03-16 18:06 DEBUG  WindowsBackend: drive=Drive(D: hd 3260.40625 mb free ntfs)
03-16 18:06 DEBUG  WindowsBackend: drive=Drive(E: hd 90.2333984375 mb free fat32)
03-16 18:06 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-16 18:06 DEBUG  WindowsBackend: drive=Drive(G: hd 19370.328125 mb free ntfs)
03-16 18:06 DEBUG  WindowsBackend: drive=Drive(H: hd 69454.2070313 mb free ntfs)
03-16 18:06 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
03-16 18:06 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
03-16 18:06 DEBUG  WindowsBackend: uninstaller_path=None
03-16 18:06 DEBUG  WindowsBackend: previous_target_dir=None
03-16 18:06 DEBUG  WindowsBackend: previous_distro_name=None
03-16 18:06 DEBUG  WindowsBackend: keyboard_id=67699721
03-16 18:06 DEBUG  WindowsBackend: keyboard_layout=us
03-16 18:06 DEBUG  WindowsBackend: keyboard_variant=
03-16 18:06 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
03-16 18:06 DEBUG  CommonBackend: locale=en_IN
03-16 18:06 DEBUG  WindowsBackend: total_memory_mb=2933.859375
03-16 18:06 DEBUG  CommonBackend: Searching ISOs on USB devices
03-16 18:06 DEBUG  CommonBackend: Searching for local CDs
03-16 18:06 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylD789.tmp is a valid Ubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylD789.tmp is a valid Ubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylD789.tmp is a valid Ubuntu Netbook CD
03-16 18:06 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylD789.tmp is a valid Kubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylD789.tmp is a valid Kubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylD789.tmp is a valid Kubuntu Netbook CD
03-16 18:06 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylD789.tmp is a valid Xubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylD789.tmp is a valid Xubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylD789.tmp is a valid Mythbuntu CD
03-16 18:06 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylD789.tmp is a valid Mythbuntu CD
03-16 18:06 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-16 18:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-16 18:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-16 18:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-16 18:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-16 18:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-16 18:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-16 18:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-16 18:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-16 18:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-16 18:06 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-16 18:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-16 18:06 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-16 18:06 INFO   root: Running the CD menu...
03-16 18:06 DEBUG  WindowsFrontend: __init__...
03-16 18:06 DEBUG  WindowsFrontend: on_init...
03-16 18:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\translations, languages=['en_IN', 'en']
03-16 18:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\translations, languages=['en_IN', 'en']
03-16 18:06 INFO   root: CD menu finished
03-16 18:06 INFO   root: Running the installer...
03-16 18:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\translations, languages=['en_IN', 'en']
03-16 18:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pylD789.tmp\translations, languages=['en_IN', 'en']
03-16 18:06 INFO   WindowsFrontend: Operation cancelled
03-16 18:06 DEBUG  WindowsFrontend: frontend.quit
03-16 18:06 DEBUG  WindowsFrontend: frontend.on_quit
03-16 18:06 DEBUG  root: application.on_quit
03-16 18:06 INFO   root: sys.exit
03-16 18:07 INFO   root: === wubi 10.10 rev197 ===
03-16 18:07 DEBUG  root: Logfile is c:\users\girish\appdata\local\temp\wubi-10.10-rev197.log
03-16 18:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-16 18:07 DEBUG  CommonBackend: data_dir=C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp\data
03-16 18:07 DEBUG  WindowsBackend: 7z=C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp\bin\7z.exe
03-16 18:07 DEBUG  CommonBackend: Fetching basic info...
03-16 18:07 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-16 18:07 DEBUG  CommonBackend: platform=win32
03-16 18:07 DEBUG  CommonBackend: osname=nt
03-16 18:07 DEBUG  CommonBackend: language=en_IN
03-16 18:07 DEBUG  CommonBackend: encoding=cp1252
03-16 18:07 DEBUG  WindowsBackend: arch=amd64
03-16 18:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp\data\isolist.ini
03-16 18:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-16 18:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-16 18:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-16 18:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-16 18:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-16 18:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-16 18:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-16 18:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-16 18:07 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-16 18:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-16 18:07 DEBUG  WindowsBackend: Fetching host info...
03-16 18:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-16 18:07 DEBUG  WindowsBackend: windows version=vista
03-16 18:07 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-16 18:07 DEBUG  WindowsBackend: windows_sp=None
03-16 18:07 DEBUG  WindowsBackend: windows_build=7600
03-16 18:07 DEBUG  WindowsBackend: gmt=5
03-16 18:07 DEBUG  WindowsBackend: country=IN
03-16 18:07 DEBUG  WindowsBackend: timezone=Asia/Calcutta
03-16 18:07 DEBUG  WindowsBackend: windows_username=Girish
03-16 18:07 DEBUG  WindowsBackend: user_full_name=Girish
03-16 18:07 DEBUG  WindowsBackend: user_directory=C:\Users\Girish
03-16 18:07 DEBUG  WindowsBackend: windows_language_code=1033
03-16 18:07 DEBUG  WindowsBackend: windows_language=English
03-16 18:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
03-16 18:07 DEBUG  WindowsBackend: bootloader=vista
03-16 18:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 66782.109375 mb free ntfs)
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(C: hd 66782.109375 mb free ntfs)
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(D: hd 3260.40625 mb free ntfs)
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(E: hd 90.2333984375 mb free fat32)
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(G: hd 19370.328125 mb free ntfs)
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(H: hd 69454.2070313 mb free ntfs)
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
03-16 18:07 DEBUG  WindowsBackend: uninstaller_path=None
03-16 18:07 DEBUG  WindowsBackend: previous_target_dir=None
03-16 18:07 DEBUG  WindowsBackend: previous_distro_name=None
03-16 18:07 DEBUG  WindowsBackend: keyboard_id=67699721
03-16 18:07 DEBUG  WindowsBackend: keyboard_layout=us
03-16 18:07 DEBUG  WindowsBackend: keyboard_variant=
03-16 18:07 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
03-16 18:07 DEBUG  CommonBackend: locale=en_IN
03-16 18:07 DEBUG  WindowsBackend: total_memory_mb=2933.859375
03-16 18:07 DEBUG  CommonBackend: Searching ISOs on USB devices
03-16 18:07 DEBUG  CommonBackend: Searching for local CDs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp is a valid Ubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp is a valid Ubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp is a valid Ubuntu Netbook CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp is a valid Kubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp is a valid Kubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp is a valid Kubuntu Netbook CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp is a valid Xubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp is a valid Xubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp is a valid Mythbuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp is a valid Mythbuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-16 18:07 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-16 18:07 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-16 18:07 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-16 18:07 INFO   root: Running the CD menu...
03-16 18:07 DEBUG  WindowsFrontend: __init__...
03-16 18:07 DEBUG  WindowsFrontend: on_init...
03-16 18:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp\translations, languages=['en_IN', 'en']
03-16 18:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pyl188F.tmp\translations, languages=['en_IN', 'en']
03-16 18:07 INFO   root: CD menu finished
03-16 18:07 DEBUG  CommonBackend: Showing info
03-16 18:07 DEBUG  root: application.quit
03-16 18:07 DEBUG  WindowsFrontend: frontend.quit
03-16 18:07 DEBUG  WindowsFrontend: frontend.on_quit
03-16 18:07 DEBUG  root: application.on_quit
03-16 18:07 INFO   root: sys.exit
03-16 18:07 INFO   root: === wubi 10.10 rev197 ===
03-16 18:07 DEBUG  root: Logfile is c:\users\girish\appdata\local\temp\wubi-10.10-rev197.log
03-16 18:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-16 18:07 DEBUG  CommonBackend: data_dir=C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\data
03-16 18:07 DEBUG  WindowsBackend: 7z=C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\bin\7z.exe
03-16 18:07 DEBUG  CommonBackend: Fetching basic info...
03-16 18:07 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-16 18:07 DEBUG  CommonBackend: platform=win32
03-16 18:07 DEBUG  CommonBackend: osname=nt
03-16 18:07 DEBUG  CommonBackend: language=en_IN
03-16 18:07 DEBUG  CommonBackend: encoding=cp1252
03-16 18:07 DEBUG  WindowsBackend: arch=amd64
03-16 18:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\data\isolist.ini
03-16 18:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-16 18:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-16 18:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-16 18:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-16 18:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-16 18:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-16 18:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-16 18:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-16 18:07 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-16 18:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-16 18:07 DEBUG  WindowsBackend: Fetching host info...
03-16 18:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-16 18:07 DEBUG  WindowsBackend: windows version=vista
03-16 18:07 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
03-16 18:07 DEBUG  WindowsBackend: windows_sp=None
03-16 18:07 DEBUG  WindowsBackend: windows_build=7600
03-16 18:07 DEBUG  WindowsBackend: gmt=5
03-16 18:07 DEBUG  WindowsBackend: country=IN
03-16 18:07 DEBUG  WindowsBackend: timezone=Asia/Calcutta
03-16 18:07 DEBUG  WindowsBackend: windows_username=Girish
03-16 18:07 DEBUG  WindowsBackend: user_full_name=Girish
03-16 18:07 DEBUG  WindowsBackend: user_directory=C:\Users\Girish
03-16 18:07 DEBUG  WindowsBackend: windows_language_code=1033
03-16 18:07 DEBUG  WindowsBackend: windows_language=English
03-16 18:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
03-16 18:07 DEBUG  WindowsBackend: bootloader=vista
03-16 18:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 66781.9453125 mb free ntfs)
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(C: hd 66781.9453125 mb free ntfs)
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(D: hd 3260.40625 mb free ntfs)
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(E: hd 90.2333984375 mb free fat32)
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(G: hd 19370.328125 mb free ntfs)
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(H: hd 69454.2070313 mb free ntfs)
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
03-16 18:07 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
03-16 18:07 DEBUG  WindowsBackend: uninstaller_path=None
03-16 18:07 DEBUG  WindowsBackend: previous_target_dir=None
03-16 18:07 DEBUG  WindowsBackend: previous_distro_name=None
03-16 18:07 DEBUG  WindowsBackend: keyboard_id=67699721
03-16 18:07 DEBUG  WindowsBackend: keyboard_layout=us
03-16 18:07 DEBUG  WindowsBackend: keyboard_variant=
03-16 18:07 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
03-16 18:07 DEBUG  CommonBackend: locale=en_IN
03-16 18:07 DEBUG  WindowsBackend: total_memory_mb=2933.859375
03-16 18:07 DEBUG  CommonBackend: Searching ISOs on USB devices
03-16 18:07 DEBUG  CommonBackend: Searching for local CDs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA968.tmp is a valid Ubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA968.tmp is a valid Ubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA968.tmp is a valid Ubuntu Netbook CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA968.tmp is a valid Kubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA968.tmp is a valid Kubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA968.tmp is a valid Kubuntu Netbook CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA968.tmp is a valid Xubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA968.tmp is a valid Xubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA968.tmp is a valid Mythbuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether C:\Users\Girish\AppData\Local\Temp\pylA968.tmp is a valid Mythbuntu CD
03-16 18:07 DEBUG  Distro:     does not contain C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-16 18:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-16 18:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-16 18:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-16 18:07 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
03-16 18:07 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
03-16 18:07 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-16 18:07 INFO   root: Running the CD menu...
03-16 18:07 DEBUG  WindowsFrontend: __init__...
03-16 18:07 DEBUG  WindowsFrontend: on_init...
03-16 18:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\translations, languages=['en_IN', 'en']
03-16 18:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\translations, languages=['en_IN', 'en']
03-16 18:07 INFO   root: CD menu finished
03-16 18:07 INFO   root: Running the installer...
03-16 18:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\translations, languages=['en_IN', 'en']
03-16 18:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\translations, languages=['en_IN', 'en']
03-16 18:08 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=8000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=girish
03-16 18:08 INFO   root: Received settings
03-16 18:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\translations, languages=['en_US', 'en']
03-16 18:08 DEBUG  TaskList: # Running tasklist...
03-16 18:08 DEBUG  TaskList: ## Running select_target_dir...
03-16 18:08 INFO   WindowsBackend: Installing into C:\ubuntu
03-16 18:08 DEBUG  TaskList: ## Finished select_target_dir
03-16 18:08 DEBUG  TaskList: ## Running create_dir_structure...
03-16 18:08 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-16 18:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-16 18:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-16 18:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-16 18:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-16 18:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-16 18:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-16 18:08 DEBUG  TaskList: ## Finished create_dir_structure
03-16 18:08 DEBUG  TaskList: ## Running uncompress_target_dir...
03-16 18:08 DEBUG  TaskList: ## Finished uncompress_target_dir
03-16 18:08 DEBUG  TaskList: ## Running create_uninstaller...
03-16 18:08 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-16 18:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-16 18:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-16 18:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-16 18:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-16 18:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-16 18:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-16 18:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-16 18:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-16 18:08 DEBUG  TaskList: ## Finished create_uninstaller
03-16 18:08 DEBUG  TaskList: ## Running copy_installation_files...
03-16 18:08 DEBUG  WindowsBackend: Copying C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-16 18:08 DEBUG  WindowsBackend: Copying C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\winboot -> C:\ubuntu\winboot
03-16 18:08 DEBUG  WindowsBackend: Copying C:\Users\Girish\AppData\Local\Temp\pylA968.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-16 18:08 DEBUG  TaskList: ## Finished copy_installation_files
03-16 18:08 DEBUG  TaskList: ## Running get_iso...
03-16 18:08 DEBUG  TaskList: New task copy_file
03-16 18:08 DEBUG  TaskList: ### Running copy_file...
03-16 18:12 DEBUG  TaskList: ### Finished copy_file
03-16 18:12 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-16 18:12 DEBUG  TaskList: # Cancelling tasklist
03-16 18:12 DEBUG  TaskList: New task check_iso
03-16 18:12 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
03-16 18:12 DEBUG  CommonBackend: Searching for local ISO
03-16 18:12 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-16 18:12 DEBUG  TaskList: New task get_metalink
03-16 18:12 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
03-16 18:12 DEBUG  TaskList: # Cancelling tasklist
03-16 18:12 DEBUG  TaskList: # Finished tasklist

"

plz help me with what to do to install ubuntu successfully on windows 7.

thank you.

---

### Post by Rubi1200 on 2011-03-17
Hi and welcome to the forums :-)

If the Windows drives are dynamic you will be unable to install Ubuntu (whether it is Wubi or regular).

If you can post a screenshot of the Windows Disk Management screen we can confirm if this is the case.

Thanks.

---

### Post by bcbc on 2011-03-17
Errno 13 on the copy of the ISO usually indicates a bad CD image, bad CD, or incompatible Optical device. You should check the CD (it's always good to have a bootable Ubuntu CD), but downloading the desktop ISO yourself into the same folder as wubi.exe before running from there is likely the easiest fix.

---

