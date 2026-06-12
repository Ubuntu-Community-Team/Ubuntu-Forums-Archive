---
title: "cannot install 9.10"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by vartok on 2010-01-26
ive been trying to install ubuntu 9.10 on my custom PC and i keep running into trouble.  if i try to install directly to the drive (boot from disk) it will lock up at random points before it actually starts installing. ive tryed redownloading and re burning with the same results.  I have also tryed the "install within windows" and it errors out tward the end of the install... the log is too big for me to attatch so here is a copy


01-22 01:14 INFO   root: === wubi 9.10ubuntu1 rev160 ===
01-22 01:14 DEBUG  root: Logfile is c:\users\vartok\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
01-22 01:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Vartok\\Downloads\\wubi.exe"']
01-22 01:14 DEBUG  CommonBackend: data_dir=C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\data
01-22 01:14 DEBUG  WindowsBackend: 7z=C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\bin\7z.exe
01-22 01:14 DEBUG  CommonBackend: Fetching basic info...
01-22 01:14 DEBUG  CommonBackend: original_exe=C:\Users\Vartok\Downloads\wubi.exe
01-22 01:14 DEBUG  CommonBackend: platform=win32
01-22 01:14 DEBUG  CommonBackend: osname=nt
01-22 01:14 DEBUG  CommonBackend: language=en_US
01-22 01:14 DEBUG  CommonBackend: encoding=cp1252
01-22 01:14 DEBUG  WindowsBackend: arch=amd64
01-22 01:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\data\isolist.ini
01-22 01:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-22 01:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-22 01:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-22 01:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-22 01:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-22 01:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-22 01:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-22 01:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-22 01:14 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-22 01:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-22 01:14 DEBUG  WindowsBackend: Fetching host info...
01-22 01:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-22 01:14 DEBUG  WindowsBackend: windows version=vista
01-22 01:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-22 01:14 DEBUG  WindowsBackend: windows_sp=None
01-22 01:14 DEBUG  WindowsBackend: windows_build=7600
01-22 01:14 DEBUG  WindowsBackend: gmt=-6
01-22 01:14 DEBUG  WindowsBackend: country=US
01-22 01:14 DEBUG  WindowsBackend: timezone=America/Chicago
01-22 01:14 DEBUG  WindowsBackend: windows_username=Vartok
01-22 01:14 DEBUG  WindowsBackend: user_full_name=Vartok
01-22 01:14 DEBUG  WindowsBackend: user_directory=C:\Users\Vartok
01-22 01:14 DEBUG  WindowsBackend: windows_language_code=1033
01-22 01:14 DEBUG  WindowsBackend: windows_language=English
01-22 01:14 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
01-22 01:14 DEBUG  WindowsBackend: bootloader=vista
01-22 01:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 15905.40625 mb free ntfs)
01-22 01:14 DEBUG  WindowsBackend: drive=Drive(C: hd 15905.40625 mb free ntfs)
01-22 01:14 DEBUG  WindowsBackend: drive=Drive(D: hd 13585.1132813 mb free ntfs)
01-22 01:14 DEBUG  WindowsBackend: drive=Drive(E: hd 134708.375 mb free ntfs)
01-22 01:14 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-22 01:14 DEBUG  WindowsBackend: drive=Drive(J: removable 5.27734375 mb free fat32)
01-22 01:14 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
01-22 01:14 DEBUG  WindowsBackend: uninstaller_path=None
01-22 01:14 DEBUG  WindowsBackend: previous_target_dir=None
01-22 01:14 DEBUG  WindowsBackend: previous_distro_name=None
01-22 01:14 DEBUG  WindowsBackend: keyboard_id=67699721
01-22 01:14 DEBUG  WindowsBackend: keyboard_layout=us
01-22 01:14 DEBUG  WindowsBackend: keyboard_variant=
01-22 01:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-22 01:14 DEBUG  CommonBackend: locale=en_US.UTF-8
01-22 01:14 DEBUG  WindowsBackend: total_memory_mb=4094.3046875
01-22 01:14 DEBUG  CommonBackend: Searching ISOs on USB devices
01-22 01:14 DEBUG  CommonBackend: Searching for local CDs
01-22 01:14 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp is a valid Ubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp is a valid Ubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp is a valid Ubuntu Netbook Remix CD
01-22 01:14 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp is a valid Kubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp is a valid Kubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp is a valid Kubuntu Netbook CD
01-22 01:14 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp is a valid Xubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp is a valid Xubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp is a valid Mythbuntu CD
01-22 01:14 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp is a valid Mythbuntu CD
01-22 01:14 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
01-22 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-22 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
01-22 01:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
01-22 01:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 01:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 01:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
01-22 01:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
01-22 01:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 01:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 01:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook Remix CD
01-22 01:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
01-22 01:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
01-22 01:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
01-22 01:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
01-22 01:14 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:14 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Netbook Remix CD
01-22 01:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu Netbook CD
01-22 01:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
01-22 01:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
01-22 01:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:15 INFO   root: Running the installer...
01-22 01:15 DEBUG  WindowsFrontend: __init__...
01-22 01:15 DEBUG  WindowsFrontend: on_init...
01-22 01:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\translations, languages=['en_US', 'en']
01-22 01:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\translations, languages=['en_US', 'en']
01-22 01:15 INFO   root: === wubi 9.10ubuntu1 rev160 ===
01-22 01:15 DEBUG  root: Logfile is c:\users\vartok\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
01-22 01:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Vartok\\Downloads\\wubi.exe"']
01-22 01:15 DEBUG  CommonBackend: data_dir=C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\data
01-22 01:15 DEBUG  WindowsBackend: 7z=C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\bin\7z.exe
01-22 01:15 DEBUG  CommonBackend: Fetching basic info...
01-22 01:15 DEBUG  CommonBackend: original_exe=C:\Users\Vartok\Downloads\wubi.exe
01-22 01:15 DEBUG  CommonBackend: platform=win32
01-22 01:15 DEBUG  CommonBackend: osname=nt
01-22 01:15 DEBUG  CommonBackend: language=en_US
01-22 01:15 DEBUG  CommonBackend: encoding=cp1252
01-22 01:15 DEBUG  WindowsBackend: arch=amd64
01-22 01:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\data\isolist.ini
01-22 01:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-22 01:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-22 01:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-22 01:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-22 01:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-22 01:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-22 01:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-22 01:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-22 01:15 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-22 01:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-22 01:15 DEBUG  WindowsBackend: Fetching host info...
01-22 01:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-22 01:15 DEBUG  WindowsBackend: windows version=vista
01-22 01:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-22 01:15 DEBUG  WindowsBackend: windows_sp=None
01-22 01:15 DEBUG  WindowsBackend: windows_build=7600
01-22 01:15 DEBUG  WindowsBackend: gmt=-6
01-22 01:15 DEBUG  WindowsBackend: country=US
01-22 01:15 DEBUG  WindowsBackend: timezone=America/Chicago
01-22 01:15 DEBUG  WindowsBackend: windows_username=Vartok
01-22 01:15 DEBUG  WindowsBackend: user_full_name=Vartok
01-22 01:15 DEBUG  WindowsBackend: user_directory=C:\Users\Vartok
01-22 01:15 DEBUG  WindowsBackend: windows_language_code=1033
01-22 01:15 DEBUG  WindowsBackend: windows_language=English
01-22 01:15 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
01-22 01:15 DEBUG  WindowsBackend: bootloader=vista
01-22 01:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 15898.5039063 mb free ntfs)
01-22 01:15 DEBUG  WindowsBackend: drive=Drive(C: hd 15898.5039063 mb free ntfs)
01-22 01:15 DEBUG  WindowsBackend: drive=Drive(D: hd 13585.1132813 mb free ntfs)
01-22 01:15 DEBUG  WindowsBackend: drive=Drive(E: hd 134708.375 mb free ntfs)
01-22 01:15 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-22 01:15 DEBUG  WindowsBackend: drive=Drive(J: removable 5.27734375 mb free fat32)
01-22 01:15 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
01-22 01:15 DEBUG  WindowsBackend: uninstaller_path=None
01-22 01:15 DEBUG  WindowsBackend: previous_target_dir=None
01-22 01:15 DEBUG  WindowsBackend: previous_distro_name=None
01-22 01:15 DEBUG  WindowsBackend: keyboard_id=67699721
01-22 01:15 DEBUG  WindowsBackend: keyboard_layout=us
01-22 01:15 DEBUG  WindowsBackend: keyboard_variant=
01-22 01:15 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-22 01:15 DEBUG  CommonBackend: locale=en_US.UTF-8
01-22 01:15 DEBUG  WindowsBackend: total_memory_mb=4094.3046875
01-22 01:15 DEBUG  CommonBackend: Searching ISOs on USB devices
01-22 01:15 DEBUG  CommonBackend: Searching for local CDs
01-22 01:15 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp is a valid Ubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp is a valid Ubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp is a valid Ubuntu Netbook Remix CD
01-22 01:15 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp is a valid Kubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp is a valid Kubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp is a valid Kubuntu Netbook CD
01-22 01:15 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp is a valid Xubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp is a valid Xubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp is a valid Mythbuntu CD
01-22 01:15 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp is a valid Mythbuntu CD
01-22 01:15 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
01-22 01:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-22 01:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 01:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 01:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
01-22 01:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
01-22 01:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 01:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 01:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
01-22 01:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
01-22 01:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 01:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 01:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook Remix CD
01-22 01:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
01-22 01:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
01-22 01:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
01-22 01:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
01-22 01:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Netbook Remix CD
01-22 01:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:15 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
01-22 01:16 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=14000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=vartok
01-22 01:16 INFO   root: Received settings
01-22 01:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\translations, languages=['en_US', 'en']
01-22 01:16 DEBUG  TaskList: # Running tasklist...
01-22 01:16 DEBUG  TaskList: ## Running select_target_dir...
01-22 01:16 INFO   WindowsBackend: Installing into E:\ubuntu
01-22 01:16 DEBUG  TaskList: ## Finished select_target_dir
01-22 01:16 DEBUG  TaskList: ## Running create_dir_structure...
01-22 01:16 DEBUG  CommonBackend: Creating dir E:\ubuntu
01-22 01:16 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
01-22 01:16 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
01-22 01:16 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
01-22 01:16 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
01-22 01:16 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
01-22 01:16 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
01-22 01:16 DEBUG  TaskList: ## Finished create_dir_structure
01-22 01:16 DEBUG  TaskList: ## Running uncompress_target_dir...
01-22 01:16 DEBUG  TaskList: ## Finished uncompress_target_dir
01-22 01:16 DEBUG  TaskList: ## Running create_uninstaller...
01-22 01:16 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Vartok\Downloads\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
01-22 01:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
01-22 01:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
01-22 01:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-22 01:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
01-22 01:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
01-22 01:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-22 01:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-22 01:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-22 01:16 DEBUG  TaskList: ## Finished create_uninstaller
01-22 01:16 DEBUG  TaskList: ## Running copy_installation_files...
01-22 01:16 DEBUG  WindowsBackend: Copying C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
01-22 01:16 DEBUG  WindowsBackend: Copying C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\winboot -> E:\ubuntu\winboot
01-22 01:16 DEBUG  WindowsBackend: Copying C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
01-22 01:16 DEBUG  TaskList: ## Finished copy_installation_files
01-22 01:16 DEBUG  TaskList: ## Running get_iso...
01-22 01:16 DEBUG  CommonBackend: Searching for local CD
01-22 01:16 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp is a valid Ubuntu CD
01-22 01:16 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylA2B4.tmp\casper\filesystem.squashfs
01-22 01:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 01:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 01:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 01:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 01:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 01:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 01:16 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-22 01:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 01:17 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
01-22 01:17 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:17 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
01-22 01:17 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:17 DEBUG  CommonBackend: Searching for local ISO
01-22 01:17 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-22 01:17 DEBUG  TaskList: New task get_metalink
01-22 01:17 DEBUG  TaskList: ### Running get_metalink...
01-22 01:17 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink) > E:\ubuntu\install
01-22 01:17 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:17 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu Netbook CD
01-22 01:17 DEBUG  downloader: Download start filename=E:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
01-22 01:17 DEBUG  downloader: download finished (read 26651 bytes)
01-22 01:17 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > E:\ubuntu\install
01-22 01:17 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
01-22 01:17 DEBUG  downloader: download finished (read 562 bytes)
01-22 01:17 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > E:\ubuntu\install
01-22 01:17 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
01-22 01:17 DEBUG  downloader: download finished (read 189 bytes)
01-22 01:17 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
01-22 01:17 INFO   saplog: Checking block bindings..
01-22 01:17 INFO   saplog: Key verified successfully.
01-22 01:17 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

01-22 01:17 DEBUG  TaskList: ### Finished get_metalink
01-22 01:17 DEBUG  TaskList: New task download
01-22 01:17 DEBUG  TaskList: ### Running download...
01-22 01:17 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent) > E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
01-22 01:17 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:17 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
01-22 01:17 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:17 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
01-22 01:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:18 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
01-22 01:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 01:38 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
01-22 02:01 DEBUG  TaskList: ### Finished download
01-22 02:01 DEBUG  TaskList: New task check_iso
01-22 02:01 DEBUG  TaskList: ### Running check_iso...
01-22 02:01 DEBUG  CommonBackend: Checking E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
01-22 02:01 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
01-22 02:01 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
01-22 02:01 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
01-22 02:01 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
01-22 02:01 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
01-22 02:01 DEBUG  TaskList: New task get_file_md5
01-22 02:01 DEBUG  TaskList: #### Running get_file_md5...
01-22 02:01 DEBUG  TaskList: #### Finished get_file_md5
01-22 02:01 DEBUG  TaskList: ### Finished check_iso
01-22 02:01 DEBUG  TaskList: ## Finished get_iso
01-22 02:01 DEBUG  TaskList: ## Running extract_kernel...
01-22 02:01 DEBUG  CommonBackend: Extracting files from ISO E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
01-22 02:01 DEBUG  WindowsBackend:   extracting md5sum.txt from E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
01-22 02:01 DEBUG  WindowsBackend:   extracting casper\vmlinuz from E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
01-22 02:01 DEBUG  WindowsBackend:   extracting casper\initrd.lz from E:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
01-22 02:01 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
01-22 02:01 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\vmlinuz
01-22 02:01 DEBUG  CommonBackend:   E:\ubuntu\install\boot\vmlinuz md5 = f2bec09da1b46a21c0e6cc3192ca2e4f == f2bec09da1b46a21c0e6cc3192ca2e4f
01-22 02:01 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\initrd.lz
01-22 02:01 DEBUG  CommonBackend:   E:\ubuntu\install\boot\initrd.lz md5 = e09f7d0e9500f67156730ad6093ce225 == e09f7d0e9500f67156730ad6093ce225
01-22 02:01 DEBUG  TaskList: ## Finished extract_kernel
01-22 02:01 DEBUG  TaskList: ## Running choose_disk_sizes...
01-22 02:01 DEBUG  WindowsBackend: total size=14000
  root=13744
  swap=256
  home=0
  usr=0
01-22 02:01 DEBUG  TaskList: ## Finished choose_disk_sizes
01-22 02:01 DEBUG  TaskList: ## Running create_preseed...
01-22 02:01 DEBUG  TaskList: ## Finished create_preseed
01-22 02:01 DEBUG  TaskList: ## Running modify_bootloader...
01-22 02:01 DEBUG  TaskList: New task modify_bcd
01-22 02:01 DEBUG  TaskList: ### Running modify_bcd...
01-22 02:01 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 15905.40625 mb free ntfs)
01-22 02:01 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {4229e6a8-a68b-11de-9364-b54f86b5dd01} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.The request is not supported.
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 629, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {4229e6a8-a68b-11de-9364-b54f86b5dd01} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.The request is not supported.
>>stdout=
01-22 02:01 DEBUG  TaskList: # Cancelling tasklist
01-22 02:01 DEBUG  TaskList: New task modify_bcd
01-22 02:01 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {4229e6a8-a68b-11de-9364-b54f86b5dd01} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.The request is not supported.
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 629, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {4229e6a8-a68b-11de-9364-b54f86b5dd01} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.The request is not supported.
>>stdout=
01-22 02:01 DEBUG  TaskList: New task modify_bcd
01-22 02:01 DEBUG  TaskList: New task modify_bcd
01-22 02:01 DEBUG  TaskList: New task modify_bcd
01-22 02:01 DEBUG  TaskList: ## Finished modify_bootloader
01-22 02:01 DEBUG  TaskList: # Finished tasklist
01-22 02:02 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 02:02 INFO   root: Running the installer...
01-22 02:02 DEBUG  WindowsFrontend: __init__...
01-22 02:02 DEBUG  WindowsFrontend: on_init...
01-22 02:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\translations, languages=['en_US', 'en']
01-22 02:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\translations, languages=['en_US', 'en']
01-22 02:03 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=vartok
01-22 02:03 INFO   root: Received settings
01-22 02:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl424D.tmp\translations, languages=['en_US', 'en']
01-22 02:03 DEBUG  TaskList: # Running tasklist...
01-22 02:03 DEBUG  TaskList: ## Running select_target_dir...
01-22 02:03 ERROR  TaskList: Cannot install into E:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 83, in select_target_dir
Exception: Cannot install into E:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
01-22 02:03 DEBUG  TaskList: # Cancelling tasklist
01-22 02:03 DEBUG  TaskList: # Finished tasklist
01-22 02:03 ERROR  root: Cannot install into E:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 83, in select_target_dir
Exception: Cannot install into E:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
01-22 02:07 INFO   root: === wubi 9.10ubuntu1 rev160 ===
01-22 02:07 DEBUG  root: Logfile is c:\users\vartok\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
01-22 02:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubuntu\\uninstall-wubi.exe"']
01-22 02:07 DEBUG  CommonBackend: data_dir=C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\data
01-22 02:07 DEBUG  WindowsBackend: 7z=C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\bin\7z.exe
01-22 02:07 DEBUG  CommonBackend: Fetching basic info...
01-22 02:07 DEBUG  CommonBackend: original_exe=E:\ubuntu\uninstall-wubi.exe
01-22 02:07 DEBUG  CommonBackend: platform=win32
01-22 02:07 DEBUG  CommonBackend: osname=nt
01-22 02:07 DEBUG  CommonBackend: language=en_US
01-22 02:07 DEBUG  CommonBackend: encoding=cp1252
01-22 02:07 DEBUG  WindowsBackend: arch=amd64
01-22 02:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\data\isolist.ini
01-22 02:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-22 02:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-22 02:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-22 02:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-22 02:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-22 02:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-22 02:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-22 02:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-22 02:07 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-22 02:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-22 02:07 DEBUG  WindowsBackend: Fetching host info...
01-22 02:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-22 02:07 DEBUG  WindowsBackend: windows version=vista
01-22 02:07 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-22 02:07 DEBUG  WindowsBackend: windows_sp=None
01-22 02:07 DEBUG  WindowsBackend: windows_build=7600
01-22 02:07 DEBUG  WindowsBackend: gmt=-6
01-22 02:07 DEBUG  WindowsBackend: country=US
01-22 02:07 DEBUG  WindowsBackend: timezone=America/Chicago
01-22 02:07 DEBUG  WindowsBackend: windows_username=Vartok
01-22 02:07 DEBUG  WindowsBackend: user_full_name=Vartok
01-22 02:07 DEBUG  WindowsBackend: user_directory=C:\Users\Vartok
01-22 02:07 DEBUG  WindowsBackend: windows_language_code=1033
01-22 02:07 DEBUG  WindowsBackend: windows_language=English
01-22 02:07 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
01-22 02:07 DEBUG  WindowsBackend: bootloader=vista
01-22 02:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 21155.6679688 mb free ntfs)
01-22 02:07 DEBUG  WindowsBackend: drive=Drive(C: hd 21155.6640625 mb free ntfs)
01-22 02:07 DEBUG  WindowsBackend: drive=Drive(D: hd 13585.1992188 mb free ntfs)
01-22 02:07 DEBUG  WindowsBackend: drive=Drive(E: hd 134658.652344 mb free ntfs)
01-22 02:07 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-22 02:07 DEBUG  WindowsBackend: drive=Drive(J: removable 5.27734375 mb free fat32)
01-22 02:07 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
01-22 02:07 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
01-22 02:07 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
01-22 02:07 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-22 02:07 DEBUG  WindowsBackend: keyboard_id=67699721
01-22 02:07 DEBUG  WindowsBackend: keyboard_layout=us
01-22 02:07 DEBUG  WindowsBackend: keyboard_variant=
01-22 02:07 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-22 02:07 DEBUG  CommonBackend: locale=en_US.UTF-8
01-22 02:07 DEBUG  WindowsBackend: total_memory_mb=4094.3046875
01-22 02:07 DEBUG  CommonBackend: Searching ISOs on USB devices
01-22 02:07 DEBUG  CommonBackend: Searching for local CDs
01-22 02:07 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp is a valid Ubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp is a valid Ubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp is a valid Ubuntu Netbook Remix CD
01-22 02:07 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp is a valid Kubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp is a valid Kubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp is a valid Kubuntu Netbook CD
01-22 02:07 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp is a valid Xubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp is a valid Xubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp is a valid Mythbuntu CD
01-22 02:07 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp is a valid Mythbuntu CD
01-22 02:07 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
01-22 02:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-22 02:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 02:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 02:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
01-22 02:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
01-22 02:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 02:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 02:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
01-22 02:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
01-22 02:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 02:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 02:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook Remix CD
01-22 02:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
01-22 02:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
01-22 02:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
01-22 02:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Netbook Remix CD
01-22 02:07 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu Netbook CD
01-22 02:07 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
01-22 02:07 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
01-22 02:07 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 02:07 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
01-22 02:07 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
01-22 02:07 INFO   root: Running the uninstaller...
01-22 02:07 INFO   CommonBackend: This is the uninstaller running
01-22 02:07 DEBUG  WindowsFrontend: __init__...
01-22 02:07 DEBUG  WindowsFrontend: on_init...
01-22 02:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\translations, languages=['en_US', 'en']
01-22 02:07 INFO   root: Received settings
01-22 02:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\translations, languages=['en_US', 'en']
01-22 02:07 DEBUG  TaskList: # Running tasklist...
01-22 02:07 DEBUG  TaskList: ## Running Backup ISO...
01-22 02:07 DEBUG  TaskList: ## Finished Backup ISO
01-22 02:07 DEBUG  TaskList: ## Running Remove bootloader entry...
01-22 02:07 DEBUG  WindowsBackend: Could not find bcd id
01-22 02:07 DEBUG  WindowsBackend: undo_bootini C:
01-22 02:07 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 21155.6640625 mb free ntfs)
01-22 02:07 DEBUG  WindowsBackend: undo_bootini D:
01-22 02:07 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 13585.1992188 mb free ntfs)
01-22 02:07 DEBUG  WindowsBackend: undo_bootini E:
01-22 02:07 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 134658.652344 mb free ntfs)
01-22 02:07 DEBUG  WindowsBackend: undo_bootini J:
01-22 02:07 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 5.27734375 mb free fat32)
01-22 02:07 DEBUG  WindowsBackend: undo_bootini K:
01-22 02:07 DEBUG  WindowsBackend: undo_configsys Drive(K: removable 0.0 mb free )
01-22 02:07 DEBUG  TaskList: ## Finished Remove bootloader entry
01-22 02:07 DEBUG  TaskList: ## Running Remove target dir...
01-22 02:07 DEBUG  CommonBackend: Deleting E:\ubuntu
01-22 02:07 DEBUG  TaskList: ## Finished Remove target dir
01-22 02:07 DEBUG  TaskList: ## Running Remove registry key...
01-22 02:07 DEBUG  TaskList: ## Finished Remove registry key
01-22 02:07 DEBUG  TaskList: # Finished tasklist
01-22 02:07 INFO   root: Almost finished uninstalling
01-22 02:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pylD47D.tmp\translations, languages=['en_US', 'en']
01-22 02:07 INFO   root: Finished uninstallation
01-22 02:07 DEBUG  root: application.quit
01-22 02:07 DEBUG  WindowsFrontend: frontend.quit
01-22 02:07 DEBUG  WindowsFrontend: frontend.on_quit
01-22 02:07 DEBUG  root: application.on_quit
01-22 02:07 INFO   root: sys.exit
01-22 02:10 INFO   root: === wubi 9.10ubuntu1 rev160 ===
01-22 02:10 DEBUG  root: Logfile is c:\users\vartok\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
01-22 02:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"', '--cdmenu']
01-22 02:10 DEBUG  CommonBackend: data_dir=C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\data
01-22 02:10 DEBUG  WindowsBackend: 7z=C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\bin\7z.exe
01-22 02:10 DEBUG  CommonBackend: Fetching basic info...
01-22 02:10 DEBUG  CommonBackend: original_exe=H:\wubi.exe
01-22 02:10 DEBUG  CommonBackend: platform=win32
01-22 02:10 DEBUG  CommonBackend: osname=nt
01-22 02:10 DEBUG  CommonBackend: language=en_US
01-22 02:10 DEBUG  CommonBackend: encoding=cp1252
01-22 02:10 DEBUG  WindowsBackend: arch=amd64
01-22 02:10 DEBUG  CommonBackend: Parsing isolist=C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\data\isolist.ini
01-22 02:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-22 02:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-22 02:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-22 02:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-22 02:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-22 02:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-22 02:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-22 02:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-22 02:10 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-22 02:10 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-22 02:10 DEBUG  WindowsBackend: Fetching host info...
01-22 02:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-22 02:10 DEBUG  WindowsBackend: windows version=vista
01-22 02:10 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-22 02:10 DEBUG  WindowsBackend: windows_sp=None
01-22 02:10 DEBUG  WindowsBackend: windows_build=7600
01-22 02:10 DEBUG  WindowsBackend: gmt=-6
01-22 02:10 DEBUG  WindowsBackend: country=US
01-22 02:10 DEBUG  WindowsBackend: timezone=America/Chicago
01-22 02:10 DEBUG  WindowsBackend: windows_username=Vartok
01-22 02:10 DEBUG  WindowsBackend: user_full_name=Vartok
01-22 02:10 DEBUG  WindowsBackend: user_directory=C:\Users\Vartok
01-22 02:10 DEBUG  WindowsBackend: windows_language_code=1033
01-22 02:10 DEBUG  WindowsBackend: windows_language=English
01-22 02:10 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
01-22 02:10 DEBUG  WindowsBackend: bootloader=vista
01-22 02:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 21151.453125 mb free ntfs)
01-22 02:10 DEBUG  WindowsBackend: drive=Drive(C: hd 21151.4492188 mb free ntfs)
01-22 02:10 DEBUG  WindowsBackend: drive=Drive(D: hd 13585.1992188 mb free ntfs)
01-22 02:10 DEBUG  WindowsBackend: drive=Drive(E: hd 135360.351563 mb free ntfs)
01-22 02:10 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-22 02:10 DEBUG  WindowsBackend: drive=Drive(G: hd 78438.8515625 mb free ntfs)
01-22 02:10 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
01-22 02:10 DEBUG  WindowsBackend: drive=Drive(J: removable 5.27734375 mb free fat32)
01-22 02:10 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
01-22 02:10 DEBUG  WindowsBackend: uninstaller_path=None
01-22 02:10 DEBUG  WindowsBackend: previous_target_dir=None
01-22 02:10 DEBUG  WindowsBackend: previous_distro_name=None
01-22 02:10 DEBUG  WindowsBackend: keyboard_id=67699721
01-22 02:10 DEBUG  WindowsBackend: keyboard_layout=us
01-22 02:10 DEBUG  WindowsBackend: keyboard_variant=
01-22 02:10 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-22 02:10 DEBUG  CommonBackend: locale=en_US.UTF-8
01-22 02:10 DEBUG  WindowsBackend: total_memory_mb=4094.3046875
01-22 02:10 DEBUG  CommonBackend: Searching ISOs on USB devices
01-22 02:10 DEBUG  CommonBackend: Searching for local CDs
01-22 02:10 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp is a valid Ubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp is a valid Ubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp is a valid Ubuntu Netbook Remix CD
01-22 02:10 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp is a valid Kubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp is a valid Kubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp is a valid Kubuntu Netbook CD
01-22 02:10 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp is a valid Xubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp is a valid Xubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp is a valid Mythbuntu CD
01-22 02:10 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp is a valid Mythbuntu CD
01-22 02:10 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
01-22 02:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-22 02:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 02:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 02:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
01-22 02:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
01-22 02:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 02:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 02:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
01-22 02:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
01-22 02:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 02:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 02:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
01-22 02:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
01-22 02:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-22 02:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-22 02:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-22 02:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-22 02:10 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
01-22 02:10 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
01-22 02:10 INFO   Distro: Found a valid CD for Ubuntu: H:\
01-22 02:10 INFO   root: Running the CD menu...
01-22 02:10 DEBUG  WindowsFrontend: __init__...
01-22 02:10 DEBUG  WindowsFrontend: on_init...
01-22 02:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\translations, languages=['en_US', 'en']
01-22 02:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\translations, languages=['en_US', 'en']
01-22 02:10 INFO   root: CD menu finished
01-22 02:10 INFO   root: Running the installer...
01-22 02:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\translations, languages=['en_US', 'en']
01-22 02:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl8084.tmp\translations, languages=['en_US', 'en']
01-22 02:13 INFO   WindowsFrontend: Operation cancelled
01-22 02:13 DEBUG  WindowsFrontend: frontend.quit
01-22 02:13 DEBUG  WindowsFrontend: frontend.on_quit
01-22 02:13 DEBUG  root: application.on_quit
01-22 02:13 INFO   root: sys.exit
01-22 02:18 INFO   root: === wubi 9.10ubuntu1 rev160 ===
01-22 02:18 DEBUG  root: Logfile is c:\users\vartok\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
01-22 02:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"', '--cdmenu']
01-22 02:18 DEBUG  CommonBackend: data_dir=C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\data
01-22 02:18 DEBUG  WindowsBackend: 7z=C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\bin\7z.exe
01-22 02:18 DEBUG  CommonBackend: Fetching basic info...
01-22 02:18 DEBUG  CommonBackend: original_exe=H:\wubi.exe
01-22 02:18 DEBUG  CommonBackend: platform=win32
01-22 02:18 DEBUG  CommonBackend: osname=nt
01-22 02:18 DEBUG  CommonBackend: language=en_US
01-22 02:18 DEBUG  CommonBackend: encoding=cp1252
01-22 02:18 DEBUG  WindowsBackend: arch=amd64
01-22 02:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\data\isolist.ini
01-22 02:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-22 02:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-22 02:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-22 02:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-22 02:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-22 02:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-22 02:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-22 02:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-22 02:18 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-22 02:18 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-22 02:18 DEBUG  WindowsBackend: Fetching host info...
01-22 02:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-22 02:18 DEBUG  WindowsBackend: windows version=vista
01-22 02:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-22 02:18 DEBUG  WindowsBackend: windows_sp=None
01-22 02:18 DEBUG  WindowsBackend: windows_build=7600
01-22 02:18 DEBUG  WindowsBackend: gmt=-6
01-22 02:18 DEBUG  WindowsBackend: country=US
01-22 02:18 DEBUG  WindowsBackend: timezone=America/Chicago
01-22 02:18 DEBUG  WindowsBackend: windows_username=Vartok
01-22 02:18 DEBUG  WindowsBackend: user_full_name=Vartok
01-22 02:18 DEBUG  WindowsBackend: user_directory=C:\Users\Vartok
01-22 02:18 DEBUG  WindowsBackend: windows_language_code=1033
01-22 02:18 DEBUG  WindowsBackend: windows_language=English
01-22 02:18 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
01-22 02:18 DEBUG  WindowsBackend: bootloader=vista
01-22 02:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 21147.1640625 mb free ntfs)
01-22 02:18 DEBUG  WindowsBackend: drive=Drive(C: hd 21147.1640625 mb free ntfs)
01-22 02:18 DEBUG  WindowsBackend: drive=Drive(D: hd 13585.1992188 mb free ntfs)
01-22 02:18 DEBUG  WindowsBackend: drive=Drive(E: hd 135360.351563 mb free ntfs)
01-22 02:18 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-22 02:18 DEBUG  WindowsBackend: drive=Drive(G: hd 31653.3046875 mb free ntfs)
01-22 02:18 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
01-22 02:18 DEBUG  WindowsBackend: drive=Drive(I: hd 46694.84375 mb free ntfs)
01-22 02:18 DEBUG  WindowsBackend: drive=Drive(J: removable 5.27734375 mb free fat32)
01-22 02:18 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
01-22 02:18 DEBUG  WindowsBackend: uninstaller_path=None
01-22 02:18 DEBUG  WindowsBackend: previous_target_dir=None
01-22 02:18 DEBUG  WindowsBackend: previous_distro_name=None
01-22 02:18 DEBUG  WindowsBackend: keyboard_id=67699721
01-22 02:18 DEBUG  WindowsBackend: keyboard_layout=us
01-22 02:18 DEBUG  WindowsBackend: keyboard_variant=
01-22 02:18 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-22 02:18 DEBUG  CommonBackend: locale=en_US.UTF-8
01-22 02:18 DEBUG  WindowsBackend: total_memory_mb=4094.3046875
01-22 02:18 DEBUG  CommonBackend: Searching ISOs on USB devices
01-22 02:18 DEBUG  CommonBackend: Searching for local CDs
01-22 02:18 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp is a valid Ubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp is a valid Ubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp is a valid Ubuntu Netbook Remix CD
01-22 02:18 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp is a valid Kubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp is a valid Kubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp is a valid Kubuntu Netbook CD
01-22 02:18 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp is a valid Xubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp is a valid Xubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp is a valid Mythbuntu CD
01-22 02:18 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp is a valid Mythbuntu CD
01-22 02:18 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
01-22 02:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-22 02:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 02:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-22 02:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
01-22 02:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
01-22 02:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 02:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-22 02:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
01-22 02:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
01-22 02:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 02:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-22 02:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
01-22 02:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
01-22 02:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-22 02:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-22 02:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-22 02:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-22 02:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-22 02:18 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
01-22 02:18 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
01-22 02:18 INFO   Distro: Found a valid CD for Ubuntu: H:\
01-22 02:18 INFO   root: Running the CD menu...
01-22 02:18 DEBUG  WindowsFrontend: __init__...
01-22 02:18 DEBUG  WindowsFrontend: on_init...
01-22 02:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\translations, languages=['en_US', 'en']
01-22 02:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\translations, languages=['en_US', 'en']
01-22 02:18 INFO   root: CD menu finished
01-22 02:18 INFO   root: Running the installer...
01-22 02:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\translations, languages=['en_US', 'en']
01-22 02:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\translations, languages=['en_US', 'en']
01-22 02:19 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=vartok
01-22 02:19 INFO   root: Received settings
01-22 02:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\translations, languages=['en_US', 'en']
01-22 02:19 DEBUG  TaskList: # Running tasklist...
01-22 02:19 DEBUG  TaskList: ## Running select_target_dir...
01-22 02:19 INFO   WindowsBackend: Installing into G:\ubuntu
01-22 02:19 DEBUG  TaskList: ## Finished select_target_dir
01-22 02:19 DEBUG  TaskList: ## Running create_dir_structure...
01-22 02:19 DEBUG  CommonBackend: Creating dir G:\ubuntu
01-22 02:19 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
01-22 02:19 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
01-22 02:19 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
01-22 02:19 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
01-22 02:19 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
01-22 02:19 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
01-22 02:19 DEBUG  TaskList: ## Finished create_dir_structure
01-22 02:19 DEBUG  TaskList: ## Running uncompress_target_dir...
01-22 02:19 DEBUG  TaskList: ## Finished uncompress_target_dir
01-22 02:19 DEBUG  TaskList: ## Running create_uninstaller...
01-22 02:19 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
01-22 02:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
01-22 02:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
01-22 02:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-22 02:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
01-22 02:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
01-22 02:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-22 02:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-22 02:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-22 02:19 DEBUG  TaskList: ## Finished create_uninstaller
01-22 02:19 DEBUG  TaskList: ## Running copy_installation_files...
01-22 02:19 DEBUG  WindowsBackend: Copying C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
01-22 02:19 DEBUG  WindowsBackend: Copying C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\winboot -> G:\ubuntu\winboot
01-22 02:19 DEBUG  WindowsBackend: Copying C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
01-22 02:19 DEBUG  TaskList: ## Finished copy_installation_files
01-22 02:19 DEBUG  TaskList: ## Running get_iso...
01-22 02:19 DEBUG  TaskList: New task copy_file
01-22 02:19 DEBUG  TaskList: ### Running copy_file...
01-22 02:19 DEBUG  TaskList: ### Finished copy_file
01-22 02:19 DEBUG  TaskList: New task check_iso
01-22 02:19 DEBUG  TaskList: ### Running check_iso...
01-22 02:19 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
01-22 02:19 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
01-22 02:19 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
01-22 02:19 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
01-22 02:19 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
01-22 02:19 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\installation.iso
01-22 02:19 DEBUG  TaskList: New task get_metalink
01-22 02:19 DEBUG  TaskList: #### Running get_metalink...
01-22 02:19 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink) > G:\ubuntu\install
01-22 02:19 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-9.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.metalink, basename=ubuntu-9.10-desktop-amd64.metalink, length=26651, text=None
01-22 02:19 DEBUG  downloader: download finished (read 26651 bytes)
01-22 02:19 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/9.10/MD5SUMS-metalink) > G:\ubuntu\install
01-22 02:19 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=562, text=None
01-22 02:19 DEBUG  downloader: download finished (read 562 bytes)
01-22 02:19 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg) > G:\ubuntu\install
01-22 02:19 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
01-22 02:19 DEBUG  downloader: download finished (read 189 bytes)
01-22 02:19 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
01-22 02:19 INFO   saplog: Checking block bindings..
01-22 02:19 INFO   saplog: Key verified successfully.
01-22 02:19 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

01-22 02:19 DEBUG  TaskList: #### Finished get_metalink
01-22 02:19 DEBUG  TaskList: New task get_file_md5
01-22 02:19 DEBUG  TaskList: #### Running get_file_md5...
01-22 02:19 DEBUG  TaskList: #### Finished get_file_md5
01-22 02:19 DEBUG  TaskList: ### Finished check_iso
01-22 02:19 DEBUG  TaskList: ## Finished get_iso
01-22 02:19 DEBUG  TaskList: ## Running extract_kernel...
01-22 02:19 DEBUG  CommonBackend: Copying files from CD H:\
01-22 02:19 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
01-22 02:19 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
01-22 02:19 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = f2bec09da1b46a21c0e6cc3192ca2e4f == f2bec09da1b46a21c0e6cc3192ca2e4f
01-22 02:19 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
01-22 02:19 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = e09f7d0e9500f67156730ad6093ce225 == e09f7d0e9500f67156730ad6093ce225
01-22 02:19 DEBUG  TaskList: ## Finished extract_kernel
01-22 02:19 DEBUG  TaskList: ## Running choose_disk_sizes...
01-22 02:19 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
01-22 02:19 DEBUG  TaskList: ## Finished choose_disk_sizes
01-22 02:19 DEBUG  TaskList: ## Running create_preseed...
01-22 02:19 DEBUG  TaskList: ## Finished create_preseed
01-22 02:19 DEBUG  TaskList: ## Running modify_bootloader...
01-22 02:19 DEBUG  TaskList: New task modify_bcd
01-22 02:19 DEBUG  TaskList: ### Running modify_bcd...
01-22 02:19 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 21147.1640625 mb free ntfs)
01-22 02:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {4229e6a9-a68b-11de-9364-b54f86b5dd01}
01-22 02:19 DEBUG  TaskList: ### Finished modify_bcd
01-22 02:19 DEBUG  TaskList: New task modify_bcd
01-22 02:19 DEBUG  TaskList: ### Running modify_bcd...
01-22 02:19 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 13585.1992188 mb free ntfs)
01-22 02:19 DEBUG  WindowsBackend: BCD has already been modified
01-22 02:19 DEBUG  TaskList: ### Finished modify_bcd
01-22 02:19 DEBUG  TaskList: New task modify_bcd
01-22 02:19 DEBUG  TaskList: ### Running modify_bcd...
01-22 02:19 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 135360.351563 mb free ntfs)
01-22 02:19 DEBUG  WindowsBackend: BCD has already been modified
01-22 02:19 DEBUG  TaskList: ### Finished modify_bcd
01-22 02:19 DEBUG  TaskList: New task modify_bcd
01-22 02:19 DEBUG  TaskList: ### Running modify_bcd...
01-22 02:19 DEBUG  WindowsBackend: modify_bcd Drive(G: hd 31653.3046875 mb free ntfs)
01-22 02:19 DEBUG  WindowsBackend: BCD has already been modified
01-22 02:19 DEBUG  TaskList: ### Finished modify_bcd
01-22 02:19 DEBUG  TaskList: New task modify_bcd
01-22 02:19 DEBUG  TaskList: ### Running modify_bcd...
01-22 02:19 DEBUG  WindowsBackend: modify_bcd Drive(I: hd 46694.84375 mb free ntfs)
01-22 02:19 DEBUG  WindowsBackend: BCD has already been modified
01-22 02:19 DEBUG  TaskList: ### Finished modify_bcd
01-22 02:19 DEBUG  TaskList: New task modify_bcd
01-22 02:19 DEBUG  TaskList: ### Running modify_bcd...
01-22 02:19 DEBUG  WindowsBackend: modify_bcd Drive(J: removable 5.27734375 mb free fat32)
01-22 02:19 DEBUG  WindowsBackend: BCD has already been modified
01-22 02:19 DEBUG  TaskList: ### Finished modify_bcd
01-22 02:19 DEBUG  TaskList: New task modify_bcd
01-22 02:19 DEBUG  TaskList: ### Running modify_bcd...
01-22 02:19 DEBUG  WindowsBackend: modify_bcd Drive(K: removable 0.0 mb free )
01-22 02:19 DEBUG  WindowsBackend: BCD has already been modified
01-22 02:19 DEBUG  TaskList: ### Finished modify_bcd
01-22 02:19 DEBUG  TaskList: ## Finished modify_bootloader
01-22 02:19 DEBUG  TaskList: ## Running modify_grub_configuration...
01-22 02:19 DEBUG  TaskList: ## Finished modify_grub_configuration
01-22 02:19 DEBUG  TaskList: ## Running create_virtual_disks...
01-22 02:19 DEBUG  Virtualdisk:  Creating virtual disk G:\ubuntu\disks\root.disk of 29744MB
01-22 02:19 DEBUG  Virtualdisk:  Creating virtual disk G:\ubuntu\disks\swap.disk of 256MB
01-22 02:19 DEBUG  TaskList: ## Finished create_virtual_disks
01-22 02:19 DEBUG  TaskList: ## Running uncompress_files...
01-22 02:19 DEBUG  WindowsBackend: compact G:\ubuntu\install\boot /U /A /F
01-22 02:19 DEBUG  WindowsBackend: compact G:\ubuntu\install\boot\*.* /U /A /F
01-22 02:19 DEBUG  TaskList: ## Finished uncompress_files
01-22 02:19 DEBUG  TaskList: ## Running eject_cd...
01-22 02:19 DEBUG  TaskList: ## Finished eject_cd
01-22 02:19 DEBUG  TaskList: # Finished tasklist
01-22 02:19 INFO   root: Almost finished installing
01-22 02:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl22EB.tmp\translations, languages=['en_US', 'en']
01-22 02:19 INFO   root: Finished installation
01-22 02:19 INFO   root: Rebooting
01-22 02:19 DEBUG  TaskList: # Running tasklist...
01-22 02:19 DEBUG  TaskList: ## Running reboot...
01-22 02:19 DEBUG  TaskList: ## Finished reboot
01-22 02:19 DEBUG  TaskList: # Finished tasklist
01-22 02:19 DEBUG  root: application.quit
01-22 02:19 DEBUG  WindowsFrontend: frontend.quit
01-22 02:19 DEBUG  WindowsFrontend: frontend.on_quit
01-22 02:19 DEBUG  root: application.on_quit
01-22 02:19 INFO   root: sys.exit
01-26 17:00 INFO   root: === wubi 9.10ubuntu1 rev160 ===
01-26 17:00 DEBUG  root: Logfile is c:\users\vartok\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
01-26 17:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
01-26 17:00 DEBUG  CommonBackend: data_dir=C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\data
01-26 17:00 DEBUG  WindowsBackend: 7z=C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\bin\7z.exe
01-26 17:00 DEBUG  CommonBackend: Fetching basic info...
01-26 17:00 DEBUG  CommonBackend: original_exe=F:\wubi.exe
01-26 17:00 DEBUG  CommonBackend: platform=win32
01-26 17:00 DEBUG  CommonBackend: osname=nt
01-26 17:00 DEBUG  CommonBackend: language=en_US
01-26 17:00 DEBUG  CommonBackend: encoding=cp1252
01-26 17:00 DEBUG  WindowsBackend: arch=amd64
01-26 17:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\data\isolist.ini
01-26 17:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-26 17:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-26 17:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-26 17:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-26 17:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-26 17:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-26 17:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-26 17:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-26 17:00 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-26 17:00 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-26 17:00 DEBUG  WindowsBackend: Fetching host info...
01-26 17:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-26 17:00 DEBUG  WindowsBackend: windows version=vista
01-26 17:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-26 17:00 DEBUG  WindowsBackend: windows_sp=None
01-26 17:00 DEBUG  WindowsBackend: windows_build=7600
01-26 17:00 DEBUG  WindowsBackend: gmt=-6
01-26 17:00 DEBUG  WindowsBackend: country=US
01-26 17:00 DEBUG  WindowsBackend: timezone=America/Chicago
01-26 17:00 DEBUG  WindowsBackend: windows_username=Vartok
01-26 17:00 DEBUG  WindowsBackend: user_full_name=Vartok
01-26 17:00 DEBUG  WindowsBackend: user_directory=C:\Users\Vartok
01-26 17:00 DEBUG  WindowsBackend: windows_language_code=1033
01-26 17:00 DEBUG  WindowsBackend: windows_language=English
01-26 17:00 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
01-26 17:00 DEBUG  WindowsBackend: bootloader=vista
01-26 17:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 21355.9179688 mb free ntfs)
01-26 17:00 DEBUG  WindowsBackend: drive=Drive(C: hd 21355.9179688 mb free ntfs)
01-26 17:00 DEBUG  WindowsBackend: drive=Drive(D: hd 13585.1992188 mb free ntfs)
01-26 17:00 DEBUG  WindowsBackend: drive=Drive(E: hd 134611.121094 mb free ntfs)
01-26 17:00 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
01-26 17:00 DEBUG  WindowsBackend: drive=Drive(J: removable 5.27734375 mb free fat32)
01-26 17:00 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
01-26 17:00 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
01-26 17:00 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-26 17:00 DEBUG  WindowsBackend: keyboard_id=67699721
01-26 17:00 DEBUG  WindowsBackend: keyboard_layout=us
01-26 17:00 DEBUG  WindowsBackend: keyboard_variant=
01-26 17:00 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-26 17:00 DEBUG  CommonBackend: locale=en_US.UTF-8
01-26 17:00 DEBUG  WindowsBackend: total_memory_mb=4094.3046875
01-26 17:00 DEBUG  CommonBackend: Searching ISOs on USB devices
01-26 17:00 DEBUG  CommonBackend: Searching for local CDs
01-26 17:00 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp is a valid Ubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp is a valid Ubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp is a valid Ubuntu Netbook Remix CD
01-26 17:00 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp is a valid Kubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp is a valid Kubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp is a valid Kubuntu Netbook CD
01-26 17:00 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp is a valid Xubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp is a valid Xubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp is a valid Mythbuntu CD
01-26 17:00 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp is a valid Mythbuntu CD
01-26 17:00 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
01-26 17:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-26 17:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-26 17:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-26 17:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
01-26 17:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
01-26 17:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-26 17:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-26 17:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-26 17:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-26 17:00 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
01-26 17:00 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
01-26 17:00 INFO   Distro: Found a valid CD for Ubuntu: F:\
01-26 17:00 INFO   root: Running the CD menu...
01-26 17:00 DEBUG  WindowsFrontend: __init__...
01-26 17:00 DEBUG  WindowsFrontend: on_init...
01-26 17:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\translations, languages=['en_US', 'en']
01-26 17:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\translations, languages=['en_US', 'en']
01-26 17:05 INFO   root: CD menu finished
01-26 17:05 INFO   root: Running the installer...
01-26 17:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\translations, languages=['en_US', 'en']
01-26 17:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pyl5DFE.tmp\translations, languages=['en_US', 'en']
01-26 17:05 INFO   WindowsFrontend: Operation cancelled
01-26 17:05 DEBUG  WindowsFrontend: frontend.quit
01-26 17:05 DEBUG  WindowsFrontend: frontend.on_quit
01-26 17:05 DEBUG  root: application.on_quit
01-26 17:05 INFO   root: sys.exit
01-26 17:06 INFO   root: === wubi 9.10ubuntu1 rev160 ===
01-26 17:06 DEBUG  root: Logfile is c:\users\vartok\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
01-26 17:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
01-26 17:06 DEBUG  CommonBackend: data_dir=C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\data
01-26 17:06 DEBUG  WindowsBackend: 7z=C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\bin\7z.exe
01-26 17:06 DEBUG  CommonBackend: Fetching basic info...
01-26 17:06 DEBUG  CommonBackend: original_exe=F:\wubi.exe
01-26 17:06 DEBUG  CommonBackend: platform=win32
01-26 17:06 DEBUG  CommonBackend: osname=nt
01-26 17:06 DEBUG  CommonBackend: language=en_US
01-26 17:06 DEBUG  CommonBackend: encoding=cp1252
01-26 17:06 DEBUG  WindowsBackend: arch=amd64
01-26 17:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\data\isolist.ini
01-26 17:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-26 17:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-26 17:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-26 17:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-26 17:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-26 17:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-26 17:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-26 17:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-26 17:06 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-26 17:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-26 17:06 DEBUG  WindowsBackend: Fetching host info...
01-26 17:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-26 17:06 DEBUG  WindowsBackend: windows version=vista
01-26 17:06 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-26 17:06 DEBUG  WindowsBackend: windows_sp=None
01-26 17:06 DEBUG  WindowsBackend: windows_build=7600
01-26 17:06 DEBUG  WindowsBackend: gmt=-6
01-26 17:06 DEBUG  WindowsBackend: country=US
01-26 17:06 DEBUG  WindowsBackend: timezone=America/Chicago
01-26 17:06 DEBUG  WindowsBackend: windows_username=Vartok
01-26 17:06 DEBUG  WindowsBackend: user_full_name=Vartok
01-26 17:06 DEBUG  WindowsBackend: user_directory=C:\Users\Vartok
01-26 17:06 DEBUG  WindowsBackend: windows_language_code=1033
01-26 17:06 DEBUG  WindowsBackend: windows_language=English
01-26 17:06 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
01-26 17:06 DEBUG  WindowsBackend: bootloader=vista
01-26 17:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 21355.3671875 mb free ntfs)
01-26 17:06 DEBUG  WindowsBackend: drive=Drive(C: hd 21355.3671875 mb free ntfs)
01-26 17:06 DEBUG  WindowsBackend: drive=Drive(D: hd 13585.1992188 mb free ntfs)
01-26 17:06 DEBUG  WindowsBackend: drive=Drive(E: hd 134611.121094 mb free ntfs)
01-26 17:06 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
01-26 17:06 DEBUG  WindowsBackend: drive=Drive(G: hd 31653.3046875 mb free ntfs)
01-26 17:06 DEBUG  WindowsBackend: drive=Drive(J: removable 5.27734375 mb free fat32)
01-26 17:06 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
01-26 17:06 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
01-26 17:06 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-26 17:06 DEBUG  WindowsBackend: keyboard_id=67699721
01-26 17:06 DEBUG  WindowsBackend: keyboard_layout=us
01-26 17:06 DEBUG  WindowsBackend: keyboard_variant=
01-26 17:06 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-26 17:06 DEBUG  CommonBackend: locale=en_US.UTF-8
01-26 17:06 DEBUG  WindowsBackend: total_memory_mb=4094.3046875
01-26 17:06 DEBUG  CommonBackend: Searching ISOs on USB devices
01-26 17:06 DEBUG  CommonBackend: Searching for local CDs
01-26 17:06 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp is a valid Ubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp is a valid Ubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp is a valid Ubuntu Netbook Remix CD
01-26 17:06 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp is a valid Kubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp is a valid Kubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp is a valid Kubuntu Netbook CD
01-26 17:06 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp is a valid Xubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp is a valid Xubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp is a valid Mythbuntu CD
01-26 17:06 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp is a valid Mythbuntu CD
01-26 17:06 DEBUG  Distro:     does not contain C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
01-26 17:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-26 17:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-26 17:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-26 17:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
01-26 17:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
01-26 17:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-26 17:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-26 17:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-26 17:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-26 17:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-26 17:06 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
01-26 17:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
01-26 17:06 INFO   Distro: Found a valid CD for Ubuntu: F:\
01-26 17:06 INFO   root: Running the CD menu...
01-26 17:06 DEBUG  WindowsFrontend: __init__...
01-26 17:06 DEBUG  WindowsFrontend: on_init...
01-26 17:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\translations, languages=['en_US', 'en']
01-26 17:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\translations, languages=['en_US', 'en']
01-26 17:06 INFO   root: CD menu finished
01-26 17:06 INFO   root: Running the installer...
01-26 17:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\translations, languages=['en_US', 'en']
01-26 17:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\translations, languages=['en_US', 'en']
01-26 17:06 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=vartok
01-26 17:06 INFO   root: Received settings
01-26 17:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\translations, languages=['en_US', 'en']
01-26 17:06 DEBUG  TaskList: # Running tasklist...
01-26 17:06 DEBUG  TaskList: ## Running select_target_dir...
01-26 17:06 INFO   WindowsBackend: Installing into G:\ubuntu
01-26 17:06 DEBUG  TaskList: ## Finished select_target_dir
01-26 17:06 DEBUG  TaskList: ## Running create_dir_structure...
01-26 17:06 DEBUG  CommonBackend: Creating dir G:\ubuntu
01-26 17:06 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
01-26 17:06 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
01-26 17:06 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
01-26 17:06 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
01-26 17:06 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
01-26 17:06 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
01-26 17:06 DEBUG  TaskList: ## Finished create_dir_structure
01-26 17:06 DEBUG  TaskList: ## Running uncompress_target_dir...
01-26 17:06 DEBUG  TaskList: ## Finished uncompress_target_dir
01-26 17:06 DEBUG  TaskList: ## Running create_uninstaller...
01-26 17:06 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
01-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
01-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
01-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
01-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
01-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-26 17:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-26 17:06 DEBUG  TaskList: ## Finished create_uninstaller
01-26 17:06 DEBUG  TaskList: ## Running copy_installation_files...
01-26 17:06 DEBUG  WindowsBackend: Copying C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
01-26 17:06 DEBUG  WindowsBackend: Copying C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\winboot -> G:\ubuntu\winboot
01-26 17:06 DEBUG  WindowsBackend: Copying C:\Users\Vartok\AppData\Local\Temp\pylBAEC.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
01-26 17:06 DEBUG  TaskList: ## Finished copy_installation_files
01-26 17:06 DEBUG  TaskList: ## Running get_iso...
01-26 17:06 DEBUG  TaskList: New task copy_file
01-26 17:06 DEBUG  TaskList: ### Running copy_file...
01-26 17:09 DEBUG  TaskList: ### Finished copy_file
01-26 17:09 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
01-26 17:09 DEBUG  TaskList: # Cancelling tasklist
01-26 17:09 DEBUG  TaskList: New task check_iso
01-26 17:09 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
01-26 17:09 DEBUG  CommonBackend: Searching for local ISO
01-26 17:09 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-26 17:09 DEBUG  TaskList: New task get_metalink
01-26 17:09 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
01-26 17:09 DEBUG  TaskList: # Cancelling tasklist
01-26 17:09 DEBUG  TaskList: # Finished tasklist

---

### Post by vartok on 2010-01-27
any ideas or can someone point me in the right direction? im kinna at a loss

---

### Post by vartok on 2010-01-27
bump

---

