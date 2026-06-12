---
title: "wubi install failed"
date: 2012-07-14
forum: Installation &amp; Upgrades
---

### Post by billchenxi on 2012-07-14
Hi, guys, 
I tried to install ubuntu with wubi, but doesn't work, I tried twice, nothing loaded and nothing work. please check the error log file:

Please help me!!!:confused:
Thanks a lot, 
Bill


> 
07-13 23:21 INFO   root: === wubi 12.04 rev266 ===
07-13 23:21 DEBUG  root: Logfile is c:\users\bill\appdata\local\temp\wubi-12.04-rev266.log
07-13 23:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Bill\\Downloads\\wubi.exe"']
07-13 23:21 DEBUG  CommonBackend: data_dir=C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\data
07-13 23:21 DEBUG  WindowsBackend: 7z=C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\bin\7z.exe
07-13 23:21 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-13 23:21 DEBUG  CommonBackend: Fetching basic info...
07-13 23:21 DEBUG  CommonBackend: original_exe=C:\Users\Bill\Downloads\wubi.exe
07-13 23:21 DEBUG  CommonBackend: platform=win32
07-13 23:21 DEBUG  CommonBackend: osname=nt
07-13 23:21 DEBUG  CommonBackend: language=en_US
07-13 23:21 DEBUG  CommonBackend: encoding=cp1252
07-13 23:21 DEBUG  WindowsBackend: arch=amd64
07-13 23:21 DEBUG  CommonBackend: Parsing isolist=C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\data\isolist.ini
07-13 23:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-13 23:21 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-13 23:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-13 23:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-13 23:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-13 23:21 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-13 23:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-13 23:21 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-13 23:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-13 23:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-13 23:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-13 23:21 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-13 23:21 DEBUG  WindowsBackend: Fetching host info...
07-13 23:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-13 23:21 DEBUG  WindowsBackend: windows version=vista
07-13 23:21 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-13 23:21 DEBUG  WindowsBackend: windows_sp=None
07-13 23:21 DEBUG  WindowsBackend: windows_build=7601
07-13 23:21 DEBUG  WindowsBackend: gmt=-5
07-13 23:21 DEBUG  WindowsBackend: country=US
07-13 23:21 DEBUG  WindowsBackend: timezone=America/New_York
07-13 23:21 DEBUG  WindowsBackend: windows_username=Bill
07-13 23:21 DEBUG  WindowsBackend: user_full_name=Bill
07-13 23:21 DEBUG  WindowsBackend: user_directory=C:\Users\Bill
07-13 23:21 DEBUG  WindowsBackend: windows_language_code=1033
07-13 23:21 DEBUG  WindowsBackend: windows_language=English
07-13 23:21 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-13 23:21 DEBUG  WindowsBackend: bootloader=vista
07-13 23:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 123341.824219 mb free ntfs)
07-13 23:21 DEBUG  WindowsBackend: drive=Drive(C: hd 123341.824219 mb free ntfs)
07-13 23:21 DEBUG  WindowsBackend: drive=Drive(D: hd 1877.453125 mb free ntfs)
07-13 23:21 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-13 23:21 DEBUG  WindowsBackend: drive=Drive(F: hd 105242.226563 mb free ntfs)
07-13 23:21 DEBUG  WindowsBackend: drive=Drive(G: hd 67593.9492188 mb free ntfs)
07-13 23:21 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-13 23:21 DEBUG  WindowsBackend: drive=Drive(I: hd 64834.03125 mb free ntfs)
07-13 23:21 DEBUG  WindowsBackend: uninstaller_path=None
07-13 23:21 DEBUG  WindowsBackend: previous_target_dir=None
07-13 23:21 DEBUG  WindowsBackend: previous_distro_name=None
07-13 23:21 DEBUG  WindowsBackend: keyboard_id=67699721
07-13 23:21 DEBUG  WindowsBackend: keyboard_layout=us
07-13 23:21 DEBUG  WindowsBackend: keyboard_variant=
07-13 23:21 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-13 23:21 DEBUG  CommonBackend: locale=en_US.UTF-8
07-13 23:21 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-13 23:21 DEBUG  CommonBackend: Searching ISOs on USB devices
07-13 23:21 DEBUG  Distro:   checking Ubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Ubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Kubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Kubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Xubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Xubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Mythbuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Mythbuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Edubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Edubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Lubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Lubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Ubuntu ISO G:\Practice Sets fo.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Ubuntu ISO G:\Practice Sets fo.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Kubuntu ISO G:\Practice Sets fo.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Kubuntu ISO G:\Practice Sets fo.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Xubuntu ISO G:\Practice Sets fo.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Xubuntu ISO G:\Practice Sets fo.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Mythbuntu ISO G:\Practice Sets fo.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Mythbuntu ISO G:\Practice Sets fo.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Edubuntu ISO G:\Practice Sets fo.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Edubuntu ISO G:\Practice Sets fo.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Lubuntu ISO G:\Practice Sets fo.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking Lubuntu ISO G:\Practice Sets fo.iso
07-13 23:21 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:21 DEBUG  CommonBackend: Searching for local CDs
07-13 23:21 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp is a valid Ubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp is a valid Ubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp is a valid Kubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp is a valid Kubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp is a valid Xubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp is a valid Xubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp is a valid Mythbuntu CD
07-13 23:21 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp is a valid Mythbuntu CD
07-13 23:21 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp is a valid Edubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp is a valid Edubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp is a valid Lubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp is a valid Lubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-13 23:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-13 23:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-13 23:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-13 23:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-13 23:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-13 23:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-13 23:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-13 23:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-13 23:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-13 23:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-13 23:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-13 23:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:21 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-13 23:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:21 INFO   root: Running the installer...
07-13 23:21 DEBUG  WindowsFrontend: __init__...
07-13 23:21 DEBUG  WindowsFrontend: on_init...
07-13 23:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\translations, languages=['en_US', 'en']
07-13 23:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\translations, languages=['en_US', 'en']
07-13 23:23 DEBUG  WinuiInstallationPage: target_drive=I:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=bill
07-13 23:23 INFO   root: Received settings
07-13 23:23 DEBUG  CommonBackend: Searching for local CD
07-13 23:23 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp is a valid Ubuntu CD
07-13 23:23 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\casper\filesystem.squashfs
07-13 23:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-13 23:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-13 23:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-13 23:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:23 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-13 23:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:23 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-13 23:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:23 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-13 23:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:23 DEBUG  CommonBackend: Searching for local ISO
07-13 23:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Bill\AppData\Local\Temp\pyl4DD1.tmp\translations, languages=['en_US', 'en']
07-13 23:23 DEBUG  TaskList: # Running tasklist...
07-13 23:23 DEBUG  TaskList: ## Running select_target_dir...
07-13 23:23 INFO   WindowsBackend: Installing into I:\ubuntu
07-13 23:23 DEBUG  TaskList: ## Finished select_target_dir
07-13 23:23 DEBUG  TaskList: ## Running create_dir_structure...
07-13 23:23 DEBUG  CommonBackend: Creating dir I:\ubuntu
07-13 23:23 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks
07-13 23:23 DEBUG  CommonBackend: Creating dir I:\ubuntu\install
07-13 23:23 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot
07-13 23:23 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot
07-13 23:23 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot\grub
07-13 23:23 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot\grub
07-13 23:23 DEBUG  TaskList: ## Finished create_dir_structure
07-13 23:23 DEBUG  TaskList: ## Running create_uninstaller...
07-13 23:23 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Bill\Downloads\wubi.exe -> I:\ubuntu\uninstall-wubi.exe
07-13 23:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString I:\ubuntu\uninstall-wubi.exe
07-13 23:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir I:\ubuntu
07-13 23:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-13 23:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon I:\ubuntu\Ubuntu.ico
07-13 23:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev266
07-13 23:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-13 23:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-13 23:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-13 23:23 DEBUG  TaskList: ## Finished create_uninstaller
07-13 23:23 DEBUG  TaskList: ## Running create_preseed_diskimage...
07-13 23:23 DEBUG  TaskList: ## Finished create_preseed_diskimage
07-13 23:23 DEBUG  TaskList: ## Running get_diskimage...
07-13 23:23 DEBUG  TaskList: New task download
07-13 23:23 DEBUG  TaskList: ### Running download...
07-13 23:23 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04/ubuntu-12.04-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04/ubuntu-12.04-wubi-amd64.tar.xz) > I:\ubuntu\disks\ubuntu-12.04-wubi-amd64.tar.xz
07-13 23:23 DEBUG  downloader: Download start filename=I:\ubuntu\disks\ubuntu-12.04-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04/ubuntu-12.04-wubi-amd64.tar.xz, basename=ubuntu-12.04-wubi-amd64.tar.xz, length=512730488, text=None
07-13 23:36 DEBUG  TaskList: ### Finished download
07-13 23:36 DEBUG  downloader: download finished (read 512730488 bytes)
07-13 23:36 DEBUG  TaskList: ## Finished get_diskimage
07-13 23:36 DEBUG  TaskList: ## Running extract_diskimage...
07-13 23:37 DEBUG  TaskList: ## Finished extract_diskimage
07-13 23:37 DEBUG  TaskList: ## Running choose_disk_sizes...
07-13 23:37 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
07-13 23:37 DEBUG  TaskList: ## Finished choose_disk_sizes
07-13 23:37 DEBUG  TaskList: ## Running expand_diskimage...
07-13 23:39 DEBUG  TaskList: ## Finished expand_diskimage
07-13 23:39 DEBUG  TaskList: ## Running create_swap_diskimage...
07-13 23:39 DEBUG  TaskList: ## Finished create_swap_diskimage
07-13 23:39 DEBUG  TaskList: ## Running modify_bootloader...
07-13 23:39 DEBUG  TaskList: New task modify_bcd
07-13 23:39 DEBUG  TaskList: ### Running modify_bcd...
07-13 23:39 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 123341.824219 mb free ntfs)
07-13 23:39 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {84cb243d-fe9d-11e0-9d9a-b55cb4610dfe} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {84cb243d-fe9d-11e0-9d9a-b55cb4610dfe} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
07-13 23:39 DEBUG  TaskList: # Cancelling tasklist
07-13 23:39 DEBUG  TaskList: New task modify_bcd
07-13 23:39 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {84cb243d-fe9d-11e0-9d9a-b55cb4610dfe} device partition=I:
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
>>command=C:\Windows\sysnative\bcdedit.exe /set {84cb243d-fe9d-11e0-9d9a-b55cb4610dfe} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
07-13 23:39 DEBUG  TaskList: New task modify_bcd
07-13 23:39 DEBUG  TaskList: New task modify_bcd
07-13 23:39 DEBUG  TaskList: New task modify_bcd
07-13 23:39 DEBUG  TaskList: ## Finished modify_bootloader
07-13 23:39 DEBUG  TaskList: # Finished tasklist
07-13 23:44 INFO   root: === wubi 12.04 rev266 ===
07-13 23:44 DEBUG  root: Logfile is c:\users\bill\appdata\local\temp\wubi-12.04-rev266.log
07-13 23:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Bill\\Downloads\\wubi.exe"']
07-13 23:44 DEBUG  CommonBackend: data_dir=C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\data
07-13 23:44 DEBUG  WindowsBackend: 7z=C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\bin\7z.exe
07-13 23:44 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-13 23:44 DEBUG  CommonBackend: Fetching basic info...
07-13 23:44 DEBUG  CommonBackend: original_exe=C:\Users\Bill\Downloads\wubi.exe
07-13 23:44 DEBUG  CommonBackend: platform=win32
07-13 23:44 DEBUG  CommonBackend: osname=nt
07-13 23:44 DEBUG  CommonBackend: language=en_US
07-13 23:44 DEBUG  CommonBackend: encoding=cp1252
07-13 23:44 DEBUG  WindowsBackend: arch=amd64
07-13 23:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\data\isolist.ini
07-13 23:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-13 23:44 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-13 23:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-13 23:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-13 23:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-13 23:44 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-13 23:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-13 23:44 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-13 23:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-13 23:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-13 23:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-13 23:44 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-13 23:44 DEBUG  WindowsBackend: Fetching host info...
07-13 23:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-13 23:44 DEBUG  WindowsBackend: windows version=vista
07-13 23:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-13 23:44 DEBUG  WindowsBackend: windows_sp=None
07-13 23:44 DEBUG  WindowsBackend: windows_build=7601
07-13 23:44 DEBUG  WindowsBackend: gmt=-5
07-13 23:44 DEBUG  WindowsBackend: country=US
07-13 23:44 DEBUG  WindowsBackend: timezone=America/New_York
07-13 23:44 DEBUG  WindowsBackend: windows_username=Bill
07-13 23:44 DEBUG  WindowsBackend: user_full_name=Bill
07-13 23:44 DEBUG  WindowsBackend: user_directory=C:\Users\Bill
07-13 23:44 DEBUG  WindowsBackend: windows_language_code=1033
07-13 23:44 DEBUG  WindowsBackend: windows_language=English
07-13 23:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-13 23:44 DEBUG  WindowsBackend: bootloader=vista
07-13 23:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 123569.566406 mb free ntfs)
07-13 23:44 DEBUG  WindowsBackend: drive=Drive(C: hd 123569.566406 mb free ntfs)
07-13 23:44 DEBUG  WindowsBackend: drive=Drive(D: hd 1877.453125 mb free ntfs)
07-13 23:44 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-13 23:44 DEBUG  WindowsBackend: drive=Drive(F: hd 105242.226563 mb free ntfs)
07-13 23:44 DEBUG  WindowsBackend: drive=Drive(G: hd 67593.9492188 mb free ntfs)
07-13 23:44 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-13 23:44 DEBUG  WindowsBackend: drive=Drive(I: hd 61405.6640625 mb free ntfs)
07-13 23:44 DEBUG  WindowsBackend: uninstaller_path=I:\ubuntu\uninstall-wubi.exe
07-13 23:44 DEBUG  WindowsBackend: previous_target_dir=I:\ubuntu
07-13 23:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-13 23:44 DEBUG  WindowsBackend: keyboard_id=67699721
07-13 23:44 DEBUG  WindowsBackend: keyboard_layout=us
07-13 23:44 DEBUG  WindowsBackend: keyboard_variant=
07-13 23:44 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-13 23:44 DEBUG  CommonBackend: locale=en_US.UTF-8
07-13 23:44 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-13 23:44 DEBUG  CommonBackend: Searching ISOs on USB devices
07-13 23:44 DEBUG  Distro:   checking Ubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Ubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Kubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Kubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Xubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Xubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Mythbuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Mythbuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Edubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Edubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Lubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Lubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Ubuntu ISO G:\Practice Sets fo.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Ubuntu ISO G:\Practice Sets fo.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Kubuntu ISO G:\Practice Sets fo.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Kubuntu ISO G:\Practice Sets fo.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Xubuntu ISO G:\Practice Sets fo.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Xubuntu ISO G:\Practice Sets fo.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Mythbuntu ISO G:\Practice Sets fo.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Mythbuntu ISO G:\Practice Sets fo.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Edubuntu ISO G:\Practice Sets fo.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Edubuntu ISO G:\Practice Sets fo.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Lubuntu ISO G:\Practice Sets fo.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking Lubuntu ISO G:\Practice Sets fo.iso
07-13 23:44 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:44 DEBUG  CommonBackend: Searching for local CDs
07-13 23:44 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp is a valid Ubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp is a valid Ubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp is a valid Kubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp is a valid Kubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp is a valid Xubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp is a valid Xubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp is a valid Mythbuntu CD
07-13 23:44 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp is a valid Mythbuntu CD
07-13 23:44 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp is a valid Edubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp is a valid Edubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp is a valid Lubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp is a valid Lubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-13 23:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-13 23:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-13 23:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-13 23:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-13 23:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-13 23:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-13 23:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-13 23:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-13 23:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-13 23:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-13 23:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-13 23:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:44 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-13 23:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:44 INFO   root: Already installed, running the uninstaller...
07-13 23:44 INFO   root: Running the uninstaller...
07-13 23:44 INFO   CommonBackend: This is the uninstaller running
07-13 23:44 DEBUG  WindowsFrontend: __init__...
07-13 23:44 DEBUG  WindowsFrontend: on_init...
07-13 23:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Bill\AppData\Local\Temp\pylB1D1.tmp\translations, languages=['en_US', 'en']
07-13 23:44 INFO   WindowsFrontend: Operation cancelled
07-13 23:44 DEBUG  WindowsFrontend: frontend.quit
07-13 23:44 DEBUG  WindowsFrontend: frontend.on_quit
07-13 23:44 DEBUG  root: application.on_quit
07-13 23:44 INFO   root: sys.exit
07-13 23:48 INFO   root: === wubi 12.04 rev266 ===
07-13 23:48 DEBUG  root: Logfile is c:\users\bill\appdata\local\temp\wubi-12.04-rev266.log
07-13 23:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Bill\\Downloads\\wubi.exe"']
07-13 23:48 DEBUG  CommonBackend: data_dir=C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\data
07-13 23:48 DEBUG  WindowsBackend: 7z=C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\bin\7z.exe
07-13 23:48 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-13 23:48 DEBUG  CommonBackend: Fetching basic info...
07-13 23:48 DEBUG  CommonBackend: original_exe=C:\Users\Bill\Downloads\wubi.exe
07-13 23:48 DEBUG  CommonBackend: platform=win32
07-13 23:48 DEBUG  CommonBackend: osname=nt
07-13 23:48 DEBUG  CommonBackend: language=en_US
07-13 23:48 DEBUG  CommonBackend: encoding=cp1252
07-13 23:48 DEBUG  WindowsBackend: arch=amd64
07-13 23:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\data\isolist.ini
07-13 23:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-13 23:48 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-13 23:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-13 23:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-13 23:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-13 23:48 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-13 23:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-13 23:48 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-13 23:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-13 23:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-13 23:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-13 23:48 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-13 23:48 DEBUG  WindowsBackend: Fetching host info...
07-13 23:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-13 23:48 DEBUG  WindowsBackend: windows version=vista
07-13 23:48 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-13 23:48 DEBUG  WindowsBackend: windows_sp=None
07-13 23:48 DEBUG  WindowsBackend: windows_build=7601
07-13 23:48 DEBUG  WindowsBackend: gmt=-5
07-13 23:48 DEBUG  WindowsBackend: country=US
07-13 23:48 DEBUG  WindowsBackend: timezone=America/New_York
07-13 23:48 DEBUG  WindowsBackend: windows_username=Bill
07-13 23:48 DEBUG  WindowsBackend: user_full_name=Bill
07-13 23:48 DEBUG  WindowsBackend: user_directory=C:\Users\Bill
07-13 23:48 DEBUG  WindowsBackend: windows_language_code=1033
07-13 23:48 DEBUG  WindowsBackend: windows_language=English
07-13 23:48 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-13 23:48 DEBUG  WindowsBackend: bootloader=vista
07-13 23:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 123731.613281 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: drive=Drive(C: hd 123731.613281 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: drive=Drive(D: hd 1877.453125 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-13 23:48 DEBUG  WindowsBackend: drive=Drive(F: hd 105242.226563 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: drive=Drive(G: hd 67593.9492188 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-13 23:48 DEBUG  WindowsBackend: drive=Drive(I: hd 63456.4140625 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: uninstaller_path=I:\ubuntu\uninstall-wubi.exe
07-13 23:48 DEBUG  WindowsBackend: previous_target_dir=I:\ubuntu
07-13 23:48 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-13 23:48 DEBUG  WindowsBackend: keyboard_id=67699721
07-13 23:48 DEBUG  WindowsBackend: keyboard_layout=us
07-13 23:48 DEBUG  WindowsBackend: keyboard_variant=
07-13 23:48 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-13 23:48 DEBUG  CommonBackend: locale=en_US.UTF-8
07-13 23:48 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-13 23:48 DEBUG  CommonBackend: Searching ISOs on USB devices
07-13 23:48 DEBUG  Distro:   checking Ubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Ubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Kubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Kubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Xubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Xubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Mythbuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Mythbuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Edubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Edubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Lubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Lubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Ubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Ubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Kubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Kubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Xubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Xubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Mythbuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Mythbuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Edubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Edubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Lubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Lubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  CommonBackend: Searching for local CDs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 INFO   root: Already installed, running the uninstaller...
07-13 23:48 INFO   root: Running the uninstaller...
07-13 23:48 INFO   CommonBackend: This is the uninstaller running
07-13 23:48 DEBUG  WindowsFrontend: __init__...
07-13 23:48 DEBUG  WindowsFrontend: on_init...
07-13 23:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\translations, languages=['en_US', 'en']
07-13 23:48 INFO   root: Received settings
07-13 23:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\translations, languages=['en_US', 'en']
07-13 23:48 DEBUG  TaskList: # Running tasklist...
07-13 23:48 DEBUG  TaskList: ## Running Remove bootloader entry...
07-13 23:48 DEBUG  WindowsBackend: Could not find bcd id
07-13 23:48 DEBUG  WindowsBackend: undo_bootini C:
07-13 23:48 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 123731.613281 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: undo_bootini D:
07-13 23:48 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1877.453125 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: undo_bootini F:
07-13 23:48 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 105242.226563 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: undo_bootini G:
07-13 23:48 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 67593.9492188 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: undo_bootini I:
07-13 23:48 DEBUG  WindowsBackend: undo_configsys Drive(I: hd 63456.4140625 mb free ntfs)
07-13 23:48 DEBUG  TaskList: ## Finished Remove bootloader entry
07-13 23:48 DEBUG  TaskList: ## Running Remove target dir...
07-13 23:48 DEBUG  CommonBackend: Deleting I:\ubuntu
07-13 23:48 DEBUG  TaskList: ## Finished Remove target dir
07-13 23:48 DEBUG  TaskList: ## Running Remove registry key...
07-13 23:48 DEBUG  TaskList: ## Finished Remove registry key
07-13 23:48 DEBUG  TaskList: # Finished tasklist
07-13 23:48 INFO   root: Almost finished uninstalling
07-13 23:48 INFO   root: Finished uninstallation
07-13 23:48 DEBUG  CommonBackend: Fetching basic info...
07-13 23:48 DEBUG  CommonBackend: original_exe=C:\Users\Bill\Downloads\wubi.exe
07-13 23:48 DEBUG  CommonBackend: platform=win32
07-13 23:48 DEBUG  CommonBackend: osname=nt
07-13 23:48 DEBUG  WindowsBackend: arch=amd64
07-13 23:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\data\isolist.ini
07-13 23:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-13 23:48 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-13 23:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-13 23:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-13 23:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-13 23:48 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-13 23:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-13 23:48 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-13 23:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-13 23:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-13 23:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-13 23:48 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-13 23:48 DEBUG  WindowsBackend: Fetching host info...
07-13 23:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-13 23:48 DEBUG  WindowsBackend: windows version=vista
07-13 23:48 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-13 23:48 DEBUG  WindowsBackend: windows_sp=None
07-13 23:48 DEBUG  WindowsBackend: windows_build=7601
07-13 23:48 DEBUG  WindowsBackend: gmt=-5
07-13 23:48 DEBUG  WindowsBackend: country=US
07-13 23:48 DEBUG  WindowsBackend: timezone=America/New_York
07-13 23:48 DEBUG  WindowsBackend: windows_username=Bill
07-13 23:48 DEBUG  WindowsBackend: user_full_name=Bill
07-13 23:48 DEBUG  WindowsBackend: user_directory=C:\Users\Bill
07-13 23:48 DEBUG  WindowsBackend: windows_language_code=1033
07-13 23:48 DEBUG  WindowsBackend: windows_language=English
07-13 23:48 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-13 23:48 DEBUG  WindowsBackend: bootloader=vista
07-13 23:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 123722.894531 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: drive=Drive(C: hd 123722.894531 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: drive=Drive(D: hd 1877.453125 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-13 23:48 DEBUG  WindowsBackend: drive=Drive(F: hd 105242.226563 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: drive=Drive(G: hd 67593.9492188 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-13 23:48 DEBUG  WindowsBackend: drive=Drive(I: hd 64833.96875 mb free ntfs)
07-13 23:48 DEBUG  WindowsBackend: uninstaller_path=None
07-13 23:48 DEBUG  WindowsBackend: previous_target_dir=None
07-13 23:48 DEBUG  WindowsBackend: previous_distro_name=None
07-13 23:48 DEBUG  WindowsBackend: keyboard_id=67699721
07-13 23:48 DEBUG  WindowsBackend: keyboard_layout=us
07-13 23:48 DEBUG  WindowsBackend: keyboard_variant=
07-13 23:48 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-13 23:48 DEBUG  CommonBackend: Searching ISOs on USB devices
07-13 23:48 DEBUG  Distro:   checking Ubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Ubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Kubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Kubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Xubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Xubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Mythbuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Mythbuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Edubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Edubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Lubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Lubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Ubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Ubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Kubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Kubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Xubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Xubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Mythbuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Mythbuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Edubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Edubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Lubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking Lubuntu ISO G:\Practice Sets fo.iso
07-13 23:48 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-13 23:48 DEBUG  CommonBackend: Searching for local CDs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-13 23:48 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-13 23:48 INFO   root: Running the installer...
07-13 23:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\translations, languages=['en_US', 'en']
07-13 23:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Bill\AppData\Local\Temp\pyl8046.tmp\translations, languages=['en_US', 'en']
07-14 00:10 INFO   WindowsFrontend: Operation cancelled
07-14 00:10 DEBUG  WindowsFrontend: frontend.quit
07-14 00:10 DEBUG  WindowsFrontend: frontend.on_quit
07-14 00:10 DEBUG  root: application.on_quit
07-14 00:10 INFO   root: sys.exit
07-14 00:27 INFO   root: === wubi 12.04 rev266 ===
07-14 00:27 DEBUG  root: Logfile is c:\users\bill\appdata\local\temp\wubi-12.04-rev266.log
07-14 00:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Bill\\Downloads\\wubi.exe"']
07-14 00:27 DEBUG  CommonBackend: data_dir=C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\data
07-14 00:27 DEBUG  WindowsBackend: 7z=C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\bin\7z.exe
07-14 00:27 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-14 00:27 DEBUG  CommonBackend: Fetching basic info...
07-14 00:27 DEBUG  CommonBackend: original_exe=C:\Users\Bill\Downloads\wubi.exe
07-14 00:27 DEBUG  CommonBackend: platform=win32
07-14 00:27 DEBUG  CommonBackend: osname=nt
07-14 00:27 DEBUG  CommonBackend: language=en_US
07-14 00:27 DEBUG  CommonBackend: encoding=cp1252
07-14 00:27 DEBUG  WindowsBackend: arch=amd64
07-14 00:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\data\isolist.ini
07-14 00:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-14 00:27 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
07-14 00:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-14 00:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-14 00:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-14 00:27 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
07-14 00:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-14 00:27 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
07-14 00:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-14 00:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-14 00:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-14 00:27 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
07-14 00:27 DEBUG  WindowsBackend: Fetching host info...
07-14 00:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-14 00:27 DEBUG  WindowsBackend: windows version=vista
07-14 00:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-14 00:27 DEBUG  WindowsBackend: windows_sp=None
07-14 00:27 DEBUG  WindowsBackend: windows_build=7601
07-14 00:27 DEBUG  WindowsBackend: gmt=-5
07-14 00:27 DEBUG  WindowsBackend: country=US
07-14 00:27 DEBUG  WindowsBackend: timezone=America/New_York
07-14 00:27 DEBUG  WindowsBackend: windows_username=Bill
07-14 00:27 DEBUG  WindowsBackend: user_full_name=Bill
07-14 00:27 DEBUG  WindowsBackend: user_directory=C:\Users\Bill
07-14 00:27 DEBUG  WindowsBackend: windows_language_code=1033
07-14 00:27 DEBUG  WindowsBackend: windows_language=English
07-14 00:27 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
07-14 00:27 DEBUG  WindowsBackend: bootloader=vista
07-14 00:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 129284.136719 mb free ntfs)
07-14 00:27 DEBUG  WindowsBackend: drive=Drive(C: hd 129284.136719 mb free ntfs)
07-14 00:27 DEBUG  WindowsBackend: drive=Drive(D: hd 1877.453125 mb free ntfs)
07-14 00:27 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-14 00:27 DEBUG  WindowsBackend: drive=Drive(F: hd 105242.226563 mb free ntfs)
07-14 00:27 DEBUG  WindowsBackend: drive=Drive(G: hd 67593.9492188 mb free ntfs)
07-14 00:27 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-14 00:27 DEBUG  WindowsBackend: drive=Drive(I: hd 64833.96875 mb free ntfs)
07-14 00:27 DEBUG  WindowsBackend: uninstaller_path=None
07-14 00:27 DEBUG  WindowsBackend: previous_target_dir=None
07-14 00:27 DEBUG  WindowsBackend: previous_distro_name=None
07-14 00:27 DEBUG  WindowsBackend: keyboard_id=67699721
07-14 00:27 DEBUG  WindowsBackend: keyboard_layout=us
07-14 00:27 DEBUG  WindowsBackend: keyboard_variant=
07-14 00:27 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-14 00:27 DEBUG  CommonBackend: locale=en_US.UTF-8
07-14 00:27 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-14 00:27 DEBUG  CommonBackend: Searching ISOs on USB devices
07-14 00:27 DEBUG  Distro:   checking Ubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Ubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Kubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Kubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Xubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Xubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Mythbuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Mythbuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Edubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Edubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Lubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Lubuntu ISO G:\7601.17514.101119-1850_x64fre_server_eval_en-us-GRMSXEVAL_EN_DVD.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Ubuntu ISO G:\Practice Sets fo.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Ubuntu ISO G:\Practice Sets fo.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Kubuntu ISO G:\Practice Sets fo.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Kubuntu ISO G:\Practice Sets fo.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Xubuntu ISO G:\Practice Sets fo.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Xubuntu ISO G:\Practice Sets fo.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Mythbuntu ISO G:\Practice Sets fo.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Mythbuntu ISO G:\Practice Sets fo.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Edubuntu ISO G:\Practice Sets fo.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Edubuntu ISO G:\Practice Sets fo.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Lubuntu ISO G:\Practice Sets fo.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking Lubuntu ISO G:\Practice Sets fo.iso
07-14 00:27 DEBUG  Distro:     does not contain casper\filesystem.squashfs
07-14 00:27 DEBUG  CommonBackend: Searching for local CDs
07-14 00:27 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp is a valid Ubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp is a valid Ubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp is a valid Kubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp is a valid Kubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp is a valid Xubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp is a valid Xubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp is a valid Mythbuntu CD
07-14 00:27 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp is a valid Mythbuntu CD
07-14 00:27 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp is a valid Edubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp is a valid Edubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp is a valid Lubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp is a valid Lubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-14 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-14 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-14 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-14 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-14 00:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-14 00:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-14 00:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-14 00:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-14 00:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-14 00:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-14 00:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-14 00:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether I:\ is a valid Edubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-14 00:27 DEBUG  Distro:   checking whether I:\ is a valid Lubuntu CD
07-14 00:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-14 00:27 INFO   root: Running the installer...
07-14 00:27 DEBUG  WindowsFrontend: __init__...
07-14 00:27 DEBUG  WindowsFrontend: on_init...
07-14 00:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\translations, languages=['en_US', 'en']
07-14 00:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\translations, languages=['en_US', 'en']
07-14 00:28 DEBUG  WinuiInstallationPage: target_drive=I:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=bill
07-14 00:28 INFO   root: Received settings
07-14 00:28 DEBUG  CommonBackend: Searching for local CD
07-14 00:28 DEBUG  Distro:   checking whether C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp is a valid Ubuntu CD
07-14 00:28 DEBUG  Distro:     does not contain C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\casper\filesystem.squashfs
07-14 00:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-14 00:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-14 00:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-14 00:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-14 00:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-14 00:28 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-14 00:28 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-14 00:28 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-14 00:28 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-14 00:28 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-14 00:28 DEBUG  CommonBackend: Searching for local ISO
07-14 00:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Bill\AppData\Local\Temp\pyl4662.tmp\translations, languages=['en_US', 'en']
07-14 00:28 DEBUG  TaskList: # Running tasklist...
07-14 00:28 DEBUG  TaskList: ## Running select_target_dir...
07-14 00:28 INFO   WindowsBackend: Installing into I:\ubuntu
07-14 00:28 DEBUG  TaskList: ## Finished select_target_dir
07-14 00:28 DEBUG  TaskList: ## Running create_dir_structure...
07-14 00:28 DEBUG  CommonBackend: Creating dir I:\ubuntu
07-14 00:28 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks
07-14 00:28 DEBUG  CommonBackend: Creating dir I:\ubuntu\install
07-14 00:28 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot
07-14 00:28 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot
07-14 00:28 DEBUG  CommonBackend: Creating dir I:\ubuntu\disks\boot\grub
07-14 00:28 DEBUG  CommonBackend: Creating dir I:\ubuntu\install\boot\grub
07-14 00:28 DEBUG  TaskList: ## Finished create_dir_structure
07-14 00:28 DEBUG  TaskList: ## Running create_uninstaller...
07-14 00:28 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Bill\Downloads\wubi.exe -> I:\ubuntu\uninstall-wubi.exe
07-14 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString I:\ubuntu\uninstall-wubi.exe
07-14 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir I:\ubuntu
07-14 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-14 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon I:\ubuntu\Ubuntu.ico
07-14 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev266
07-14 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-14 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-14 00:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-14 00:28 DEBUG  TaskList: ## Finished create_uninstaller
07-14 00:28 DEBUG  TaskList: ## Running create_preseed_diskimage...
07-14 00:28 DEBUG  TaskList: ## Finished create_preseed_diskimage
07-14 00:28 DEBUG  TaskList: ## Running get_diskimage...
07-14 00:28 DEBUG  TaskList: New task download
07-14 00:28 DEBUG  TaskList: ### Running download...
07-14 00:28 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04/ubuntu-12.04-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04/ubuntu-12.04-wubi-amd64.tar.xz) > I:\ubuntu\disks\ubuntu-12.04-wubi-amd64.tar.xz
07-14 00:28 DEBUG  downloader: Download start filename=I:\ubuntu\disks\ubuntu-12.04-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04/ubuntu-12.04-wubi-amd64.tar.xz, basename=ubuntu-12.04-wubi-amd64.tar.xz, length=512730488, text=None
07-14 00:36 DEBUG  TaskList: ### Finished download
07-14 00:36 DEBUG  downloader: download finished (read 512730488 bytes)
07-14 00:36 DEBUG  TaskList: ## Finished get_diskimage
07-14 00:36 DEBUG  TaskList: ## Running extract_diskimage...
07-14 00:39 DEBUG  TaskList: ## Finished extract_diskimage
07-14 00:39 DEBUG  TaskList: ## Running choose_disk_sizes...
07-14 00:39 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
07-14 00:39 DEBUG  TaskList: ## Finished choose_disk_sizes
07-14 00:39 DEBUG  TaskList: ## Running expand_diskimage...
07-14 00:40 DEBUG  TaskList: ## Finished expand_diskimage
07-14 00:40 DEBUG  TaskList: ## Running create_swap_diskimage...
07-14 00:40 DEBUG  TaskList: ## Finished create_swap_diskimage
07-14 00:40 DEBUG  TaskList: ## Running modify_bootloader...
07-14 00:40 DEBUG  TaskList: New task modify_bcd
07-14 00:40 DEBUG  TaskList: ### Running modify_bcd...
07-14 00:40 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 129284.136719 mb free ntfs)
07-14 00:40 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {84cb243e-fe9d-11e0-9d9a-b55cb4610dfe} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {84cb243e-fe9d-11e0-9d9a-b55cb4610dfe} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
07-14 00:40 DEBUG  TaskList: # Cancelling tasklist
07-14 00:40 DEBUG  TaskList: New task modify_bcd
07-14 00:40 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {84cb243e-fe9d-11e0-9d9a-b55cb4610dfe} device partition=I:
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
>>command=C:\Windows\sysnative\bcdedit.exe /set {84cb243e-fe9d-11e0-9d9a-b55cb4610dfe} device partition=I:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
07-14 00:40 DEBUG  TaskList: New task modify_bcd
07-14 00:40 DEBUG  TaskList: New task modify_bcd
07-14 00:40 DEBUG  TaskList: New task modify_bcd
07-14 00:40 DEBUG  TaskList: ## Finished modify_bootloader
07-14 00:40 DEBUG  TaskList: # Finished tasklist


---

