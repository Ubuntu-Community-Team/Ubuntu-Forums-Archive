---
title: "Ubuntu 12.04 Wubi Install Error! Please help."
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Futureking on 2012-04-27
Hi,

I have Windows 7 Pro 64bit on my Workstation. When I try to install Ubuntu 12.04 from Wubi I get Error msg: 'NodeType' object has no attribute get_info .

Error log has the following contents.

> 04-27 19:01 INFO   root: === wubi 12.04 rev266 ===
04-27 19:01 DEBUG  root: Logfile is c:\users\ankurg~1\appdata\local\temp\wubi-12.04-rev266.log
04-27 19:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Ankur Gupta\\Desktop\\wubi.exe"']
04-27 19:01 DEBUG  CommonBackend: data_dir=C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\data
04-27 19:01 DEBUG  WindowsBackend: 7z=C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\bin\7z.exe
04-27 19:01 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-27 19:01 DEBUG  CommonBackend: Fetching basic info...
04-27 19:01 DEBUG  CommonBackend: original_exe=C:\Users\Ankur Gupta\Desktop\wubi.exe
04-27 19:01 DEBUG  CommonBackend: platform=win32
04-27 19:01 DEBUG  CommonBackend: osname=nt
04-27 19:01 DEBUG  CommonBackend: language=hi_IN
04-27 19:01 DEBUG  CommonBackend: encoding=cp1252
04-27 19:01 DEBUG  WindowsBackend: arch=amd64
04-27 19:01 DEBUG  CommonBackend: Parsing isolist=C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\data\isolist.ini
04-27 19:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-27 19:01 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-27 19:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-27 19:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-27 19:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-27 19:01 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-27 19:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-27 19:01 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-27 19:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-27 19:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-27 19:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-27 19:01 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-27 19:01 DEBUG  WindowsBackend: Fetching host info...
04-27 19:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-27 19:01 DEBUG  WindowsBackend: windows version=vista
04-27 19:01 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-27 19:01 DEBUG  WindowsBackend: windows_sp=None
04-27 19:01 DEBUG  WindowsBackend: windows_build=7601
04-27 19:01 DEBUG  WindowsBackend: gmt=5
04-27 19:01 DEBUG  WindowsBackend: country=IN
04-27 19:01 DEBUG  WindowsBackend: timezone=Asia/Calcutta
04-27 19:01 DEBUG  WindowsBackend: windows_username=Ankur Gupta
04-27 19:01 DEBUG  WindowsBackend: user_full_name=Ankur Gupta
04-27 19:01 DEBUG  WindowsBackend: user_directory=C:\Users\Ankur Gupta
04-27 19:01 DEBUG  WindowsBackend: windows_language_code=None
04-27 19:01 DEBUG  WindowsBackend: windows_language=English
04-27 19:01 DEBUG  WindowsBackend: processor_name=Intel(R) Xeon(R) CPU           W3520  @ 2.67GHz
04-27 19:01 DEBUG  WindowsBackend: bootloader=vista
04-27 19:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11924.9101563 mb free ntfs)
04-27 19:01 DEBUG  WindowsBackend: drive=Drive(C: hd 11924.9101563 mb free ntfs)
04-27 19:01 DEBUG  WindowsBackend: drive=Drive(D: hd 15472.7929688 mb free ntfs)
04-27 19:01 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-27 19:01 DEBUG  WindowsBackend: drive=Drive(F: hd 28660.921875 mb free ntfs)
04-27 19:01 DEBUG  WindowsBackend: drive=Drive(G: hd 25214.8710938 mb free ntfs)
04-27 19:01 DEBUG  WindowsBackend: drive=Drive(H: hd 9087.0625 mb free ntfs)
04-27 19:01 DEBUG  WindowsBackend: drive=Drive(I: hd 31661.59375 mb free ntfs)
04-27 19:01 DEBUG  WindowsBackend: drive=Drive(J: hd 26558.578125 mb free ntfs)
04-27 19:01 DEBUG  WindowsBackend: drive=Drive(K: hd 19330.0039063 mb free ntfs)
04-27 19:01 DEBUG  WindowsBackend: drive=Drive(L: hd 26716.640625 mb free ntfs)
04-27 19:01 DEBUG  WindowsBackend: drive=Drive(P: cd 0.0 mb free cdfs)
04-27 19:01 DEBUG  WindowsBackend: uninstaller_path=None
04-27 19:01 DEBUG  WindowsBackend: previous_target_dir=None
04-27 19:01 DEBUG  WindowsBackend: previous_distro_name=None
04-27 19:01 DEBUG  WindowsBackend: keyboard_id=67699721
04-27 19:01 DEBUG  WindowsBackend: keyboard_layout=us
04-27 19:01 DEBUG  WindowsBackend: keyboard_variant=
04-27 19:01 DEBUG  CommonBackend: python locale=('hi_IN', 'cp1252')
04-27 19:01 DEBUG  CommonBackend: locale=hi_IN
04-27 19:01 DEBUG  WindowsBackend: total_memory_mb=4079.22265625
04-27 19:01 DEBUG  CommonBackend: Searching ISOs on USB devices
04-27 19:01 DEBUG  CommonBackend: Searching for local CDs
04-27 19:01 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
04-27 19:01 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether L:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether L:\ is a valid Edubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether L:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether L:\ is a valid Lubuntu CD
04-27 19:01 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:01 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
04-27 19:01 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
04-27 19:01 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
04-27 19:01 INFO   Distro: Found a valid CD for Ubuntu: P:\
04-27 19:01 INFO   root: Running the installer...
04-27 19:01 DEBUG  WindowsFrontend: __init__...
04-27 19:01 DEBUG  WindowsFrontend: on_init...
04-27 19:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\translations, languages=['hi_IN', 'hi']
04-27 19:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\translations, languages=['hi_IN', 'hi']
04-27 19:02 DEBUG  WinuiInstallationPage: target_drive=K:, installation_size=8000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ankurgupta
04-27 19:02 INFO   root: Received settings
04-27 19:02 DEBUG  CommonBackend: Searching for local CD
04-27 19:02 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp is a valid Ubuntu CD
04-27 19:02 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\casper\filesystem.squashfs
04-27 19:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-27 19:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-27 19:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-27 19:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-27 19:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-27 19:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:02 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-27 19:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:02 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-27 19:02 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:02 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-27 19:02 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:02 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
04-27 19:02 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:02 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
04-27 19:02 INFO   Distro: Found a valid CD for Ubuntu: P:\
04-27 19:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\translations, languages=['en_US', 'en']
04-27 19:02 DEBUG  TaskList: # Running tasklist...
04-27 19:02 DEBUG  TaskList: ## Running select_target_dir...
04-27 19:02 INFO   WindowsBackend: Installing into K:\ubuntu
04-27 19:02 DEBUG  TaskList: ## Finished select_target_dir
04-27 19:02 DEBUG  TaskList: ## Running create_dir_structure...
04-27 19:02 DEBUG  CommonBackend: Creating dir K:\ubuntu
04-27 19:02 DEBUG  CommonBackend: Creating dir K:\ubuntu\disks
04-27 19:02 DEBUG  CommonBackend: Creating dir K:\ubuntu\install
04-27 19:02 DEBUG  CommonBackend: Creating dir K:\ubuntu\install\boot
04-27 19:02 DEBUG  CommonBackend: Creating dir K:\ubuntu\disks\boot
04-27 19:02 DEBUG  CommonBackend: Creating dir K:\ubuntu\disks\boot\grub
04-27 19:02 DEBUG  CommonBackend: Creating dir K:\ubuntu\install\boot\grub
04-27 19:02 DEBUG  TaskList: ## Finished create_dir_structure
04-27 19:02 DEBUG  TaskList: ## Running uncompress_target_dir...
04-27 19:02 DEBUG  TaskList: ## Finished uncompress_target_dir
04-27 19:02 DEBUG  TaskList: ## Running create_uninstaller...
04-27 19:02 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Ankur Gupta\Desktop\wubi.exe -> K:\ubuntu\uninstall-wubi.exe
04-27 19:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString K:\ubuntu\uninstall-wubi.exe
04-27 19:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir K:\ubuntu
04-27 19:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-27 19:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon K:\ubuntu\Ubuntu.ico
04-27 19:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev266
04-27 19:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-27 19:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-27 19:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-27 19:02 DEBUG  TaskList: ## Finished create_uninstaller
04-27 19:02 DEBUG  TaskList: ## Running copy_installation_files...
04-27 19:02 DEBUG  WindowsBackend: Copying C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\data\custom-installation -> K:\ubuntu\install\custom-installation
04-27 19:02 DEBUG  WindowsBackend: Copying C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\winboot -> K:\ubuntu\winboot
04-27 19:02 DEBUG  WindowsBackend: Copying C:\Users\ANKURG~1\AppData\Local\Temp\pyl14E0.tmp\data\images\Ubuntu.ico -> K:\ubuntu\Ubuntu.ico
04-27 19:02 DEBUG  TaskList: ## Finished copy_installation_files
04-27 19:02 DEBUG  TaskList: ## Running get_iso...
04-27 19:02 DEBUG  TaskList: New task copy_file
04-27 19:02 DEBUG  TaskList: ### Running copy_file...
04-27 19:02 DEBUG  TaskList: ### Finished copy_file
04-27 19:02 DEBUG  TaskList: New task check_iso
04-27 19:02 DEBUG  TaskList: ### Running check_iso...
04-27 19:02 DEBUG  CommonBackend: Checking K:\ubuntu\install\installation.iso
04-27 19:02 DEBUG  Distro:   checking Ubuntu ISO K:\ubuntu\install\installation.iso
04-27 19:02 DEBUG  WindowsBackend:   extracting .disk\info from K:\ubuntu\install\installation.iso
04-27 19:02 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
04-27 19:02 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
04-27 19:02 INFO   Distro: Found a valid iso for Ubuntu: K:\ubuntu\install\installation.iso
04-27 19:02 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
04-27 19:02 DEBUG  TaskList: New task get_metalink
04-27 19:02 DEBUG  TaskList: #### Running get_metalink...
04-27 19:02 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.metalink](http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.metalink) > K:\ubuntu\install
04-27 19:02 DEBUG  downloader: Download start filename=K:\ubuntu\install\ubuntu-12.04-desktop-i386.metalink, url=http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.metalink, basename=ubuntu-12.04-desktop-i386.metalink, length=30559, text=None
04-27 19:03 DEBUG  downloader: download finished (read 30559 bytes)
04-27 19:03 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04/MD5SUMS-metalink](http://releases.ubuntu.com/12.04/MD5SUMS-metalink) > K:\ubuntu\install
04-27 19:03 DEBUG  downloader: Download start filename=K:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/12.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=419, text=None
04-27 19:03 DEBUG  downloader: download finished (read 419 bytes)
04-27 19:03 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/12.04/MD5SUMS-metalink.gpg) > K:\ubuntu\install
04-27 19:03 DEBUG  downloader: Download start filename=K:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/12.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-27 19:03 DEBUG  downloader: download finished (read 198 bytes)
04-27 19:03 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-27 19:03 INFO   saplog: Checking block bindings..
04-27 19:03 INFO   saplog: Key verified successfully.
04-27 19:03 DEBUG  CommonBackend: metalink md5sums:
1e2a0b0f07bc43ab5924767a9cc03e82  ubuntu-12.04-alternate-amd64.metalink
4413660abc989dbbfe6e4abedc9a3ec1  ubuntu-12.04-alternate-i386.metalink
c29be6d58c1581d9cd679aca25db77d1  ubuntu-12.04-desktop-amd64.metalink
c7a6b99206703cfe37f1da5af1d28e3a  ubuntu-12.04-desktop-i386.metalink
4e44ca9bc7ee8ab54ff9565a5437bdc2  ubuntu-12.04-server-amd64.metalink
c9cfc1dd8c65099d929189eedc157f3c  ubuntu-12.04-server-i386.metalink

04-27 19:03 DEBUG  TaskList: #### Finished get_metalink
04-27 19:03 DEBUG  TaskList: New task get_file_md5
04-27 19:03 DEBUG  TaskList: #### Running get_file_md5...
04-27 19:03 DEBUG  TaskList: #### Finished get_file_md5
04-27 19:03 ERROR  CommonBackend: Invalid md5 for ISO K:\ubuntu\install\installation.iso (d791352694374f1c478779f7f4447a3f != 866bdfa347b5425b18fdafe719a956df)
None
04-27 19:03 DEBUG  TaskList: ### Finished check_iso
04-27 19:03 ERROR  TaskList: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
04-27 19:03 DEBUG  TaskList: # Cancelling tasklist
04-27 19:03 DEBUG  TaskList: # Finished tasklist
04-27 19:03 ERROR  root: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
04-27 19:05 INFO   root: === wubi 12.04 rev266 ===
04-27 19:05 DEBUG  root: Logfile is c:\users\ankurg~1\appdata\local\temp\wubi-12.04-rev266.log
04-27 19:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Ankur Gupta\\Desktop\\wubi.exe"']
04-27 19:05 DEBUG  CommonBackend: data_dir=C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\data
04-27 19:05 DEBUG  WindowsBackend: 7z=C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\bin\7z.exe
04-27 19:05 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-27 19:05 DEBUG  CommonBackend: Fetching basic info...
04-27 19:05 DEBUG  CommonBackend: original_exe=C:\Users\Ankur Gupta\Desktop\wubi.exe
04-27 19:05 DEBUG  CommonBackend: platform=win32
04-27 19:05 DEBUG  CommonBackend: osname=nt
04-27 19:05 DEBUG  CommonBackend: language=hi_IN
04-27 19:05 DEBUG  CommonBackend: encoding=cp1252
04-27 19:05 DEBUG  WindowsBackend: arch=amd64
04-27 19:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\data\isolist.ini
04-27 19:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-27 19:05 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-27 19:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-27 19:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-27 19:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-27 19:05 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-27 19:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-27 19:05 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-27 19:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-27 19:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-27 19:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-27 19:05 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-27 19:05 DEBUG  WindowsBackend: Fetching host info...
04-27 19:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-27 19:05 DEBUG  WindowsBackend: windows version=vista
04-27 19:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-27 19:05 DEBUG  WindowsBackend: windows_sp=None
04-27 19:05 DEBUG  WindowsBackend: windows_build=7601
04-27 19:05 DEBUG  WindowsBackend: gmt=5
04-27 19:05 DEBUG  WindowsBackend: country=IN
04-27 19:05 DEBUG  WindowsBackend: timezone=Asia/Calcutta
04-27 19:05 DEBUG  WindowsBackend: windows_username=Ankur Gupta
04-27 19:05 DEBUG  WindowsBackend: user_full_name=Ankur Gupta
04-27 19:05 DEBUG  WindowsBackend: user_directory=C:\Users\Ankur Gupta
04-27 19:05 DEBUG  WindowsBackend: windows_language_code=None
04-27 19:05 DEBUG  WindowsBackend: windows_language=English
04-27 19:05 DEBUG  WindowsBackend: processor_name=Intel(R) Xeon(R) CPU           W3520  @ 2.67GHz
04-27 19:05 DEBUG  WindowsBackend: bootloader=vista
04-27 19:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11925.0429688 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(C: hd 11925.0429688 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(D: hd 15472.7929688 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(F: hd 28660.921875 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(G: hd 25215.375 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(H: hd 9087.0625 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(I: hd 31661.59375 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(J: hd 26558.578125 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(K: hd 18626.0742188 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(L: hd 26716.640625 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(P: cd 0.0 mb free cdfs)
04-27 19:05 DEBUG  WindowsBackend: uninstaller_path=K:\ubuntu\uninstall-wubi.exe
04-27 19:05 DEBUG  WindowsBackend: previous_target_dir=K:\ubuntu
04-27 19:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-27 19:05 DEBUG  WindowsBackend: keyboard_id=67699721
04-27 19:05 DEBUG  WindowsBackend: keyboard_layout=us
04-27 19:05 DEBUG  WindowsBackend: keyboard_variant=
04-27 19:05 DEBUG  CommonBackend: python locale=('hi_IN', 'cp1252')
04-27 19:05 DEBUG  CommonBackend: locale=hi_IN
04-27 19:05 DEBUG  WindowsBackend: total_memory_mb=4079.22265625
04-27 19:05 DEBUG  CommonBackend: Searching ISOs on USB devices
04-27 19:05 DEBUG  CommonBackend: Searching for local CDs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
04-27 19:05 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
04-27 19:05 INFO   Distro: Found a valid CD for Ubuntu: P:\
04-27 19:05 INFO   root: Already installed, running the uninstaller...
04-27 19:05 INFO   root: Running the uninstaller...
04-27 19:05 INFO   CommonBackend: This is the uninstaller running
04-27 19:05 DEBUG  WindowsFrontend: __init__...
04-27 19:05 DEBUG  WindowsFrontend: on_init...
04-27 19:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\translations, languages=['hi_IN', 'hi']
04-27 19:05 INFO   root: Received settings
04-27 19:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\translations, languages=['hi_IN', 'hi']
04-27 19:05 DEBUG  TaskList: # Running tasklist...
04-27 19:05 DEBUG  TaskList: ## Running Remove bootloader entry...
04-27 19:05 DEBUG  WindowsBackend: Could not find bcd id
04-27 19:05 DEBUG  WindowsBackend: undo_bootini C:
04-27 19:05 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 11925.0429688 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: undo_bootini D:
04-27 19:05 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 15472.7929688 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: undo_bootini F:
04-27 19:05 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 28660.921875 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: undo_bootini G:
04-27 19:05 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 25215.375 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: undo_bootini H:
04-27 19:05 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 9087.0625 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: undo_bootini I:
04-27 19:05 DEBUG  WindowsBackend: undo_configsys Drive(I: hd 31661.59375 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: undo_bootini J:
04-27 19:05 DEBUG  WindowsBackend: undo_configsys Drive(J: hd 26558.578125 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: undo_bootini K:
04-27 19:05 DEBUG  WindowsBackend: undo_configsys Drive(K: hd 18626.0742188 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: undo_bootini L:
04-27 19:05 DEBUG  WindowsBackend: undo_configsys Drive(L: hd 26716.640625 mb free ntfs)
04-27 19:05 DEBUG  TaskList: ## Finished Remove bootloader entry
04-27 19:05 DEBUG  TaskList: ## Running Remove target dir...
04-27 19:05 DEBUG  CommonBackend: Deleting K:\ubuntu
04-27 19:05 DEBUG  TaskList: ## Finished Remove target dir
04-27 19:05 DEBUG  TaskList: ## Running Remove registry key...
04-27 19:05 DEBUG  TaskList: ## Finished Remove registry key
04-27 19:05 DEBUG  TaskList: # Finished tasklist
04-27 19:05 INFO   root: Almost finished uninstalling
04-27 19:05 INFO   root: Finished uninstallation
04-27 19:05 DEBUG  CommonBackend: Fetching basic info...
04-27 19:05 DEBUG  CommonBackend: original_exe=C:\Users\Ankur Gupta\Desktop\wubi.exe
04-27 19:05 DEBUG  CommonBackend: platform=win32
04-27 19:05 DEBUG  CommonBackend: osname=nt
04-27 19:05 DEBUG  WindowsBackend: arch=amd64
04-27 19:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\data\isolist.ini
04-27 19:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-27 19:05 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-27 19:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-27 19:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-27 19:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-27 19:05 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-27 19:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-27 19:05 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-27 19:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-27 19:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-27 19:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-27 19:05 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-27 19:05 DEBUG  WindowsBackend: Fetching host info...
04-27 19:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-27 19:05 DEBUG  WindowsBackend: windows version=vista
04-27 19:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-27 19:05 DEBUG  WindowsBackend: windows_sp=None
04-27 19:05 DEBUG  WindowsBackend: windows_build=7601
04-27 19:05 DEBUG  WindowsBackend: gmt=5
04-27 19:05 DEBUG  WindowsBackend: country=IN
04-27 19:05 DEBUG  WindowsBackend: timezone=Asia/Calcutta
04-27 19:05 DEBUG  WindowsBackend: windows_username=Ankur Gupta
04-27 19:05 DEBUG  WindowsBackend: user_full_name=Ankur Gupta
04-27 19:05 DEBUG  WindowsBackend: user_directory=C:\Users\Ankur Gupta
04-27 19:05 DEBUG  WindowsBackend: windows_language_code=None
04-27 19:05 DEBUG  WindowsBackend: windows_language=English
04-27 19:05 DEBUG  WindowsBackend: processor_name=Intel(R) Xeon(R) CPU           W3520  @ 2.67GHz
04-27 19:05 DEBUG  WindowsBackend: bootloader=vista
04-27 19:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 11925.015625 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(C: hd 11925.015625 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(D: hd 15472.7929688 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(F: hd 28660.921875 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(G: hd 25215.375 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(H: hd 9087.0625 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(I: hd 31661.59375 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(J: hd 26558.578125 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(K: hd 19330.0039063 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(L: hd 26716.640625 mb free ntfs)
04-27 19:05 DEBUG  WindowsBackend: drive=Drive(P: cd 0.0 mb free cdfs)
04-27 19:05 DEBUG  WindowsBackend: uninstaller_path=None
04-27 19:05 DEBUG  WindowsBackend: previous_target_dir=None
04-27 19:05 DEBUG  WindowsBackend: previous_distro_name=None
04-27 19:05 DEBUG  WindowsBackend: keyboard_id=67699721
04-27 19:05 DEBUG  WindowsBackend: keyboard_layout=us
04-27 19:05 DEBUG  WindowsBackend: keyboard_variant=
04-27 19:05 DEBUG  WindowsBackend: total_memory_mb=4079.22265625
04-27 19:05 DEBUG  CommonBackend: Searching ISOs on USB devices
04-27 19:05 DEBUG  CommonBackend: Searching for local CDs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Edubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Lubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
04-27 19:05 INFO   Distro: Found a valid CD for Ubuntu: P:\
04-27 19:05 INFO   root: Running the installer...
04-27 19:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\translations, languages=['hi_IN', 'hi']
04-27 19:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\translations, languages=['hi_IN', 'hi']
04-27 19:05 DEBUG  WinuiInstallationPage: target_drive=K:, installation_size=8000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ankurgupta
04-27 19:05 INFO   root: Received settings
04-27 19:05 DEBUG  CommonBackend: Searching for local CD
04-27 19:05 DEBUG  Distro:   checking whether C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
04-27 19:05 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
04-27 19:05 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
04-27 19:05 INFO   Distro: Found a valid CD for Ubuntu: P:\
04-27 19:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\translations, languages=['en_US', 'en']
04-27 19:05 DEBUG  TaskList: # Running tasklist...
04-27 19:05 DEBUG  TaskList: ## Running select_target_dir...
04-27 19:05 INFO   WindowsBackend: Installing into K:\ubuntu
04-27 19:05 DEBUG  TaskList: ## Finished select_target_dir
04-27 19:05 DEBUG  TaskList: ## Running create_dir_structure...
04-27 19:05 DEBUG  CommonBackend: Creating dir K:\ubuntu
04-27 19:05 DEBUG  CommonBackend: Creating dir K:\ubuntu\disks
04-27 19:05 DEBUG  CommonBackend: Creating dir K:\ubuntu\install
04-27 19:05 DEBUG  CommonBackend: Creating dir K:\ubuntu\install\boot
04-27 19:05 DEBUG  CommonBackend: Creating dir K:\ubuntu\disks\boot
04-27 19:05 DEBUG  CommonBackend: Creating dir K:\ubuntu\disks\boot\grub
04-27 19:05 DEBUG  CommonBackend: Creating dir K:\ubuntu\install\boot\grub
04-27 19:05 DEBUG  TaskList: ## Finished create_dir_structure
04-27 19:05 DEBUG  TaskList: ## Running uncompress_target_dir...
04-27 19:05 DEBUG  TaskList: ## Finished uncompress_target_dir
04-27 19:05 DEBUG  TaskList: ## Running create_uninstaller...
04-27 19:05 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Ankur Gupta\Desktop\wubi.exe -> K:\ubuntu\uninstall-wubi.exe
04-27 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString K:\ubuntu\uninstall-wubi.exe
04-27 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir K:\ubuntu
04-27 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-27 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon K:\ubuntu\Ubuntu.ico
04-27 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev266
04-27 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-27 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-27 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-27 19:05 DEBUG  TaskList: ## Finished create_uninstaller
04-27 19:05 DEBUG  TaskList: ## Running copy_installation_files...
04-27 19:05 DEBUG  WindowsBackend: Copying C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\data\custom-installation -> K:\ubuntu\install\custom-installation
04-27 19:05 DEBUG  WindowsBackend: Copying C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\winboot -> K:\ubuntu\winboot
04-27 19:05 DEBUG  WindowsBackend: Copying C:\Users\ANKURG~1\AppData\Local\Temp\pyl6BA6.tmp\data\images\Ubuntu.ico -> K:\ubuntu\Ubuntu.ico
04-27 19:05 DEBUG  TaskList: ## Finished copy_installation_files
04-27 19:05 DEBUG  TaskList: ## Running get_iso...
04-27 19:05 DEBUG  TaskList: New task copy_file
04-27 19:05 DEBUG  TaskList: ### Running copy_file...
04-27 19:05 DEBUG  TaskList: ### Finished copy_file
04-27 19:05 DEBUG  TaskList: New task check_iso
04-27 19:05 DEBUG  TaskList: ### Running check_iso...
04-27 19:05 DEBUG  CommonBackend: Checking K:\ubuntu\install\installation.iso
04-27 19:05 DEBUG  Distro:   checking Ubuntu ISO K:\ubuntu\install\installation.iso
04-27 19:05 DEBUG  WindowsBackend:   extracting .disk\info from K:\ubuntu\install\installation.iso
04-27 19:05 DEBUG  Distro:   parsing info from str=Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
04-27 19:05 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
04-27 19:05 INFO   Distro: Found a valid iso for Ubuntu: K:\ubuntu\install\installation.iso
04-27 19:05 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
04-27 19:05 DEBUG  TaskList: New task get_metalink
04-27 19:05 DEBUG  TaskList: #### Running get_metalink...
04-27 19:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.metalink](http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.metalink) > K:\ubuntu\install
04-27 19:05 DEBUG  downloader: Download start filename=K:\ubuntu\install\ubuntu-12.04-desktop-i386.metalink, url=http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.metalink, basename=ubuntu-12.04-desktop-i386.metalink, length=30559, text=None
04-27 19:05 DEBUG  downloader: download finished (read 30559 bytes)
04-27 19:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04/MD5SUMS-metalink](http://releases.ubuntu.com/12.04/MD5SUMS-metalink) > K:\ubuntu\install
04-27 19:05 DEBUG  downloader: Download start filename=K:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/12.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=419, text=None
04-27 19:05 DEBUG  downloader: download finished (read 419 bytes)
04-27 19:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/12.04/MD5SUMS-metalink.gpg) > K:\ubuntu\install
04-27 19:05 DEBUG  downloader: Download start filename=K:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/12.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-27 19:05 DEBUG  downloader: download finished (read 198 bytes)
04-27 19:05 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-27 19:05 INFO   saplog: Checking block bindings..
04-27 19:05 INFO   saplog: Key verified successfully.
04-27 19:05 DEBUG  CommonBackend: metalink md5sums:
1e2a0b0f07bc43ab5924767a9cc03e82  ubuntu-12.04-alternate-amd64.metalink
4413660abc989dbbfe6e4abedc9a3ec1  ubuntu-12.04-alternate-i386.metalink
c29be6d58c1581d9cd679aca25db77d1  ubuntu-12.04-desktop-amd64.metalink
c7a6b99206703cfe37f1da5af1d28e3a  ubuntu-12.04-desktop-i386.metalink
4e44ca9bc7ee8ab54ff9565a5437bdc2  ubuntu-12.04-server-amd64.metalink
c9cfc1dd8c65099d929189eedc157f3c  ubuntu-12.04-server-i386.metalink

04-27 19:05 DEBUG  TaskList: #### Finished get_metalink
04-27 19:05 DEBUG  TaskList: New task get_file_md5
04-27 19:05 DEBUG  TaskList: #### Running get_file_md5...
04-27 19:05 DEBUG  TaskList: #### Finished get_file_md5
04-27 19:05 ERROR  CommonBackend: Invalid md5 for ISO K:\ubuntu\install\installation.iso (d791352694374f1c478779f7f4447a3f != 866bdfa347b5425b18fdafe719a956df)
None
04-27 19:05 DEBUG  TaskList: ### Finished check_iso
04-27 19:05 ERROR  TaskList: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'
04-27 19:05 DEBUG  TaskList: # Cancelling tasklist
04-27 19:05 DEBUG  TaskList: # Finished tasklist
04-27 19:05 ERROR  root: 'NoneType' object has no attribute 'get_info'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 564, in use_cd
AttributeError: 'NoneType' object has no attribute 'get_info'


Please help

---

### Post by jadtech on 2012-04-27
best thing you can do with wubi and I have install many times is when the install is done even if it dont prompt you is do a reboot and see if ubuntu will load..

if it dont boot back to window uninstall and try the install again..

---

### Post by bcbc on 2012-04-27
The problem is that the md5 check failed. When you ran Wubi.exe it found the ISO in the P: drive, but whatever is in there doesn't match the md5 sum it downloaded. So your options are:
1. get a good ISO
2. remove the disk from P: and run wubi again. This time it will download a preinstalled image (tar.xz) that is 500MB (not the ISO) and install using that.

If you prefer the ISO then download it manually, save it in the same directory as wubi.exe, and then wubi will find it and use it. 

You should also file a bug because the error message is bogus and due to an uninitialized variable being referenced.

---

### Post by bcbc on 2012-04-27
> **jadtech said:**
> best thing you can do with wubi and I have install many times is when the install is done even if it dont prompt you is do a reboot and see if ubuntu will load..

if it dont boot back to window uninstall and try the install again..

This was only true for bug [lpbug]862003[/lpbug] which is fixed in 12.04.

---

### Post by bcbc on 2012-04-27
PS I filed a bug for you - feel free to add your comments to it: bug [lpbug]989991[/lpbug]

---

### Post by Futureking on 2012-04-27
I was trying to install ubuntu by mounting its iso in virtual cd drive(Magic Disc). 
I removed iso image from virtual cd drive, Placed Wubi file in the directory of Ubuntu ISO and run wubi, BINGO! It worked perfectly.

But I was still facing problem. When I rebooted and choosen Ubuntu from boot menu. after few seconds my monitor goes to sleep. I restarted and it happend again.
Now this time I pressed ESC after choosing Ubuntu from Boot menu. It showed me a menu. I chosen ACPI Mode. And Ubuntu installed successfully.

But problem was still not fixed. After installation I was not able to run ubuntu. because when I boot ubuntu after few seconds my monitor goes to sleep.

So solve this problem I run ubuntu in recovery mode and choosen Safe Graphics mode from recovery menu. Then I saw my desktop in low resolution.

I installed my nVidia Graphics Drivers and restared the computer. 
Now this time Ubuntu booted without any problem. 


Thanks everybody for your help. Thank you!

---

