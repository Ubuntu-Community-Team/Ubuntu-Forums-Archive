---
title: "problem with wubi"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by vanduc2514 on 2011-11-25
hi guys, i'm from vn and new to ubuntu :D

I install ubuntu with wubi and got this error

[img]http://img600.imageshack.us/img600/9531/51798024.jpg[/img]

Are there any fix for that, i want to try ubuntu but install is quite difficult :( 

Thank for helping me :D

P.s: sorry for my bad English :D

---

### Post by sprintexec on 2011-11-25
Hi, 

Can you open the log file, copy it and post it here?

---

### Post by bcbc on 2011-11-25
Usually that error is because you have dynamic drives. Linux does not support these. The actual error is Windows not allowing you to boot from U: which probably means it's a dynamic partition and also isn't in the partition table.

You can check by going to the Disk Management console - it will tell you if you have dynamic drives (and you might also recall being prompted to switch to dynamic drives when you created a partition). While it's easy to switch to dynamic drives, Windows won't allow you to switch back. It recommends deleting all partitions and recreating which is usually not easily done. See this link for other options: [http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)

---

### Post by vanduc2514 on 2011-11-25
Yes, here is my log :( 
```

11-25 15:37 INFO   root: === wubi 11.10 rev241 ===
11-25 15:37 DEBUG  root: Logfile is c:\users\ductot~1\appdata\local\temp\wubi-11.10-rev241.log
11-25 15:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
11-25 15:37 DEBUG  CommonBackend: data_dir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp\data
11-25 15:37 DEBUG  WindowsBackend: 7z=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp\bin\7z.exe
11-25 15:37 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-25 15:37 DEBUG  CommonBackend: Fetching basic info...
11-25 15:37 DEBUG  CommonBackend: original_exe=H:\wubi.exe
11-25 15:37 DEBUG  CommonBackend: platform=win32
11-25 15:37 DEBUG  CommonBackend: osname=nt
11-25 15:37 DEBUG  CommonBackend: language=en_US
11-25 15:37 DEBUG  CommonBackend: encoding=cp1252
11-25 15:37 DEBUG  WindowsBackend: arch=amd64
11-25 15:37 DEBUG  CommonBackend: Parsing isolist=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp\data\isolist.ini
11-25 15:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-25 15:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-25 15:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-25 15:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-25 15:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-25 15:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-25 15:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-25 15:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-25 15:37 DEBUG  WindowsBackend: Fetching host info...
11-25 15:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-25 15:37 DEBUG  WindowsBackend: windows version=vista
11-25 15:37 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-25 15:37 DEBUG  WindowsBackend: windows_sp=None
11-25 15:37 DEBUG  WindowsBackend: windows_build=7601
11-25 15:37 DEBUG  WindowsBackend: gmt=7
11-25 15:37 DEBUG  WindowsBackend: country=US
11-25 15:37 DEBUG  WindowsBackend: timezone=America/New_York
11-25 15:37 DEBUG  WindowsBackend: windows_username=Duc tot bung
11-25 15:37 DEBUG  WindowsBackend: user_full_name=Duc tot bung
11-25 15:37 DEBUG  WindowsBackend: user_directory=C:\Users\Duc tot bung
11-25 15:37 DEBUG  WindowsBackend: windows_language_code=1033
11-25 15:37 DEBUG  WindowsBackend: windows_language=English
11-25 15:37 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
11-25 15:37 DEBUG  WindowsBackend: bootloader=vista
11-25 15:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5251.93359375 mb free ntfs)
11-25 15:37 DEBUG  WindowsBackend: drive=Drive(A: hd 37079.984375 mb free ntfs)
11-25 15:37 DEBUG  WindowsBackend: drive=Drive(B: hd 5799.64453125 mb free ntfs)
11-25 15:37 DEBUG  WindowsBackend: drive=Drive(C: hd 5251.93359375 mb free ntfs)
11-25 15:37 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-25 15:37 DEBUG  WindowsBackend: drive=Drive(E: hd 25941.8632813 mb free ntfs)
11-25 15:37 DEBUG  WindowsBackend: drive=Drive(F: hd 10569.2851563 mb free ntfs)
11-25 15:37 DEBUG  WindowsBackend: drive=Drive(G: hd 8133.34375 mb free ntfs)
11-25 15:37 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-25 15:37 DEBUG  WindowsBackend: drive=Drive(U: hd 18950.5976563 mb free ntfs)
11-25 15:37 DEBUG  WindowsBackend: uninstaller_path=U:\ubuntu\uninstall-wubi.exe
11-25 15:37 DEBUG  WindowsBackend: previous_target_dir=U:\ubuntu
11-25 15:37 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-25 15:37 DEBUG  WindowsBackend: keyboard_id=67699721
11-25 15:37 DEBUG  WindowsBackend: keyboard_layout=us
11-25 15:37 DEBUG  WindowsBackend: keyboard_variant=
11-25 15:37 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-25 15:37 DEBUG  CommonBackend: locale=en_US.UTF-8
11-25 15:37 DEBUG  WindowsBackend: total_memory_mb=3947.53515625
11-25 15:37 DEBUG  CommonBackend: Searching ISOs on USB devices
11-25 15:37 DEBUG  Distro:   checking Ubuntu ISO B:\X17-59465.iso
11-25 15:37 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:37 DEBUG  Distro:   checking Ubuntu ISO B:\X17-59465.iso
11-25 15:37 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:37 DEBUG  Distro:   checking Kubuntu ISO B:\X17-59465.iso
11-25 15:37 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:37 DEBUG  Distro:   checking Kubuntu ISO B:\X17-59465.iso
11-25 15:37 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:37 DEBUG  Distro:   checking Xubuntu ISO B:\X17-59465.iso
11-25 15:37 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:37 DEBUG  Distro:   checking Xubuntu ISO B:\X17-59465.iso
11-25 15:37 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:37 DEBUG  Distro:   checking Mythbuntu ISO B:\X17-59465.iso
11-25 15:37 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:37 DEBUG  Distro:   checking Mythbuntu ISO B:\X17-59465.iso
11-25 15:37 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:37 DEBUG  Distro:   checking Ubuntu ISO U:\ubuntu-11.10-desktop-i386.iso
11-25 15:37 DEBUG  WindowsBackend:   extracting .disk\info from U:\ubuntu-11.10-desktop-i386.iso
11-25 15:37 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
11-25 15:37 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
11-25 15:37 INFO   Distro: Found a valid iso for Ubuntu: U:\ubuntu-11.10-desktop-i386.iso
11-25 15:37 DEBUG  CommonBackend: Searching for local CDs
11-25 15:37 DEBUG  Distro:   checking whether A:\ is a valid Ubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether A:\ is a valid Ubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether A:\ is a valid Kubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether A:\ is a valid Kubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether A:\ is a valid Xubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether A:\ is a valid Xubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether A:\ is a valid Mythbuntu CD
11-25 15:37 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether A:\ is a valid Mythbuntu CD
11-25 15:37 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
11-25 15:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
11-25 15:37 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp is a valid Ubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp is a valid Ubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp is a valid Kubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp is a valid Kubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp is a valid Xubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp is a valid Xubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp is a valid Mythbuntu CD
11-25 15:37 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp is a valid Mythbuntu CD
11-25 15:37 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-25 15:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-25 15:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 15:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 15:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-25 15:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-25 15:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-25 15:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-25 15:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-25 15:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:37 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-25 15:37 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
11-25 15:37 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
11-25 15:37 INFO   Distro: Found a valid CD for Ubuntu: H:\
11-25 15:37 INFO   root: Running the CD menu...
11-25 15:37 DEBUG  WindowsFrontend: __init__...
11-25 15:37 DEBUG  WindowsFrontend: on_init...
11-25 15:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp\translations, languages=['en_US', 'en']
11-25 15:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl384F.tmp\translations, languages=['en_US', 'en']
11-25 15:38 INFO   root: CD menu finished
11-25 15:38 INFO   root: Already installed, running the uninstaller...
11-25 15:38 INFO   root: Running the uninstaller...
11-25 15:38 INFO   CommonBackend: Launching previous uninestaller U:\ubuntu\uninstall-wubi.exe
11-25 15:38 DEBUG  root: application.quit
11-25 15:38 DEBUG  WindowsFrontend: frontend.quit
11-25 15:38 DEBUG  WindowsFrontend: frontend.on_quit
11-25 15:38 DEBUG  root: application.on_quit
11-25 15:38 INFO   root: sys.exit
11-25 15:56 INFO   root: === wubi 11.10 rev241 ===
11-25 15:56 DEBUG  root: Logfile is c:\users\ductot~1\appdata\local\temp\wubi-11.10-rev241.log
11-25 15:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
11-25 15:56 DEBUG  CommonBackend: data_dir=C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp\data
11-25 15:56 DEBUG  WindowsBackend: 7z=C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp\bin\7z.exe
11-25 15:56 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-25 15:56 DEBUG  CommonBackend: Fetching basic info...
11-25 15:56 DEBUG  CommonBackend: original_exe=H:\wubi.exe
11-25 15:56 DEBUG  CommonBackend: platform=win32
11-25 15:56 DEBUG  CommonBackend: osname=nt
11-25 15:56 DEBUG  CommonBackend: language=en_US
11-25 15:56 DEBUG  CommonBackend: encoding=cp1252
11-25 15:56 DEBUG  WindowsBackend: arch=amd64
11-25 15:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp\data\isolist.ini
11-25 15:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-25 15:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-25 15:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-25 15:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-25 15:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-25 15:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-25 15:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-25 15:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-25 15:56 DEBUG  WindowsBackend: Fetching host info...
11-25 15:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-25 15:56 DEBUG  WindowsBackend: windows version=vista
11-25 15:56 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-25 15:56 DEBUG  WindowsBackend: windows_sp=None
11-25 15:56 DEBUG  WindowsBackend: windows_build=7601
11-25 15:56 DEBUG  WindowsBackend: gmt=7
11-25 15:56 DEBUG  WindowsBackend: country=US
11-25 15:56 DEBUG  WindowsBackend: timezone=America/New_York
11-25 15:56 DEBUG  WindowsBackend: windows_username=Duc tot bung
11-25 15:56 DEBUG  WindowsBackend: user_full_name=Duc tot bung
11-25 15:56 DEBUG  WindowsBackend: user_directory=C:\Users\Duc tot bung
11-25 15:56 DEBUG  WindowsBackend: windows_language_code=1033
11-25 15:56 DEBUG  WindowsBackend: windows_language=English
11-25 15:56 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
11-25 15:56 DEBUG  WindowsBackend: bootloader=vista
11-25 15:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5274.5625 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(A: hd 37078.84375 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(B: hd 5799.64453125 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(C: hd 5274.5625 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(E: hd 25941.8632813 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(F: hd 10569.2851563 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(G: hd 8133.34375 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(U: hd 18950.6171875 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: uninstaller_path=U:\ubuntu\uninstall-wubi.exe
11-25 15:56 DEBUG  WindowsBackend: previous_target_dir=U:\ubuntu
11-25 15:56 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-25 15:56 DEBUG  WindowsBackend: keyboard_id=67699721
11-25 15:56 DEBUG  WindowsBackend: keyboard_layout=us
11-25 15:56 DEBUG  WindowsBackend: keyboard_variant=
11-25 15:56 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-25 15:56 DEBUG  CommonBackend: locale=en_US.UTF-8
11-25 15:56 DEBUG  WindowsBackend: total_memory_mb=3947.53515625
11-25 15:56 DEBUG  CommonBackend: Searching ISOs on USB devices
11-25 15:56 DEBUG  Distro:   checking Ubuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Ubuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Kubuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Kubuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Xubuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Xubuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Mythbuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Mythbuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Ubuntu ISO U:\ubuntu-11.10-desktop-i386.iso
11-25 15:56 DEBUG  WindowsBackend:   extracting .disk\info from U:\ubuntu-11.10-desktop-i386.iso
11-25 15:56 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
11-25 15:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
11-25 15:56 INFO   Distro: Found a valid iso for Ubuntu: U:\ubuntu-11.10-desktop-i386.iso
11-25 15:56 DEBUG  CommonBackend: Searching for local CDs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
11-25 15:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
11-25 15:56 INFO   Distro: Found a valid CD for Ubuntu: H:\
11-25 15:56 INFO   root: Running the CD menu...
11-25 15:56 DEBUG  WindowsFrontend: __init__...
11-25 15:56 DEBUG  WindowsFrontend: on_init...
11-25 15:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp\translations, languages=['en_US', 'en']
11-25 15:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pylF018.tmp\translations, languages=['en_US', 'en']
11-25 15:56 INFO   root: CD menu finished
11-25 15:56 INFO   root: Already installed, running the uninstaller...
11-25 15:56 INFO   root: Running the uninstaller...
11-25 15:56 INFO   CommonBackend: Launching previous uninestaller U:\ubuntu\uninstall-wubi.exe
11-25 15:56 DEBUG  root: application.quit
11-25 15:56 DEBUG  WindowsFrontend: frontend.quit
11-25 15:56 DEBUG  WindowsFrontend: frontend.on_quit
11-25 15:56 DEBUG  root: application.on_quit
11-25 15:56 INFO   root: sys.exit
11-25 15:56 INFO   root: === wubi 11.10 rev241 ===
11-25 15:56 DEBUG  root: Logfile is c:\users\ductot~1\appdata\local\temp\wubi-11.10-rev241.log
11-25 15:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
11-25 15:56 DEBUG  CommonBackend: data_dir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp\data
11-25 15:56 DEBUG  WindowsBackend: 7z=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp\bin\7z.exe
11-25 15:56 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-25 15:56 DEBUG  CommonBackend: Fetching basic info...
11-25 15:56 DEBUG  CommonBackend: original_exe=H:\wubi.exe
11-25 15:56 DEBUG  CommonBackend: platform=win32
11-25 15:56 DEBUG  CommonBackend: osname=nt
11-25 15:56 DEBUG  CommonBackend: language=en_US
11-25 15:56 DEBUG  CommonBackend: encoding=cp1252
11-25 15:56 DEBUG  WindowsBackend: arch=amd64
11-25 15:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp\data\isolist.ini
11-25 15:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-25 15:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-25 15:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-25 15:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-25 15:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-25 15:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-25 15:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-25 15:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-25 15:56 DEBUG  WindowsBackend: Fetching host info...
11-25 15:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-25 15:56 DEBUG  WindowsBackend: windows version=vista
11-25 15:56 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-25 15:56 DEBUG  WindowsBackend: windows_sp=None
11-25 15:56 DEBUG  WindowsBackend: windows_build=7601
11-25 15:56 DEBUG  WindowsBackend: gmt=7
11-25 15:56 DEBUG  WindowsBackend: country=US
11-25 15:56 DEBUG  WindowsBackend: timezone=America/New_York
11-25 15:56 DEBUG  WindowsBackend: windows_username=Duc tot bung
11-25 15:56 DEBUG  WindowsBackend: user_full_name=Duc tot bung
11-25 15:56 DEBUG  WindowsBackend: user_directory=C:\Users\Duc tot bung
11-25 15:56 DEBUG  WindowsBackend: windows_language_code=1033
11-25 15:56 DEBUG  WindowsBackend: windows_language=English
11-25 15:56 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
11-25 15:56 DEBUG  WindowsBackend: bootloader=vista
11-25 15:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5274.42578125 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(A: hd 37078.84375 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(B: hd 5799.64453125 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(C: hd 5274.42578125 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(E: hd 25941.8632813 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(F: hd 10569.2851563 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(G: hd 8133.34375 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-25 15:56 DEBUG  WindowsBackend: drive=Drive(U: hd 19666.6953125 mb free ntfs)
11-25 15:56 DEBUG  WindowsBackend: uninstaller_path=None
11-25 15:56 DEBUG  WindowsBackend: previous_target_dir=None
11-25 15:56 DEBUG  WindowsBackend: previous_distro_name=None
11-25 15:56 DEBUG  WindowsBackend: keyboard_id=67699721
11-25 15:56 DEBUG  WindowsBackend: keyboard_layout=us
11-25 15:56 DEBUG  WindowsBackend: keyboard_variant=
11-25 15:56 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-25 15:56 DEBUG  CommonBackend: locale=en_US.UTF-8
11-25 15:56 DEBUG  WindowsBackend: total_memory_mb=3947.53515625
11-25 15:56 DEBUG  CommonBackend: Searching ISOs on USB devices
11-25 15:56 DEBUG  Distro:   checking Ubuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Ubuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Kubuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Kubuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Xubuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Xubuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Mythbuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Mythbuntu ISO B:\X17-59465.iso
11-25 15:56 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:56 DEBUG  Distro:   checking Ubuntu ISO U:\ubuntu-11.10-desktop-i386.iso
11-25 15:56 DEBUG  WindowsBackend:   extracting .disk\info from U:\ubuntu-11.10-desktop-i386.iso
11-25 15:56 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
11-25 15:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
11-25 15:56 INFO   Distro: Found a valid iso for Ubuntu: U:\ubuntu-11.10-desktop-i386.iso
11-25 15:56 DEBUG  CommonBackend: Searching for local CDs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether A:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-25 15:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-25 15:56 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
11-25 15:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
11-25 15:56 INFO   Distro: Found a valid CD for Ubuntu: H:\
11-25 15:56 INFO   root: Running the CD menu...
11-25 15:56 DEBUG  WindowsFrontend: __init__...
11-25 15:56 DEBUG  WindowsFrontend: on_init...
11-25 15:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp\translations, languages=['en_US', 'en']
11-25 15:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl40B7.tmp\translations, languages=['en_US', 'en']
11-25 15:56 INFO   WindowsFrontend: Operation cancelled
11-25 15:56 DEBUG  WindowsFrontend: frontend.quit
11-25 15:56 DEBUG  WindowsFrontend: frontend.on_quit
11-25 15:56 DEBUG  root: application.on_quit
11-25 15:56 INFO   root: sys.exit
11-25 15:57 INFO   root: === wubi 11.10 rev241 ===
11-25 15:57 DEBUG  root: Logfile is c:\users\ductot~1\appdata\local\temp\wubi-11.10-rev241.log
11-25 15:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
11-25 15:57 DEBUG  CommonBackend: data_dir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\data
11-25 15:57 DEBUG  WindowsBackend: 7z=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\bin\7z.exe
11-25 15:57 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-25 15:57 DEBUG  CommonBackend: Fetching basic info...
11-25 15:57 DEBUG  CommonBackend: original_exe=H:\wubi.exe
11-25 15:57 DEBUG  CommonBackend: platform=win32
11-25 15:57 DEBUG  CommonBackend: osname=nt
11-25 15:57 DEBUG  CommonBackend: language=en_US
11-25 15:57 DEBUG  CommonBackend: encoding=cp1252
11-25 15:57 DEBUG  WindowsBackend: arch=amd64
11-25 15:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\data\isolist.ini
11-25 15:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-25 15:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-25 15:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-25 15:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-25 15:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-25 15:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-25 15:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-25 15:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-25 15:57 DEBUG  WindowsBackend: Fetching host info...
11-25 15:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-25 15:57 DEBUG  WindowsBackend: windows version=vista
11-25 15:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-25 15:57 DEBUG  WindowsBackend: windows_sp=None
11-25 15:57 DEBUG  WindowsBackend: windows_build=7601
11-25 15:57 DEBUG  WindowsBackend: gmt=7
11-25 15:57 DEBUG  WindowsBackend: country=US
11-25 15:57 DEBUG  WindowsBackend: timezone=America/New_York
11-25 15:57 DEBUG  WindowsBackend: windows_username=Duc tot bung
11-25 15:57 DEBUG  WindowsBackend: user_full_name=Duc tot bung
11-25 15:57 DEBUG  WindowsBackend: user_directory=C:\Users\Duc tot bung
11-25 15:57 DEBUG  WindowsBackend: windows_language_code=1033
11-25 15:57 DEBUG  WindowsBackend: windows_language=English
11-25 15:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
11-25 15:57 DEBUG  WindowsBackend: bootloader=vista
11-25 15:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5274.359375 mb free ntfs)
11-25 15:57 DEBUG  WindowsBackend: drive=Drive(A: hd 37078.84375 mb free ntfs)
11-25 15:57 DEBUG  WindowsBackend: drive=Drive(B: hd 5799.64453125 mb free ntfs)
11-25 15:57 DEBUG  WindowsBackend: drive=Drive(C: hd 5274.359375 mb free ntfs)
11-25 15:57 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-25 15:57 DEBUG  WindowsBackend: drive=Drive(E: hd 25941.8632813 mb free ntfs)
11-25 15:57 DEBUG  WindowsBackend: drive=Drive(F: hd 10569.2851563 mb free ntfs)
11-25 15:57 DEBUG  WindowsBackend: drive=Drive(G: hd 8133.34375 mb free ntfs)
11-25 15:57 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-25 15:57 DEBUG  WindowsBackend: drive=Drive(U: hd 19666.6953125 mb free ntfs)
11-25 15:57 DEBUG  WindowsBackend: uninstaller_path=None
11-25 15:57 DEBUG  WindowsBackend: previous_target_dir=None
11-25 15:57 DEBUG  WindowsBackend: previous_distro_name=None
11-25 15:57 DEBUG  WindowsBackend: keyboard_id=67699721
11-25 15:57 DEBUG  WindowsBackend: keyboard_layout=us
11-25 15:57 DEBUG  WindowsBackend: keyboard_variant=
11-25 15:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-25 15:57 DEBUG  CommonBackend: locale=en_US.UTF-8
11-25 15:57 DEBUG  WindowsBackend: total_memory_mb=3947.53515625
11-25 15:57 DEBUG  CommonBackend: Searching ISOs on USB devices
11-25 15:57 DEBUG  Distro:   checking Ubuntu ISO B:\X17-59465.iso
11-25 15:57 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:57 DEBUG  Distro:   checking Ubuntu ISO B:\X17-59465.iso
11-25 15:57 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:57 DEBUG  Distro:   checking Kubuntu ISO B:\X17-59465.iso
11-25 15:57 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:57 DEBUG  Distro:   checking Kubuntu ISO B:\X17-59465.iso
11-25 15:57 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:57 DEBUG  Distro:   checking Xubuntu ISO B:\X17-59465.iso
11-25 15:57 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:57 DEBUG  Distro:   checking Xubuntu ISO B:\X17-59465.iso
11-25 15:57 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:57 DEBUG  Distro:   checking Mythbuntu ISO B:\X17-59465.iso
11-25 15:57 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:57 DEBUG  Distro:   checking Mythbuntu ISO B:\X17-59465.iso
11-25 15:57 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:57 DEBUG  Distro:   checking Ubuntu ISO U:\ubuntu-11.10-desktop-i386.iso
11-25 15:57 DEBUG  WindowsBackend:   extracting .disk\info from U:\ubuntu-11.10-desktop-i386.iso
11-25 15:57 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
11-25 15:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
11-25 15:57 INFO   Distro: Found a valid iso for Ubuntu: U:\ubuntu-11.10-desktop-i386.iso
11-25 15:57 DEBUG  CommonBackend: Searching for local CDs
11-25 15:57 DEBUG  Distro:   checking whether A:\ is a valid Ubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether A:\ is a valid Ubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether A:\ is a valid Kubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether A:\ is a valid Kubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether A:\ is a valid Xubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether A:\ is a valid Xubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether A:\ is a valid Mythbuntu CD
11-25 15:57 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether A:\ is a valid Mythbuntu CD
11-25 15:57 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
11-25 15:57 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
11-25 15:57 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp is a valid Ubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp is a valid Ubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp is a valid Kubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp is a valid Kubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp is a valid Xubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp is a valid Xubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp is a valid Mythbuntu CD
11-25 15:57 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp is a valid Mythbuntu CD
11-25 15:57 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-25 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-25 15:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 15:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-25 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-25 15:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-25 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-25 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-25 15:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:57 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-25 15:57 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
11-25 15:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
11-25 15:57 INFO   Distro: Found a valid CD for Ubuntu: H:\
11-25 15:57 INFO   root: Running the CD menu...
11-25 15:57 DEBUG  WindowsFrontend: __init__...
11-25 15:57 DEBUG  WindowsFrontend: on_init...
11-25 15:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\translations, languages=['en_US', 'en']
11-25 15:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\translations, languages=['en_US', 'en']
11-25 15:57 INFO   root: CD menu finished
11-25 15:57 INFO   root: Running the installer...
11-25 15:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\translations, languages=['en_US', 'en']
11-25 15:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\translations, languages=['en_US', 'en']
11-25 15:57 DEBUG  WinuiInstallationPage: target_drive=A:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ductotbung
11-25 15:57 INFO   root: Received settings
11-25 15:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\translations, languages=['en_US', 'en']
11-25 15:57 DEBUG  TaskList: # Running tasklist...
11-25 15:57 DEBUG  TaskList: ## Running select_target_dir...
11-25 15:57 INFO   WindowsBackend: Installing into A:\ubuntu
11-25 15:57 DEBUG  TaskList: ## Finished select_target_dir
11-25 15:57 DEBUG  TaskList: ## Running create_dir_structure...
11-25 15:57 DEBUG  CommonBackend: Creating dir A:\ubuntu
11-25 15:57 DEBUG  CommonBackend: Creating dir A:\ubuntu\disks
11-25 15:57 DEBUG  CommonBackend: Creating dir A:\ubuntu\install
11-25 15:57 DEBUG  CommonBackend: Creating dir A:\ubuntu\install\boot
11-25 15:57 DEBUG  CommonBackend: Creating dir A:\ubuntu\disks\boot
11-25 15:57 DEBUG  CommonBackend: Creating dir A:\ubuntu\disks\boot\grub
11-25 15:57 DEBUG  CommonBackend: Creating dir A:\ubuntu\install\boot\grub
11-25 15:57 DEBUG  TaskList: ## Finished create_dir_structure
11-25 15:57 DEBUG  TaskList: ## Running uncompress_target_dir...
11-25 15:57 DEBUG  TaskList: ## Finished uncompress_target_dir
11-25 15:57 DEBUG  TaskList: ## Running create_uninstaller...
11-25 15:57 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> A:\ubuntu\uninstall-wubi.exe
11-25 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString A:\ubuntu\uninstall-wubi.exe
11-25 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir A:\ubuntu
11-25 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-25 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon A:\ubuntu\Ubuntu.ico
11-25 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
11-25 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-25 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
11-25 15:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-25 15:57 DEBUG  TaskList: ## Finished create_uninstaller
11-25 15:57 DEBUG  TaskList: ## Running copy_installation_files...
11-25 15:57 DEBUG  WindowsBackend: Copying C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\data\custom-installation -> A:\ubuntu\install\custom-installation
11-25 15:57 DEBUG  WindowsBackend: Copying C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\winboot -> A:\ubuntu\winboot
11-25 15:57 DEBUG  WindowsBackend: Copying C:\Users\DUCTOT~1\AppData\Local\Temp\pyl5D8A.tmp\data\images\Ubuntu.ico -> A:\ubuntu\Ubuntu.ico
11-25 15:57 DEBUG  TaskList: ## Finished copy_installation_files
11-25 15:57 DEBUG  TaskList: ## Running get_iso...
11-25 15:57 DEBUG  CommonBackend: Trying to use pre-specified ISO U:\ubuntu-11.10-desktop-i386.iso
11-25 15:57 DEBUG  TaskList: New task is_valid_iso
11-25 15:57 DEBUG  TaskList: ### Running is_valid_iso...
11-25 15:57 DEBUG  Distro:   checking Ubuntu ISO U:\ubuntu-11.10-desktop-i386.iso
11-25 15:57 INFO   Distro: Found a valid iso for Ubuntu: U:\ubuntu-11.10-desktop-i386.iso
11-25 15:57 DEBUG  TaskList: ### Finished is_valid_iso
11-25 15:57 DEBUG  TaskList: New task check_iso
11-25 15:57 DEBUG  TaskList: ### Running check_iso...
11-25 15:57 DEBUG  CommonBackend: Checking U:\ubuntu-11.10-desktop-i386.iso
11-25 15:57 DEBUG  Distro:   checking Ubuntu ISO U:\ubuntu-11.10-desktop-i386.iso
11-25 15:57 INFO   Distro: Found a valid iso for Ubuntu: U:\ubuntu-11.10-desktop-i386.iso
11-25 15:57 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
11-25 15:57 DEBUG  TaskList: New task get_metalink
11-25 15:57 DEBUG  TaskList: #### Running get_metalink...
11-25 15:57 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink](http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink) > A:\ubuntu\install
11-25 15:57 DEBUG  downloader: Download start filename=A:\ubuntu\install\ubuntu-11.10-desktop-i386.metalink, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink, basename=ubuntu-11.10-desktop-i386.metalink, length=4867, text=None
11-25 15:57 DEBUG  downloader: download finished (read 4867 bytes)
11-25 15:57 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/MD5SUMS-metalink](http://releases.ubuntu.com/11.10/MD5SUMS-metalink) > A:\ubuntu\install
11-25 15:57 DEBUG  downloader: Download start filename=A:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=419, text=None
11-25 15:57 DEBUG  downloader: download finished (read 419 bytes)
11-25 15:57 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.10/MD5SUMS-metalink.gpg) > A:\ubuntu\install
11-25 15:57 DEBUG  downloader: Download start filename=A:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
11-25 15:57 DEBUG  downloader: download finished (read 198 bytes)
11-25 15:57 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
11-25 15:57 INFO   saplog: Checking block bindings..
11-25 15:57 INFO   saplog: Key verified successfully.
11-25 15:57 DEBUG  CommonBackend: metalink md5sums:
a65c220b437d6907ba9463b7f479fea5  ubuntu-11.10-alternate-amd64.metalink
bdbf5bf7dfa85cad2cd711f081b071ec  ubuntu-11.10-alternate-i386.metalink
4a4ddfa7d6eea4d9cf7a9f8d854e0418  ubuntu-11.10-desktop-amd64.metalink
a84050d7b00ff42b83a69ad7309b6f36  ubuntu-11.10-desktop-i386.metalink
c2f7e1f7352a8d3cd1c2dede0c709a1a  ubuntu-11.10-server-amd64.metalink
2b296035b3ba3f8536dc0efa49a52fc2  ubuntu-11.10-server-i386.metalink

11-25 15:57 DEBUG  TaskList: #### Finished get_metalink
11-25 15:57 DEBUG  TaskList: New task get_file_md5
11-25 15:57 DEBUG  TaskList: #### Running get_file_md5...
11-25 15:57 DEBUG  TaskList: #### Finished get_file_md5
11-25 15:57 DEBUG  TaskList: ### Finished check_iso
11-25 15:57 DEBUG  TaskList: New task copy_file
11-25 15:57 DEBUG  CommonBackend: Copying U:\ubuntu-11.10-desktop-i386.iso > A:\ubuntu\install\installation.iso
11-25 15:57 DEBUG  TaskList: ### Running copy_file...
11-25 15:57 DEBUG  TaskList: ### Finished copy_file
11-25 15:57 DEBUG  TaskList: ## Finished get_iso
11-25 15:57 DEBUG  TaskList: ## Running extract_kernel...
11-25 15:57 DEBUG  CommonBackend: Extracting files from ISO A:\ubuntu\install\installation.iso
11-25 15:57 DEBUG  WindowsBackend:   extracting md5sum.txt from A:\ubuntu\install\installation.iso
11-25 15:57 DEBUG  WindowsBackend:   extracting casper\vmlinuz from A:\ubuntu\install\installation.iso
11-25 15:57 DEBUG  WindowsBackend:   extracting casper\initrd.lz from A:\ubuntu\install\installation.iso
11-25 15:57 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
11-25 15:57 DEBUG  CommonBackend:   checking A:\ubuntu\install\boot\vmlinuz
11-25 15:57 DEBUG  CommonBackend:   A:\ubuntu\install\boot\vmlinuz md5 = fde150f5c6fd2de66ed7876efbfcc4c7 == fde150f5c6fd2de66ed7876efbfcc4c7
11-25 15:57 DEBUG  CommonBackend:   checking A:\ubuntu\install\boot\initrd.lz
11-25 15:57 DEBUG  CommonBackend:   A:\ubuntu\install\boot\initrd.lz md5 = d6baee1e11f1d6de6eba6bd43dbde352 == d6baee1e11f1d6de6eba6bd43dbde352
11-25 15:57 DEBUG  TaskList: ## Finished extract_kernel
11-25 15:57 DEBUG  TaskList: ## Running choose_disk_sizes...
11-25 15:57 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
11-25 15:57 DEBUG  TaskList: ## Finished choose_disk_sizes
11-25 15:57 DEBUG  TaskList: ## Running create_preseed...
11-25 15:57 DEBUG  TaskList: ## Finished create_preseed
11-25 15:57 DEBUG  TaskList: ## Running modify_bootloader...
11-25 15:57 DEBUG  TaskList: New task modify_bcd
11-25 15:57 DEBUG  TaskList: ### Running modify_bcd...
11-25 15:57 DEBUG  WindowsBackend: modify_bcd Drive(A: hd 37078.84375 mb free ntfs)
11-25 15:57 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {edea7bcc-f968-11e0-b2d0-f0c2a6084129} device partition=A:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 692, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {edea7bcc-f968-11e0-b2d0-f0c2a6084129} device partition=A:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
11-25 15:57 DEBUG  TaskList: # Cancelling tasklist
11-25 15:57 DEBUG  TaskList: New task modify_bcd
11-25 15:57 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {edea7bcc-f968-11e0-b2d0-f0c2a6084129} device partition=A:
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
  File "\lib\wubi\backends\win32\backend.py", line 692, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {edea7bcc-f968-11e0-b2d0-f0c2a6084129} device partition=A:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
11-25 15:57 DEBUG  TaskList: New task modify_bcd
11-25 15:57 DEBUG  TaskList: New task modify_bcd
11-25 15:57 DEBUG  TaskList: New task modify_bcd
11-25 15:57 DEBUG  TaskList: New task modify_bcd
11-25 15:57 DEBUG  TaskList: New task modify_bcd
11-25 15:57 DEBUG  TaskList: ## Finished modify_bootloader
11-25 15:57 DEBUG  TaskList: # Finished tasklist
11-25 15:58 INFO   root: === wubi 11.10 rev241 ===
11-25 15:58 DEBUG  root: Logfile is c:\users\ductot~1\appdata\local\temp\wubi-11.10-rev241.log
11-25 15:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
11-25 15:58 DEBUG  CommonBackend: data_dir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\data
11-25 15:58 DEBUG  WindowsBackend: 7z=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\bin\7z.exe
11-25 15:58 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-25 15:58 DEBUG  CommonBackend: Fetching basic info...
11-25 15:58 DEBUG  CommonBackend: original_exe=H:\wubi.exe
11-25 15:58 DEBUG  CommonBackend: platform=win32
11-25 15:58 DEBUG  CommonBackend: osname=nt
11-25 15:58 DEBUG  CommonBackend: language=en_US
11-25 15:58 DEBUG  CommonBackend: encoding=cp1252
11-25 15:58 DEBUG  WindowsBackend: arch=amd64
11-25 15:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\data\isolist.ini
11-25 15:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-25 15:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-25 15:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-25 15:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-25 15:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-25 15:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-25 15:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-25 15:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-25 15:58 DEBUG  WindowsBackend: Fetching host info...
11-25 15:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-25 15:58 DEBUG  WindowsBackend: windows version=vista
11-25 15:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-25 15:58 DEBUG  WindowsBackend: windows_sp=None
11-25 15:58 DEBUG  WindowsBackend: windows_build=7601
11-25 15:58 DEBUG  WindowsBackend: gmt=7
11-25 15:58 DEBUG  WindowsBackend: country=US
11-25 15:58 DEBUG  WindowsBackend: timezone=America/New_York
11-25 15:58 DEBUG  WindowsBackend: windows_username=Duc tot bung
11-25 15:58 DEBUG  WindowsBackend: user_full_name=Duc tot bung
11-25 15:58 DEBUG  WindowsBackend: user_directory=C:\Users\Duc tot bung
11-25 15:58 DEBUG  WindowsBackend: windows_language_code=1033
11-25 15:58 DEBUG  WindowsBackend: windows_language=English
11-25 15:58 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
11-25 15:58 DEBUG  WindowsBackend: bootloader=vista
11-25 15:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5266.7265625 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(A: hd 36362.8710938 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(B: hd 5799.64453125 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(C: hd 5266.7265625 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(E: hd 25941.8632813 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(F: hd 10569.2851563 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(G: hd 8133.34375 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(U: hd 19666.6953125 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: uninstaller_path=A:\ubuntu\uninstall-wubi.exe
11-25 15:58 DEBUG  WindowsBackend: previous_target_dir=A:\ubuntu
11-25 15:58 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-25 15:58 DEBUG  WindowsBackend: keyboard_id=67699721
11-25 15:58 DEBUG  WindowsBackend: keyboard_layout=us
11-25 15:58 DEBUG  WindowsBackend: keyboard_variant=
11-25 15:58 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-25 15:58 DEBUG  CommonBackend: locale=en_US.UTF-8
11-25 15:58 DEBUG  WindowsBackend: total_memory_mb=3947.53515625
11-25 15:58 DEBUG  CommonBackend: Searching ISOs on USB devices
11-25 15:58 DEBUG  Distro:   checking Ubuntu ISO B:\X17-59465.iso
11-25 15:58 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:58 DEBUG  Distro:   checking Ubuntu ISO B:\X17-59465.iso
11-25 15:58 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:58 DEBUG  Distro:   checking Kubuntu ISO B:\X17-59465.iso
11-25 15:58 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:58 DEBUG  Distro:   checking Kubuntu ISO B:\X17-59465.iso
11-25 15:58 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:58 DEBUG  Distro:   checking Xubuntu ISO B:\X17-59465.iso
11-25 15:58 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:58 DEBUG  Distro:   checking Xubuntu ISO B:\X17-59465.iso
11-25 15:58 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:58 DEBUG  Distro:   checking Mythbuntu ISO B:\X17-59465.iso
11-25 15:58 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:58 DEBUG  Distro:   checking Mythbuntu ISO B:\X17-59465.iso
11-25 15:58 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 15:58 DEBUG  Distro:   checking Ubuntu ISO U:\ubuntu-11.10-desktop-i386.iso
11-25 15:58 DEBUG  WindowsBackend:   extracting .disk\info from U:\ubuntu-11.10-desktop-i386.iso
11-25 15:58 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
11-25 15:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
11-25 15:58 INFO   Distro: Found a valid iso for Ubuntu: U:\ubuntu-11.10-desktop-i386.iso
11-25 15:58 DEBUG  CommonBackend: Searching for local CDs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
11-25 15:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
11-25 15:58 INFO   Distro: Found a valid CD for Ubuntu: H:\
11-25 15:58 INFO   root: Running the CD menu...
11-25 15:58 DEBUG  WindowsFrontend: __init__...
11-25 15:58 DEBUG  WindowsFrontend: on_init...
11-25 15:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\translations, languages=['en_US', 'en']
11-25 15:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\translations, languages=['en_US', 'en']
11-25 15:58 INFO   root: CD menu finished
11-25 15:58 INFO   root: Already installed, running the uninstaller...
11-25 15:58 INFO   root: Running the uninstaller...
11-25 15:58 INFO   CommonBackend: This is the uninstaller running
11-25 15:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\translations, languages=['en_US', 'en']
11-25 15:58 INFO   root: Received settings
11-25 15:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\translations, languages=['en_US', 'en']
11-25 15:58 DEBUG  TaskList: # Running tasklist...
11-25 15:58 DEBUG  TaskList: ## Running Remove bootloader entry...
11-25 15:58 DEBUG  WindowsBackend: Could not find bcd id
11-25 15:58 DEBUG  WindowsBackend: undo_bootini A:
11-25 15:58 DEBUG  WindowsBackend: undo_configsys Drive(A: hd 36362.8710938 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: undo_bootini B:
11-25 15:58 DEBUG  WindowsBackend: undo_configsys Drive(B: hd 5799.64453125 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: undo_bootini C:
11-25 15:58 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 5266.7265625 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: undo_bootini E:
11-25 15:58 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 25941.8632813 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: undo_bootini F:
11-25 15:58 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 10569.2851563 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: undo_bootini G:
11-25 15:58 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 8133.34375 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: undo_bootini U:
11-25 15:58 DEBUG  WindowsBackend: undo_configsys Drive(U: hd 19666.6953125 mb free ntfs)
11-25 15:58 DEBUG  TaskList: ## Finished Remove bootloader entry
11-25 15:58 DEBUG  TaskList: ## Running Remove target dir...
11-25 15:58 DEBUG  CommonBackend: Deleting A:\ubuntu
11-25 15:58 DEBUG  TaskList: ## Finished Remove target dir
11-25 15:58 DEBUG  TaskList: ## Running Remove registry key...
11-25 15:58 DEBUG  TaskList: ## Finished Remove registry key
11-25 15:58 DEBUG  TaskList: # Finished tasklist
11-25 15:58 INFO   root: Almost finished uninstalling
11-25 15:58 INFO   root: Finished uninstallation
11-25 15:58 DEBUG  CommonBackend: Fetching basic info...
11-25 15:58 DEBUG  CommonBackend: original_exe=H:\wubi.exe
11-25 15:58 DEBUG  CommonBackend: platform=win32
11-25 15:58 DEBUG  CommonBackend: osname=nt
11-25 15:58 DEBUG  WindowsBackend: arch=amd64
11-25 15:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\data\isolist.ini
11-25 15:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-25 15:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-25 15:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-25 15:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-25 15:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-25 15:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-25 15:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-25 15:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-25 15:58 DEBUG  WindowsBackend: Fetching host info...
11-25 15:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-25 15:58 DEBUG  WindowsBackend: windows version=vista
11-25 15:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-25 15:58 DEBUG  WindowsBackend: windows_sp=None
11-25 15:58 DEBUG  WindowsBackend: windows_build=7601
11-25 15:58 DEBUG  WindowsBackend: gmt=7
11-25 15:58 DEBUG  WindowsBackend: country=US
11-25 15:58 DEBUG  WindowsBackend: timezone=America/New_York
11-25 15:58 DEBUG  WindowsBackend: windows_username=Duc tot bung
11-25 15:58 DEBUG  WindowsBackend: user_full_name=Duc tot bung
11-25 15:58 DEBUG  WindowsBackend: user_directory=C:\Users\Duc tot bung
11-25 15:58 DEBUG  WindowsBackend: windows_language_code=1033
11-25 15:58 DEBUG  WindowsBackend: windows_language=English
11-25 15:58 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
11-25 15:58 DEBUG  WindowsBackend: bootloader=vista
11-25 15:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5266.90234375 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(A: hd 37078.84375 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(B: hd 5799.64453125 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(C: hd 5266.90234375 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(E: hd 25941.8632813 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(F: hd 10569.2851563 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(G: hd 8133.34375 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-25 15:58 DEBUG  WindowsBackend: drive=Drive(U: hd 19666.6953125 mb free ntfs)
11-25 15:58 DEBUG  WindowsBackend: uninstaller_path=None
11-25 15:58 DEBUG  WindowsBackend: previous_target_dir=None
11-25 15:58 DEBUG  WindowsBackend: previous_distro_name=None
11-25 15:58 DEBUG  WindowsBackend: keyboard_id=67699721
11-25 15:58 DEBUG  WindowsBackend: keyboard_layout=us
11-25 15:58 DEBUG  WindowsBackend: keyboard_variant=
11-25 15:58 DEBUG  WindowsBackend: total_memory_mb=3947.53515625
11-25 15:58 DEBUG  CommonBackend: Checking pre-specified ISO U:\ubuntu-11.10-desktop-i386.iso
11-25 15:58 DEBUG  Distro:   checking Ubuntu ISO U:\ubuntu-11.10-desktop-i386.iso
11-25 15:58 INFO   Distro: Found a valid iso for Ubuntu: U:\ubuntu-11.10-desktop-i386.iso
11-25 15:58 DEBUG  CommonBackend: Searching for local CDs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether A:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-25 15:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 15:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-25 15:58 INFO   Distro: Found a valid CD for Ubuntu: H:\
11-25 15:58 INFO   root: Running the installer...
11-25 15:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\translations, languages=['en_US', 'en']
11-25 15:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\translations, languages=['en_US', 'en']
11-25 15:58 DEBUG  WinuiInstallationPage: target_drive=U:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ductotbung
11-25 15:58 INFO   root: Received settings
11-25 15:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\translations, languages=['en_US', 'en']
11-25 15:58 DEBUG  TaskList: # Running tasklist...
11-25 15:58 DEBUG  TaskList: ## Running select_target_dir...
11-25 15:58 INFO   WindowsBackend: Installing into U:\ubuntu
11-25 15:58 DEBUG  TaskList: ## Finished select_target_dir
11-25 15:58 DEBUG  TaskList: ## Running create_dir_structure...
11-25 15:58 DEBUG  CommonBackend: Creating dir U:\ubuntu
11-25 15:58 DEBUG  CommonBackend: Creating dir U:\ubuntu\disks
11-25 15:58 DEBUG  CommonBackend: Creating dir U:\ubuntu\install
11-25 15:58 DEBUG  CommonBackend: Creating dir U:\ubuntu\install\boot
11-25 15:58 DEBUG  CommonBackend: Creating dir U:\ubuntu\disks\boot
11-25 15:58 DEBUG  CommonBackend: Creating dir U:\ubuntu\disks\boot\grub
11-25 15:58 DEBUG  CommonBackend: Creating dir U:\ubuntu\install\boot\grub
11-25 15:58 DEBUG  TaskList: ## Finished create_dir_structure
11-25 15:58 DEBUG  TaskList: ## Running uncompress_target_dir...
11-25 15:58 DEBUG  TaskList: ## Finished uncompress_target_dir
11-25 15:58 DEBUG  TaskList: ## Running create_uninstaller...
11-25 15:58 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> U:\ubuntu\uninstall-wubi.exe
11-25 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString U:\ubuntu\uninstall-wubi.exe
11-25 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir U:\ubuntu
11-25 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-25 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon U:\ubuntu\Ubuntu.ico
11-25 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
11-25 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-25 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
11-25 15:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-25 15:58 DEBUG  TaskList: ## Finished create_uninstaller
11-25 15:58 DEBUG  TaskList: ## Running copy_installation_files...
11-25 15:58 DEBUG  WindowsBackend: Copying C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\data\custom-installation -> U:\ubuntu\install\custom-installation
11-25 15:58 DEBUG  WindowsBackend: Copying C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\winboot -> U:\ubuntu\winboot
11-25 15:58 DEBUG  WindowsBackend: Copying C:\Users\DUCTOT~1\AppData\Local\Temp\pyl7425.tmp\data\images\Ubuntu.ico -> U:\ubuntu\Ubuntu.ico
11-25 15:58 DEBUG  TaskList: ## Finished copy_installation_files
11-25 15:58 DEBUG  TaskList: ## Running get_iso...
11-25 15:58 DEBUG  CommonBackend: Trying to use pre-specified ISO U:\ubuntu-11.10-desktop-i386.iso
11-25 15:58 DEBUG  TaskList: New task is_valid_iso
11-25 15:58 DEBUG  TaskList: ### Running is_valid_iso...
11-25 15:58 DEBUG  Distro:   checking Ubuntu ISO U:\ubuntu-11.10-desktop-i386.iso
11-25 15:58 INFO   Distro: Found a valid iso for Ubuntu: U:\ubuntu-11.10-desktop-i386.iso
11-25 15:58 DEBUG  TaskList: ### Finished is_valid_iso
11-25 15:58 DEBUG  TaskList: New task check_iso
11-25 15:58 DEBUG  TaskList: ### Running check_iso...
11-25 15:58 DEBUG  CommonBackend: Checking U:\ubuntu-11.10-desktop-i386.iso
11-25 15:58 DEBUG  Distro:   checking Ubuntu ISO U:\ubuntu-11.10-desktop-i386.iso
11-25 15:58 INFO   Distro: Found a valid iso for Ubuntu: U:\ubuntu-11.10-desktop-i386.iso
11-25 15:58 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
11-25 15:58 DEBUG  TaskList: New task get_metalink
11-25 15:58 DEBUG  TaskList: #### Running get_metalink...
11-25 15:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink](http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink) > U:\ubuntu\install
11-25 15:58 DEBUG  downloader: Download start filename=U:\ubuntu\install\ubuntu-11.10-desktop-i386.metalink, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink, basename=ubuntu-11.10-desktop-i386.metalink, length=4867, text=None
11-25 15:58 DEBUG  downloader: download finished (read 4867 bytes)
11-25 15:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/MD5SUMS-metalink](http://releases.ubuntu.com/11.10/MD5SUMS-metalink) > U:\ubuntu\install
11-25 15:59 DEBUG  downloader: Download start filename=U:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=419, text=None
11-25 15:59 DEBUG  downloader: download finished (read 419 bytes)
11-25 15:59 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.10/MD5SUMS-metalink.gpg) > U:\ubuntu\install
11-25 15:59 DEBUG  downloader: Download start filename=U:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
11-25 15:59 DEBUG  downloader: download finished (read 198 bytes)
11-25 15:59 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
11-25 15:59 INFO   saplog: Checking block bindings..
11-25 15:59 INFO   saplog: Key verified successfully.
11-25 15:59 DEBUG  CommonBackend: metalink md5sums:
a65c220b437d6907ba9463b7f479fea5  ubuntu-11.10-alternate-amd64.metalink
bdbf5bf7dfa85cad2cd711f081b071ec  ubuntu-11.10-alternate-i386.metalink
4a4ddfa7d6eea4d9cf7a9f8d854e0418  ubuntu-11.10-desktop-amd64.metalink
a84050d7b00ff42b83a69ad7309b6f36  ubuntu-11.10-desktop-i386.metalink
c2f7e1f7352a8d3cd1c2dede0c709a1a  ubuntu-11.10-server-amd64.metalink
2b296035b3ba3f8536dc0efa49a52fc2  ubuntu-11.10-server-i386.metalink

11-25 15:59 DEBUG  TaskList: #### Finished get_metalink
11-25 15:59 DEBUG  TaskList: New task get_file_md5
11-25 15:59 DEBUG  TaskList: #### Running get_file_md5...
11-25 15:59 DEBUG  TaskList: #### Finished get_file_md5
11-25 15:59 DEBUG  TaskList: ### Finished check_iso
11-25 15:59 DEBUG  TaskList: New task copy_file
11-25 15:59 DEBUG  CommonBackend: Copying U:\ubuntu-11.10-desktop-i386.iso > U:\ubuntu\install\installation.iso
11-25 15:59 DEBUG  TaskList: ### Running copy_file...
11-25 15:59 DEBUG  TaskList: ### Finished copy_file
11-25 15:59 DEBUG  TaskList: ## Finished get_iso
11-25 15:59 DEBUG  TaskList: ## Running extract_kernel...
11-25 15:59 DEBUG  CommonBackend: Extracting files from ISO U:\ubuntu\install\installation.iso
11-25 15:59 DEBUG  WindowsBackend:   extracting md5sum.txt from U:\ubuntu\install\installation.iso
11-25 15:59 DEBUG  WindowsBackend:   extracting casper\vmlinuz from U:\ubuntu\install\installation.iso
11-25 15:59 DEBUG  WindowsBackend:   extracting casper\initrd.lz from U:\ubuntu\install\installation.iso
11-25 15:59 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
11-25 15:59 DEBUG  CommonBackend:   checking U:\ubuntu\install\boot\vmlinuz
11-25 15:59 DEBUG  CommonBackend:   U:\ubuntu\install\boot\vmlinuz md5 = fde150f5c6fd2de66ed7876efbfcc4c7 == fde150f5c6fd2de66ed7876efbfcc4c7
11-25 15:59 DEBUG  CommonBackend:   checking U:\ubuntu\install\boot\initrd.lz
11-25 15:59 DEBUG  CommonBackend:   U:\ubuntu\install\boot\initrd.lz md5 = d6baee1e11f1d6de6eba6bd43dbde352 == d6baee1e11f1d6de6eba6bd43dbde352
11-25 15:59 DEBUG  TaskList: ## Finished extract_kernel
11-25 15:59 DEBUG  TaskList: ## Running choose_disk_sizes...
11-25 15:59 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
11-25 15:59 DEBUG  TaskList: ## Finished choose_disk_sizes
11-25 15:59 DEBUG  TaskList: ## Running create_preseed...
11-25 15:59 DEBUG  TaskList: ## Finished create_preseed
11-25 15:59 DEBUG  TaskList: ## Running modify_bootloader...
11-25 15:59 DEBUG  TaskList: New task modify_bcd
11-25 15:59 DEBUG  TaskList: ### Running modify_bcd...
11-25 15:59 DEBUG  WindowsBackend: modify_bcd Drive(A: hd 37078.84375 mb free ntfs)
11-25 15:59 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {edea7bcd-f968-11e0-b2d0-f0c2a6084129} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 692, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {edea7bcd-f968-11e0-b2d0-f0c2a6084129} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
11-25 15:59 DEBUG  TaskList: # Cancelling tasklist
11-25 15:59 DEBUG  TaskList: New task modify_bcd
11-25 15:59 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {edea7bcd-f968-11e0-b2d0-f0c2a6084129} device partition=U:
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
  File "\lib\wubi\backends\win32\backend.py", line 692, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {edea7bcd-f968-11e0-b2d0-f0c2a6084129} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
11-25 15:59 DEBUG  TaskList: New task modify_bcd
11-25 15:59 DEBUG  TaskList: New task modify_bcd
11-25 15:59 DEBUG  TaskList: New task modify_bcd
11-25 15:59 DEBUG  TaskList: New task modify_bcd
11-25 15:59 DEBUG  TaskList: New task modify_bcd
11-25 15:59 DEBUG  TaskList: ## Finished modify_bootloader
11-25 15:59 DEBUG  TaskList: # Finished tasklist
11-25 16:05 INFO   root: === wubi 11.10 rev241 ===
11-25 16:05 DEBUG  root: Logfile is c:\users\ductot~1\appdata\local\temp\wubi-11.10-rev241.log
11-25 16:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="U:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
11-25 16:05 DEBUG  CommonBackend: data_dir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp\data
11-25 16:05 DEBUG  WindowsBackend: 7z=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp\bin\7z.exe
11-25 16:05 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-25 16:05 DEBUG  CommonBackend: Fetching basic info...
11-25 16:05 DEBUG  CommonBackend: original_exe=U:\ubuntu\uninstall-wubi.exe
11-25 16:05 DEBUG  CommonBackend: platform=win32
11-25 16:05 DEBUG  CommonBackend: osname=nt
11-25 16:05 DEBUG  CommonBackend: language=en_US
11-25 16:05 DEBUG  CommonBackend: encoding=cp1252
11-25 16:05 DEBUG  WindowsBackend: arch=amd64
11-25 16:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp\data\isolist.ini
11-25 16:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-25 16:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-25 16:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-25 16:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-25 16:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-25 16:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-25 16:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-25 16:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-25 16:05 DEBUG  WindowsBackend: Fetching host info...
11-25 16:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-25 16:05 DEBUG  WindowsBackend: windows version=vista
11-25 16:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-25 16:05 DEBUG  WindowsBackend: windows_sp=None
11-25 16:05 DEBUG  WindowsBackend: windows_build=7601
11-25 16:05 DEBUG  WindowsBackend: gmt=7
11-25 16:05 DEBUG  WindowsBackend: country=US
11-25 16:05 DEBUG  WindowsBackend: timezone=America/New_York
11-25 16:05 DEBUG  WindowsBackend: windows_username=Duc tot bung
11-25 16:05 DEBUG  WindowsBackend: user_full_name=Duc tot bung
11-25 16:05 DEBUG  WindowsBackend: user_directory=C:\Users\Duc tot bung
11-25 16:05 DEBUG  WindowsBackend: windows_language_code=1033
11-25 16:05 DEBUG  WindowsBackend: windows_language=English
11-25 16:05 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
11-25 16:05 DEBUG  WindowsBackend: bootloader=vista
11-25 16:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5238.03515625 mb free ntfs)
11-25 16:05 DEBUG  WindowsBackend: drive=Drive(A: hd 37078.84375 mb free ntfs)
11-25 16:05 DEBUG  WindowsBackend: drive=Drive(B: hd 5799.64453125 mb free ntfs)
11-25 16:05 DEBUG  WindowsBackend: drive=Drive(C: hd 5238.03515625 mb free ntfs)
11-25 16:05 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-25 16:05 DEBUG  WindowsBackend: drive=Drive(E: hd 25941.8632813 mb free ntfs)
11-25 16:05 DEBUG  WindowsBackend: drive=Drive(F: hd 10569.2851563 mb free ntfs)
11-25 16:05 DEBUG  WindowsBackend: drive=Drive(G: hd 8133.34375 mb free ntfs)
11-25 16:05 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-25 16:05 DEBUG  WindowsBackend: drive=Drive(U: hd 18950.5976563 mb free ntfs)
11-25 16:05 DEBUG  WindowsBackend: uninstaller_path=U:\ubuntu\uninstall-wubi.exe
11-25 16:05 DEBUG  WindowsBackend: previous_target_dir=U:\ubuntu
11-25 16:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-25 16:05 DEBUG  WindowsBackend: keyboard_id=67699721
11-25 16:05 DEBUG  WindowsBackend: keyboard_layout=us
11-25 16:05 DEBUG  WindowsBackend: keyboard_variant=
11-25 16:05 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-25 16:05 DEBUG  CommonBackend: locale=en_US.UTF-8
11-25 16:05 DEBUG  WindowsBackend: total_memory_mb=3947.53515625
11-25 16:05 DEBUG  CommonBackend: Searching ISOs on USB devices
11-25 16:05 DEBUG  Distro:   checking Ubuntu ISO B:\X17-59465.iso
11-25 16:05 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 16:05 DEBUG  Distro:   checking Ubuntu ISO B:\X17-59465.iso
11-25 16:05 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 16:05 DEBUG  Distro:   checking Kubuntu ISO B:\X17-59465.iso
11-25 16:05 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 16:05 DEBUG  Distro:   checking Kubuntu ISO B:\X17-59465.iso
11-25 16:05 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 16:05 DEBUG  Distro:   checking Xubuntu ISO B:\X17-59465.iso
11-25 16:05 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 16:05 DEBUG  Distro:   checking Xubuntu ISO B:\X17-59465.iso
11-25 16:05 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 16:05 DEBUG  Distro:   checking Mythbuntu ISO B:\X17-59465.iso
11-25 16:05 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 16:05 DEBUG  Distro:   checking Mythbuntu ISO B:\X17-59465.iso
11-25 16:05 DEBUG  Distro:     wrong size: 3320903680 > 900000000
11-25 16:05 DEBUG  Distro:   checking Ubuntu ISO U:\ubuntu-11.10-desktop-i386.iso
11-25 16:05 DEBUG  WindowsBackend:   extracting .disk\info from U:\ubuntu-11.10-desktop-i386.iso
11-25 16:06 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
11-25 16:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
11-25 16:06 INFO   Distro: Found a valid iso for Ubuntu: U:\ubuntu-11.10-desktop-i386.iso
11-25 16:06 DEBUG  CommonBackend: Searching for local CDs
11-25 16:06 DEBUG  Distro:   checking whether A:\ is a valid Ubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether A:\ is a valid Ubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether A:\ is a valid Kubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether A:\ is a valid Kubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether A:\ is a valid Xubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether A:\ is a valid Xubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether A:\ is a valid Mythbuntu CD
11-25 16:06 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether A:\ is a valid Mythbuntu CD
11-25 16:06 DEBUG  Distro:     does not contain A:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
11-25 16:06 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
11-25 16:06 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp is a valid Ubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp is a valid Ubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp is a valid Kubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp is a valid Kubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp is a valid Xubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp is a valid Xubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp is a valid Mythbuntu CD
11-25 16:06 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp is a valid Mythbuntu CD
11-25 16:06 DEBUG  Distro:     does not contain C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-25 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-25 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-25 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-25 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-25 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-25 16:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-25 16:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-25 16:06 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-25 16:06 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-25 16:06 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
11-25 16:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
11-25 16:06 INFO   Distro: Found a valid CD for Ubuntu: H:\
11-25 16:06 INFO   root: Running the uninstaller...
11-25 16:06 INFO   CommonBackend: This is the uninstaller running
11-25 16:06 DEBUG  WindowsFrontend: __init__...
11-25 16:06 DEBUG  WindowsFrontend: on_init...
11-25 16:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp\translations, languages=['en_US', 'en']
11-25 16:06 INFO   root: Received settings
11-25 16:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp\translations, languages=['en_US', 'en']
11-25 16:06 DEBUG  TaskList: # Running tasklist...
11-25 16:06 DEBUG  TaskList: ## Running Remove bootloader entry...
11-25 16:06 DEBUG  WindowsBackend: Could not find bcd id
11-25 16:06 DEBUG  WindowsBackend: undo_bootini A:
11-25 16:06 DEBUG  WindowsBackend: undo_configsys Drive(A: hd 37078.84375 mb free ntfs)
11-25 16:06 DEBUG  WindowsBackend: undo_bootini B:
11-25 16:06 DEBUG  WindowsBackend: undo_configsys Drive(B: hd 5799.64453125 mb free ntfs)
11-25 16:06 DEBUG  WindowsBackend: undo_bootini C:
11-25 16:06 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 5238.03515625 mb free ntfs)
11-25 16:06 DEBUG  WindowsBackend: undo_bootini E:
11-25 16:06 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 25941.8632813 mb free ntfs)
11-25 16:06 DEBUG  WindowsBackend: undo_bootini F:
11-25 16:06 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 10569.2851563 mb free ntfs)
11-25 16:06 DEBUG  WindowsBackend: undo_bootini G:
11-25 16:06 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 8133.34375 mb free ntfs)
11-25 16:06 DEBUG  WindowsBackend: undo_bootini U:
11-25 16:06 DEBUG  WindowsBackend: undo_configsys Drive(U: hd 18950.5976563 mb free ntfs)
11-25 16:06 DEBUG  TaskList: ## Finished Remove bootloader entry
11-25 16:06 DEBUG  TaskList: ## Running Remove target dir...
11-25 16:06 DEBUG  CommonBackend: Deleting U:\ubuntu
11-25 16:06 DEBUG  TaskList: ## Finished Remove target dir
11-25 16:06 DEBUG  TaskList: ## Running Remove registry key...
11-25 16:06 DEBUG  TaskList: ## Finished Remove registry key
11-25 16:06 DEBUG  TaskList: # Finished tasklist
11-25 16:06 INFO   root: Almost finished uninstalling
11-25 16:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DUCTOT~1\AppData\Local\Temp\pyl8F24.tmp\translations, languages=['en_US', 'en']
11-25 16:06 INFO   root: Finished uninstallation
11-25 16:06 DEBUG  root: application.quit
11-25 16:06 DEBUG  WindowsFrontend: frontend.quit
11-25 16:06 DEBUG  WindowsFrontend: frontend.on_quit
11-25 16:06 DEBUG  root: application.on_quit
11-25 16:06 INFO   root: sys.exit
```

---

### Post by Rubi1200 on 2011-11-25
As bcbc already mentioned, you probably have dynamic disks. Attempting to install Ubuntu, Wubi or regular, has the potential to cause serious issues.

Follow the link posted for more options.

---

