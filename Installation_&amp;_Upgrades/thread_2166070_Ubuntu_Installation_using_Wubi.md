---
title: "Ubuntu Installation using Wubi"
date: 2013-08-07
forum: Installation &amp; Upgrades
---

### Post by deepraj2 on 2013-08-07
Really, it's irritating for me. Every time I try to install ubuntu using Wubi, I the eror message (Picture uploaded).
Log file...
```

08-03 22:43 INFO   root: === wubi 12.04 rev272 ===
08-03 22:43 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-03 22:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
08-03 22:43 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\data
08-03 22:43 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\bin\7z.exe
08-03 22:43 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-03 22:43 DEBUG  CommonBackend: Fetching basic info...
08-03 22:43 DEBUG  CommonBackend: original_exe=I:\wubi.exe
08-03 22:43 DEBUG  CommonBackend: platform=win32
08-03 22:43 DEBUG  CommonBackend: osname=nt
08-03 22:43 DEBUG  CommonBackend: language=en_IN
08-03 22:43 DEBUG  CommonBackend: encoding=cp1252
08-03 22:43 DEBUG  WindowsBackend: arch=amd64
08-03 22:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\data\isolist.ini
08-03 22:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-03 22:43 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-03 22:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-03 22:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-03 22:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-03 22:43 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-03 22:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-03 22:43 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-03 22:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-03 22:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-03 22:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-03 22:43 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-03 22:43 DEBUG  WindowsBackend: Fetching host info...
08-03 22:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-03 22:43 DEBUG  WindowsBackend: windows version=vista
08-03 22:43 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-03 22:43 DEBUG  WindowsBackend: windows_sp=None
08-03 22:43 DEBUG  WindowsBackend: windows_build=7600
08-03 22:43 DEBUG  WindowsBackend: gmt=5
08-03 22:43 DEBUG  WindowsBackend: country=IN
08-03 22:43 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-03 22:43 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-03 22:43 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-03 22:43 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-03 22:43 DEBUG  WindowsBackend: windows_language_code=1033
08-03 22:43 DEBUG  WindowsBackend: windows_language=English
08-03 22:43 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-03 22:43 DEBUG  WindowsBackend: bootloader=vista
08-03 22:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139346.832031 mb free ntfs)
08-03 22:43 DEBUG  WindowsBackend: drive=Drive(C: hd 139346.832031 mb free ntfs)
08-03 22:43 DEBUG  WindowsBackend: drive=Drive(D: hd 46336.2578125 mb free ntfs)
08-03 22:43 DEBUG  WindowsBackend: drive=Drive(E: hd 123512.265625 mb free ntfs)
08-03 22:43 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-03 22:43 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-03 22:43 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-03 22:43 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.56640625 mb free fat32)
08-03 22:43 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-03 22:43 DEBUG  WindowsBackend: uninstaller_path=None
08-03 22:43 DEBUG  WindowsBackend: previous_target_dir=None
08-03 22:43 DEBUG  WindowsBackend: previous_distro_name=None
08-03 22:43 DEBUG  WindowsBackend: keyboard_id=67699721
08-03 22:43 DEBUG  WindowsBackend: keyboard_layout=us
08-03 22:43 DEBUG  WindowsBackend: keyboard_variant=
08-03 22:43 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-03 22:43 DEBUG  CommonBackend: locale=en_IN
08-03 22:43 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-03 22:43 DEBUG  CommonBackend: Searching ISOs on USB devices
08-03 22:43 DEBUG  CommonBackend: Searching for local CDs
08-03 22:43 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:43 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:43 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:43 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:43 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:43 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:43 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:43 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:43 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:43 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:43 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:43 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:43 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-03 22:43 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:43 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-03 22:43 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:43 INFO   root: Running the installer...
08-03 22:43 DEBUG  WindowsFrontend: __init__...
08-03 22:43 DEBUG  WindowsFrontend: on_init...
08-03 22:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\translations, languages=['en_IN', 'en']
08-03 22:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylDF67.tmp\translations, languages=['en_IN', 'en']
08-03 22:44 INFO   WindowsFrontend: Operation cancelled
08-03 22:44 DEBUG  WindowsFrontend: frontend.quit
08-03 22:44 DEBUG  WindowsFrontend: frontend.on_quit
08-03 22:44 DEBUG  root: application.on_quit
08-03 22:44 INFO   root: sys.exit
08-03 22:44 INFO   root: === wubi 12.04 rev272 ===
08-03 22:44 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-03 22:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
08-03 22:44 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\data
08-03 22:44 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\bin\7z.exe
08-03 22:44 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-03 22:44 DEBUG  CommonBackend: Fetching basic info...
08-03 22:44 DEBUG  CommonBackend: original_exe=I:\wubi.exe
08-03 22:44 DEBUG  CommonBackend: platform=win32
08-03 22:44 DEBUG  CommonBackend: osname=nt
08-03 22:44 DEBUG  CommonBackend: language=en_IN
08-03 22:44 DEBUG  CommonBackend: encoding=cp1252
08-03 22:44 DEBUG  WindowsBackend: arch=amd64
08-03 22:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\data\isolist.ini
08-03 22:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-03 22:44 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-03 22:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-03 22:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-03 22:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-03 22:44 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-03 22:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-03 22:44 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-03 22:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-03 22:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-03 22:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-03 22:44 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-03 22:44 DEBUG  WindowsBackend: Fetching host info...
08-03 22:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-03 22:44 DEBUG  WindowsBackend: windows version=vista
08-03 22:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-03 22:44 DEBUG  WindowsBackend: windows_sp=None
08-03 22:44 DEBUG  WindowsBackend: windows_build=7600
08-03 22:44 DEBUG  WindowsBackend: gmt=5
08-03 22:44 DEBUG  WindowsBackend: country=IN
08-03 22:44 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-03 22:44 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-03 22:44 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-03 22:44 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-03 22:44 DEBUG  WindowsBackend: windows_language_code=1033
08-03 22:44 DEBUG  WindowsBackend: windows_language=English
08-03 22:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-03 22:44 DEBUG  WindowsBackend: bootloader=vista
08-03 22:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139346.265625 mb free ntfs)
08-03 22:44 DEBUG  WindowsBackend: drive=Drive(C: hd 139346.265625 mb free ntfs)
08-03 22:44 DEBUG  WindowsBackend: drive=Drive(D: hd 46336.2578125 mb free ntfs)
08-03 22:44 DEBUG  WindowsBackend: drive=Drive(E: hd 123512.265625 mb free ntfs)
08-03 22:44 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-03 22:44 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-03 22:44 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-03 22:44 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.56640625 mb free fat32)
08-03 22:44 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-03 22:44 DEBUG  WindowsBackend: uninstaller_path=None
08-03 22:44 DEBUG  WindowsBackend: previous_target_dir=None
08-03 22:44 DEBUG  WindowsBackend: previous_distro_name=None
08-03 22:44 DEBUG  WindowsBackend: keyboard_id=67699721
08-03 22:44 DEBUG  WindowsBackend: keyboard_layout=us
08-03 22:44 DEBUG  WindowsBackend: keyboard_variant=
08-03 22:44 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-03 22:44 DEBUG  CommonBackend: locale=en_IN
08-03 22:44 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-03 22:44 DEBUG  CommonBackend: Searching ISOs on USB devices
08-03 22:44 DEBUG  CommonBackend: Searching for local CDs
08-03 22:44 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:44 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:44 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:44 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:44 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:44 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:44 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:44 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:44 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:44 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:44 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:44 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:44 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-03 22:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:44 INFO   root: Running the installer...
08-03 22:44 DEBUG  WindowsFrontend: __init__...
08-03 22:44 DEBUG  WindowsFrontend: on_init...
08-03 22:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\translations, languages=['en_IN', 'en']
08-03 22:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\translations, languages=['en_IN', 'en']
08-03 22:44 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=deepraj
08-03 22:44 INFO   root: Received settings
08-03 22:44 DEBUG  CommonBackend: Searching for local CD
08-03 22:44 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 22:44 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 22:44 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-03 22:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 22:44 DEBUG  CommonBackend: Searching for local ISO
08-03 22:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylA69C.tmp\translations, languages=['en_US', 'en']
08-03 22:44 DEBUG  TaskList: # Running tasklist...
08-03 22:44 DEBUG  TaskList: ## Running select_target_dir...
08-03 22:44 INFO   WindowsBackend: Installing into E:\ubuntu
08-03 22:44 DEBUG  TaskList: ## Finished select_target_dir
08-03 22:44 DEBUG  TaskList: ## Running create_dir_structure...
08-03 22:44 DEBUG  CommonBackend: Creating dir E:\ubuntu
08-03 22:44 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
08-03 22:44 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
08-03 22:44 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
08-03 22:44 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
08-03 22:44 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
08-03 22:44 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
08-03 22:44 DEBUG  TaskList: ## Finished create_dir_structure
08-03 22:44 DEBUG  TaskList: ## Running create_uninstaller...
08-03 22:44 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
08-03 22:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
08-03 22:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
08-03 22:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-03 22:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
08-03 22:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev272
08-03 22:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-03 22:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-03 22:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-03 22:44 DEBUG  TaskList: ## Finished create_uninstaller
08-03 22:44 DEBUG  TaskList: ## Running create_preseed_diskimage...
08-03 22:44 DEBUG  TaskList: ## Finished create_preseed_diskimage
08-03 22:44 DEBUG  TaskList: ## Running get_diskimage...
08-03 22:44 DEBUG  TaskList: New task download
08-03 22:44 DEBUG  TaskList: ### Running download...
08-03 22:44 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > E:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
08-03 22:44 DEBUG  downloader: Download start filename=E:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz, basename=ubuntu-12.04.2-wubi-amd64.tar.xz, length=549666608, text=None
08-03 23:51 DEBUG  TaskList: ### Finished download
08-03 23:51 DEBUG  downloader: download finished (read 549666608 bytes)
08-03 23:51 DEBUG  TaskList: ## Finished get_diskimage
08-03 23:51 DEBUG  TaskList: ## Running extract_diskimage...
08-03 23:52 DEBUG  TaskList: ## Finished extract_diskimage
08-03 23:52 DEBUG  TaskList: ## Running choose_disk_sizes...
08-03 23:52 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
08-03 23:52 DEBUG  TaskList: ## Finished choose_disk_sizes
08-03 23:52 DEBUG  TaskList: ## Running expand_diskimage...
08-03 23:53 DEBUG  TaskList: ## Finished expand_diskimage
08-03 23:53 DEBUG  TaskList: ## Running create_swap_diskimage...
08-03 23:53 DEBUG  TaskList: ## Finished create_swap_diskimage
08-03 23:53 DEBUG  TaskList: ## Running modify_bootloader...
08-03 23:53 DEBUG  TaskList: New task modify_bcd
08-03 23:53 DEBUG  TaskList: ### Running modify_bcd...
08-03 23:53 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 139346.265625 mb free ntfs)
08-03 23:53 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {226b5c46-6353-11e2-bdad-8af5da54fbf8} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {226b5c46-6353-11e2-bdad-8af5da54fbf8} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
08-03 23:53 DEBUG  TaskList: # Cancelling tasklist
08-03 23:53 DEBUG  TaskList: New task modify_bcd
08-03 23:53 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {226b5c46-6353-11e2-bdad-8af5da54fbf8} device partition=E:
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
>>command=C:\Windows\System32\bcdedit.exe /set {226b5c46-6353-11e2-bdad-8af5da54fbf8} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
08-03 23:53 DEBUG  TaskList: New task modify_bcd
08-03 23:53 DEBUG  TaskList: New task modify_bcd
08-03 23:53 DEBUG  TaskList: New task modify_bcd
08-03 23:53 DEBUG  TaskList: New task modify_bcd
08-03 23:53 DEBUG  TaskList: ## Finished modify_bootloader
08-03 23:53 DEBUG  TaskList: # Finished tasklist
08-03 23:54 INFO   root: === wubi 12.04 rev272 ===
08-03 23:54 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-03 23:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
08-03 23:54 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\data
08-03 23:54 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\bin\7z.exe
08-03 23:54 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-03 23:54 DEBUG  CommonBackend: Fetching basic info...
08-03 23:54 DEBUG  CommonBackend: original_exe=I:\wubi.exe
08-03 23:54 DEBUG  CommonBackend: platform=win32
08-03 23:54 DEBUG  CommonBackend: osname=nt
08-03 23:54 DEBUG  CommonBackend: language=en_IN
08-03 23:54 DEBUG  CommonBackend: encoding=cp1252
08-03 23:54 DEBUG  WindowsBackend: arch=amd64
08-03 23:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\data\isolist.ini
08-03 23:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-03 23:54 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-03 23:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-03 23:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-03 23:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-03 23:54 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-03 23:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-03 23:54 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-03 23:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-03 23:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-03 23:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-03 23:54 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-03 23:54 DEBUG  WindowsBackend: Fetching host info...
08-03 23:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-03 23:54 DEBUG  WindowsBackend: windows version=vista
08-03 23:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-03 23:54 DEBUG  WindowsBackend: windows_sp=None
08-03 23:54 DEBUG  WindowsBackend: windows_build=7600
08-03 23:54 DEBUG  WindowsBackend: gmt=5
08-03 23:54 DEBUG  WindowsBackend: country=IN
08-03 23:54 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-03 23:54 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-03 23:54 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-03 23:54 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-03 23:54 DEBUG  WindowsBackend: windows_language_code=1033
08-03 23:54 DEBUG  WindowsBackend: windows_language=English
08-03 23:54 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-03 23:54 DEBUG  WindowsBackend: bootloader=vista
08-03 23:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139343.414063 mb free ntfs)
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(C: hd 139343.414063 mb free ntfs)
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(D: hd 46336.2578125 mb free ntfs)
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(E: hd 119856.988281 mb free ntfs)
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.36132813 mb free fat32)
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-03 23:54 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
08-03 23:54 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
08-03 23:54 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-03 23:54 DEBUG  WindowsBackend: keyboard_id=67699721
08-03 23:54 DEBUG  WindowsBackend: keyboard_layout=us
08-03 23:54 DEBUG  WindowsBackend: keyboard_variant=
08-03 23:54 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-03 23:54 DEBUG  CommonBackend: locale=en_IN
08-03 23:54 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-03 23:54 DEBUG  CommonBackend: Searching ISOs on USB devices
08-03 23:54 DEBUG  CommonBackend: Searching for local CDs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 INFO   root: Already installed, running the uninstaller...
08-03 23:54 INFO   root: Running the uninstaller...
08-03 23:54 INFO   CommonBackend: This is the uninstaller running
08-03 23:54 DEBUG  WindowsFrontend: __init__...
08-03 23:54 DEBUG  WindowsFrontend: on_init...
08-03 23:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\translations, languages=['en_IN', 'en']
08-03 23:54 INFO   root: Received settings
08-03 23:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\translations, languages=['en_IN', 'en']
08-03 23:54 DEBUG  TaskList: # Running tasklist...
08-03 23:54 DEBUG  TaskList: ## Running Remove bootloader entry...
08-03 23:54 DEBUG  WindowsBackend: Could not find bcd id
08-03 23:54 DEBUG  WindowsBackend: undo_bootini C:
08-03 23:54 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 139343.414063 mb free ntfs)
08-03 23:54 DEBUG  WindowsBackend: undo_bootini D:
08-03 23:54 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 46336.2578125 mb free ntfs)
08-03 23:54 DEBUG  WindowsBackend: undo_bootini E:
08-03 23:54 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 119856.988281 mb free ntfs)
08-03 23:54 DEBUG  WindowsBackend: undo_bootini F:
08-03 23:54 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 92.4111328125 mb free fat32)
08-03 23:54 DEBUG  WindowsBackend: undo_bootini G:
08-03 23:54 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 2008.9765625 mb free ntfs)
08-03 23:54 DEBUG  WindowsBackend: undo_bootini I:
08-03 23:54 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 3950.36132813 mb free fat32)
08-03 23:54 DEBUG  TaskList: ## Finished Remove bootloader entry
08-03 23:54 DEBUG  TaskList: ## Running Remove target dir...
08-03 23:54 DEBUG  CommonBackend: Deleting E:\ubuntu
08-03 23:54 DEBUG  TaskList: ## Finished Remove target dir
08-03 23:54 DEBUG  TaskList: ## Running Remove registry key...
08-03 23:54 DEBUG  TaskList: ## Finished Remove registry key
08-03 23:54 DEBUG  TaskList: # Finished tasklist
08-03 23:54 INFO   root: Almost finished uninstalling
08-03 23:54 INFO   root: Finished uninstallation
08-03 23:54 DEBUG  CommonBackend: Fetching basic info...
08-03 23:54 DEBUG  CommonBackend: original_exe=I:\wubi.exe
08-03 23:54 DEBUG  CommonBackend: platform=win32
08-03 23:54 DEBUG  CommonBackend: osname=nt
08-03 23:54 DEBUG  WindowsBackend: arch=amd64
08-03 23:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\data\isolist.ini
08-03 23:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-03 23:54 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-03 23:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-03 23:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-03 23:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-03 23:54 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-03 23:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-03 23:54 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-03 23:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-03 23:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-03 23:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-03 23:54 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-03 23:54 DEBUG  WindowsBackend: Fetching host info...
08-03 23:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-03 23:54 DEBUG  WindowsBackend: windows version=vista
08-03 23:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-03 23:54 DEBUG  WindowsBackend: windows_sp=None
08-03 23:54 DEBUG  WindowsBackend: windows_build=7600
08-03 23:54 DEBUG  WindowsBackend: gmt=5
08-03 23:54 DEBUG  WindowsBackend: country=IN
08-03 23:54 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-03 23:54 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-03 23:54 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-03 23:54 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-03 23:54 DEBUG  WindowsBackend: windows_language_code=1033
08-03 23:54 DEBUG  WindowsBackend: windows_language=English
08-03 23:54 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-03 23:54 DEBUG  WindowsBackend: bootloader=vista
08-03 23:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139343.542969 mb free ntfs)
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(C: hd 139343.542969 mb free ntfs)
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(D: hd 46336.2578125 mb free ntfs)
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(E: hd 123512.265625 mb free ntfs)
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.36132813 mb free fat32)
08-03 23:54 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-03 23:54 DEBUG  WindowsBackend: uninstaller_path=None
08-03 23:54 DEBUG  WindowsBackend: previous_target_dir=None
08-03 23:54 DEBUG  WindowsBackend: previous_distro_name=None
08-03 23:54 DEBUG  WindowsBackend: keyboard_id=67699721
08-03 23:54 DEBUG  WindowsBackend: keyboard_layout=us
08-03 23:54 DEBUG  WindowsBackend: keyboard_variant=
08-03 23:54 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-03 23:54 DEBUG  CommonBackend: Searching ISOs on USB devices
08-03 23:54 DEBUG  CommonBackend: Searching for local CDs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 INFO   root: Running the installer...
08-03 23:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\translations, languages=['en_IN', 'en']
08-03 23:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\translations, languages=['en_IN', 'en']
08-03 23:54 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=deepraj
08-03 23:54 INFO   root: Received settings
08-03 23:54 DEBUG  CommonBackend: Searching for local CD
08-03 23:54 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:54 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:54 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-03 23:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:54 DEBUG  CommonBackend: Searching for local ISO
08-03 23:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl7502.tmp\translations, languages=['en_US', 'en']
08-03 23:54 DEBUG  TaskList: # Running tasklist...
08-03 23:54 DEBUG  TaskList: ## Running select_target_dir...
08-03 23:54 INFO   WindowsBackend: Installing into E:\ubuntu
08-03 23:54 DEBUG  TaskList: ## Finished select_target_dir
08-03 23:54 DEBUG  TaskList: ## Running create_dir_structure...
08-03 23:54 DEBUG  CommonBackend: Creating dir E:\ubuntu
08-03 23:54 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
08-03 23:54 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
08-03 23:54 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
08-03 23:54 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
08-03 23:54 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
08-03 23:54 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
08-03 23:54 DEBUG  TaskList: ## Finished create_dir_structure
08-03 23:54 DEBUG  TaskList: ## Running create_uninstaller...
08-03 23:54 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
08-03 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
08-03 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
08-03 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-03 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
08-03 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev272
08-03 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-03 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-03 23:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-03 23:54 DEBUG  TaskList: ## Finished create_uninstaller
08-03 23:54 DEBUG  TaskList: ## Running create_preseed_diskimage...
08-03 23:54 DEBUG  TaskList: ## Finished create_preseed_diskimage
08-03 23:54 DEBUG  TaskList: ## Running get_diskimage...
08-03 23:54 DEBUG  TaskList: New task download
08-03 23:54 DEBUG  TaskList: ### Running download...
08-03 23:54 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > E:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
08-03 23:54 DEBUG  downloader: Download start filename=E:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz, basename=ubuntu-12.04.2-wubi-amd64.tar.xz, length=549666608, text=None
08-03 23:55 INFO   WindowsFrontend: Operation cancelled
08-03 23:55 DEBUG  WindowsFrontend: frontend.quit
08-03 23:55 DEBUG  WindowsFrontend: frontend.on_quit
08-03 23:55 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
08-03 23:55 DEBUG  TaskList: # Cancelling tasklist
08-03 23:55 DEBUG  downloader: download finished (read 2842624 bytes)
08-03 23:55 DEBUG  TaskList: ### Finished download
08-03 23:55 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
08-03 23:55 DEBUG  root: application.on_quit
08-03 23:55 DEBUG  root: Forceful exit
08-03 23:55 INFO   root: sys.exit
08-03 23:55 INFO   root: === wubi 12.04 rev272 ===
08-03 23:55 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-03 23:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
08-03 23:55 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\data
08-03 23:55 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\bin\7z.exe
08-03 23:55 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-03 23:55 DEBUG  CommonBackend: Fetching basic info...
08-03 23:55 DEBUG  CommonBackend: original_exe=I:\wubi.exe
08-03 23:55 DEBUG  CommonBackend: platform=win32
08-03 23:55 DEBUG  CommonBackend: osname=nt
08-03 23:55 DEBUG  CommonBackend: language=en_IN
08-03 23:55 DEBUG  CommonBackend: encoding=cp1252
08-03 23:55 DEBUG  WindowsBackend: arch=amd64
08-03 23:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\data\isolist.ini
08-03 23:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-03 23:55 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-03 23:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-03 23:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-03 23:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-03 23:55 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-03 23:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-03 23:55 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-03 23:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-03 23:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-03 23:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-03 23:55 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-03 23:55 DEBUG  WindowsBackend: Fetching host info...
08-03 23:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-03 23:55 DEBUG  WindowsBackend: windows version=vista
08-03 23:55 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-03 23:55 DEBUG  WindowsBackend: windows_sp=None
08-03 23:55 DEBUG  WindowsBackend: windows_build=7600
08-03 23:55 DEBUG  WindowsBackend: gmt=5
08-03 23:55 DEBUG  WindowsBackend: country=IN
08-03 23:55 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-03 23:55 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-03 23:55 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-03 23:55 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-03 23:55 DEBUG  WindowsBackend: windows_language_code=1033
08-03 23:55 DEBUG  WindowsBackend: windows_language=English
08-03 23:55 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-03 23:55 DEBUG  WindowsBackend: bootloader=vista
08-03 23:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139343.480469 mb free ntfs)
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(C: hd 139343.480469 mb free ntfs)
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(D: hd 46336.2578125 mb free ntfs)
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(E: hd 123507.171875 mb free ntfs)
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.36132813 mb free fat32)
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-03 23:55 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
08-03 23:55 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
08-03 23:55 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-03 23:55 DEBUG  WindowsBackend: keyboard_id=67699721
08-03 23:55 DEBUG  WindowsBackend: keyboard_layout=us
08-03 23:55 DEBUG  WindowsBackend: keyboard_variant=
08-03 23:55 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-03 23:55 DEBUG  CommonBackend: locale=en_IN
08-03 23:55 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-03 23:55 DEBUG  CommonBackend: Searching ISOs on USB devices
08-03 23:55 DEBUG  CommonBackend: Searching for local CDs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 INFO   root: Already installed, running the uninstaller...
08-03 23:55 INFO   root: Running the uninstaller...
08-03 23:55 INFO   CommonBackend: This is the uninstaller running
08-03 23:55 DEBUG  WindowsFrontend: __init__...
08-03 23:55 DEBUG  WindowsFrontend: on_init...
08-03 23:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\translations, languages=['en_IN', 'en']
08-03 23:55 INFO   root: Received settings
08-03 23:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\translations, languages=['en_IN', 'en']
08-03 23:55 DEBUG  TaskList: # Running tasklist...
08-03 23:55 DEBUG  TaskList: ## Running Remove bootloader entry...
08-03 23:55 DEBUG  WindowsBackend: Could not find bcd id
08-03 23:55 DEBUG  WindowsBackend: undo_bootini C:
08-03 23:55 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 139343.480469 mb free ntfs)
08-03 23:55 DEBUG  WindowsBackend: undo_bootini D:
08-03 23:55 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 46336.2578125 mb free ntfs)
08-03 23:55 DEBUG  WindowsBackend: undo_bootini E:
08-03 23:55 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 123507.171875 mb free ntfs)
08-03 23:55 DEBUG  WindowsBackend: undo_bootini F:
08-03 23:55 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 92.4111328125 mb free fat32)
08-03 23:55 DEBUG  WindowsBackend: undo_bootini G:
08-03 23:55 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 2008.9765625 mb free ntfs)
08-03 23:55 DEBUG  WindowsBackend: undo_bootini I:
08-03 23:55 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 3950.36132813 mb free fat32)
08-03 23:55 DEBUG  TaskList: ## Finished Remove bootloader entry
08-03 23:55 DEBUG  TaskList: ## Running Remove target dir...
08-03 23:55 DEBUG  CommonBackend: Deleting E:\ubuntu
08-03 23:55 DEBUG  TaskList: ## Finished Remove target dir
08-03 23:55 DEBUG  TaskList: ## Running Remove registry key...
08-03 23:55 DEBUG  TaskList: ## Finished Remove registry key
08-03 23:55 DEBUG  TaskList: # Finished tasklist
08-03 23:55 INFO   root: Almost finished uninstalling
08-03 23:55 INFO   root: Finished uninstallation
08-03 23:55 DEBUG  CommonBackend: Fetching basic info...
08-03 23:55 DEBUG  CommonBackend: original_exe=I:\wubi.exe
08-03 23:55 DEBUG  CommonBackend: platform=win32
08-03 23:55 DEBUG  CommonBackend: osname=nt
08-03 23:55 DEBUG  WindowsBackend: arch=amd64
08-03 23:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\data\isolist.ini
08-03 23:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-03 23:55 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-03 23:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-03 23:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-03 23:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-03 23:55 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-03 23:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-03 23:55 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-03 23:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-03 23:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-03 23:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-03 23:55 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-03 23:55 DEBUG  WindowsBackend: Fetching host info...
08-03 23:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-03 23:55 DEBUG  WindowsBackend: windows version=vista
08-03 23:55 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-03 23:55 DEBUG  WindowsBackend: windows_sp=None
08-03 23:55 DEBUG  WindowsBackend: windows_build=7600
08-03 23:55 DEBUG  WindowsBackend: gmt=5
08-03 23:55 DEBUG  WindowsBackend: country=IN
08-03 23:55 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-03 23:55 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-03 23:55 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-03 23:55 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-03 23:55 DEBUG  WindowsBackend: windows_language_code=1033
08-03 23:55 DEBUG  WindowsBackend: windows_language=English
08-03 23:55 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-03 23:55 DEBUG  WindowsBackend: bootloader=vista
08-03 23:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139343.449219 mb free ntfs)
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(C: hd 139343.449219 mb free ntfs)
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(D: hd 46336.2578125 mb free ntfs)
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(E: hd 123512.265625 mb free ntfs)
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.36132813 mb free fat32)
08-03 23:55 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-03 23:55 DEBUG  WindowsBackend: uninstaller_path=None
08-03 23:55 DEBUG  WindowsBackend: previous_target_dir=None
08-03 23:55 DEBUG  WindowsBackend: previous_distro_name=None
08-03 23:55 DEBUG  WindowsBackend: keyboard_id=67699721
08-03 23:55 DEBUG  WindowsBackend: keyboard_layout=us
08-03 23:55 DEBUG  WindowsBackend: keyboard_variant=
08-03 23:55 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-03 23:55 DEBUG  CommonBackend: Searching ISOs on USB devices
08-03 23:55 DEBUG  CommonBackend: Searching for local CDs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-03 23:55 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-03 23:55 INFO   root: Running the installer...
08-03 23:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\translations, languages=['en_IN', 'en']
08-03 23:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl49AF.tmp\translations, languages=['en_IN', 'en']
08-03 23:55 INFO   WindowsFrontend: Operation cancelled
08-03 23:55 DEBUG  WindowsFrontend: frontend.quit
08-03 23:55 DEBUG  WindowsFrontend: frontend.on_quit
08-03 23:55 DEBUG  root: application.on_quit
08-03 23:55 INFO   root: sys.exit
08-04 19:29 INFO   root: === wubi 12.04 rev272 ===
08-04 19:29 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-04 19:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\Ubuntu\\wubi.exe"']
08-04 19:29 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\data
08-04 19:29 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\bin\7z.exe
08-04 19:29 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-04 19:29 DEBUG  CommonBackend: Fetching basic info...
08-04 19:29 DEBUG  CommonBackend: original_exe=E:\Ubuntu\wubi.exe
08-04 19:29 DEBUG  CommonBackend: platform=win32
08-04 19:29 DEBUG  CommonBackend: osname=nt
08-04 19:29 DEBUG  CommonBackend: language=en_IN
08-04 19:29 DEBUG  CommonBackend: encoding=cp1252
08-04 19:29 DEBUG  WindowsBackend: arch=amd64
08-04 19:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\data\isolist.ini
08-04 19:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-04 19:29 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-04 19:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-04 19:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-04 19:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-04 19:29 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-04 19:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-04 19:29 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-04 19:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-04 19:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-04 19:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-04 19:29 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-04 19:29 DEBUG  WindowsBackend: Fetching host info...
08-04 19:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-04 19:29 DEBUG  WindowsBackend: windows version=vista
08-04 19:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-04 19:29 DEBUG  WindowsBackend: windows_sp=None
08-04 19:29 DEBUG  WindowsBackend: windows_build=7600
08-04 19:29 DEBUG  WindowsBackend: gmt=5
08-04 19:29 DEBUG  WindowsBackend: country=IN
08-04 19:29 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-04 19:29 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-04 19:29 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-04 19:29 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-04 19:29 DEBUG  WindowsBackend: windows_language_code=1033
08-04 19:29 DEBUG  WindowsBackend: windows_language=English
08-04 19:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-04 19:29 DEBUG  WindowsBackend: bootloader=vista
08-04 19:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139081.851563 mb free ntfs)
08-04 19:29 DEBUG  WindowsBackend: drive=Drive(C: hd 139081.851563 mb free ntfs)
08-04 19:29 DEBUG  WindowsBackend: drive=Drive(D: hd 51108.4296875 mb free ntfs)
08-04 19:29 DEBUG  WindowsBackend: drive=Drive(E: hd 122492.6875 mb free ntfs)
08-04 19:29 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-04 19:29 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-04 19:29 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-04 19:29 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.36132813 mb free fat32)
08-04 19:29 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-04 19:29 DEBUG  WindowsBackend: uninstaller_path=None
08-04 19:29 DEBUG  WindowsBackend: previous_target_dir=None
08-04 19:29 DEBUG  WindowsBackend: previous_distro_name=None
08-04 19:29 DEBUG  WindowsBackend: keyboard_id=67699721
08-04 19:29 DEBUG  WindowsBackend: keyboard_layout=us
08-04 19:29 DEBUG  WindowsBackend: keyboard_variant=
08-04 19:29 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-04 19:29 DEBUG  CommonBackend: locale=en_IN
08-04 19:29 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-04 19:29 DEBUG  CommonBackend: Searching ISOs on USB devices
08-04 19:29 DEBUG  CommonBackend: Searching for local CDs
08-04 19:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:29 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:29 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:29 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:29 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:29 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:29 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:29 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:29 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:29 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:29 INFO   root: Running the installer...
08-04 19:29 DEBUG  WindowsFrontend: __init__...
08-04 19:29 DEBUG  WindowsFrontend: on_init...
08-04 19:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\translations, languages=['en_IN', 'en']
08-04 19:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\translations, languages=['en_IN', 'en']
08-04 19:29 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=deepraj
08-04 19:29 INFO   root: Received settings
08-04 19:29 DEBUG  CommonBackend: Searching for local CD
08-04 19:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:29 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:29 DEBUG  CommonBackend: Searching for local ISO
08-04 19:29 DEBUG  Distro:   checking Ubuntu ISO E:\Ubuntu\ubuntu-12.04.2-desktop-amd64.iso
08-04 19:29 DEBUG  Distro:     does not contain casper\vmlinuz
08-04 19:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl3E76.tmp\translations, languages=['en_US', 'en']
08-04 19:29 DEBUG  TaskList: # Running tasklist...
08-04 19:29 DEBUG  TaskList: ## Running select_target_dir...
08-04 19:29 ERROR  TaskList: Cannot install into E:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into E:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
08-04 19:29 DEBUG  TaskList: # Cancelling tasklist
08-04 19:29 DEBUG  TaskList: # Finished tasklist
08-04 19:29 ERROR  root: Cannot install into E:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into E:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
08-04 19:30 INFO   root: === wubi 12.04 rev272 ===
08-04 19:30 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-04 19:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\Ubuntu_Setup\\wubi.exe"']
08-04 19:30 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\data
08-04 19:30 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\bin\7z.exe
08-04 19:30 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-04 19:30 DEBUG  CommonBackend: Fetching basic info...
08-04 19:30 DEBUG  CommonBackend: original_exe=E:\Ubuntu_Setup\wubi.exe
08-04 19:30 DEBUG  CommonBackend: platform=win32
08-04 19:30 DEBUG  CommonBackend: osname=nt
08-04 19:30 DEBUG  CommonBackend: language=en_IN
08-04 19:30 DEBUG  CommonBackend: encoding=cp1252
08-04 19:30 DEBUG  WindowsBackend: arch=amd64
08-04 19:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\data\isolist.ini
08-04 19:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-04 19:30 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-04 19:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-04 19:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-04 19:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-04 19:30 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-04 19:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-04 19:30 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-04 19:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-04 19:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-04 19:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-04 19:30 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-04 19:30 DEBUG  WindowsBackend: Fetching host info...
08-04 19:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-04 19:30 DEBUG  WindowsBackend: windows version=vista
08-04 19:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-04 19:30 DEBUG  WindowsBackend: windows_sp=None
08-04 19:30 DEBUG  WindowsBackend: windows_build=7600
08-04 19:30 DEBUG  WindowsBackend: gmt=5
08-04 19:30 DEBUG  WindowsBackend: country=IN
08-04 19:30 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-04 19:30 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-04 19:30 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-04 19:30 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-04 19:30 DEBUG  WindowsBackend: windows_language_code=1033
08-04 19:30 DEBUG  WindowsBackend: windows_language=English
08-04 19:30 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-04 19:30 DEBUG  WindowsBackend: bootloader=vista
08-04 19:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139081.785156 mb free ntfs)
08-04 19:30 DEBUG  WindowsBackend: drive=Drive(C: hd 139081.785156 mb free ntfs)
08-04 19:30 DEBUG  WindowsBackend: drive=Drive(D: hd 51108.4296875 mb free ntfs)
08-04 19:30 DEBUG  WindowsBackend: drive=Drive(E: hd 122492.6875 mb free ntfs)
08-04 19:30 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-04 19:30 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-04 19:30 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-04 19:30 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.36132813 mb free fat32)
08-04 19:30 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-04 19:30 DEBUG  WindowsBackend: uninstaller_path=None
08-04 19:30 DEBUG  WindowsBackend: previous_target_dir=None
08-04 19:30 DEBUG  WindowsBackend: previous_distro_name=None
08-04 19:30 DEBUG  WindowsBackend: keyboard_id=67699721
08-04 19:30 DEBUG  WindowsBackend: keyboard_layout=us
08-04 19:30 DEBUG  WindowsBackend: keyboard_variant=
08-04 19:30 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-04 19:30 DEBUG  CommonBackend: locale=en_IN
08-04 19:30 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-04 19:30 DEBUG  CommonBackend: Searching ISOs on USB devices
08-04 19:30 DEBUG  CommonBackend: Searching for local CDs
08-04 19:30 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:30 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:30 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:30 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:30 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:30 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:30 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:30 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:30 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:30 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:30 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:30 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:30 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:30 INFO   root: Running the installer...
08-04 19:30 DEBUG  WindowsFrontend: __init__...
08-04 19:30 DEBUG  WindowsFrontend: on_init...
08-04 19:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\translations, languages=['en_IN', 'en']
08-04 19:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\translations, languages=['en_IN', 'en']
08-04 19:30 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=deepraj
08-04 19:30 INFO   root: Received settings
08-04 19:30 DEBUG  CommonBackend: Searching for local CD
08-04 19:30 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:30 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:30 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:30 DEBUG  CommonBackend: Searching for local ISO
08-04 19:30 DEBUG  Distro:   checking Ubuntu ISO E:\Ubuntu_Setup\ubuntu-12.04.2-desktop-amd64.iso
08-04 19:30 DEBUG  Distro:     does not contain casper\vmlinuz
08-04 19:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl1979.tmp\translations, languages=['en_US', 'en']
08-04 19:30 DEBUG  TaskList: # Running tasklist...
08-04 19:30 DEBUG  TaskList: ## Running select_target_dir...
08-04 19:30 INFO   WindowsBackend: Installing into E:\ubuntu
08-04 19:30 DEBUG  TaskList: ## Finished select_target_dir
08-04 19:30 DEBUG  TaskList: ## Running create_dir_structure...
08-04 19:30 DEBUG  CommonBackend: Creating dir E:\ubuntu
08-04 19:30 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
08-04 19:30 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
08-04 19:30 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
08-04 19:30 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
08-04 19:30 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
08-04 19:30 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
08-04 19:30 DEBUG  TaskList: ## Finished create_dir_structure
08-04 19:30 DEBUG  TaskList: ## Running create_uninstaller...
08-04 19:30 DEBUG  WindowsBackend: Copying uninstaller E:\Ubuntu_Setup\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
08-04 19:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
08-04 19:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
08-04 19:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-04 19:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
08-04 19:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev272
08-04 19:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-04 19:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-04 19:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-04 19:30 DEBUG  TaskList: ## Finished create_uninstaller
08-04 19:30 DEBUG  TaskList: ## Running create_preseed_diskimage...
08-04 19:30 DEBUG  TaskList: ## Finished create_preseed_diskimage
08-04 19:30 DEBUG  TaskList: ## Running get_diskimage...
08-04 19:30 DEBUG  TaskList: New task download
08-04 19:30 DEBUG  TaskList: ### Running download...
08-04 19:30 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > E:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
08-04 19:30 DEBUG  downloader: Download start filename=E:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz, basename=ubuntu-12.04.2-wubi-amd64.tar.xz, length=549666608, text=None
08-04 19:31 INFO   WindowsFrontend: Operation cancelled
08-04 19:31 DEBUG  WindowsFrontend: frontend.quit
08-04 19:31 DEBUG  WindowsFrontend: frontend.on_quit
08-04 19:31 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
08-04 19:31 DEBUG  TaskList: # Cancelling tasklist
08-04 19:31 DEBUG  downloader: download finished (read 11796480 bytes)
08-04 19:31 DEBUG  TaskList: ### Finished download
08-04 19:31 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
08-04 19:31 DEBUG  root: application.on_quit
08-04 19:31 DEBUG  root: Forceful exit
08-04 19:31 INFO   root: sys.exit
08-04 19:31 INFO   root: === wubi 12.04 rev272 ===
08-04 19:31 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-04 19:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\Ubuntu_Setup\\wubi.exe"']
08-04 19:31 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\data
08-04 19:31 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\bin\7z.exe
08-04 19:31 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-04 19:31 DEBUG  CommonBackend: Fetching basic info...
08-04 19:31 DEBUG  CommonBackend: original_exe=E:\Ubuntu_Setup\wubi.exe
08-04 19:31 DEBUG  CommonBackend: platform=win32
08-04 19:31 DEBUG  CommonBackend: osname=nt
08-04 19:31 DEBUG  CommonBackend: language=en_IN
08-04 19:31 DEBUG  CommonBackend: encoding=cp1252
08-04 19:31 DEBUG  WindowsBackend: arch=amd64
08-04 19:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\data\isolist.ini
08-04 19:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-04 19:31 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-04 19:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-04 19:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-04 19:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-04 19:31 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-04 19:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-04 19:31 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-04 19:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-04 19:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-04 19:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-04 19:31 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-04 19:31 DEBUG  WindowsBackend: Fetching host info...
08-04 19:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-04 19:31 DEBUG  WindowsBackend: windows version=vista
08-04 19:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-04 19:31 DEBUG  WindowsBackend: windows_sp=None
08-04 19:31 DEBUG  WindowsBackend: windows_build=7600
08-04 19:31 DEBUG  WindowsBackend: gmt=5
08-04 19:31 DEBUG  WindowsBackend: country=IN
08-04 19:31 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-04 19:31 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-04 19:31 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-04 19:31 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-04 19:31 DEBUG  WindowsBackend: windows_language_code=1033
08-04 19:31 DEBUG  WindowsBackend: windows_language=English
08-04 19:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-04 19:31 DEBUG  WindowsBackend: bootloader=vista
08-04 19:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139082.484375 mb free ntfs)
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(C: hd 139082.484375 mb free ntfs)
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(D: hd 51108.4296875 mb free ntfs)
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(E: hd 122479.054688 mb free ntfs)
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.36132813 mb free fat32)
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-04 19:31 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
08-04 19:31 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
08-04 19:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-04 19:31 DEBUG  WindowsBackend: keyboard_id=67699721
08-04 19:31 DEBUG  WindowsBackend: keyboard_layout=us
08-04 19:31 DEBUG  WindowsBackend: keyboard_variant=
08-04 19:31 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-04 19:31 DEBUG  CommonBackend: locale=en_IN
08-04 19:31 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-04 19:31 DEBUG  CommonBackend: Searching ISOs on USB devices
08-04 19:31 DEBUG  CommonBackend: Searching for local CDs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 INFO   root: Already installed, running the uninstaller...
08-04 19:31 INFO   root: Running the uninstaller...
08-04 19:31 INFO   CommonBackend: This is the uninstaller running
08-04 19:31 DEBUG  WindowsFrontend: __init__...
08-04 19:31 DEBUG  WindowsFrontend: on_init...
08-04 19:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\translations, languages=['en_IN', 'en']
08-04 19:31 INFO   root: Received settings
08-04 19:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\translations, languages=['en_IN', 'en']
08-04 19:31 DEBUG  TaskList: # Running tasklist...
08-04 19:31 DEBUG  TaskList: ## Running Remove bootloader entry...
08-04 19:31 DEBUG  WindowsBackend: Could not find bcd id
08-04 19:31 DEBUG  WindowsBackend: undo_bootini C:
08-04 19:31 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 139082.484375 mb free ntfs)
08-04 19:31 DEBUG  WindowsBackend: undo_bootini D:
08-04 19:31 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 51108.4296875 mb free ntfs)
08-04 19:31 DEBUG  WindowsBackend: undo_bootini E:
08-04 19:31 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 122479.054688 mb free ntfs)
08-04 19:31 DEBUG  WindowsBackend: undo_bootini F:
08-04 19:31 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 92.4111328125 mb free fat32)
08-04 19:31 DEBUG  WindowsBackend: undo_bootini G:
08-04 19:31 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 2008.9765625 mb free ntfs)
08-04 19:31 DEBUG  WindowsBackend: undo_bootini I:
08-04 19:31 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 3950.36132813 mb free fat32)
08-04 19:31 DEBUG  TaskList: ## Finished Remove bootloader entry
08-04 19:31 DEBUG  TaskList: ## Running Remove target dir...
08-04 19:31 DEBUG  CommonBackend: Deleting E:\ubuntu
08-04 19:31 DEBUG  TaskList: ## Finished Remove target dir
08-04 19:31 DEBUG  TaskList: ## Running Remove registry key...
08-04 19:31 DEBUG  TaskList: ## Finished Remove registry key
08-04 19:31 DEBUG  TaskList: # Finished tasklist
08-04 19:31 INFO   root: Almost finished uninstalling
08-04 19:31 INFO   root: Finished uninstallation
08-04 19:31 DEBUG  CommonBackend: Fetching basic info...
08-04 19:31 DEBUG  CommonBackend: original_exe=E:\Ubuntu_Setup\wubi.exe
08-04 19:31 DEBUG  CommonBackend: platform=win32
08-04 19:31 DEBUG  CommonBackend: osname=nt
08-04 19:31 DEBUG  WindowsBackend: arch=amd64
08-04 19:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\data\isolist.ini
08-04 19:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-04 19:31 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-04 19:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-04 19:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-04 19:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-04 19:31 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-04 19:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-04 19:31 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-04 19:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-04 19:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-04 19:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-04 19:31 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-04 19:31 DEBUG  WindowsBackend: Fetching host info...
08-04 19:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-04 19:31 DEBUG  WindowsBackend: windows version=vista
08-04 19:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-04 19:31 DEBUG  WindowsBackend: windows_sp=None
08-04 19:31 DEBUG  WindowsBackend: windows_build=7600
08-04 19:31 DEBUG  WindowsBackend: gmt=5
08-04 19:31 DEBUG  WindowsBackend: country=IN
08-04 19:31 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-04 19:31 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-04 19:31 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-04 19:31 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-04 19:31 DEBUG  WindowsBackend: windows_language_code=1033
08-04 19:31 DEBUG  WindowsBackend: windows_language=English
08-04 19:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-04 19:31 DEBUG  WindowsBackend: bootloader=vista
08-04 19:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139082.449219 mb free ntfs)
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(C: hd 139082.449219 mb free ntfs)
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(D: hd 51108.4296875 mb free ntfs)
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(E: hd 122492.6875 mb free ntfs)
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.36132813 mb free fat32)
08-04 19:31 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-04 19:31 DEBUG  WindowsBackend: uninstaller_path=None
08-04 19:31 DEBUG  WindowsBackend: previous_target_dir=None
08-04 19:31 DEBUG  WindowsBackend: previous_distro_name=None
08-04 19:31 DEBUG  WindowsBackend: keyboard_id=67699721
08-04 19:31 DEBUG  WindowsBackend: keyboard_layout=us
08-04 19:31 DEBUG  WindowsBackend: keyboard_variant=
08-04 19:31 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-04 19:31 DEBUG  CommonBackend: Searching ISOs on USB devices
08-04 19:31 DEBUG  CommonBackend: Searching for local CDs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:31 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:31 INFO   root: Running the installer...
08-04 19:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\translations, languages=['en_IN', 'en']
08-04 19:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\translations, languages=['en_IN', 'en']
08-04 19:32 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=deepraj
08-04 19:32 INFO   root: Received settings
08-04 19:32 DEBUG  CommonBackend: Searching for local CD
08-04 19:32 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp is a valid Ubuntu CD
08-04 19:32 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\casper\filesystem.squashfs
08-04 19:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:32 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:32 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:32 DEBUG  CommonBackend: Searching for local ISO
08-04 19:32 DEBUG  Distro:   checking Ubuntu ISO E:\Ubuntu_Setup\ubuntu-12.04.2-desktop-amd64.iso
08-04 19:32 DEBUG  Distro:     does not contain casper\vmlinuz
08-04 19:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylB07A.tmp\translations, languages=['en_US', 'en']
08-04 19:32 DEBUG  TaskList: # Running tasklist...
08-04 19:32 DEBUG  TaskList: ## Running select_target_dir...
08-04 19:32 INFO   WindowsBackend: Installing into E:\ubuntu
08-04 19:32 DEBUG  TaskList: ## Finished select_target_dir
08-04 19:32 DEBUG  TaskList: ## Running create_dir_structure...
08-04 19:32 DEBUG  CommonBackend: Creating dir E:\ubuntu
08-04 19:32 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
08-04 19:32 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
08-04 19:32 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
08-04 19:32 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
08-04 19:32 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
08-04 19:32 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
08-04 19:32 DEBUG  TaskList: ## Finished create_dir_structure
08-04 19:32 DEBUG  TaskList: ## Running create_uninstaller...
08-04 19:32 DEBUG  WindowsBackend: Copying uninstaller E:\Ubuntu_Setup\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
08-04 19:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
08-04 19:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
08-04 19:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-04 19:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
08-04 19:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev272
08-04 19:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-04 19:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-04 19:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-04 19:32 DEBUG  TaskList: ## Finished create_uninstaller
08-04 19:32 DEBUG  TaskList: ## Running create_preseed_diskimage...
08-04 19:32 DEBUG  TaskList: ## Finished create_preseed_diskimage
08-04 19:32 DEBUG  TaskList: ## Running get_diskimage...
08-04 19:32 DEBUG  TaskList: New task download
08-04 19:32 DEBUG  TaskList: ### Running download...
08-04 19:32 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > E:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
08-04 19:32 DEBUG  downloader: Download start filename=E:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz, basename=ubuntu-12.04.2-wubi-amd64.tar.xz, length=549666608, text=None
08-04 19:33 INFO   WindowsFrontend: Operation cancelled
08-04 19:33 DEBUG  WindowsFrontend: frontend.quit
08-04 19:33 DEBUG  WindowsFrontend: frontend.on_quit
08-04 19:33 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
08-04 19:33 DEBUG  TaskList: # Cancelling tasklist
08-04 19:33 DEBUG  downloader: download finished (read 6995968 bytes)
08-04 19:33 DEBUG  TaskList: ### Finished download
08-04 19:33 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
08-04 19:33 DEBUG  root: application.on_quit
08-04 19:33 DEBUG  root: Forceful exit
08-04 19:33 INFO   root: sys.exit
08-04 19:33 INFO   root: === wubi 12.04 rev272 ===
08-04 19:33 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-04 19:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\Ubuntu_Setup\\wubi.exe"']
08-04 19:33 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\data
08-04 19:33 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\bin\7z.exe
08-04 19:33 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-04 19:33 DEBUG  CommonBackend: Fetching basic info...
08-04 19:33 DEBUG  CommonBackend: original_exe=E:\Ubuntu_Setup\wubi.exe
08-04 19:33 DEBUG  CommonBackend: platform=win32
08-04 19:33 DEBUG  CommonBackend: osname=nt
08-04 19:33 DEBUG  CommonBackend: language=en_IN
08-04 19:33 DEBUG  CommonBackend: encoding=cp1252
08-04 19:33 DEBUG  WindowsBackend: arch=amd64
08-04 19:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\data\isolist.ini
08-04 19:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-04 19:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-04 19:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-04 19:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-04 19:33 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-04 19:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-04 19:33 DEBUG  WindowsBackend: Fetching host info...
08-04 19:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-04 19:33 DEBUG  WindowsBackend: windows version=vista
08-04 19:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-04 19:33 DEBUG  WindowsBackend: windows_sp=None
08-04 19:33 DEBUG  WindowsBackend: windows_build=7600
08-04 19:33 DEBUG  WindowsBackend: gmt=5
08-04 19:33 DEBUG  WindowsBackend: country=IN
08-04 19:33 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-04 19:33 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-04 19:33 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-04 19:33 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-04 19:33 DEBUG  WindowsBackend: windows_language_code=1033
08-04 19:33 DEBUG  WindowsBackend: windows_language=English
08-04 19:33 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-04 19:33 DEBUG  WindowsBackend: bootloader=vista
08-04 19:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139081.738281 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(C: hd 139081.738281 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(D: hd 51108.4296875 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(E: hd 122483.632813 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.36132813 mb free fat32)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-04 19:33 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
08-04 19:33 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
08-04 19:33 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-04 19:33 DEBUG  WindowsBackend: keyboard_id=67699721
08-04 19:33 DEBUG  WindowsBackend: keyboard_layout=us
08-04 19:33 DEBUG  WindowsBackend: keyboard_variant=
08-04 19:33 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-04 19:33 DEBUG  CommonBackend: locale=en_IN
08-04 19:33 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-04 19:33 DEBUG  CommonBackend: Searching ISOs on USB devices
08-04 19:33 DEBUG  CommonBackend: Searching for local CDs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 INFO   root: Already installed, running the uninstaller...
08-04 19:33 INFO   root: Running the uninstaller...
08-04 19:33 INFO   CommonBackend: This is the uninstaller running
08-04 19:33 DEBUG  WindowsFrontend: __init__...
08-04 19:33 DEBUG  WindowsFrontend: on_init...
08-04 19:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\translations, languages=['en_IN', 'en']
08-04 19:33 INFO   root: Received settings
08-04 19:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\translations, languages=['en_IN', 'en']
08-04 19:33 DEBUG  TaskList: # Running tasklist...
08-04 19:33 DEBUG  TaskList: ## Running Remove bootloader entry...
08-04 19:33 DEBUG  WindowsBackend: Could not find bcd id
08-04 19:33 DEBUG  WindowsBackend: undo_bootini C:
08-04 19:33 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 139081.738281 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: undo_bootini D:
08-04 19:33 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 51108.4296875 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: undo_bootini E:
08-04 19:33 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 122483.632813 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: undo_bootini F:
08-04 19:33 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 92.4111328125 mb free fat32)
08-04 19:33 DEBUG  WindowsBackend: undo_bootini G:
08-04 19:33 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 2008.9765625 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: undo_bootini I:
08-04 19:33 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 3950.36132813 mb free fat32)
08-04 19:33 DEBUG  TaskList: ## Finished Remove bootloader entry
08-04 19:33 DEBUG  TaskList: ## Running Remove target dir...
08-04 19:33 DEBUG  CommonBackend: Deleting E:\ubuntu
08-04 19:33 DEBUG  TaskList: ## Finished Remove target dir
08-04 19:33 DEBUG  TaskList: ## Running Remove registry key...
08-04 19:33 DEBUG  TaskList: ## Finished Remove registry key
08-04 19:33 DEBUG  TaskList: # Finished tasklist
08-04 19:33 INFO   root: Almost finished uninstalling
08-04 19:33 INFO   root: Finished uninstallation
08-04 19:33 DEBUG  CommonBackend: Fetching basic info...
08-04 19:33 DEBUG  CommonBackend: original_exe=E:\Ubuntu_Setup\wubi.exe
08-04 19:33 DEBUG  CommonBackend: platform=win32
08-04 19:33 DEBUG  CommonBackend: osname=nt
08-04 19:33 DEBUG  WindowsBackend: arch=amd64
08-04 19:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\data\isolist.ini
08-04 19:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-04 19:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-04 19:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-04 19:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-04 19:33 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-04 19:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-04 19:33 DEBUG  WindowsBackend: Fetching host info...
08-04 19:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-04 19:33 DEBUG  WindowsBackend: windows version=vista
08-04 19:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-04 19:33 DEBUG  WindowsBackend: windows_sp=None
08-04 19:33 DEBUG  WindowsBackend: windows_build=7600
08-04 19:33 DEBUG  WindowsBackend: gmt=5
08-04 19:33 DEBUG  WindowsBackend: country=IN
08-04 19:33 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-04 19:33 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-04 19:33 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-04 19:33 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-04 19:33 DEBUG  WindowsBackend: windows_language_code=1033
08-04 19:33 DEBUG  WindowsBackend: windows_language=English
08-04 19:33 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-04 19:33 DEBUG  WindowsBackend: bootloader=vista
08-04 19:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139081.714844 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(C: hd 139081.714844 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(D: hd 51108.4296875 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(E: hd 122492.6875 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.36132813 mb free fat32)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-04 19:33 DEBUG  WindowsBackend: uninstaller_path=None
08-04 19:33 DEBUG  WindowsBackend: previous_target_dir=None
08-04 19:33 DEBUG  WindowsBackend: previous_distro_name=None
08-04 19:33 DEBUG  WindowsBackend: keyboard_id=67699721
08-04 19:33 DEBUG  WindowsBackend: keyboard_layout=us
08-04 19:33 DEBUG  WindowsBackend: keyboard_variant=
08-04 19:33 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-04 19:33 DEBUG  CommonBackend: Searching ISOs on USB devices
08-04 19:33 DEBUG  CommonBackend: Searching for local CDs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 INFO   root: Running the installer...
08-04 19:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\translations, languages=['en_IN', 'en']
08-04 19:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl888.tmp\translations, languages=['en_IN', 'en']
08-04 19:33 INFO   WindowsFrontend: Operation cancelled
08-04 19:33 DEBUG  WindowsFrontend: frontend.quit
08-04 19:33 DEBUG  WindowsFrontend: frontend.on_quit
08-04 19:33 DEBUG  root: application.on_quit
08-04 19:33 INFO   root: sys.exit
08-04 19:33 INFO   root: === wubi 12.04 rev272 ===
08-04 19:33 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-04 19:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\Ubuntu_Setup\\wubi.exe"', 'E:\\Ubuntu_Setup\\ubuntu-12.04.2-desktop-amd64.iso']
08-04 19:33 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\data
08-04 19:33 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\bin\7z.exe
08-04 19:33 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-04 19:33 DEBUG  CommonBackend: Fetching basic info...
08-04 19:33 DEBUG  CommonBackend: original_exe=E:\Ubuntu_Setup\wubi.exe
08-04 19:33 DEBUG  CommonBackend: platform=win32
08-04 19:33 DEBUG  CommonBackend: osname=nt
08-04 19:33 DEBUG  CommonBackend: language=en_IN
08-04 19:33 DEBUG  CommonBackend: encoding=cp1252
08-04 19:33 DEBUG  WindowsBackend: arch=amd64
08-04 19:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\data\isolist.ini
08-04 19:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-04 19:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-04 19:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-04 19:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-04 19:33 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-04 19:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-04 19:33 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-04 19:33 DEBUG  WindowsBackend: Fetching host info...
08-04 19:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-04 19:33 DEBUG  WindowsBackend: windows version=vista
08-04 19:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-04 19:33 DEBUG  WindowsBackend: windows_sp=None
08-04 19:33 DEBUG  WindowsBackend: windows_build=7600
08-04 19:33 DEBUG  WindowsBackend: gmt=5
08-04 19:33 DEBUG  WindowsBackend: country=IN
08-04 19:33 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-04 19:33 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-04 19:33 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-04 19:33 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-04 19:33 DEBUG  WindowsBackend: windows_language_code=1033
08-04 19:33 DEBUG  WindowsBackend: windows_language=English
08-04 19:33 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-04 19:33 DEBUG  WindowsBackend: bootloader=vista
08-04 19:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139081.535156 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(C: hd 139081.535156 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(D: hd 51108.4296875 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(E: hd 122492.6875 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.36132813 mb free fat32)
08-04 19:33 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-04 19:33 DEBUG  WindowsBackend: uninstaller_path=None
08-04 19:33 DEBUG  WindowsBackend: previous_target_dir=None
08-04 19:33 DEBUG  WindowsBackend: previous_distro_name=None
08-04 19:33 DEBUG  WindowsBackend: keyboard_id=67699721
08-04 19:33 DEBUG  WindowsBackend: keyboard_layout=us
08-04 19:33 DEBUG  WindowsBackend: keyboard_variant=
08-04 19:33 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-04 19:33 DEBUG  CommonBackend: locale=en_IN
08-04 19:33 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-04 19:33 DEBUG  CommonBackend: Searching ISOs on USB devices
08-04 19:33 DEBUG  CommonBackend: Searching for local CDs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 INFO   root: Running the installer...
08-04 19:33 DEBUG  WindowsFrontend: __init__...
08-04 19:33 DEBUG  WindowsFrontend: on_init...
08-04 19:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\translations, languages=['en_IN', 'en']
08-04 19:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\translations, languages=['en_IN', 'en']
08-04 19:33 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=deepraj
08-04 19:33 INFO   root: Received settings
08-04 19:33 DEBUG  CommonBackend: Searching for local CD
08-04 19:33 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:33 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:33 DEBUG  CommonBackend: Searching for local ISO
08-04 19:33 DEBUG  Distro:   checking Ubuntu ISO E:\Ubuntu_Setup\ubuntu-12.04.2-desktop-amd64.iso
08-04 19:33 DEBUG  Distro:     does not contain casper\vmlinuz
08-04 19:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl2F88.tmp\translations, languages=['en_US', 'en']
08-04 19:33 DEBUG  TaskList: # Running tasklist...
08-04 19:33 DEBUG  TaskList: ## Running select_target_dir...
08-04 19:33 INFO   WindowsBackend: Installing into E:\ubuntu
08-04 19:33 DEBUG  TaskList: ## Finished select_target_dir
08-04 19:33 DEBUG  TaskList: ## Running create_dir_structure...
08-04 19:33 DEBUG  CommonBackend: Creating dir E:\ubuntu
08-04 19:33 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
08-04 19:33 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
08-04 19:33 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
08-04 19:33 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
08-04 19:33 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
08-04 19:33 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
08-04 19:33 DEBUG  TaskList: ## Finished create_dir_structure
08-04 19:33 DEBUG  TaskList: ## Running create_uninstaller...
08-04 19:33 DEBUG  WindowsBackend: Copying uninstaller E:\Ubuntu_Setup\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
08-04 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
08-04 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
08-04 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-04 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
08-04 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev272
08-04 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-04 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-04 19:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-04 19:33 DEBUG  TaskList: ## Finished create_uninstaller
08-04 19:33 DEBUG  TaskList: ## Running create_preseed_diskimage...
08-04 19:33 DEBUG  TaskList: ## Finished create_preseed_diskimage
08-04 19:33 DEBUG  TaskList: ## Running get_diskimage...
08-04 19:33 DEBUG  TaskList: New task download
08-04 19:33 DEBUG  TaskList: ### Running download...
08-04 19:33 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > E:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
08-04 19:33 DEBUG  downloader: Download start filename=E:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz, basename=ubuntu-12.04.2-wubi-amd64.tar.xz, length=549666608, text=None
08-04 19:35 INFO   WindowsFrontend: Operation cancelled
08-04 19:35 DEBUG  WindowsFrontend: frontend.quit
08-04 19:35 DEBUG  WindowsFrontend: frontend.on_quit
08-04 19:35 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
08-04 19:35 DEBUG  TaskList: # Cancelling tasklist
08-04 19:35 DEBUG  downloader: download finished (read 10780672 bytes)
08-04 19:35 DEBUG  TaskList: ### Finished download
08-04 19:35 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
08-04 19:35 DEBUG  root: application.on_quit
08-04 19:35 DEBUG  root: Forceful exit
08-04 19:35 INFO   root: sys.exit
08-04 19:35 INFO   root: === wubi 12.04 rev272 ===
08-04 19:35 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-04 19:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\Ubuntu_Setup\\wubi.exe"']
08-04 19:35 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\data
08-04 19:35 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\bin\7z.exe
08-04 19:35 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-04 19:35 DEBUG  CommonBackend: Fetching basic info...
08-04 19:35 DEBUG  CommonBackend: original_exe=E:\Ubuntu_Setup\wubi.exe
08-04 19:35 DEBUG  CommonBackend: platform=win32
08-04 19:35 DEBUG  CommonBackend: osname=nt
08-04 19:35 DEBUG  CommonBackend: language=en_IN
08-04 19:35 DEBUG  CommonBackend: encoding=cp1252
08-04 19:35 DEBUG  WindowsBackend: arch=amd64
08-04 19:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\data\isolist.ini
08-04 19:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-04 19:35 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-04 19:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-04 19:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-04 19:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-04 19:35 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-04 19:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-04 19:35 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-04 19:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-04 19:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-04 19:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-04 19:35 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-04 19:35 DEBUG  WindowsBackend: Fetching host info...
08-04 19:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-04 19:35 DEBUG  WindowsBackend: windows version=vista
08-04 19:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-04 19:35 DEBUG  WindowsBackend: windows_sp=None
08-04 19:35 DEBUG  WindowsBackend: windows_build=7600
08-04 19:35 DEBUG  WindowsBackend: gmt=5
08-04 19:35 DEBUG  WindowsBackend: country=IN
08-04 19:35 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-04 19:35 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-04 19:35 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-04 19:35 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-04 19:35 DEBUG  WindowsBackend: windows_language_code=1033
08-04 19:35 DEBUG  WindowsBackend: windows_language=English
08-04 19:35 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-04 19:35 DEBUG  WindowsBackend: bootloader=vista
08-04 19:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139081.03125 mb free ntfs)
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(C: hd 139081.03125 mb free ntfs)
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(D: hd 51108.4296875 mb free ntfs)
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(E: hd 122480.023438 mb free ntfs)
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.36132813 mb free fat32)
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-04 19:35 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
08-04 19:35 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
08-04 19:35 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-04 19:35 DEBUG  WindowsBackend: keyboard_id=67699721
08-04 19:35 DEBUG  WindowsBackend: keyboard_layout=us
08-04 19:35 DEBUG  WindowsBackend: keyboard_variant=
08-04 19:35 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-04 19:35 DEBUG  CommonBackend: locale=en_IN
08-04 19:35 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-04 19:35 DEBUG  CommonBackend: Searching ISOs on USB devices
08-04 19:35 DEBUG  CommonBackend: Searching for local CDs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 INFO   root: Already installed, running the uninstaller...
08-04 19:35 INFO   root: Running the uninstaller...
08-04 19:35 INFO   CommonBackend: This is the uninstaller running
08-04 19:35 DEBUG  WindowsFrontend: __init__...
08-04 19:35 DEBUG  WindowsFrontend: on_init...
08-04 19:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\translations, languages=['en_IN', 'en']
08-04 19:35 INFO   root: Received settings
08-04 19:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\translations, languages=['en_IN', 'en']
08-04 19:35 DEBUG  TaskList: # Running tasklist...
08-04 19:35 DEBUG  TaskList: ## Running Remove bootloader entry...
08-04 19:35 DEBUG  WindowsBackend: Could not find bcd id
08-04 19:35 DEBUG  WindowsBackend: undo_bootini C:
08-04 19:35 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 139081.03125 mb free ntfs)
08-04 19:35 DEBUG  WindowsBackend: undo_bootini D:
08-04 19:35 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 51108.4296875 mb free ntfs)
08-04 19:35 DEBUG  WindowsBackend: undo_bootini E:
08-04 19:35 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 122480.023438 mb free ntfs)
08-04 19:35 DEBUG  WindowsBackend: undo_bootini F:
08-04 19:35 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 92.4111328125 mb free fat32)
08-04 19:35 DEBUG  WindowsBackend: undo_bootini G:
08-04 19:35 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 2008.9765625 mb free ntfs)
08-04 19:35 DEBUG  WindowsBackend: undo_bootini I:
08-04 19:35 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 3950.36132813 mb free fat32)
08-04 19:35 DEBUG  TaskList: ## Finished Remove bootloader entry
08-04 19:35 DEBUG  TaskList: ## Running Remove target dir...
08-04 19:35 DEBUG  CommonBackend: Deleting E:\ubuntu
08-04 19:35 DEBUG  TaskList: ## Finished Remove target dir
08-04 19:35 DEBUG  TaskList: ## Running Remove registry key...
08-04 19:35 DEBUG  TaskList: ## Finished Remove registry key
08-04 19:35 DEBUG  TaskList: # Finished tasklist
08-04 19:35 INFO   root: Almost finished uninstalling
08-04 19:35 INFO   root: Finished uninstallation
08-04 19:35 DEBUG  CommonBackend: Fetching basic info...
08-04 19:35 DEBUG  CommonBackend: original_exe=E:\Ubuntu_Setup\wubi.exe
08-04 19:35 DEBUG  CommonBackend: platform=win32
08-04 19:35 DEBUG  CommonBackend: osname=nt
08-04 19:35 DEBUG  WindowsBackend: arch=amd64
08-04 19:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\data\isolist.ini
08-04 19:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-04 19:35 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-04 19:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-04 19:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-04 19:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-04 19:35 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-04 19:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-04 19:35 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-04 19:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-04 19:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-04 19:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-04 19:35 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-04 19:35 DEBUG  WindowsBackend: Fetching host info...
08-04 19:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-04 19:35 DEBUG  WindowsBackend: windows version=vista
08-04 19:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-04 19:35 DEBUG  WindowsBackend: windows_sp=None
08-04 19:35 DEBUG  WindowsBackend: windows_build=7600
08-04 19:35 DEBUG  WindowsBackend: gmt=5
08-04 19:35 DEBUG  WindowsBackend: country=IN
08-04 19:35 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-04 19:35 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-04 19:35 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-04 19:35 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-04 19:35 DEBUG  WindowsBackend: windows_language_code=1033
08-04 19:35 DEBUG  WindowsBackend: windows_language=English
08-04 19:35 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-04 19:35 DEBUG  WindowsBackend: bootloader=vista
08-04 19:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139080.992188 mb free ntfs)
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(C: hd 139080.992188 mb free ntfs)
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(D: hd 51108.4296875 mb free ntfs)
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(E: hd 122492.6875 mb free ntfs)
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.36132813 mb free fat32)
08-04 19:35 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-04 19:35 DEBUG  WindowsBackend: uninstaller_path=None
08-04 19:35 DEBUG  WindowsBackend: previous_target_dir=None
08-04 19:35 DEBUG  WindowsBackend: previous_distro_name=None
08-04 19:35 DEBUG  WindowsBackend: keyboard_id=67699721
08-04 19:35 DEBUG  WindowsBackend: keyboard_layout=us
08-04 19:35 DEBUG  WindowsBackend: keyboard_variant=
08-04 19:35 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-04 19:35 DEBUG  CommonBackend: Searching ISOs on USB devices
08-04 19:35 DEBUG  CommonBackend: Searching for local CDs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:35 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:35 INFO   root: Running the installer...
08-04 19:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\translations, languages=['en_IN', 'en']
08-04 19:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylCF9E.tmp\translations, languages=['en_IN', 'en']
08-04 19:35 INFO   WindowsFrontend: Operation cancelled
08-04 19:35 DEBUG  WindowsFrontend: frontend.quit
08-04 19:35 DEBUG  WindowsFrontend: frontend.on_quit
08-04 19:35 DEBUG  root: application.on_quit
08-04 19:35 INFO   root: sys.exit
08-04 19:36 INFO   root: === wubi 12.04 rev272 ===
08-04 19:36 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-04 19:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Ubuntu_Setup\\wubi.exe"', 'C:\\Ubuntu_Setup\\ubuntu-12.04.2-desktop-amd64.iso']
08-04 19:36 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\data
08-04 19:36 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\bin\7z.exe
08-04 19:36 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-04 19:36 DEBUG  CommonBackend: Fetching basic info...
08-04 19:36 DEBUG  CommonBackend: original_exe=C:\Ubuntu_Setup\wubi.exe
08-04 19:36 DEBUG  CommonBackend: platform=win32
08-04 19:36 DEBUG  CommonBackend: osname=nt
08-04 19:36 DEBUG  CommonBackend: language=en_IN
08-04 19:36 DEBUG  CommonBackend: encoding=cp1252
08-04 19:36 DEBUG  WindowsBackend: arch=amd64
08-04 19:36 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\data\isolist.ini
08-04 19:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-04 19:36 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-04 19:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-04 19:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-04 19:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-04 19:36 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-04 19:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-04 19:36 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-04 19:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-04 19:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-04 19:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-04 19:36 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-04 19:36 DEBUG  WindowsBackend: Fetching host info...
08-04 19:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-04 19:36 DEBUG  WindowsBackend: windows version=vista
08-04 19:36 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-04 19:36 DEBUG  WindowsBackend: windows_sp=None
08-04 19:36 DEBUG  WindowsBackend: windows_build=7600
08-04 19:36 DEBUG  WindowsBackend: gmt=5
08-04 19:36 DEBUG  WindowsBackend: country=IN
08-04 19:36 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-04 19:36 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-04 19:36 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-04 19:36 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-04 19:36 DEBUG  WindowsBackend: windows_language_code=1033
08-04 19:36 DEBUG  WindowsBackend: windows_language=English
08-04 19:36 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-04 19:36 DEBUG  WindowsBackend: bootloader=vista
08-04 19:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 138383.542969 mb free ntfs)
08-04 19:36 DEBUG  WindowsBackend: drive=Drive(C: hd 138383.542969 mb free ntfs)
08-04 19:36 DEBUG  WindowsBackend: drive=Drive(D: hd 51108.4296875 mb free ntfs)
08-04 19:36 DEBUG  WindowsBackend: drive=Drive(E: hd 123190.078125 mb free ntfs)
08-04 19:36 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-04 19:36 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-04 19:36 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-04 19:36 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.36132813 mb free fat32)
08-04 19:36 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-04 19:36 DEBUG  WindowsBackend: uninstaller_path=None
08-04 19:36 DEBUG  WindowsBackend: previous_target_dir=None
08-04 19:36 DEBUG  WindowsBackend: previous_distro_name=None
08-04 19:36 DEBUG  WindowsBackend: keyboard_id=67699721
08-04 19:36 DEBUG  WindowsBackend: keyboard_layout=us
08-04 19:36 DEBUG  WindowsBackend: keyboard_variant=
08-04 19:36 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-04 19:36 DEBUG  CommonBackend: locale=en_IN
08-04 19:36 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-04 19:36 DEBUG  CommonBackend: Searching ISOs on USB devices
08-04 19:36 DEBUG  CommonBackend: Searching for local CDs
08-04 19:36 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:36 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:36 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:36 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:36 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:36 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:36 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:36 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:36 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:36 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:36 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:36 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:36 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:36 INFO   root: Running the installer...
08-04 19:36 DEBUG  WindowsFrontend: __init__...
08-04 19:36 DEBUG  WindowsFrontend: on_init...
08-04 19:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\translations, languages=['en_IN', 'en']
08-04 19:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\translations, languages=['en_IN', 'en']
08-04 19:36 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=deepraj
08-04 19:36 INFO   root: Received settings
08-04 19:36 DEBUG  CommonBackend: Searching for local CD
08-04 19:36 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 19:36 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 19:36 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 19:36 DEBUG  CommonBackend: Searching for local ISO
08-04 19:36 DEBUG  Distro:   checking Ubuntu ISO C:\Ubuntu_Setup\ubuntu-12.04.2-desktop-amd64.iso
08-04 19:36 DEBUG  Distro:     does not contain casper\vmlinuz
08-04 19:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl8E2B.tmp\translations, languages=['en_US', 'en']
08-04 19:36 DEBUG  TaskList: # Running tasklist...
08-04 19:36 DEBUG  TaskList: ## Running select_target_dir...
08-04 19:36 INFO   WindowsBackend: Installing into E:\ubuntu
08-04 19:36 DEBUG  TaskList: ## Finished select_target_dir
08-04 19:36 DEBUG  TaskList: ## Running create_dir_structure...
08-04 19:36 DEBUG  CommonBackend: Creating dir E:\ubuntu
08-04 19:36 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
08-04 19:36 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
08-04 19:36 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
08-04 19:36 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
08-04 19:36 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
08-04 19:36 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
08-04 19:36 DEBUG  TaskList: ## Finished create_dir_structure
08-04 19:36 DEBUG  TaskList: ## Running create_uninstaller...
08-04 19:36 DEBUG  WindowsBackend: Copying uninstaller C:\Ubuntu_Setup\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
08-04 19:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
08-04 19:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
08-04 19:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-04 19:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
08-04 19:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev272
08-04 19:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-04 19:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-04 19:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-04 19:36 DEBUG  TaskList: ## Finished create_uninstaller
08-04 19:36 DEBUG  TaskList: ## Running create_preseed_diskimage...
08-04 19:36 DEBUG  TaskList: ## Finished create_preseed_diskimage
08-04 19:36 DEBUG  TaskList: ## Running get_diskimage...
08-04 19:36 DEBUG  TaskList: New task download
08-04 19:36 DEBUG  TaskList: ### Running download...
08-04 19:36 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > E:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
08-04 19:36 DEBUG  downloader: Download start filename=E:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz, basename=ubuntu-12.04.2-wubi-amd64.tar.xz, length=549666608, text=None
08-04 20:36 DEBUG  downloader: download finished (read 489416565 bytes)
08-04 20:36 DEBUG  TaskList: ### Finished download
08-04 20:36 DEBUG  TaskList: ## Finished get_diskimage
08-04 20:36 DEBUG  TaskList: ## Running extract_diskimage...
08-04 20:38 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
08-04 20:38 DEBUG  TaskList: # Cancelling tasklist
08-04 20:38 DEBUG  TaskList: # Finished tasklist
08-04 20:38 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
08-04 20:40 INFO   root: === wubi 12.04 rev272 ===
08-04 20:40 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-04 20:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubuntu\\uninstall-wubi.exe"']
08-04 20:40 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\data
08-04 20:40 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\bin\7z.exe
08-04 20:40 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-04 20:40 DEBUG  CommonBackend: Fetching basic info...
08-04 20:40 DEBUG  CommonBackend: original_exe=E:\ubuntu\uninstall-wubi.exe
08-04 20:40 DEBUG  CommonBackend: platform=win32
08-04 20:40 DEBUG  CommonBackend: osname=nt
08-04 20:40 DEBUG  CommonBackend: language=en_IN
08-04 20:40 DEBUG  CommonBackend: encoding=cp1252
08-04 20:40 DEBUG  WindowsBackend: arch=amd64
08-04 20:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\data\isolist.ini
08-04 20:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-04 20:40 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-04 20:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-04 20:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-04 20:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-04 20:40 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-04 20:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-04 20:40 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-04 20:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-04 20:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-04 20:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-04 20:40 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-04 20:40 DEBUG  WindowsBackend: Fetching host info...
08-04 20:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-04 20:40 DEBUG  WindowsBackend: windows version=vista
08-04 20:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-04 20:40 DEBUG  WindowsBackend: windows_sp=None
08-04 20:40 DEBUG  WindowsBackend: windows_build=7600
08-04 20:40 DEBUG  WindowsBackend: gmt=5
08-04 20:40 DEBUG  WindowsBackend: country=IN
08-04 20:40 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-04 20:40 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-04 20:40 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-04 20:40 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-04 20:40 DEBUG  WindowsBackend: windows_language_code=1033
08-04 20:40 DEBUG  WindowsBackend: windows_language=English
08-04 20:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-04 20:40 DEBUG  WindowsBackend: bootloader=vista
08-04 20:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 138374.300781 mb free ntfs)
08-04 20:40 DEBUG  WindowsBackend: drive=Drive(C: hd 138374.300781 mb free ntfs)
08-04 20:40 DEBUG  WindowsBackend: drive=Drive(D: hd 51108.4296875 mb free ntfs)
08-04 20:40 DEBUG  WindowsBackend: drive=Drive(E: hd 120594.609375 mb free ntfs)
08-04 20:40 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-04 20:40 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-04 20:40 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-04 20:40 DEBUG  WindowsBackend: drive=Drive(I: removable 3950.36132813 mb free fat32)
08-04 20:40 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-04 20:40 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
08-04 20:40 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
08-04 20:40 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-04 20:40 DEBUG  WindowsBackend: keyboard_id=67699721
08-04 20:40 DEBUG  WindowsBackend: keyboard_layout=us
08-04 20:40 DEBUG  WindowsBackend: keyboard_variant=
08-04 20:40 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-04 20:40 DEBUG  CommonBackend: locale=en_IN
08-04 20:40 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-04 20:40 DEBUG  CommonBackend: Searching ISOs on USB devices
08-04 20:40 DEBUG  CommonBackend: Searching for local CDs
08-04 20:40 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 20:40 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 20:40 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 20:40 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 20:40 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 20:40 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 20:40 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 20:40 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 20:40 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 20:40 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 20:40 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 20:40 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 20:40 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 20:40 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 20:40 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 20:40 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 20:40 INFO   root: Running the uninstaller...
08-04 20:40 INFO   CommonBackend: This is the uninstaller running
08-04 20:40 DEBUG  WindowsFrontend: __init__...
08-04 20:40 DEBUG  WindowsFrontend: on_init...
08-04 20:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\translations, languages=['en_IN', 'en']
08-04 20:40 INFO   root: Received settings
08-04 20:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\translations, languages=['en_IN', 'en']
08-04 20:40 DEBUG  TaskList: # Running tasklist...
08-04 20:40 DEBUG  TaskList: ## Running Remove bootloader entry...
08-04 20:40 DEBUG  WindowsBackend: Could not find bcd id
08-04 20:40 DEBUG  WindowsBackend: undo_bootini C:
08-04 20:40 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 138374.300781 mb free ntfs)
08-04 20:40 DEBUG  WindowsBackend: undo_bootini D:
08-04 20:40 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 51108.4296875 mb free ntfs)
08-04 20:40 DEBUG  WindowsBackend: undo_bootini E:
08-04 20:40 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 120594.609375 mb free ntfs)
08-04 20:40 DEBUG  WindowsBackend: undo_bootini F:
08-04 20:40 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 92.4111328125 mb free fat32)
08-04 20:40 DEBUG  WindowsBackend: undo_bootini G:
08-04 20:40 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 2008.9765625 mb free ntfs)
08-04 20:40 DEBUG  WindowsBackend: undo_bootini I:
08-04 20:40 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 3950.36132813 mb free fat32)
08-04 20:40 DEBUG  TaskList: ## Finished Remove bootloader entry
08-04 20:40 DEBUG  TaskList: ## Running Remove target dir...
08-04 20:40 DEBUG  CommonBackend: Deleting E:\ubuntu
08-04 20:40 DEBUG  TaskList: ## Finished Remove target dir
08-04 20:40 DEBUG  TaskList: ## Running Remove registry key...
08-04 20:40 DEBUG  TaskList: ## Finished Remove registry key
08-04 20:40 DEBUG  TaskList: # Finished tasklist
08-04 20:40 INFO   root: Almost finished uninstalling
08-04 20:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4174.tmp\translations, languages=['en_IN', 'en']
08-04 20:40 INFO   root: Finished uninstallation
08-04 20:40 DEBUG  root: application.quit
08-04 20:40 DEBUG  WindowsFrontend: frontend.quit
08-04 20:40 DEBUG  WindowsFrontend: frontend.on_quit
08-04 20:40 DEBUG  root: application.on_quit
08-04 20:40 INFO   root: sys.exit
08-04 22:29 INFO   root: === wubi 12.04 rev272 ===
08-04 22:29 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-04 22:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
08-04 22:29 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\data
08-04 22:29 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\bin\7z.exe
08-04 22:29 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-04 22:29 DEBUG  CommonBackend: Fetching basic info...
08-04 22:29 DEBUG  CommonBackend: original_exe=I:\wubi.exe
08-04 22:29 DEBUG  CommonBackend: platform=win32
08-04 22:29 DEBUG  CommonBackend: osname=nt
08-04 22:29 DEBUG  CommonBackend: language=en_IN
08-04 22:29 DEBUG  CommonBackend: encoding=cp1252
08-04 22:29 DEBUG  WindowsBackend: arch=amd64
08-04 22:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\data\isolist.ini
08-04 22:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-04 22:29 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-04 22:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-04 22:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-04 22:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-04 22:29 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-04 22:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-04 22:29 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-04 22:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-04 22:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-04 22:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-04 22:29 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-04 22:29 DEBUG  WindowsBackend: Fetching host info...
08-04 22:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-04 22:29 DEBUG  WindowsBackend: windows version=vista
08-04 22:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-04 22:29 DEBUG  WindowsBackend: windows_sp=None
08-04 22:29 DEBUG  WindowsBackend: windows_build=7600
08-04 22:29 DEBUG  WindowsBackend: gmt=5
08-04 22:29 DEBUG  WindowsBackend: country=IN
08-04 22:29 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-04 22:29 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-04 22:29 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-04 22:29 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-04 22:29 DEBUG  WindowsBackend: windows_language_code=1033
08-04 22:29 DEBUG  WindowsBackend: windows_language=English
08-04 22:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-04 22:29 DEBUG  WindowsBackend: bootloader=vista
08-04 22:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 138028.148438 mb free ntfs)
08-04 22:29 DEBUG  WindowsBackend: drive=Drive(C: hd 138028.148438 mb free ntfs)
08-04 22:29 DEBUG  WindowsBackend: drive=Drive(D: hd 51108.6835938 mb free ntfs)
08-04 22:29 DEBUG  WindowsBackend: drive=Drive(E: hd 107830.074219 mb free ntfs)
08-04 22:29 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-04 22:29 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-04 22:29 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-04 22:29 DEBUG  WindowsBackend: drive=Drive(I: removable 2806.08984375 mb free ntfs)
08-04 22:29 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-04 22:29 DEBUG  WindowsBackend: uninstaller_path=None
08-04 22:29 DEBUG  WindowsBackend: previous_target_dir=None
08-04 22:29 DEBUG  WindowsBackend: previous_distro_name=None
08-04 22:29 DEBUG  WindowsBackend: keyboard_id=67699721
08-04 22:29 DEBUG  WindowsBackend: keyboard_layout=us
08-04 22:29 DEBUG  WindowsBackend: keyboard_variant=
08-04 22:29 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-04 22:29 DEBUG  CommonBackend: locale=en_IN
08-04 22:29 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-04 22:29 DEBUG  CommonBackend: Searching ISOs on USB devices
08-04 22:29 DEBUG  CommonBackend: Searching for local CDs
08-04 22:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 22:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 22:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 22:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 22:29 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 22:29 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 22:29 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 22:29 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 22:29 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 22:29 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 22:29 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 22:29 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain I:\casper\vmlinuz
08-04 22:29 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-04 22:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 22:29 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-04 22:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-04 22:29 INFO   root: Running the installer...
08-04 22:29 DEBUG  WindowsFrontend: __init__...
08-04 22:29 DEBUG  WindowsFrontend: on_init...
08-04 22:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\translations, languages=['en_IN', 'en']
08-04 22:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl737B.tmp\translations, languages=['en_IN', 'en']
08-04 22:29 INFO   WindowsFrontend: Operation cancelled
08-04 22:29 DEBUG  WindowsFrontend: frontend.quit
08-04 22:29 DEBUG  WindowsFrontend: frontend.on_quit
08-04 22:29 DEBUG  root: application.on_quit
08-04 22:29 INFO   root: sys.exit
08-07 20:28 INFO   root: === wubi 12.04 rev272 ===
08-07 20:28 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-07 20:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Ubuntu_Setup\\wubi.exe"']
08-07 20:28 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\data
08-07 20:28 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\bin\7z.exe
08-07 20:28 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-07 20:28 DEBUG  CommonBackend: Fetching basic info...
08-07 20:28 DEBUG  CommonBackend: original_exe=C:\Ubuntu_Setup\wubi.exe
08-07 20:28 DEBUG  CommonBackend: platform=win32
08-07 20:28 DEBUG  CommonBackend: osname=nt
08-07 20:28 DEBUG  CommonBackend: language=en_IN
08-07 20:28 DEBUG  CommonBackend: encoding=cp1252
08-07 20:28 DEBUG  WindowsBackend: arch=amd64
08-07 20:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\data\isolist.ini
08-07 20:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-07 20:28 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-07 20:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-07 20:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-07 20:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-07 20:28 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-07 20:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-07 20:28 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-07 20:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-07 20:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-07 20:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-07 20:28 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-07 20:28 DEBUG  WindowsBackend: Fetching host info...
08-07 20:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-07 20:28 DEBUG  WindowsBackend: windows version=vista
08-07 20:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-07 20:28 DEBUG  WindowsBackend: windows_sp=None
08-07 20:28 DEBUG  WindowsBackend: windows_build=7600
08-07 20:28 DEBUG  WindowsBackend: gmt=5
08-07 20:28 DEBUG  WindowsBackend: country=IN
08-07 20:28 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-07 20:28 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-07 20:28 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-07 20:28 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-07 20:28 DEBUG  WindowsBackend: windows_language_code=1033
08-07 20:28 DEBUG  WindowsBackend: windows_language=English
08-07 20:28 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-07 20:28 DEBUG  WindowsBackend: bootloader=vista
08-07 20:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 137862.746094 mb free ntfs)
08-07 20:28 DEBUG  WindowsBackend: drive=Drive(C: hd 137862.746094 mb free ntfs)
08-07 20:28 DEBUG  WindowsBackend: drive=Drive(E: hd 174388.042969 mb free ntfs)
08-07 20:28 DEBUG  WindowsBackend: drive=Drive(F: hd 92.4111328125 mb free fat32)
08-07 20:28 DEBUG  WindowsBackend: drive=Drive(G: hd 2008.9765625 mb free ntfs)
08-07 20:28 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-07 20:28 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
08-07 20:28 DEBUG  WindowsBackend: uninstaller_path=None
08-07 20:28 DEBUG  WindowsBackend: previous_target_dir=None
08-07 20:28 DEBUG  WindowsBackend: previous_distro_name=None
08-07 20:28 DEBUG  WindowsBackend: keyboard_id=67699721
08-07 20:28 DEBUG  WindowsBackend: keyboard_layout=us
08-07 20:28 DEBUG  WindowsBackend: keyboard_variant=
08-07 20:28 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-07 20:28 DEBUG  CommonBackend: locale=en_IN
08-07 20:28 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-07 20:28 DEBUG  CommonBackend: Searching ISOs on USB devices
08-07 20:28 DEBUG  CommonBackend: Searching for local CDs
08-07 20:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp is a valid Ubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp is a valid Ubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp is a valid Kubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp is a valid Kubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp is a valid Xubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp is a valid Xubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp is a valid Mythbuntu CD
08-07 20:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp is a valid Mythbuntu CD
08-07 20:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp is a valid Edubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp is a valid Edubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp is a valid Lubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp is a valid Lubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-07 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-07 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-07 20:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-07 20:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-07 20:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-07 20:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-07 20:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-07 20:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-07 20:28 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-07 20:28 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-07 20:28 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
08-07 20:28 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-07 20:28 INFO   root: Running the installer...
08-07 20:28 DEBUG  WindowsFrontend: __init__...
08-07 20:28 DEBUG  WindowsFrontend: on_init...
08-07 20:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\translations, languages=['en_IN', 'en']
08-07 20:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylBE11.tmp\translations, languages=['en_IN', 'en']
08-07 20:28 INFO   WindowsFrontend: Operation cancelled
08-07 20:28 DEBUG  WindowsFrontend: frontend.quit
08-07 20:28 DEBUG  WindowsFrontend: frontend.on_quit
08-07 20:28 DEBUG  root: application.on_quit
08-07 20:28 INFO   root: sys.exit
08-07 20:31 INFO   root: === wubi 12.04 rev272 ===
08-07 20:31 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-07 20:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Ubuntu_Setup\\wubi.exe"']
08-07 20:31 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\data
08-07 20:31 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\bin\7z.exe
08-07 20:31 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-07 20:31 DEBUG  CommonBackend: Fetching basic info...
08-07 20:31 DEBUG  CommonBackend: original_exe=C:\Ubuntu_Setup\wubi.exe
08-07 20:31 DEBUG  CommonBackend: platform=win32
08-07 20:31 DEBUG  CommonBackend: osname=nt
08-07 20:31 DEBUG  CommonBackend: language=en_IN
08-07 20:31 DEBUG  CommonBackend: encoding=cp1252
08-07 20:31 DEBUG  WindowsBackend: arch=amd64
08-07 20:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\data\isolist.ini
08-07 20:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-07 20:31 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-07 20:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-07 20:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-07 20:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-07 20:31 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-07 20:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-07 20:31 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-07 20:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-07 20:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-07 20:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-07 20:31 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-07 20:31 DEBUG  WindowsBackend: Fetching host info...
08-07 20:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-07 20:31 DEBUG  WindowsBackend: windows version=vista
08-07 20:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-07 20:31 DEBUG  WindowsBackend: windows_sp=None
08-07 20:31 DEBUG  WindowsBackend: windows_build=7600
08-07 20:31 DEBUG  WindowsBackend: gmt=5
08-07 20:31 DEBUG  WindowsBackend: country=IN
08-07 20:31 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-07 20:31 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-07 20:31 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-07 20:31 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-07 20:31 DEBUG  WindowsBackend: windows_language_code=1033
08-07 20:31 DEBUG  WindowsBackend: windows_language=English
08-07 20:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-07 20:31 DEBUG  WindowsBackend: bootloader=vista
08-07 20:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 137862.058594 mb free ntfs)
08-07 20:31 DEBUG  WindowsBackend: drive=Drive(C: hd 137862.058594 mb free ntfs)
08-07 20:31 DEBUG  WindowsBackend: drive=Drive(D: hd 174388.042969 mb free ntfs)
08-07 20:31 DEBUG  WindowsBackend: drive=Drive(E: hd 92.4111328125 mb free fat32)
08-07 20:31 DEBUG  WindowsBackend: drive=Drive(F: hd 2008.9765625 mb free ntfs)
08-07 20:31 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
08-07 20:31 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-07 20:31 DEBUG  WindowsBackend: uninstaller_path=None
08-07 20:31 DEBUG  WindowsBackend: previous_target_dir=None
08-07 20:31 DEBUG  WindowsBackend: previous_distro_name=None
08-07 20:31 DEBUG  WindowsBackend: keyboard_id=67699721
08-07 20:31 DEBUG  WindowsBackend: keyboard_layout=us
08-07 20:31 DEBUG  WindowsBackend: keyboard_variant=
08-07 20:31 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-07 20:31 DEBUG  CommonBackend: locale=en_IN
08-07 20:31 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-07 20:31 DEBUG  CommonBackend: Searching ISOs on USB devices
08-07 20:31 DEBUG  CommonBackend: Searching for local CDs
08-07 20:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp is a valid Kubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp is a valid Kubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp is a valid Xubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp is a valid Xubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp is a valid Mythbuntu CD
08-07 20:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp is a valid Mythbuntu CD
08-07 20:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp is a valid Edubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp is a valid Edubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp is a valid Lubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp is a valid Lubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-07 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-07 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-07 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-07 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-07 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-07 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-07 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-07 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-07 20:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-07 20:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:31 INFO   root: Running the installer...
08-07 20:31 DEBUG  WindowsFrontend: __init__...
08-07 20:31 DEBUG  WindowsFrontend: on_init...
08-07 20:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\translations, languages=['en_IN', 'en']
08-07 20:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\translations, languages=['en_IN', 'en']
08-07 20:31 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=15000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=deepraj
08-07 20:31 INFO   root: Received settings
08-07 20:31 DEBUG  CommonBackend: Searching for local CD
08-07 20:31 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 20:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-07 20:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 20:31 DEBUG  CommonBackend: Searching for local ISO
08-07 20:31 DEBUG  Distro:   checking Ubuntu ISO C:\Ubuntu_Setup\ubuntu-12.04.2-desktop-amd64.iso
08-07 20:31 DEBUG  Distro:     does not contain casper\vmlinuz
08-07 20:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pylA6AB.tmp\translations, languages=['en_US', 'en']
08-07 20:31 DEBUG  TaskList: # Running tasklist...
08-07 20:31 DEBUG  TaskList: ## Running select_target_dir...
08-07 20:31 INFO   WindowsBackend: Installing into D:\ubuntu
08-07 20:31 DEBUG  TaskList: ## Finished select_target_dir
08-07 20:31 DEBUG  TaskList: ## Running create_dir_structure...
08-07 20:31 DEBUG  CommonBackend: Creating dir D:\ubuntu
08-07 20:31 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
08-07 20:31 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
08-07 20:31 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
08-07 20:31 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
08-07 20:31 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
08-07 20:31 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
08-07 20:31 DEBUG  TaskList: ## Finished create_dir_structure
08-07 20:31 DEBUG  TaskList: ## Running create_uninstaller...
08-07 20:31 DEBUG  WindowsBackend: Copying uninstaller C:\Ubuntu_Setup\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
08-07 20:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
08-07 20:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
08-07 20:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-07 20:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
08-07 20:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev272
08-07 20:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-07 20:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-07 20:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-07 20:31 DEBUG  TaskList: ## Finished create_uninstaller
08-07 20:31 DEBUG  TaskList: ## Running create_preseed_diskimage...
08-07 20:31 DEBUG  TaskList: ## Finished create_preseed_diskimage
08-07 20:31 DEBUG  TaskList: ## Running get_diskimage...
08-07 20:31 DEBUG  TaskList: New task download
08-07 20:31 DEBUG  TaskList: ### Running download...
08-07 20:31 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > D:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
08-07 20:31 DEBUG  downloader: Download start filename=D:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz, basename=ubuntu-12.04.2-wubi-amd64.tar.xz, length=549666608, text=None
08-07 21:24 DEBUG  TaskList: ### Finished download
08-07 21:24 DEBUG  downloader: download finished (read 549666608 bytes)
08-07 21:24 DEBUG  TaskList: ## Finished get_diskimage
08-07 21:24 DEBUG  TaskList: ## Running extract_diskimage...
08-07 21:25 DEBUG  TaskList: ## Finished extract_diskimage
08-07 21:25 DEBUG  TaskList: ## Running choose_disk_sizes...
08-07 21:25 DEBUG  WindowsBackend: total size=15000
  root=14744
  swap=256
  home=0
  usr=0
08-07 21:25 DEBUG  TaskList: ## Finished choose_disk_sizes
08-07 21:25 DEBUG  TaskList: ## Running expand_diskimage...
08-07 21:26 DEBUG  TaskList: ## Finished expand_diskimage
08-07 21:26 DEBUG  TaskList: ## Running create_swap_diskimage...
08-07 21:26 DEBUG  TaskList: ## Finished create_swap_diskimage
08-07 21:26 DEBUG  TaskList: ## Running modify_bootloader...
08-07 21:26 DEBUG  TaskList: New task modify_bcd
08-07 21:26 DEBUG  TaskList: ### Running modify_bcd...
08-07 21:26 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 137862.058594 mb free ntfs)
08-07 21:26 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {226b5c47-6353-11e2-bdad-8af5da54fbf8} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {226b5c47-6353-11e2-bdad-8af5da54fbf8} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
08-07 21:26 DEBUG  TaskList: # Cancelling tasklist
08-07 21:26 DEBUG  TaskList: New task modify_bcd
08-07 21:26 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {226b5c47-6353-11e2-bdad-8af5da54fbf8} device partition=D:
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
>>command=C:\Windows\System32\bcdedit.exe /set {226b5c47-6353-11e2-bdad-8af5da54fbf8} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
08-07 21:26 DEBUG  TaskList: New task modify_bcd
08-07 21:26 DEBUG  TaskList: New task modify_bcd
08-07 21:26 DEBUG  TaskList: ## Finished modify_bootloader
08-07 21:26 DEBUG  TaskList: # Finished tasklist
08-07 21:28 INFO   root: === wubi 12.04 rev272 ===
08-07 21:28 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-07 21:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Ubuntu_Setup\\wubi.exe"']
08-07 21:28 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\data
08-07 21:28 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\bin\7z.exe
08-07 21:28 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-07 21:28 DEBUG  CommonBackend: Fetching basic info...
08-07 21:28 DEBUG  CommonBackend: original_exe=C:\Ubuntu_Setup\wubi.exe
08-07 21:28 DEBUG  CommonBackend: platform=win32
08-07 21:28 DEBUG  CommonBackend: osname=nt
08-07 21:28 DEBUG  CommonBackend: language=en_IN
08-07 21:28 DEBUG  CommonBackend: encoding=cp1252
08-07 21:28 DEBUG  WindowsBackend: arch=amd64
08-07 21:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\data\isolist.ini
08-07 21:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-07 21:28 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-07 21:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-07 21:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-07 21:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-07 21:28 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-07 21:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-07 21:28 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-07 21:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-07 21:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-07 21:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-07 21:28 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-07 21:28 DEBUG  WindowsBackend: Fetching host info...
08-07 21:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-07 21:28 DEBUG  WindowsBackend: windows version=vista
08-07 21:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-07 21:28 DEBUG  WindowsBackend: windows_sp=None
08-07 21:28 DEBUG  WindowsBackend: windows_build=7600
08-07 21:28 DEBUG  WindowsBackend: gmt=5
08-07 21:28 DEBUG  WindowsBackend: country=IN
08-07 21:28 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-07 21:28 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-07 21:28 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-07 21:28 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-07 21:28 DEBUG  WindowsBackend: windows_language_code=1033
08-07 21:28 DEBUG  WindowsBackend: windows_language=English
08-07 21:28 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-07 21:28 DEBUG  WindowsBackend: bootloader=vista
08-07 21:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 137861.214844 mb free ntfs)
08-07 21:28 DEBUG  WindowsBackend: drive=Drive(C: hd 137861.214844 mb free ntfs)
08-07 21:28 DEBUG  WindowsBackend: drive=Drive(D: hd 171319.265625 mb free ntfs)
08-07 21:28 DEBUG  WindowsBackend: drive=Drive(E: hd 92.4111328125 mb free fat32)
08-07 21:28 DEBUG  WindowsBackend: drive=Drive(F: hd 2008.9765625 mb free ntfs)
08-07 21:28 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
08-07 21:28 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-07 21:28 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
08-07 21:28 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
08-07 21:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-07 21:28 DEBUG  WindowsBackend: keyboard_id=67699721
08-07 21:28 DEBUG  WindowsBackend: keyboard_layout=us
08-07 21:28 DEBUG  WindowsBackend: keyboard_variant=
08-07 21:28 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-07 21:28 DEBUG  CommonBackend: locale=en_IN
08-07 21:28 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-07 21:28 DEBUG  CommonBackend: Searching ISOs on USB devices
08-07 21:28 DEBUG  CommonBackend: Searching for local CDs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 INFO   root: Already installed, running the uninstaller...
08-07 21:28 INFO   root: Running the uninstaller...
08-07 21:28 INFO   CommonBackend: This is the uninstaller running
08-07 21:28 DEBUG  WindowsFrontend: __init__...
08-07 21:28 DEBUG  WindowsFrontend: on_init...
08-07 21:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\translations, languages=['en_IN', 'en']
08-07 21:28 INFO   root: Received settings
08-07 21:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\translations, languages=['en_IN', 'en']
08-07 21:28 DEBUG  TaskList: # Running tasklist...
08-07 21:28 DEBUG  TaskList: ## Running Remove bootloader entry...
08-07 21:28 DEBUG  WindowsBackend: Could not find bcd id
08-07 21:28 DEBUG  WindowsBackend: undo_bootini C:
08-07 21:28 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 137861.214844 mb free ntfs)
08-07 21:28 DEBUG  WindowsBackend: undo_bootini D:
08-07 21:28 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 171319.265625 mb free ntfs)
08-07 21:28 DEBUG  WindowsBackend: undo_bootini E:
08-07 21:28 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 92.4111328125 mb free fat32)
08-07 21:28 DEBUG  WindowsBackend: undo_bootini F:
08-07 21:28 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 2008.9765625 mb free ntfs)
08-07 21:28 DEBUG  TaskList: ## Finished Remove bootloader entry
08-07 21:28 DEBUG  TaskList: ## Running Remove target dir...
08-07 21:28 DEBUG  CommonBackend: Deleting D:\ubuntu
08-07 21:28 DEBUG  TaskList: ## Finished Remove target dir
08-07 21:28 DEBUG  TaskList: ## Running Remove registry key...
08-07 21:28 DEBUG  TaskList: ## Finished Remove registry key
08-07 21:28 DEBUG  TaskList: # Finished tasklist
08-07 21:28 INFO   root: Almost finished uninstalling
08-07 21:28 INFO   root: Finished uninstallation
08-07 21:28 DEBUG  CommonBackend: Fetching basic info...
08-07 21:28 DEBUG  CommonBackend: original_exe=C:\Ubuntu_Setup\wubi.exe
08-07 21:28 DEBUG  CommonBackend: platform=win32
08-07 21:28 DEBUG  CommonBackend: osname=nt
08-07 21:28 DEBUG  WindowsBackend: arch=amd64
08-07 21:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\data\isolist.ini
08-07 21:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-07 21:28 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-07 21:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-07 21:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-07 21:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-07 21:28 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-07 21:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-07 21:28 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-07 21:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-07 21:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-07 21:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-07 21:28 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-07 21:28 DEBUG  WindowsBackend: Fetching host info...
08-07 21:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-07 21:28 DEBUG  WindowsBackend: windows version=vista
08-07 21:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-07 21:28 DEBUG  WindowsBackend: windows_sp=None
08-07 21:28 DEBUG  WindowsBackend: windows_build=7600
08-07 21:28 DEBUG  WindowsBackend: gmt=5
08-07 21:28 DEBUG  WindowsBackend: country=IN
08-07 21:28 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-07 21:28 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-07 21:28 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-07 21:28 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-07 21:28 DEBUG  WindowsBackend: windows_language_code=1033
08-07 21:28 DEBUG  WindowsBackend: windows_language=English
08-07 21:28 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-07 21:28 DEBUG  WindowsBackend: bootloader=vista
08-07 21:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 137861.320313 mb free ntfs)
08-07 21:28 DEBUG  WindowsBackend: drive=Drive(C: hd 137861.320313 mb free ntfs)
08-07 21:28 DEBUG  WindowsBackend: drive=Drive(D: hd 174388.042969 mb free ntfs)
08-07 21:28 DEBUG  WindowsBackend: drive=Drive(E: hd 92.4111328125 mb free fat32)
08-07 21:28 DEBUG  WindowsBackend: drive=Drive(F: hd 2008.9765625 mb free ntfs)
08-07 21:28 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
08-07 21:28 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-07 21:28 DEBUG  WindowsBackend: uninstaller_path=None
08-07 21:28 DEBUG  WindowsBackend: previous_target_dir=None
08-07 21:28 DEBUG  WindowsBackend: previous_distro_name=None
08-07 21:28 DEBUG  WindowsBackend: keyboard_id=67699721
08-07 21:28 DEBUG  WindowsBackend: keyboard_layout=us
08-07 21:28 DEBUG  WindowsBackend: keyboard_variant=
08-07 21:28 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-07 21:28 DEBUG  CommonBackend: Searching ISOs on USB devices
08-07 21:28 DEBUG  CommonBackend: Searching for local CDs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-07 21:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 21:28 INFO   root: Running the installer...
08-07 21:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\translations, languages=['en_IN', 'en']
08-07 21:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl9B66.tmp\translations, languages=['en_IN', 'en']
08-07 21:28 INFO   WindowsFrontend: Operation cancelled
08-07 21:28 DEBUG  WindowsFrontend: frontend.quit
08-07 21:28 DEBUG  WindowsFrontend: frontend.on_quit
08-07 21:28 DEBUG  root: application.on_quit
08-07 21:28 INFO   root: sys.exit
08-07 23:12 INFO   root: === wubi 12.04 rev272 ===
08-07 23:12 DEBUG  root: Logfile is c:\users\deepraj\appdata\local\temp\wubi-12.04-rev272.log
08-07 23:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Ubuntu_Setup\\wubi.exe"']
08-07 23:12 DEBUG  CommonBackend: data_dir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\data
08-07 23:12 DEBUG  WindowsBackend: 7z=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\bin\7z.exe
08-07 23:12 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-07 23:12 DEBUG  CommonBackend: Fetching basic info...
08-07 23:12 DEBUG  CommonBackend: original_exe=C:\Ubuntu_Setup\wubi.exe
08-07 23:12 DEBUG  CommonBackend: platform=win32
08-07 23:12 DEBUG  CommonBackend: osname=nt
08-07 23:12 DEBUG  CommonBackend: language=en_IN
08-07 23:12 DEBUG  CommonBackend: encoding=cp1252
08-07 23:12 DEBUG  WindowsBackend: arch=amd64
08-07 23:12 DEBUG  CommonBackend: Parsing isolist=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\data\isolist.ini
08-07 23:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-07 23:12 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
08-07 23:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-07 23:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-07 23:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-07 23:12 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
08-07 23:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-07 23:12 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
08-07 23:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-07 23:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-07 23:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-07 23:12 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
08-07 23:12 DEBUG  WindowsBackend: Fetching host info...
08-07 23:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-07 23:12 DEBUG  WindowsBackend: windows version=vista
08-07 23:12 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-07 23:12 DEBUG  WindowsBackend: windows_sp=None
08-07 23:12 DEBUG  WindowsBackend: windows_build=7600
08-07 23:12 DEBUG  WindowsBackend: gmt=5
08-07 23:12 DEBUG  WindowsBackend: country=IN
08-07 23:12 DEBUG  WindowsBackend: timezone=Asia/Calcutta
08-07 23:12 DEBUG  WindowsBackend: windows_username=dEEPRAJ
08-07 23:12 DEBUG  WindowsBackend: user_full_name=dEEPRAJ
08-07 23:12 DEBUG  WindowsBackend: user_directory=C:\Users\dEEPRAJ
08-07 23:12 DEBUG  WindowsBackend: windows_language_code=1033
08-07 23:12 DEBUG  WindowsBackend: windows_language=English
08-07 23:12 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
08-07 23:12 DEBUG  WindowsBackend: bootloader=vista
08-07 23:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 137498.25 mb free ntfs)
08-07 23:12 DEBUG  WindowsBackend: drive=Drive(C: hd 137498.25 mb free ntfs)
08-07 23:12 DEBUG  WindowsBackend: drive=Drive(D: hd 174388.042969 mb free ntfs)
08-07 23:12 DEBUG  WindowsBackend: drive=Drive(E: hd 92.4111328125 mb free fat32)
08-07 23:12 DEBUG  WindowsBackend: drive=Drive(F: hd 2008.9765625 mb free ntfs)
08-07 23:12 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
08-07 23:12 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-07 23:12 DEBUG  WindowsBackend: drive=Drive(K: hd 849714.546875 mb free ntfs)
08-07 23:12 DEBUG  WindowsBackend: uninstaller_path=None
08-07 23:12 DEBUG  WindowsBackend: previous_target_dir=None
08-07 23:12 DEBUG  WindowsBackend: previous_distro_name=None
08-07 23:12 DEBUG  WindowsBackend: keyboard_id=67699721
08-07 23:12 DEBUG  WindowsBackend: keyboard_layout=us
08-07 23:12 DEBUG  WindowsBackend: keyboard_variant=
08-07 23:12 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
08-07 23:12 DEBUG  CommonBackend: locale=en_IN
08-07 23:12 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-07 23:12 DEBUG  CommonBackend: Searching ISOs on USB devices
08-07 23:12 DEBUG  CommonBackend: Searching for local CDs
08-07 23:12 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp is a valid Ubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp is a valid Ubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp is a valid Kubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp is a valid Kubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp is a valid Xubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp is a valid Xubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp is a valid Mythbuntu CD
08-07 23:12 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp is a valid Mythbuntu CD
08-07 23:12 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp is a valid Edubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp is a valid Edubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp is a valid Lubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp is a valid Lubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-07 23:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-07 23:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-07 23:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-07 23:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-07 23:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-07 23:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-07 23:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
08-07 23:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-07 23:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-07 23:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
08-07 23:12 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
08-07 23:12 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-07 23:12 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
08-07 23:12 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-07 23:12 INFO   root: Running the installer...
08-07 23:12 DEBUG  WindowsFrontend: __init__...
08-07 23:12 DEBUG  WindowsFrontend: on_init...
08-07 23:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\translations, languages=['en_IN', 'en']
08-07 23:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\translations, languages=['en_IN', 'en']
08-07 23:13 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=15000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=deepraj
08-07 23:13 INFO   root: Received settings
08-07 23:13 DEBUG  CommonBackend: Searching for local CD
08-07 23:13 DEBUG  Distro:   checking whether C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp is a valid Ubuntu CD
08-07 23:13 DEBUG  Distro:     does not contain C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\casper\filesystem.squashfs
08-07 23:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-07 23:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-07 23:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-07 23:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-07 23:13 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-07 23:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-07 23:13 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
08-07 23:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
08-07 23:13 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-07 23:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-07 23:13 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
08-07 23:13 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-07 23:13 DEBUG  CommonBackend: Searching for local ISO
08-07 23:13 DEBUG  Distro:   checking Ubuntu ISO C:\Ubuntu_Setup\ubuntu-12.04.2-desktop-amd64.iso
08-07 23:13 DEBUG  Distro:     does not contain casper\vmlinuz
08-07 23:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\dEEPRAJ\AppData\Local\Temp\pyl4D1.tmp\translations, languages=['en_US', 'en']
08-07 23:13 DEBUG  TaskList: # Running tasklist...
08-07 23:13 DEBUG  TaskList: ## Running select_target_dir...
08-07 23:13 INFO   WindowsBackend: Installing into D:\ubuntu
08-07 23:13 DEBUG  TaskList: ## Finished select_target_dir
08-07 23:13 DEBUG  TaskList: ## Running create_dir_structure...
08-07 23:13 DEBUG  CommonBackend: Creating dir D:\ubuntu
08-07 23:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
08-07 23:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
08-07 23:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
08-07 23:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
08-07 23:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
08-07 23:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
08-07 23:13 DEBUG  TaskList: ## Finished create_dir_structure
08-07 23:13 DEBUG  TaskList: ## Running create_uninstaller...
08-07 23:13 DEBUG  WindowsBackend: Copying uninstaller C:\Ubuntu_Setup\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
08-07 23:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
08-07 23:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
08-07 23:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-07 23:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
08-07 23:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev272
08-07 23:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-07 23:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-07 23:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-07 23:13 DEBUG  TaskList: ## Finished create_uninstaller
08-07 23:13 DEBUG  TaskList: ## Running create_preseed_diskimage...
08-07 23:13 DEBUG  TaskList: ## Finished create_preseed_diskimage
08-07 23:13 DEBUG  TaskList: ## Running get_diskimage...
08-07 23:13 DEBUG  TaskList: New task download
08-07 23:13 DEBUG  TaskList: ### Running download...
08-07 23:13 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > D:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
08-07 23:13 DEBUG  downloader: Download start filename=D:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz, basename=ubuntu-12.04.2-wubi-amd64.tar.xz, length=549666608, text=None
08-08 00:05 DEBUG  TaskList: ### Finished download
08-08 00:05 DEBUG  downloader: download finished (read 549666608 bytes)
08-08 00:05 DEBUG  TaskList: ## Finished get_diskimage
08-08 00:05 DEBUG  TaskList: ## Running extract_diskimage...
08-08 00:07 DEBUG  TaskList: ## Finished extract_diskimage
08-08 00:07 DEBUG  TaskList: ## Running choose_disk_sizes...
08-08 00:07 DEBUG  WindowsBackend: total size=15000
  root=14744
  swap=256
  home=0
  usr=0
08-08 00:07 DEBUG  TaskList: ## Finished choose_disk_sizes
08-08 00:07 DEBUG  TaskList: ## Running expand_diskimage...
08-08 00:07 DEBUG  TaskList: ## Finished expand_diskimage
08-08 00:07 DEBUG  TaskList: ## Running create_swap_diskimage...
08-08 00:07 DEBUG  TaskList: ## Finished create_swap_diskimage
08-08 00:07 DEBUG  TaskList: ## Running modify_bootloader...
08-08 00:07 DEBUG  TaskList: New task modify_bcd
08-08 00:07 DEBUG  TaskList: ### Running modify_bcd...
08-08 00:07 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 137498.25 mb free ntfs)
08-08 00:07 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {226b5c48-6353-11e2-bdad-8af5da54fbf8} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {226b5c48-6353-11e2-bdad-8af5da54fbf8} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
08-08 00:07 DEBUG  TaskList: # Cancelling tasklist
08-08 00:07 DEBUG  TaskList: New task modify_bcd
08-08 00:07 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {226b5c48-6353-11e2-bdad-8af5da54fbf8} device partition=D:
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
>>command=C:\Windows\System32\bcdedit.exe /set {226b5c48-6353-11e2-bdad-8af5da54fbf8} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
08-08 00:07 DEBUG  TaskList: New task modify_bcd
08-08 00:07 DEBUG  TaskList: New task modify_bcd
08-08 00:07 DEBUG  TaskList: New task modify_bcd
08-08 00:07 DEBUG  TaskList: ## Finished modify_bootloader
08-08 00:07 DEBUG  TaskList: # Finished tasklist
```

---

### Post by QIII on 2013-08-07
Hello, deepraj2!

Please enclose code in code tags.

You can do this by either clicking the # symbol above the input box, placing your cursor between the tags and pasting your text; or by pasting your text, highlighting it and then clicking the # symbol.

Thank you.

---

### Post by deepraj2 on 2013-08-08
Does any one have any solution to the problem?
I am using HP laptop...DV-6 2155TX Model.

---

### Post by fantab on 2013-08-08
If you are trying to install WUBI on a pre-installed Windows8 PC then it WON'T work as WUBI is NOT compatible with 'Secure Boot' feature of Windows8.

---

### Post by Mark Phelps on 2013-08-08
From the log, it looks like you're trying to install Ubuntu 12.04 -- which should work.

It's likely this is a UUID error -- and the procedure for fixing that (even though it says "Vista") is described in the link:  [http://askubuntu.com/questions/146305/wubi-bcdedit-error]("http://askubuntu.com/questions/146305/wubi-bcdedit-error")

---

### Post by deepraj2 on 2013-08-08
Well, I have Windows 7...its not win8

---

