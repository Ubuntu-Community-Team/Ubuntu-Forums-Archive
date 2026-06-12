---
title: "Extraction error. Log included"
date: 2012-10-01
forum: Installation &amp; Upgrades
---

### Post by Zomgrick on 2012-10-01
[FONT="Tahoma"][SIZE="2"]Hello everyone, 

I'm new to Ubuntu and I have succesfully installed it on my laptop. I'm using it for school and it would be of much use for me if my PC also ran Ubuntu. Unfortunately I haven't been able to install it yet since I'm getting an error at the installation. When the downloading part is finished the installer starts extracting it, and then things go wrong. I have no idea what the problem is. The error log is included. I very much hope someone is able to help me with this problem.

Thanks in advanced,

Rick[/SIZE][/FONT]

```
10-01 15:32 INFO   root: === wubi 12.04 rev269 ===
10-01 15:32 DEBUG  root: Logfile is c:\users\rick\appdata\local\temp\wubi-12.04-rev269.log
10-01 15:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Rick\\Downloads\\wubi.exe"']
10-01 15:32 DEBUG  CommonBackend: data_dir=C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\data
10-01 15:32 DEBUG  WindowsBackend: 7z=C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\bin\7z.exe
10-01 15:32 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-01 15:32 DEBUG  CommonBackend: Fetching basic info...
10-01 15:32 DEBUG  CommonBackend: original_exe=C:\Users\Rick\Downloads\wubi.exe
10-01 15:32 DEBUG  CommonBackend: platform=win32
10-01 15:32 DEBUG  CommonBackend: osname=nt
10-01 15:32 DEBUG  CommonBackend: language=nl_NL
10-01 15:32 DEBUG  CommonBackend: encoding=cp1252
10-01 15:32 DEBUG  WindowsBackend: arch=amd64
10-01 15:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\data\isolist.ini
10-01 15:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-01 15:32 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-01 15:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-01 15:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-01 15:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-01 15:32 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-01 15:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-01 15:32 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-01 15:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-01 15:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-01 15:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-01 15:32 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-01 15:32 DEBUG  WindowsBackend: Fetching host info...
10-01 15:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-01 15:32 DEBUG  WindowsBackend: windows version=vista
10-01 15:32 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-01 15:32 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-01 15:32 DEBUG  WindowsBackend: windows_build=7601
10-01 15:32 DEBUG  WindowsBackend: gmt=1
10-01 15:32 DEBUG  WindowsBackend: country=NL
10-01 15:32 DEBUG  WindowsBackend: timezone=Europe/Amsterdam
10-01 15:32 DEBUG  WindowsBackend: windows_username=Rick
10-01 15:32 DEBUG  WindowsBackend: user_full_name=Rick
10-01 15:32 DEBUG  WindowsBackend: user_directory=C:\Users\Rick
10-01 15:32 DEBUG  WindowsBackend: windows_language_code=1043
10-01 15:32 DEBUG  WindowsBackend: windows_language=Dutch
10-01 15:32 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 9950 Quad-Core Processor
10-01 15:32 DEBUG  WindowsBackend: bootloader=vista
10-01 15:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28574.375 mb free ntfs)
10-01 15:32 DEBUG  WindowsBackend: drive=Drive(C: hd 28574.375 mb free ntfs)
10-01 15:32 DEBUG  WindowsBackend: drive=Drive(D: hd 76475.5507813 mb free ntfs)
10-01 15:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
10-01 15:32 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
10-01 15:32 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-01 15:32 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
10-01 15:32 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
10-01 15:32 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
10-01 15:32 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-01 15:32 DEBUG  WindowsBackend: uninstaller_path=None
10-01 15:32 DEBUG  WindowsBackend: previous_target_dir=None
10-01 15:32 DEBUG  WindowsBackend: previous_distro_name=None
10-01 15:32 DEBUG  WindowsBackend: keyboard_id=-268368877
10-01 15:32 DEBUG  WindowsBackend: keyboard_layout=us
10-01 15:32 DEBUG  WindowsBackend: keyboard_variant=
10-01 15:32 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
10-01 15:32 DEBUG  CommonBackend: locale=nl_NL.UTF-8
10-01 15:32 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
10-01 15:32 DEBUG  CommonBackend: Searching ISOs on USB devices
10-01 15:32 DEBUG  CommonBackend: Searching for local CDs
10-01 15:32 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-01 15:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:32 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-01 15:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:32 INFO   root: Running the installer...
10-01 15:32 DEBUG  WindowsFrontend: __init__...
10-01 15:32 DEBUG  WindowsFrontend: on_init...
10-01 15:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\translations, languages=['nl_NL', 'nl']
10-01 15:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\translations, languages=['nl_NL', 'nl']
10-01 15:33 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=16000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=rick
10-01 15:33 INFO   root: Received settings
10-01 15:33 DEBUG  CommonBackend: Searching for local CD
10-01 15:33 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp is a valid Ubuntu CD
10-01 15:33 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\casper\filesystem.squashfs
10-01 15:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-01 15:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-01 15:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-01 15:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-01 15:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-01 15:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:33 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
10-01 15:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:33 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-01 15:33 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:33 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-01 15:33 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:33 DEBUG  CommonBackend: Searching for local ISO
10-01 15:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Rick\AppData\Local\Temp\pyl315E.tmp\translations, languages=['en_US', 'en']
10-01 15:33 DEBUG  TaskList: # Running tasklist...
10-01 15:33 DEBUG  TaskList: ## Running select_target_dir...
10-01 15:33 INFO   WindowsBackend: Installing into C:\ubuntu
10-01 15:33 DEBUG  TaskList: ## Finished select_target_dir
10-01 15:33 DEBUG  TaskList: ## Running create_dir_structure...
10-01 15:33 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-01 15:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-01 15:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-01 15:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-01 15:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-01 15:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-01 15:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-01 15:33 DEBUG  TaskList: ## Finished create_dir_structure
10-01 15:33 DEBUG  TaskList: ## Running create_uninstaller...
10-01 15:33 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Rick\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-01 15:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-01 15:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-01 15:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-01 15:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-01 15:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269
10-01 15:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-01 15:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-01 15:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-01 15:33 DEBUG  TaskList: ## Finished create_uninstaller
10-01 15:33 DEBUG  TaskList: ## Running create_preseed_diskimage...
10-01 15:33 DEBUG  TaskList: ## Finished create_preseed_diskimage
10-01 15:33 DEBUG  TaskList: ## Running get_diskimage...
10-01 15:33 DEBUG  TaskList: New task download
10-01 15:33 DEBUG  TaskList: ### Running download...
10-01 15:33 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz
10-01 15:33 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz, basename=ubuntu-12.04.1-wubi-amd64.tar.xz, length=506081252, text=None
10-01 15:37 DEBUG  downloader: download finished (read 506053512 bytes)
10-01 15:37 DEBUG  TaskList: ### Finished download
10-01 15:37 DEBUG  TaskList: ## Finished get_diskimage
10-01 15:37 DEBUG  TaskList: ## Running extract_diskimage...
10-01 15:37 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
10-01 15:37 DEBUG  TaskList: # Cancelling tasklist
10-01 15:37 DEBUG  TaskList: # Finished tasklist
10-01 15:37 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
10-01 15:38 INFO   root: === wubi 12.04 rev269 ===
10-01 15:38 DEBUG  root: Logfile is c:\users\rick\appdata\local\temp\wubi-12.04-rev269.log
10-01 15:38 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
10-01 15:38 DEBUG  CommonBackend: data_dir=C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\data
10-01 15:38 DEBUG  WindowsBackend: 7z=C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\bin\7z.exe
10-01 15:38 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-01 15:38 DEBUG  CommonBackend: Fetching basic info...
10-01 15:38 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
10-01 15:38 DEBUG  CommonBackend: platform=win32
10-01 15:38 DEBUG  CommonBackend: osname=nt
10-01 15:38 DEBUG  CommonBackend: language=nl_NL
10-01 15:38 DEBUG  CommonBackend: encoding=cp1252
10-01 15:38 DEBUG  WindowsBackend: arch=amd64
10-01 15:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\data\isolist.ini
10-01 15:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-01 15:38 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-01 15:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-01 15:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-01 15:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-01 15:38 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-01 15:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-01 15:38 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-01 15:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-01 15:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-01 15:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-01 15:38 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-01 15:38 DEBUG  WindowsBackend: Fetching host info...
10-01 15:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-01 15:38 DEBUG  WindowsBackend: windows version=vista
10-01 15:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-01 15:38 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-01 15:38 DEBUG  WindowsBackend: windows_build=7601
10-01 15:38 DEBUG  WindowsBackend: gmt=1
10-01 15:38 DEBUG  WindowsBackend: country=NL
10-01 15:38 DEBUG  WindowsBackend: timezone=Europe/Amsterdam
10-01 15:38 DEBUG  WindowsBackend: windows_username=Rick
10-01 15:38 DEBUG  WindowsBackend: user_full_name=Rick
10-01 15:38 DEBUG  WindowsBackend: user_directory=C:\Users\Rick
10-01 15:38 DEBUG  WindowsBackend: windows_language_code=1043
10-01 15:38 DEBUG  WindowsBackend: windows_language=Dutch
10-01 15:38 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 9950 Quad-Core Processor
10-01 15:38 DEBUG  WindowsBackend: bootloader=vista
10-01 15:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 27971.4765625 mb free ntfs)
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(C: hd 27971.4765625 mb free ntfs)
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(D: hd 76475.5546875 mb free ntfs)
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-01 15:38 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-01 15:38 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-01 15:38 DEBUG  WindowsBackend: keyboard_id=-268368877
10-01 15:38 DEBUG  WindowsBackend: keyboard_layout=us
10-01 15:38 DEBUG  WindowsBackend: keyboard_variant=
10-01 15:38 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
10-01 15:38 DEBUG  CommonBackend: locale=nl_NL.UTF-8
10-01 15:38 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
10-01 15:38 DEBUG  CommonBackend: Searching ISOs on USB devices
10-01 15:38 DEBUG  CommonBackend: Searching for local CDs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 INFO   root: Running the uninstaller...
10-01 15:38 INFO   CommonBackend: This is the uninstaller running
10-01 15:38 DEBUG  WindowsFrontend: __init__...
10-01 15:38 DEBUG  WindowsFrontend: on_init...
10-01 15:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\translations, languages=['nl_NL', 'nl']
10-01 15:38 INFO   root: Received settings
10-01 15:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\translations, languages=['nl_NL', 'nl']
10-01 15:38 DEBUG  TaskList: # Running tasklist...
10-01 15:38 DEBUG  TaskList: ## Running Opstartladervermelding verwijderen...
10-01 15:38 DEBUG  WindowsBackend: Could not find bcd id
10-01 15:38 DEBUG  WindowsBackend: undo_bootini C:
10-01 15:38 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 27971.4765625 mb free ntfs)
10-01 15:38 DEBUG  WindowsBackend: undo_bootini D:
10-01 15:38 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 76475.5546875 mb free ntfs)
10-01 15:38 DEBUG  WindowsBackend: undo_bootini G:
10-01 15:38 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: undo_bootini H:
10-01 15:38 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: undo_bootini I:
10-01 15:38 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: undo_bootini J:
10-01 15:38 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: undo_bootini M:
10-01 15:38 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
10-01 15:38 DEBUG  TaskList: ## Finished Opstartladervermelding verwijderen
10-01 15:38 DEBUG  TaskList: ## Running Doelmap verwijderen...
10-01 15:38 DEBUG  CommonBackend: Deleting C:\ubuntu
10-01 15:38 DEBUG  TaskList: ## Finished Doelmap verwijderen
10-01 15:38 DEBUG  TaskList: ## Running Registersleutel verwijderen...
10-01 15:38 DEBUG  TaskList: ## Finished Registersleutel verwijderen
10-01 15:38 DEBUG  TaskList: # Finished tasklist
10-01 15:38 INFO   root: Almost finished uninstalling
10-01 15:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Rick\AppData\Local\Temp\pylEF4F.tmp\translations, languages=['nl_NL', 'nl']
10-01 15:38 INFO   root: Finished uninstallation
10-01 15:38 DEBUG  root: application.quit
10-01 15:38 DEBUG  WindowsFrontend: frontend.quit
10-01 15:38 DEBUG  WindowsFrontend: frontend.on_quit
10-01 15:38 DEBUG  root: application.on_quit
10-01 15:38 INFO   root: sys.exit
10-01 15:38 INFO   root: === wubi 12.04 rev269 ===
10-01 15:38 DEBUG  root: Logfile is c:\users\rick\appdata\local\temp\wubi-12.04-rev269.log
10-01 15:38 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Rick\\Downloads\\wubi.exe"']
10-01 15:38 DEBUG  CommonBackend: data_dir=C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\data
10-01 15:38 DEBUG  WindowsBackend: 7z=C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\bin\7z.exe
10-01 15:38 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-01 15:38 DEBUG  CommonBackend: Fetching basic info...
10-01 15:38 DEBUG  CommonBackend: original_exe=C:\Users\Rick\Downloads\wubi.exe
10-01 15:38 DEBUG  CommonBackend: platform=win32
10-01 15:38 DEBUG  CommonBackend: osname=nt
10-01 15:38 DEBUG  CommonBackend: language=nl_NL
10-01 15:38 DEBUG  CommonBackend: encoding=cp1252
10-01 15:38 DEBUG  WindowsBackend: arch=amd64
10-01 15:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\data\isolist.ini
10-01 15:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-01 15:38 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-01 15:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-01 15:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-01 15:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-01 15:38 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-01 15:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-01 15:38 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-01 15:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-01 15:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-01 15:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-01 15:38 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-01 15:38 DEBUG  WindowsBackend: Fetching host info...
10-01 15:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-01 15:38 DEBUG  WindowsBackend: windows version=vista
10-01 15:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-01 15:38 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-01 15:38 DEBUG  WindowsBackend: windows_build=7601
10-01 15:38 DEBUG  WindowsBackend: gmt=1
10-01 15:38 DEBUG  WindowsBackend: country=NL
10-01 15:38 DEBUG  WindowsBackend: timezone=Europe/Amsterdam
10-01 15:38 DEBUG  WindowsBackend: windows_username=Rick
10-01 15:38 DEBUG  WindowsBackend: user_full_name=Rick
10-01 15:38 DEBUG  WindowsBackend: user_directory=C:\Users\Rick
10-01 15:38 DEBUG  WindowsBackend: windows_language_code=1043
10-01 15:38 DEBUG  WindowsBackend: windows_language=Dutch
10-01 15:38 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 9950 Quad-Core Processor
10-01 15:38 DEBUG  WindowsBackend: bootloader=vista
10-01 15:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28519.046875 mb free ntfs)
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(C: hd 28519.046875 mb free ntfs)
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(D: hd 76475.5546875 mb free ntfs)
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-01 15:38 DEBUG  WindowsBackend: uninstaller_path=None
10-01 15:38 DEBUG  WindowsBackend: previous_target_dir=None
10-01 15:38 DEBUG  WindowsBackend: previous_distro_name=None
10-01 15:38 DEBUG  WindowsBackend: keyboard_id=-268368877
10-01 15:38 DEBUG  WindowsBackend: keyboard_layout=us
10-01 15:38 DEBUG  WindowsBackend: keyboard_variant=
10-01 15:38 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
10-01 15:38 DEBUG  CommonBackend: locale=nl_NL.UTF-8
10-01 15:38 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
10-01 15:38 DEBUG  CommonBackend: Searching ISOs on USB devices
10-01 15:38 DEBUG  CommonBackend: Searching for local CDs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 INFO   root: Running the installer...
10-01 15:38 DEBUG  WindowsFrontend: __init__...
10-01 15:38 DEBUG  WindowsFrontend: on_init...
10-01 15:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\translations, languages=['nl_NL', 'nl']
10-01 15:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\translations, languages=['nl_NL', 'nl']
10-01 15:38 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=16000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=rick
10-01 15:38 INFO   root: Received settings
10-01 15:38 DEBUG  CommonBackend: Searching for local CD
10-01 15:38 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:38 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-01 15:38 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:38 DEBUG  CommonBackend: Searching for local ISO
10-01 15:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Rick\AppData\Local\Temp\pyl2195.tmp\translations, languages=['en_US', 'en']
10-01 15:38 DEBUG  TaskList: # Running tasklist...
10-01 15:38 DEBUG  TaskList: ## Running select_target_dir...
10-01 15:38 INFO   WindowsBackend: Installing into C:\ubuntu
10-01 15:38 DEBUG  TaskList: ## Finished select_target_dir
10-01 15:38 DEBUG  TaskList: ## Running create_dir_structure...
10-01 15:38 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-01 15:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-01 15:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-01 15:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-01 15:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-01 15:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-01 15:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-01 15:38 DEBUG  TaskList: ## Finished create_dir_structure
10-01 15:38 DEBUG  TaskList: ## Running create_uninstaller...
10-01 15:38 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Rick\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-01 15:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-01 15:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-01 15:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-01 15:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-01 15:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269
10-01 15:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-01 15:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-01 15:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-01 15:38 DEBUG  TaskList: ## Finished create_uninstaller
10-01 15:38 DEBUG  TaskList: ## Running create_preseed_diskimage...
10-01 15:38 DEBUG  TaskList: ## Finished create_preseed_diskimage
10-01 15:38 DEBUG  TaskList: ## Running get_diskimage...
10-01 15:38 DEBUG  TaskList: New task download
10-01 15:38 DEBUG  TaskList: ### Running download...
10-01 15:38 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz
10-01 15:38 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.1-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz, basename=ubuntu-12.04.1-wubi-amd64.tar.xz, length=506081252, text=None
10-01 15:42 DEBUG  downloader: download finished (read 506071032 bytes)
10-01 15:42 DEBUG  TaskList: ### Finished download
10-01 15:42 DEBUG  TaskList: ## Finished get_diskimage
10-01 15:42 DEBUG  TaskList: ## Running extract_diskimage...
10-01 15:42 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
10-01 15:42 DEBUG  TaskList: # Cancelling tasklist
10-01 15:42 DEBUG  TaskList: # Finished tasklist
10-01 15:42 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
10-01 15:44 INFO   root: === wubi 12.04 rev269 ===
10-01 15:44 DEBUG  root: Logfile is c:\users\rick\appdata\local\temp\wubi-12.04-rev269.log
10-01 15:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
10-01 15:44 DEBUG  CommonBackend: data_dir=C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\data
10-01 15:44 DEBUG  WindowsBackend: 7z=C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\bin\7z.exe
10-01 15:44 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-01 15:44 DEBUG  CommonBackend: Fetching basic info...
10-01 15:44 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
10-01 15:44 DEBUG  CommonBackend: platform=win32
10-01 15:44 DEBUG  CommonBackend: osname=nt
10-01 15:44 DEBUG  CommonBackend: language=nl_NL
10-01 15:44 DEBUG  CommonBackend: encoding=cp1252
10-01 15:44 DEBUG  WindowsBackend: arch=amd64
10-01 15:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\data\isolist.ini
10-01 15:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-01 15:44 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-01 15:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-01 15:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-01 15:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-01 15:44 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-01 15:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-01 15:44 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-01 15:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-01 15:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-01 15:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-01 15:44 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-01 15:44 DEBUG  WindowsBackend: Fetching host info...
10-01 15:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-01 15:44 DEBUG  WindowsBackend: windows version=vista
10-01 15:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-01 15:44 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-01 15:44 DEBUG  WindowsBackend: windows_build=7601
10-01 15:44 DEBUG  WindowsBackend: gmt=1
10-01 15:44 DEBUG  WindowsBackend: country=NL
10-01 15:44 DEBUG  WindowsBackend: timezone=Europe/Amsterdam
10-01 15:44 DEBUG  WindowsBackend: windows_username=Rick
10-01 15:44 DEBUG  WindowsBackend: user_full_name=Rick
10-01 15:44 DEBUG  WindowsBackend: user_directory=C:\Users\Rick
10-01 15:44 DEBUG  WindowsBackend: windows_language_code=1043
10-01 15:44 DEBUG  WindowsBackend: windows_language=Dutch
10-01 15:44 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) 9950 Quad-Core Processor
10-01 15:44 DEBUG  WindowsBackend: bootloader=vista
10-01 15:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29256.9804688 mb free ntfs)
10-01 15:44 DEBUG  WindowsBackend: drive=Drive(C: hd 29256.9804688 mb free ntfs)
10-01 15:44 DEBUG  WindowsBackend: drive=Drive(D: hd 76475.5546875 mb free ntfs)
10-01 15:44 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
10-01 15:44 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
10-01 15:44 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
10-01 15:44 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
10-01 15:44 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
10-01 15:44 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
10-01 15:44 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-01 15:44 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-01 15:44 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-01 15:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-01 15:44 DEBUG  WindowsBackend: keyboard_id=-268368877
10-01 15:44 DEBUG  WindowsBackend: keyboard_layout=us
10-01 15:44 DEBUG  WindowsBackend: keyboard_variant=
10-01 15:44 DEBUG  CommonBackend: python locale=('nl_NL', 'cp1252')
10-01 15:44 DEBUG  CommonBackend: locale=nl_NL.UTF-8
10-01 15:44 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
10-01 15:44 DEBUG  CommonBackend: Searching ISOs on USB devices
10-01 15:44 DEBUG  CommonBackend: Searching for local CDs
10-01 15:44 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether J:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether J:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether K:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether K:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-01 15:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:44 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-01 15:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-01 15:44 INFO   root: Running the uninstaller...
10-01 15:44 INFO   CommonBackend: This is the uninstaller running
10-01 15:44 DEBUG  WindowsFrontend: __init__...
10-01 15:44 DEBUG  WindowsFrontend: on_init...
10-01 15:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\translations, languages=['nl_NL', 'nl']
10-01 15:44 INFO   root: Received settings
10-01 15:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\translations, languages=['nl_NL', 'nl']
10-01 15:44 DEBUG  TaskList: # Running tasklist...
10-01 15:44 DEBUG  TaskList: ## Running Opstartladervermelding verwijderen...
10-01 15:44 DEBUG  WindowsBackend: Could not find bcd id
10-01 15:44 DEBUG  WindowsBackend: undo_bootini C:
10-01 15:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 29256.9804688 mb free ntfs)
10-01 15:44 DEBUG  WindowsBackend: undo_bootini D:
10-01 15:44 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 76475.5546875 mb free ntfs)
10-01 15:44 DEBUG  WindowsBackend: undo_bootini G:
10-01 15:44 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
10-01 15:44 DEBUG  WindowsBackend: undo_bootini H:
10-01 15:44 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
10-01 15:44 DEBUG  WindowsBackend: undo_bootini I:
10-01 15:44 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
10-01 15:44 DEBUG  WindowsBackend: undo_bootini J:
10-01 15:44 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 0.0 mb free )
10-01 15:44 DEBUG  WindowsBackend: undo_bootini M:
10-01 15:44 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
10-01 15:44 DEBUG  TaskList: ## Finished Opstartladervermelding verwijderen
10-01 15:44 DEBUG  TaskList: ## Running Doelmap verwijderen...
10-01 15:44 DEBUG  CommonBackend: Deleting C:\ubuntu
10-01 15:44 DEBUG  TaskList: ## Finished Doelmap verwijderen
10-01 15:44 DEBUG  TaskList: ## Running Registersleutel verwijderen...
10-01 15:44 DEBUG  TaskList: ## Finished Registersleutel verwijderen
10-01 15:44 DEBUG  TaskList: # Finished tasklist
10-01 15:44 INFO   root: Almost finished uninstalling
10-01 15:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Rick\AppData\Local\Temp\pylB0CA.tmp\translations, languages=['nl_NL', 'nl']
10-01 15:44 INFO   root: Finished uninstallation
10-01 15:44 DEBUG  root: application.quit
10-01 15:44 DEBUG  WindowsFrontend: frontend.quit
10-01 15:44 DEBUG  WindowsFrontend: frontend.on_quit
10-01 15:44 DEBUG  root: application.on_quit
10-01 15:44 INFO   root: sys.exit
```

---

### Post by Zomgrick on 2012-10-01
Bump. Someone please look at the log and see if you can find the solution..

---

### Post by windscape on 2012-10-01
Hi,

This has come up before. The size of the downloaded file doesn't match the size it was expecting. I believe the solution is to manually download the file and put it in the same folder as the installer. The file is at [http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-wubi-amd64.tar.xz) and it should be 506081252 bytes in size.

---

### Post by Zomgrick on 2012-10-01
Hey windscape, thanks for the help!
I've downloaded the file from the site you gave me and placed it in the same destination as the installer itself. I'm guessing I should just run the installer now? 
After doing so though it just starts to download that exact same file. I'm sorry if I'm not seeing something simple or whatever.

---

### Post by windscape on 2012-10-01
Hi,

I forgot to add that you have to use the instructions here: [http://askubuntu.com/questions/143463/ubuntu-12-04-wubi-i386-tar-xz-for-the-wubi-installer/143478#143478]("http://askubuntu.com/questions/143463/ubuntu-12-04-wubi-i386-tar-xz-for-the-wubi-installer/143478#143478") to tell wubi.exe to use the file you downloaded manually.

---

### Post by Zomgrick on 2012-10-01
Hello windscape, 

Thanks alot for helping me out. I'm actually typing this comment on Ubuntu right now. Your help is much appreciated.

EDIT: How do I tag this thread as "Solved" ?

---

