---
title: "WUBI fails to install"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by iTails on 2011-11-20
I tried installing Ubuntu again from WUBI and this error keeps popping up every time I try to install it. Any suggestions?

[IMG]http://dl.dropbox.com/u/21577357/wth.PNG[/IMG]

---

### Post by emagine1 on 2011-11-20
post the log

---

### Post by iTails on 2011-11-20
```
11-20 19:36 INFO   root: === wubi 11.10 rev245 ===
11-20 19:36 DEBUG  root: Logfile is c:\users\robert\appdata\local\temp\wubi-11.10-rev245.log
11-20 19:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Robert\\Downloads\\wubi.exe"']
11-20 19:36 DEBUG  CommonBackend: data_dir=C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\data
11-20 19:36 DEBUG  WindowsBackend: 7z=C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\bin\7z.exe
11-20 19:36 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-20 19:36 DEBUG  CommonBackend: Fetching basic info...
11-20 19:36 DEBUG  CommonBackend: original_exe=C:\Users\Robert\Downloads\wubi.exe
11-20 19:36 DEBUG  CommonBackend: platform=win32
11-20 19:36 DEBUG  CommonBackend: osname=nt
11-20 19:36 DEBUG  CommonBackend: language=en_US
11-20 19:36 DEBUG  CommonBackend: encoding=cp1252
11-20 19:36 DEBUG  WindowsBackend: arch=amd64
11-20 19:36 DEBUG  CommonBackend: Parsing isolist=C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\data\isolist.ini
11-20 19:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-20 19:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-20 19:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-20 19:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-20 19:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-20 19:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-20 19:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-20 19:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-20 19:36 DEBUG  WindowsBackend: Fetching host info...
11-20 19:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-20 19:36 DEBUG  WindowsBackend: windows version=vista
11-20 19:36 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-20 19:36 DEBUG  WindowsBackend: windows_sp=None
11-20 19:36 DEBUG  WindowsBackend: windows_build=7601
11-20 19:36 DEBUG  WindowsBackend: gmt=-5
11-20 19:36 DEBUG  WindowsBackend: country=US
11-20 19:36 DEBUG  WindowsBackend: timezone=America/New_York
11-20 19:36 DEBUG  WindowsBackend: windows_username=Robert
11-20 19:36 DEBUG  WindowsBackend: user_full_name=Robert
11-20 19:36 DEBUG  WindowsBackend: user_directory=C:\Users\Robert
11-20 19:36 DEBUG  WindowsBackend: windows_language_code=1033
11-20 19:36 DEBUG  WindowsBackend: windows_language=English
11-20 19:36 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
11-20 19:36 DEBUG  WindowsBackend: bootloader=vista
11-20 19:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 34592.1210938 mb free ntfs)
11-20 19:36 DEBUG  WindowsBackend: drive=Drive(C: hd 34592.1210938 mb free ntfs)
11-20 19:36 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-20 19:36 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
11-20 19:36 DEBUG  WindowsBackend: drive=Drive(F: hd 115790.21875 mb free ntfs)
11-20 19:36 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
11-20 19:36 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-20 19:36 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
11-20 19:36 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free udf)
11-20 19:36 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
11-20 19:36 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free )
11-20 19:36 DEBUG  WindowsBackend: drive=Drive(N: removable 0.0 mb free )
11-20 19:36 DEBUG  WindowsBackend: uninstaller_path=None
11-20 19:36 DEBUG  WindowsBackend: previous_target_dir=None
11-20 19:36 DEBUG  WindowsBackend: previous_distro_name=None
11-20 19:36 DEBUG  WindowsBackend: keyboard_id=67699721
11-20 19:36 DEBUG  WindowsBackend: keyboard_layout=us
11-20 19:36 DEBUG  WindowsBackend: keyboard_variant=
11-20 19:36 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-20 19:36 DEBUG  CommonBackend: locale=en_US.UTF-8
11-20 19:36 DEBUG  WindowsBackend: total_memory_mb=4095.26953125
11-20 19:36 DEBUG  CommonBackend: Searching ISOs on USB devices
11-20 19:36 DEBUG  CommonBackend: Searching for local CDs
11-20 19:36 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
11-20 19:36 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 19:36 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
11-20 19:36 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 19:36 INFO   root: Running the installer...
11-20 19:36 DEBUG  WindowsFrontend: __init__...
11-20 19:36 DEBUG  WindowsFrontend: on_init...
11-20 19:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\translations, languages=['en_US', 'en']
11-20 19:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\translations, languages=['en_US', 'en']
11-20 19:37 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=robert
11-20 19:37 INFO   root: Received settings
11-20 19:37 DEBUG  CommonBackend: Searching for local CD
11-20 19:37 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp is a valid Ubuntu CD
11-20 19:37 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\casper\filesystem.squashfs
11-20 19:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 19:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 19:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-20 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 19:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 19:37 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 19:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 19:37 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 19:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 19:37 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 19:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 19:37 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 19:37 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 19:37 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 19:37 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 19:37 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 19:37 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 19:37 DEBUG  CommonBackend: Searching for local ISO
11-20 19:37 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Robert\Downloads\rld-bme2.iso
11-20 19:37 DEBUG  Distro:     wrong size: 5953308672 > 900000000
11-20 19:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\translations, languages=['en_US', 'en']
11-20 19:37 DEBUG  TaskList: # Running tasklist...
11-20 19:37 DEBUG  TaskList: ## Running select_target_dir...
11-20 19:37 INFO   WindowsBackend: Installing into C:\ubuntu
11-20 19:37 DEBUG  TaskList: ## Finished select_target_dir
11-20 19:37 DEBUG  TaskList: ## Running create_dir_structure...
11-20 19:37 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-20 19:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-20 19:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-20 19:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-20 19:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-20 19:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-20 19:37 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-20 19:37 DEBUG  TaskList: ## Finished create_dir_structure
11-20 19:37 DEBUG  TaskList: ## Running create_uninstaller...
11-20 19:37 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Robert\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-20 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-20 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-20 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-20 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-20 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-20 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-20 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
11-20 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
11-20 19:37 DEBUG  TaskList: ## Finished create_uninstaller
11-20 19:37 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-20 19:37 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-20 19:37 DEBUG  TaskList: ## Running get_diskimage...
11-20 19:37 DEBUG  TaskList: New task download
11-20 19:37 DEBUG  TaskList: ### Running download...
11-20 19:37 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
11-20 19:37 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
11-20 19:44 DEBUG  TaskList: ### Finished download
11-20 19:44 DEBUG  downloader: download finished (read 507143012 bytes)
11-20 19:44 DEBUG  TaskList: ## Finished get_diskimage
11-20 19:44 DEBUG  TaskList: ## Running extract_diskimage...
11-20 19:46 DEBUG  TaskList: ## Finished extract_diskimage
11-20 19:46 DEBUG  TaskList: ## Running choose_disk_sizes...
11-20 19:46 DEBUG  WindowsBackend: total size=20000
  root=19744
  swap=256
  home=0
  usr=0
11-20 19:46 DEBUG  TaskList: ## Finished choose_disk_sizes
11-20 19:46 DEBUG  TaskList: ## Running expand_diskimage...
11-20 19:55 DEBUG  TaskList: ## Finished expand_diskimage
11-20 19:55 DEBUG  TaskList: ## Running create_swap_diskimage...
11-20 19:55 DEBUG  TaskList: ## Finished create_swap_diskimage
11-20 19:55 DEBUG  TaskList: ## Running modify_bootloader...
11-20 19:55 DEBUG  TaskList: New task modify_bcd
11-20 19:55 DEBUG  TaskList: ### Running modify_bcd...
11-20 19:55 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 34592.1210938 mb free ntfs)
11-20 19:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {a9a046a7-ab69-11e0-b3b5-bd688f2b94bb}
11-20 19:55 DEBUG  TaskList: ### Finished modify_bcd
11-20 19:55 DEBUG  TaskList: New task modify_bcd
11-20 19:55 DEBUG  TaskList: ### Running modify_bcd...
11-20 19:55 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 115790.21875 mb free ntfs)
11-20 19:55 DEBUG  WindowsBackend: BCD has already been modified
11-20 19:55 DEBUG  TaskList: ### Finished modify_bcd
11-20 19:55 DEBUG  TaskList: New task modify_bcd
11-20 19:55 DEBUG  TaskList: ### Running modify_bcd...
11-20 19:55 DEBUG  WindowsBackend: modify_bcd Drive(N: removable 0.0 mb free )
11-20 19:55 DEBUG  WindowsBackend: BCD has already been modified
11-20 19:55 DEBUG  TaskList: ### Finished modify_bcd
11-20 19:55 DEBUG  TaskList: ## Finished modify_bootloader
11-20 19:55 DEBUG  TaskList: ## Running diskimage_bootloader...
11-20 19:55 DEBUG  WindowsBackend: Copying C:\Users\Robert\AppData\Local\Temp\pyl8803.tmp\winboot -> C:\ubuntu\winboot
11-20 19:55 ERROR  TaskList: [Errno 13] Permission denied: 'N:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'N:\\wubildr'
11-20 19:55 DEBUG  TaskList: # Cancelling tasklist
11-20 19:55 DEBUG  TaskList: # Finished tasklist
11-20 19:55 ERROR  root: [Errno 13] Permission denied: 'N:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'N:\\wubildr'
11-20 21:53 INFO   root: === wubi 11.10 rev245 ===
11-20 21:53 DEBUG  root: Logfile is c:\users\robert\appdata\local\temp\wubi-11.10-rev245.log
11-20 21:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Robert\\Downloads\\wubi.exe"']
11-20 21:53 DEBUG  CommonBackend: data_dir=C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\data
11-20 21:53 DEBUG  WindowsBackend: 7z=C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\bin\7z.exe
11-20 21:53 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-20 21:53 DEBUG  CommonBackend: Fetching basic info...
11-20 21:53 DEBUG  CommonBackend: original_exe=C:\Users\Robert\Downloads\wubi.exe
11-20 21:53 DEBUG  CommonBackend: platform=win32
11-20 21:53 DEBUG  CommonBackend: osname=nt
11-20 21:53 DEBUG  CommonBackend: language=en_US
11-20 21:53 DEBUG  CommonBackend: encoding=cp1252
11-20 21:53 DEBUG  WindowsBackend: arch=amd64
11-20 21:53 DEBUG  CommonBackend: Parsing isolist=C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\data\isolist.ini
11-20 21:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-20 21:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-20 21:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-20 21:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-20 21:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-20 21:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-20 21:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-20 21:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-20 21:53 DEBUG  WindowsBackend: Fetching host info...
11-20 21:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-20 21:53 DEBUG  WindowsBackend: windows version=vista
11-20 21:53 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-20 21:53 DEBUG  WindowsBackend: windows_sp=None
11-20 21:53 DEBUG  WindowsBackend: windows_build=7601
11-20 21:53 DEBUG  WindowsBackend: gmt=-5
11-20 21:53 DEBUG  WindowsBackend: country=US
11-20 21:53 DEBUG  WindowsBackend: timezone=America/New_York
11-20 21:53 DEBUG  WindowsBackend: windows_username=Robert
11-20 21:53 DEBUG  WindowsBackend: user_full_name=Robert
11-20 21:53 DEBUG  WindowsBackend: user_directory=C:\Users\Robert
11-20 21:53 DEBUG  WindowsBackend: windows_language_code=1033
11-20 21:53 DEBUG  WindowsBackend: windows_language=English
11-20 21:53 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
11-20 21:53 DEBUG  WindowsBackend: bootloader=vista
11-20 21:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 34916.1289063 mb free ntfs)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(C: hd 34916.1289063 mb free ntfs)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(F: hd 115790.089844 mb free ntfs)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free udf)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free )
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(N: removable 0.0 mb free )
11-20 21:53 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-20 21:53 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-20 21:53 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-20 21:53 DEBUG  WindowsBackend: keyboard_id=67699721
11-20 21:53 DEBUG  WindowsBackend: keyboard_layout=us
11-20 21:53 DEBUG  WindowsBackend: keyboard_variant=
11-20 21:53 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-20 21:53 DEBUG  CommonBackend: locale=en_US.UTF-8
11-20 21:53 DEBUG  WindowsBackend: total_memory_mb=4095.26953125
11-20 21:53 DEBUG  CommonBackend: Searching ISOs on USB devices
11-20 21:53 DEBUG  CommonBackend: Searching for local CDs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 INFO   root: Already installed, running the uninstaller...
11-20 21:53 INFO   root: Running the uninstaller...
11-20 21:53 INFO   CommonBackend: This is the uninstaller running
11-20 21:53 DEBUG  WindowsFrontend: __init__...
11-20 21:53 DEBUG  WindowsFrontend: on_init...
11-20 21:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\translations, languages=['en_US', 'en']
11-20 21:53 INFO   root: Received settings
11-20 21:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\translations, languages=['en_US', 'en']
11-20 21:53 DEBUG  TaskList: # Running tasklist...
11-20 21:53 DEBUG  TaskList: ## Running Remove bootloader entry...
11-20 21:53 DEBUG  WindowsBackend: Removing bcd entry {a9a046a7-ab69-11e0-b3b5-bd688f2b94bb}
11-20 21:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
11-20 21:53 DEBUG  WindowsBackend: undo_bootini C:
11-20 21:53 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 34916.1289063 mb free ntfs)
11-20 21:53 DEBUG  WindowsBackend: undo_bootini F:
11-20 21:53 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 115790.089844 mb free ntfs)
11-20 21:53 DEBUG  WindowsBackend: undo_bootini N:
11-20 21:53 DEBUG  WindowsBackend: undo_configsys Drive(N: removable 0.0 mb free )
11-20 21:53 DEBUG  TaskList: ## Finished Remove bootloader entry
11-20 21:53 DEBUG  TaskList: ## Running Remove target dir...
11-20 21:53 DEBUG  CommonBackend: Deleting C:\ubuntu
11-20 21:53 DEBUG  TaskList: ## Finished Remove target dir
11-20 21:53 DEBUG  TaskList: ## Running Remove registry key...
11-20 21:53 DEBUG  TaskList: ## Finished Remove registry key
11-20 21:53 DEBUG  TaskList: # Finished tasklist
11-20 21:53 INFO   root: Almost finished uninstalling
11-20 21:53 INFO   root: Finished uninstallation
11-20 21:53 DEBUG  CommonBackend: Fetching basic info...
11-20 21:53 DEBUG  CommonBackend: original_exe=C:\Users\Robert\Downloads\wubi.exe
11-20 21:53 DEBUG  CommonBackend: platform=win32
11-20 21:53 DEBUG  CommonBackend: osname=nt
11-20 21:53 DEBUG  WindowsBackend: arch=amd64
11-20 21:53 DEBUG  CommonBackend: Parsing isolist=C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\data\isolist.ini
11-20 21:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-20 21:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-20 21:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-20 21:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-20 21:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-20 21:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-20 21:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-20 21:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-20 21:53 DEBUG  WindowsBackend: Fetching host info...
11-20 21:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-20 21:53 DEBUG  WindowsBackend: windows version=vista
11-20 21:53 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-20 21:53 DEBUG  WindowsBackend: windows_sp=None
11-20 21:53 DEBUG  WindowsBackend: windows_build=7601
11-20 21:53 DEBUG  WindowsBackend: gmt=-5
11-20 21:53 DEBUG  WindowsBackend: country=US
11-20 21:53 DEBUG  WindowsBackend: timezone=America/New_York
11-20 21:53 DEBUG  WindowsBackend: windows_username=Robert
11-20 21:53 DEBUG  WindowsBackend: user_full_name=Robert
11-20 21:53 DEBUG  WindowsBackend: user_directory=C:\Users\Robert
11-20 21:53 DEBUG  WindowsBackend: windows_language_code=1033
11-20 21:53 DEBUG  WindowsBackend: windows_language=English
11-20 21:53 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
11-20 21:53 DEBUG  WindowsBackend: bootloader=vista
11-20 21:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 38080.84375 mb free ntfs)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(C: hd 38080.84375 mb free ntfs)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(F: hd 115790.21875 mb free ntfs)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free udf)
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free )
11-20 21:53 DEBUG  WindowsBackend: drive=Drive(N: removable 0.0 mb free )
11-20 21:53 DEBUG  WindowsBackend: uninstaller_path=None
11-20 21:53 DEBUG  WindowsBackend: previous_target_dir=None
11-20 21:53 DEBUG  WindowsBackend: previous_distro_name=None
11-20 21:53 DEBUG  WindowsBackend: keyboard_id=67699721
11-20 21:53 DEBUG  WindowsBackend: keyboard_layout=us
11-20 21:53 DEBUG  WindowsBackend: keyboard_variant=
11-20 21:53 DEBUG  WindowsBackend: total_memory_mb=4095.26953125
11-20 21:53 DEBUG  CommonBackend: Searching ISOs on USB devices
11-20 21:53 DEBUG  CommonBackend: Searching for local CDs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
11-20 21:53 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:53 INFO   root: Running the installer...
11-20 21:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\translations, languages=['en_US', 'en']
11-20 21:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\translations, languages=['en_US', 'en']
11-20 21:54 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=25000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=robert
11-20 21:54 INFO   root: Received settings
11-20 21:54 DEBUG  CommonBackend: Searching for local CD
11-20 21:54 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp is a valid Ubuntu CD
11-20 21:54 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\casper\filesystem.squashfs
11-20 21:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 21:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 21:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 21:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-20 21:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 21:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 21:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 21:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 21:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 21:54 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 21:54 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 21:54 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 21:54 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 21:54 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 21:54 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 21:54 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 21:54 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 21:54 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 21:54 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 21:54 DEBUG  CommonBackend: Searching for local ISO
11-20 21:54 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Robert\Downloads\rld-bme2.iso
11-20 21:54 DEBUG  Distro:     wrong size: 5953308672 > 900000000
11-20 21:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\translations, languages=['en_US', 'en']
11-20 21:54 DEBUG  TaskList: # Running tasklist...
11-20 21:54 DEBUG  TaskList: ## Running select_target_dir...
11-20 21:54 INFO   WindowsBackend: Installing into C:\ubuntu
11-20 21:54 DEBUG  TaskList: ## Finished select_target_dir
11-20 21:54 DEBUG  TaskList: ## Running create_dir_structure...
11-20 21:54 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-20 21:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-20 21:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-20 21:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-20 21:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-20 21:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-20 21:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-20 21:54 DEBUG  TaskList: ## Finished create_dir_structure
11-20 21:54 DEBUG  TaskList: ## Running create_uninstaller...
11-20 21:54 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Robert\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-20 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-20 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-20 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-20 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-20 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-20 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-20 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
11-20 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
11-20 21:54 DEBUG  TaskList: ## Finished create_uninstaller
11-20 21:54 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-20 21:54 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-20 21:54 DEBUG  TaskList: ## Running get_diskimage...
11-20 21:54 DEBUG  TaskList: New task download
11-20 21:54 DEBUG  TaskList: ### Running download...
11-20 21:54 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
11-20 21:54 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
11-20 22:01 DEBUG  TaskList: ### Finished download
11-20 22:01 DEBUG  downloader: download finished (read 507143012 bytes)
11-20 22:01 DEBUG  TaskList: ## Finished get_diskimage
11-20 22:01 DEBUG  TaskList: ## Running extract_diskimage...
11-20 22:03 DEBUG  TaskList: ## Finished extract_diskimage
11-20 22:03 DEBUG  TaskList: ## Running choose_disk_sizes...
11-20 22:03 DEBUG  WindowsBackend: total size=25000
  root=24744
  swap=256
  home=0
  usr=0
11-20 22:03 DEBUG  TaskList: ## Finished choose_disk_sizes
11-20 22:03 DEBUG  TaskList: ## Running expand_diskimage...
11-20 22:18 DEBUG  TaskList: ## Finished expand_diskimage
11-20 22:18 DEBUG  TaskList: ## Running create_swap_diskimage...
11-20 22:18 DEBUG  TaskList: ## Finished create_swap_diskimage
11-20 22:18 DEBUG  TaskList: ## Running modify_bootloader...
11-20 22:18 DEBUG  TaskList: New task modify_bcd
11-20 22:18 DEBUG  TaskList: ### Running modify_bcd...
11-20 22:18 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 38080.84375 mb free ntfs)
11-20 22:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {a9a046a8-ab69-11e0-b3b5-bd688f2b94bb}
11-20 22:18 DEBUG  TaskList: ### Finished modify_bcd
11-20 22:18 DEBUG  TaskList: New task modify_bcd
11-20 22:18 DEBUG  TaskList: ### Running modify_bcd...
11-20 22:18 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 115790.21875 mb free ntfs)
11-20 22:18 DEBUG  WindowsBackend: BCD has already been modified
11-20 22:18 DEBUG  TaskList: ### Finished modify_bcd
11-20 22:18 DEBUG  TaskList: New task modify_bcd
11-20 22:18 DEBUG  TaskList: ### Running modify_bcd...
11-20 22:18 DEBUG  WindowsBackend: modify_bcd Drive(N: removable 0.0 mb free )
11-20 22:18 DEBUG  WindowsBackend: BCD has already been modified
11-20 22:18 DEBUG  TaskList: ### Finished modify_bcd
11-20 22:18 DEBUG  TaskList: ## Finished modify_bootloader
11-20 22:18 DEBUG  TaskList: ## Running diskimage_bootloader...
11-20 22:18 DEBUG  WindowsBackend: Copying C:\Users\Robert\AppData\Local\Temp\pylF3B3.tmp\winboot -> C:\ubuntu\winboot
11-20 22:18 ERROR  TaskList: [Errno 13] Permission denied: 'N:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'N:\\wubildr'
11-20 22:18 DEBUG  TaskList: # Cancelling tasklist
11-20 22:18 DEBUG  TaskList: # Finished tasklist
11-20 22:18 ERROR  root: [Errno 13] Permission denied: 'N:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'N:\\wubildr'
11-20 22:18 INFO   root: === wubi 11.10 rev245 ===
11-20 22:18 DEBUG  root: Logfile is c:\users\robert\appdata\local\temp\wubi-11.10-rev245.log
11-20 22:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Robert\\Downloads\\wubi.exe"']
11-20 22:18 DEBUG  CommonBackend: data_dir=C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\data
11-20 22:18 DEBUG  WindowsBackend: 7z=C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\bin\7z.exe
11-20 22:18 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-20 22:18 DEBUG  CommonBackend: Fetching basic info...
11-20 22:18 DEBUG  CommonBackend: original_exe=C:\Users\Robert\Downloads\wubi.exe
11-20 22:18 DEBUG  CommonBackend: platform=win32
11-20 22:18 DEBUG  CommonBackend: osname=nt
11-20 22:18 DEBUG  CommonBackend: language=en_US
11-20 22:18 DEBUG  CommonBackend: encoding=cp1252
11-20 22:18 DEBUG  WindowsBackend: arch=amd64
11-20 22:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\data\isolist.ini
11-20 22:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-20 22:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-20 22:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-20 22:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-20 22:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-20 22:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-20 22:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-20 22:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-20 22:18 DEBUG  WindowsBackend: Fetching host info...
11-20 22:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-20 22:18 DEBUG  WindowsBackend: windows version=vista
11-20 22:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-20 22:18 DEBUG  WindowsBackend: windows_sp=None
11-20 22:18 DEBUG  WindowsBackend: windows_build=7601
11-20 22:18 DEBUG  WindowsBackend: gmt=-5
11-20 22:18 DEBUG  WindowsBackend: country=US
11-20 22:18 DEBUG  WindowsBackend: timezone=America/New_York
11-20 22:18 DEBUG  WindowsBackend: windows_username=Robert
11-20 22:18 DEBUG  WindowsBackend: user_full_name=Robert
11-20 22:18 DEBUG  WindowsBackend: user_directory=C:\Users\Robert
11-20 22:18 DEBUG  WindowsBackend: windows_language_code=1033
11-20 22:18 DEBUG  WindowsBackend: windows_language=English
11-20 22:18 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
11-20 22:18 DEBUG  WindowsBackend: bootloader=vista
11-20 22:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 34549.8789063 mb free ntfs)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(C: hd 34549.8789063 mb free ntfs)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(F: hd 115790.089844 mb free ntfs)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free udf)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free )
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(N: removable 0.0 mb free )
11-20 22:18 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-20 22:18 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-20 22:18 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-20 22:18 DEBUG  WindowsBackend: keyboard_id=67699721
11-20 22:18 DEBUG  WindowsBackend: keyboard_layout=us
11-20 22:18 DEBUG  WindowsBackend: keyboard_variant=
11-20 22:18 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-20 22:18 DEBUG  CommonBackend: locale=en_US.UTF-8
11-20 22:18 DEBUG  WindowsBackend: total_memory_mb=4095.26953125
11-20 22:18 DEBUG  CommonBackend: Searching ISOs on USB devices
11-20 22:18 DEBUG  CommonBackend: Searching for local CDs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 INFO   root: Already installed, running the uninstaller...
11-20 22:18 INFO   root: Running the uninstaller...
11-20 22:18 INFO   CommonBackend: This is the uninstaller running
11-20 22:18 DEBUG  WindowsFrontend: __init__...
11-20 22:18 DEBUG  WindowsFrontend: on_init...
11-20 22:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\translations, languages=['en_US', 'en']
11-20 22:18 INFO   root: Received settings
11-20 22:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\translations, languages=['en_US', 'en']
11-20 22:18 DEBUG  TaskList: # Running tasklist...
11-20 22:18 DEBUG  TaskList: ## Running Remove bootloader entry...
11-20 22:18 DEBUG  WindowsBackend: Removing bcd entry {a9a046a8-ab69-11e0-b3b5-bd688f2b94bb}
11-20 22:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
11-20 22:18 DEBUG  WindowsBackend: undo_bootini C:
11-20 22:18 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 34549.8789063 mb free ntfs)
11-20 22:18 DEBUG  WindowsBackend: undo_bootini F:
11-20 22:18 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 115790.089844 mb free ntfs)
11-20 22:18 DEBUG  WindowsBackend: undo_bootini N:
11-20 22:18 DEBUG  WindowsBackend: undo_configsys Drive(N: removable 0.0 mb free )
11-20 22:18 DEBUG  TaskList: ## Finished Remove bootloader entry
11-20 22:18 DEBUG  TaskList: ## Running Remove target dir...
11-20 22:18 DEBUG  CommonBackend: Deleting C:\ubuntu
11-20 22:18 DEBUG  TaskList: ## Finished Remove target dir
11-20 22:18 DEBUG  TaskList: ## Running Remove registry key...
11-20 22:18 DEBUG  TaskList: ## Finished Remove registry key
11-20 22:18 DEBUG  TaskList: # Finished tasklist
11-20 22:18 INFO   root: Almost finished uninstalling
11-20 22:18 INFO   root: Finished uninstallation
11-20 22:18 DEBUG  CommonBackend: Fetching basic info...
11-20 22:18 DEBUG  CommonBackend: original_exe=C:\Users\Robert\Downloads\wubi.exe
11-20 22:18 DEBUG  CommonBackend: platform=win32
11-20 22:18 DEBUG  CommonBackend: osname=nt
11-20 22:18 DEBUG  WindowsBackend: arch=amd64
11-20 22:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\data\isolist.ini
11-20 22:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-20 22:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-20 22:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-20 22:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-20 22:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-20 22:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-20 22:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-20 22:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-20 22:18 DEBUG  WindowsBackend: Fetching host info...
11-20 22:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-20 22:18 DEBUG  WindowsBackend: windows version=vista
11-20 22:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-20 22:18 DEBUG  WindowsBackend: windows_sp=None
11-20 22:18 DEBUG  WindowsBackend: windows_build=7601
11-20 22:18 DEBUG  WindowsBackend: gmt=-5
11-20 22:18 DEBUG  WindowsBackend: country=US
11-20 22:18 DEBUG  WindowsBackend: timezone=America/New_York
11-20 22:18 DEBUG  WindowsBackend: windows_username=Robert
11-20 22:18 DEBUG  WindowsBackend: user_full_name=Robert
11-20 22:18 DEBUG  WindowsBackend: user_directory=C:\Users\Robert
11-20 22:18 DEBUG  WindowsBackend: windows_language_code=1033
11-20 22:18 DEBUG  WindowsBackend: windows_language=English
11-20 22:18 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
11-20 22:18 DEBUG  WindowsBackend: bootloader=vista
11-20 22:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 38031.2734375 mb free ntfs)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(C: hd 38031.2734375 mb free ntfs)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(F: hd 115790.21875 mb free ntfs)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free udf)
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free )
11-20 22:18 DEBUG  WindowsBackend: drive=Drive(N: removable 0.0 mb free )
11-20 22:18 DEBUG  WindowsBackend: uninstaller_path=None
11-20 22:18 DEBUG  WindowsBackend: previous_target_dir=None
11-20 22:18 DEBUG  WindowsBackend: previous_distro_name=None
11-20 22:18 DEBUG  WindowsBackend: keyboard_id=67699721
11-20 22:18 DEBUG  WindowsBackend: keyboard_layout=us
11-20 22:18 DEBUG  WindowsBackend: keyboard_variant=
11-20 22:18 DEBUG  WindowsBackend: total_memory_mb=4095.26953125
11-20 22:18 DEBUG  CommonBackend: Searching ISOs on USB devices
11-20 22:18 DEBUG  CommonBackend: Searching for local CDs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 INFO   root: Running the installer...
11-20 22:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\translations, languages=['en_US', 'en']
11-20 22:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\translations, languages=['en_US', 'en']
11-20 22:18 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=25000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=robert
11-20 22:18 INFO   root: Received settings
11-20 22:18 DEBUG  CommonBackend: Searching for local CD
11-20 22:18 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:18 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 22:18 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:18 DEBUG  CommonBackend: Searching for local ISO
11-20 22:18 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Robert\Downloads\rld-bme2.iso
11-20 22:18 DEBUG  Distro:     wrong size: 5953308672 > 900000000
11-20 22:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\translations, languages=['en_US', 'en']
11-20 22:18 DEBUG  TaskList: # Running tasklist...
11-20 22:18 DEBUG  TaskList: ## Running select_target_dir...
11-20 22:18 INFO   WindowsBackend: Installing into C:\ubuntu
11-20 22:18 DEBUG  TaskList: ## Finished select_target_dir
11-20 22:18 DEBUG  TaskList: ## Running create_dir_structure...
11-20 22:18 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-20 22:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-20 22:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-20 22:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-20 22:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-20 22:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-20 22:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-20 22:18 DEBUG  TaskList: ## Finished create_dir_structure
11-20 22:18 DEBUG  TaskList: ## Running create_uninstaller...
11-20 22:18 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Robert\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-20 22:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-20 22:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-20 22:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-20 22:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-20 22:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-20 22:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-20 22:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
11-20 22:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
11-20 22:18 DEBUG  TaskList: ## Finished create_uninstaller
11-20 22:18 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-20 22:18 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-20 22:18 DEBUG  TaskList: ## Running get_diskimage...
11-20 22:18 DEBUG  TaskList: New task download
11-20 22:18 DEBUG  TaskList: ### Running download...
11-20 22:18 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
11-20 22:18 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
11-20 22:26 DEBUG  TaskList: ### Finished download
11-20 22:26 DEBUG  downloader: download finished (read 507143012 bytes)
11-20 22:26 DEBUG  TaskList: ## Finished get_diskimage
11-20 22:26 DEBUG  TaskList: ## Running extract_diskimage...
11-20 22:28 DEBUG  TaskList: ## Finished extract_diskimage
11-20 22:28 DEBUG  TaskList: ## Running choose_disk_sizes...
11-20 22:28 DEBUG  WindowsBackend: total size=25000
  root=24744
  swap=256
  home=0
  usr=0
11-20 22:28 DEBUG  TaskList: ## Finished choose_disk_sizes
11-20 22:28 DEBUG  TaskList: ## Running expand_diskimage...
11-20 22:42 DEBUG  TaskList: ## Finished expand_diskimage
11-20 22:42 DEBUG  TaskList: ## Running create_swap_diskimage...
11-20 22:42 DEBUG  TaskList: ## Finished create_swap_diskimage
11-20 22:42 DEBUG  TaskList: ## Running modify_bootloader...
11-20 22:42 DEBUG  TaskList: New task modify_bcd
11-20 22:42 DEBUG  TaskList: ### Running modify_bcd...
11-20 22:42 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 38031.2734375 mb free ntfs)
11-20 22:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {a9a046a9-ab69-11e0-b3b5-bd688f2b94bb}
11-20 22:42 DEBUG  TaskList: ### Finished modify_bcd
11-20 22:42 DEBUG  TaskList: New task modify_bcd
11-20 22:42 DEBUG  TaskList: ### Running modify_bcd...
11-20 22:42 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 115790.21875 mb free ntfs)
11-20 22:42 DEBUG  WindowsBackend: BCD has already been modified
11-20 22:42 DEBUG  TaskList: ### Finished modify_bcd
11-20 22:42 DEBUG  TaskList: New task modify_bcd
11-20 22:42 DEBUG  TaskList: ### Running modify_bcd...
11-20 22:42 DEBUG  WindowsBackend: modify_bcd Drive(N: removable 0.0 mb free )
11-20 22:42 DEBUG  WindowsBackend: BCD has already been modified
11-20 22:42 DEBUG  TaskList: ### Finished modify_bcd
11-20 22:42 DEBUG  TaskList: ## Finished modify_bootloader
11-20 22:42 DEBUG  TaskList: ## Running diskimage_bootloader...
11-20 22:42 DEBUG  WindowsBackend: Copying C:\Users\Robert\AppData\Local\Temp\pylDC0F.tmp\winboot -> C:\ubuntu\winboot
11-20 22:42 ERROR  TaskList: [Errno 2] No such file or directory: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'F:\\wubildr'
11-20 22:42 DEBUG  TaskList: # Cancelling tasklist
11-20 22:42 DEBUG  TaskList: # Finished tasklist
11-20 22:42 ERROR  root: [Errno 2] No such file or directory: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'F:\\wubildr'
11-20 22:51 INFO   root: === wubi 11.10 rev245 ===
11-20 22:51 DEBUG  root: Logfile is c:\users\robert\appdata\local\temp\wubi-11.10-rev245.log
11-20 22:51 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Robert\\Downloads\\wubi.exe"']
11-20 22:51 DEBUG  CommonBackend: data_dir=C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\data
11-20 22:51 DEBUG  WindowsBackend: 7z=C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\bin\7z.exe
11-20 22:51 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-20 22:51 DEBUG  CommonBackend: Fetching basic info...
11-20 22:51 DEBUG  CommonBackend: original_exe=C:\Users\Robert\Downloads\wubi.exe
11-20 22:51 DEBUG  CommonBackend: platform=win32
11-20 22:51 DEBUG  CommonBackend: osname=nt
11-20 22:51 DEBUG  CommonBackend: language=en_US
11-20 22:51 DEBUG  CommonBackend: encoding=cp1252
11-20 22:51 DEBUG  WindowsBackend: arch=amd64
11-20 22:51 DEBUG  CommonBackend: Parsing isolist=C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\data\isolist.ini
11-20 22:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-20 22:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-20 22:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-20 22:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-20 22:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-20 22:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-20 22:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-20 22:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-20 22:51 DEBUG  WindowsBackend: Fetching host info...
11-20 22:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-20 22:51 DEBUG  WindowsBackend: windows version=vista
11-20 22:51 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-20 22:51 DEBUG  WindowsBackend: windows_sp=None
11-20 22:51 DEBUG  WindowsBackend: windows_build=7601
11-20 22:51 DEBUG  WindowsBackend: gmt=-5
11-20 22:51 DEBUG  WindowsBackend: country=US
11-20 22:51 DEBUG  WindowsBackend: timezone=America/New_York
11-20 22:51 DEBUG  WindowsBackend: windows_username=Robert
11-20 22:51 DEBUG  WindowsBackend: user_full_name=Robert
11-20 22:51 DEBUG  WindowsBackend: user_directory=C:\Users\Robert
11-20 22:51 DEBUG  WindowsBackend: windows_language_code=1033
11-20 22:51 DEBUG  WindowsBackend: windows_language=English
11-20 22:51 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
11-20 22:51 DEBUG  WindowsBackend: bootloader=vista
11-20 22:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 34532.3671875 mb free ntfs)
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(C: hd 34532.3671875 mb free ntfs)
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free udf)
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free )
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(N: removable 0.0 mb free )
11-20 22:51 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-20 22:51 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-20 22:51 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-20 22:51 DEBUG  WindowsBackend: keyboard_id=67699721
11-20 22:51 DEBUG  WindowsBackend: keyboard_layout=us
11-20 22:51 DEBUG  WindowsBackend: keyboard_variant=
11-20 22:51 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-20 22:51 DEBUG  CommonBackend: locale=en_US.UTF-8
11-20 22:51 DEBUG  WindowsBackend: total_memory_mb=4095.26953125
11-20 22:51 DEBUG  CommonBackend: Searching ISOs on USB devices
11-20 22:51 DEBUG  CommonBackend: Searching for local CDs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 INFO   root: Already installed, running the uninstaller...
11-20 22:51 INFO   root: Running the uninstaller...
11-20 22:51 INFO   CommonBackend: This is the uninstaller running
11-20 22:51 DEBUG  WindowsFrontend: __init__...
11-20 22:51 DEBUG  WindowsFrontend: on_init...
11-20 22:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\translations, languages=['en_US', 'en']
11-20 22:51 INFO   root: Received settings
11-20 22:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\translations, languages=['en_US', 'en']
11-20 22:51 DEBUG  TaskList: # Running tasklist...
11-20 22:51 DEBUG  TaskList: ## Running Remove bootloader entry...
11-20 22:51 DEBUG  WindowsBackend: Removing bcd entry {a9a046a9-ab69-11e0-b3b5-bd688f2b94bb}
11-20 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
11-20 22:51 DEBUG  WindowsBackend: undo_bootini C:
11-20 22:51 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 34532.3671875 mb free ntfs)
11-20 22:51 DEBUG  WindowsBackend: undo_bootini N:
11-20 22:51 DEBUG  WindowsBackend: undo_configsys Drive(N: removable 0.0 mb free )
11-20 22:51 DEBUG  TaskList: ## Finished Remove bootloader entry
11-20 22:51 DEBUG  TaskList: ## Running Remove target dir...
11-20 22:51 DEBUG  CommonBackend: Deleting C:\ubuntu
11-20 22:51 DEBUG  TaskList: ## Finished Remove target dir
11-20 22:51 DEBUG  TaskList: ## Running Remove registry key...
11-20 22:51 DEBUG  TaskList: ## Finished Remove registry key
11-20 22:51 DEBUG  TaskList: # Finished tasklist
11-20 22:51 INFO   root: Almost finished uninstalling
11-20 22:51 INFO   root: Finished uninstallation
11-20 22:51 DEBUG  CommonBackend: Fetching basic info...
11-20 22:51 DEBUG  CommonBackend: original_exe=C:\Users\Robert\Downloads\wubi.exe
11-20 22:51 DEBUG  CommonBackend: platform=win32
11-20 22:51 DEBUG  CommonBackend: osname=nt
11-20 22:51 DEBUG  WindowsBackend: arch=amd64
11-20 22:51 DEBUG  CommonBackend: Parsing isolist=C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\data\isolist.ini
11-20 22:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-20 22:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-20 22:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-20 22:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-20 22:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-20 22:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-20 22:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-20 22:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-20 22:51 DEBUG  WindowsBackend: Fetching host info...
11-20 22:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-20 22:51 DEBUG  WindowsBackend: windows version=vista
11-20 22:51 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-20 22:51 DEBUG  WindowsBackend: windows_sp=None
11-20 22:51 DEBUG  WindowsBackend: windows_build=7601
11-20 22:51 DEBUG  WindowsBackend: gmt=-5
11-20 22:51 DEBUG  WindowsBackend: country=US
11-20 22:51 DEBUG  WindowsBackend: timezone=America/New_York
11-20 22:51 DEBUG  WindowsBackend: windows_username=Robert
11-20 22:51 DEBUG  WindowsBackend: user_full_name=Robert
11-20 22:51 DEBUG  WindowsBackend: user_directory=C:\Users\Robert
11-20 22:51 DEBUG  WindowsBackend: windows_language_code=1033
11-20 22:51 DEBUG  WindowsBackend: windows_language=English
11-20 22:51 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
11-20 22:51 DEBUG  WindowsBackend: bootloader=vista
11-20 22:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 38012.8164063 mb free ntfs)
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(C: hd 38012.8164063 mb free ntfs)
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free udf)
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(L: cd 0.0 mb free )
11-20 22:51 DEBUG  WindowsBackend: drive=Drive(N: removable 0.0 mb free )
11-20 22:51 DEBUG  WindowsBackend: uninstaller_path=None
11-20 22:51 DEBUG  WindowsBackend: previous_target_dir=None
11-20 22:51 DEBUG  WindowsBackend: previous_distro_name=None
11-20 22:51 DEBUG  WindowsBackend: keyboard_id=67699721
11-20 22:51 DEBUG  WindowsBackend: keyboard_layout=us
11-20 22:51 DEBUG  WindowsBackend: keyboard_variant=
11-20 22:51 DEBUG  WindowsBackend: total_memory_mb=4095.26953125
11-20 22:51 DEBUG  CommonBackend: Searching ISOs on USB devices
11-20 22:51 DEBUG  CommonBackend: Searching for local CDs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 INFO   root: Running the installer...
11-20 22:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\translations, languages=['en_US', 'en']
11-20 22:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\translations, languages=['en_US', 'en']
11-20 22:51 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=25000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=robert
11-20 22:51 INFO   root: Received settings
11-20 22:51 DEBUG  CommonBackend: Searching for local CD
11-20 22:51 DEBUG  Distro:   checking whether C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
11-20 22:51 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
11-20 22:51 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
11-20 22:51 DEBUG  CommonBackend: Searching for local ISO
11-20 22:51 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Robert\Downloads\rld-bme2.iso
11-20 22:51 DEBUG  Distro:     wrong size: 5953308672 > 900000000
11-20 22:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\translations, languages=['en_US', 'en']
11-20 22:51 DEBUG  TaskList: # Running tasklist...
11-20 22:51 DEBUG  TaskList: ## Running select_target_dir...
11-20 22:51 INFO   WindowsBackend: Installing into C:\ubuntu
11-20 22:51 DEBUG  TaskList: ## Finished select_target_dir
11-20 22:51 DEBUG  TaskList: ## Running create_dir_structure...
11-20 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-20 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-20 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-20 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-20 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-20 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-20 22:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-20 22:51 DEBUG  TaskList: ## Finished create_dir_structure
11-20 22:51 DEBUG  TaskList: ## Running create_uninstaller...
11-20 22:51 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Robert\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-20 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-20 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-20 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-20 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-20 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-20 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-20 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
11-20 22:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
11-20 22:51 DEBUG  TaskList: ## Finished create_uninstaller
11-20 22:51 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-20 22:51 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-20 22:51 DEBUG  TaskList: ## Running get_diskimage...
11-20 22:51 DEBUG  TaskList: New task download
11-20 22:51 DEBUG  TaskList: ### Running download...
11-20 22:51 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
11-20 22:51 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
11-20 22:59 DEBUG  TaskList: ### Finished download
11-20 22:59 DEBUG  downloader: download finished (read 507143012 bytes)
11-20 22:59 DEBUG  TaskList: ## Finished get_diskimage
11-20 22:59 DEBUG  TaskList: ## Running extract_diskimage...
11-20 23:01 DEBUG  TaskList: ## Finished extract_diskimage
11-20 23:01 DEBUG  TaskList: ## Running choose_disk_sizes...
11-20 23:01 DEBUG  WindowsBackend: total size=25000
  root=24744
  swap=256
  home=0
  usr=0
11-20 23:01 DEBUG  TaskList: ## Finished choose_disk_sizes
11-20 23:01 DEBUG  TaskList: ## Running expand_diskimage...
11-20 23:14 DEBUG  TaskList: ## Finished expand_diskimage
11-20 23:14 DEBUG  TaskList: ## Running create_swap_diskimage...
11-20 23:14 DEBUG  TaskList: ## Finished create_swap_diskimage
11-20 23:14 DEBUG  TaskList: ## Running modify_bootloader...
11-20 23:14 DEBUG  TaskList: New task modify_bcd
11-20 23:14 DEBUG  TaskList: ### Running modify_bcd...
11-20 23:14 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 38012.8164063 mb free ntfs)
11-20 23:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {a9a046aa-ab69-11e0-b3b5-bd688f2b94bb}
11-20 23:14 DEBUG  TaskList: ### Finished modify_bcd
11-20 23:14 DEBUG  TaskList: New task modify_bcd
11-20 23:14 DEBUG  TaskList: ### Running modify_bcd...
11-20 23:14 DEBUG  WindowsBackend: modify_bcd Drive(N: removable 0.0 mb free )
11-20 23:14 DEBUG  WindowsBackend: BCD has already been modified
11-20 23:14 DEBUG  TaskList: ### Finished modify_bcd
11-20 23:14 DEBUG  TaskList: ## Finished modify_bootloader
11-20 23:14 DEBUG  TaskList: ## Running diskimage_bootloader...
11-20 23:14 DEBUG  WindowsBackend: Copying C:\Users\Robert\AppData\Local\Temp\pylD2CC.tmp\winboot -> C:\ubuntu\winboot
11-20 23:14 ERROR  TaskList: [Errno 13] Permission denied: 'N:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'N:\\wubildr'
11-20 23:14 DEBUG  TaskList: # Cancelling tasklist
11-20 23:14 DEBUG  TaskList: # Finished tasklist
11-20 23:14 ERROR  root: [Errno 13] Permission denied: 'N:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'N:\\wubildr'

```

---

### Post by iTails on 2011-11-21
bump

---

### Post by bcbc on 2011-11-21
The install is successful - just a weird error message: bug [lpbug]862003[/lpbug]

---

