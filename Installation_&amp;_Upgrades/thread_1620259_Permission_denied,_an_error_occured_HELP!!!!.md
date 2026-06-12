---
title: "Permission denied, an error occured HELP!!!!"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by cook 321 on 2010-11-12
eeeeeeek!! When I was Installing Ubuntu inside Windows,using wubi, the installer failed and an error message popped out, saying 
"An error occurred:

Permission denied

For more information, please see the log file:
C:\Users\Koo Jie Hui\AppData\Local\Temp\wubi-10.10-rev197.log

so here is the log file.... (its a bit long... I don't know which parts to extract so I took out everything..... but the last part should hold all the answers... XD)




"11-11 14:38 INFO   root: === wubi 10.10 rev197 ===
11-11 14:38 DEBUG  root: Logfile is c:\users\koojie~1\appdata\local\temp\wubi-10.10-rev197.log
11-11 14:38 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-11 14:38 DEBUG  CommonBackend: data_dir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp\data
11-11 14:38 DEBUG  WindowsBackend: 7z=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp\bin\7z.exe
11-11 14:38 DEBUG  CommonBackend: Fetching basic info...
11-11 14:38 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-11 14:38 DEBUG  CommonBackend: platform=win32
11-11 14:38 DEBUG  CommonBackend: osname=nt
11-11 14:38 DEBUG  CommonBackend: language=en_SG
11-11 14:38 DEBUG  CommonBackend: encoding=cp1252
11-11 14:38 DEBUG  WindowsBackend: arch=amd64
11-11 14:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp\data\isolist.ini
11-11 14:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-11 14:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-11 14:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-11 14:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-11 14:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-11 14:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-11 14:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-11 14:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-11 14:38 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-11 14:38 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-11 14:38 DEBUG  WindowsBackend: Fetching host info...
11-11 14:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-11 14:38 DEBUG  WindowsBackend: windows version=vista
11-11 14:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Enterprise
11-11 14:38 DEBUG  WindowsBackend: windows_sp=None
11-11 14:38 DEBUG  WindowsBackend: windows_build=7600
11-11 14:38 DEBUG  WindowsBackend: gmt=8
11-11 14:38 DEBUG  WindowsBackend: country=SG
11-11 14:38 DEBUG  WindowsBackend: timezone=Asia/Singapore
11-11 14:38 DEBUG  WindowsBackend: windows_username=Koo Jie Hui
11-11 14:38 DEBUG  WindowsBackend: user_full_name=Koo Jie Hui
11-11 14:38 DEBUG  WindowsBackend: user_directory=C:\Users\Koo Jie Hui
11-11 14:38 DEBUG  WindowsBackend: windows_language_code=1033
11-11 14:38 DEBUG  WindowsBackend: windows_language=English
11-11 14:38 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
11-11 14:38 DEBUG  WindowsBackend: bootloader=vista
11-11 14:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 95590.2734375 mb free ntfs)
11-11 14:38 DEBUG  WindowsBackend: drive=Drive(C: hd 95590.2734375 mb free ntfs)
11-11 14:38 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-11 14:38 DEBUG  WindowsBackend: drive=Drive(F: hd 228240.300781 mb free ntfs)
11-11 14:38 DEBUG  WindowsBackend: drive=Drive(G: hd 15437.9765625 mb free fat32)
11-11 14:38 DEBUG  WindowsBackend: drive=Drive(H: hd 24841.125 mb free exfat)
11-11 14:38 DEBUG  WindowsBackend: drive=Drive(I: hd 20378.1445313 mb free ntfs)
11-11 14:38 DEBUG  WindowsBackend: uninstaller_path=None
11-11 14:38 DEBUG  WindowsBackend: previous_target_dir=None
11-11 14:38 DEBUG  WindowsBackend: previous_distro_name=None
11-11 14:38 DEBUG  WindowsBackend: keyboard_id=67699721
11-11 14:38 DEBUG  WindowsBackend: keyboard_layout=us
11-11 14:38 DEBUG  WindowsBackend: keyboard_variant=
11-11 14:38 DEBUG  CommonBackend: python locale=('en_SG', 'cp1252')
11-11 14:38 DEBUG  CommonBackend: locale=en_SG.UTF-8
11-11 14:38 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
11-11 14:38 DEBUG  CommonBackend: Searching ISOs on USB devices
11-11 14:38 DEBUG  Distro:   checking Ubuntu ISO H:\ubuntu-10.10-desktop-i386.iso
11-11 14:38 DEBUG  WindowsBackend:   extracting .disk\info from H:\ubuntu-10.10-desktop-i386.iso
11-11 14:38 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-11 14:38 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-11 14:38 INFO   Distro: Found a valid iso for Ubuntu: H:\ubuntu-10.10-desktop-i386.iso
11-11 14:38 DEBUG  CommonBackend: Searching for local CDs
11-11 14:38 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp is a valid Ubuntu CD
11-11 14:38 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp\casper\filesystem.squashfs
11-11 14:38 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp is a valid Ubuntu CD
11-11 14:38 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp\casper\filesystem.squashfs
11-11 14:38 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp is a valid Ubuntu Netbook CD
11-11 14:38 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp\casper\filesystem.squashfs
11-11 14:38 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp is a valid Kubuntu CD
11-11 14:38 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp\casper\filesystem.squashfs
11-11 14:38 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp is a valid Kubuntu CD
11-11 14:38 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp\casper\filesystem.squashfs
11-11 14:38 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp is a valid Kubuntu Netbook CD
11-11 14:38 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp\casper\filesystem.squashfs
11-11 14:38 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp is a valid Xubuntu CD
11-11 14:38 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp\casper\filesystem.squashfs
11-11 14:38 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp is a valid Xubuntu CD
11-11 14:38 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp\casper\filesystem.squashfs
11-11 14:38 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp is a valid Mythbuntu CD
11-11 14:38 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp\casper\filesystem.squashfs
11-11 14:38 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp is a valid Mythbuntu CD
11-11 14:38 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp\casper\filesystem.squashfs
11-11 14:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-11 14:38 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-11 14:38 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-11 14:38 INFO   Distro: Found a valid CD for Ubuntu: D:\
11-11 14:38 INFO   root: Running the CD menu...
11-11 14:38 DEBUG  WindowsFrontend: __init__...
11-11 14:38 DEBUG  WindowsFrontend: on_init...
11-11 14:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp\translations, languages=['en_SG', 'en']
11-11 14:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl15E4.tmp\translations, languages=['en_SG', 'en']
11-11 14:38 INFO   root: CD menu finished
11-11 14:38 INFO   root: Rebooting
11-11 14:38 DEBUG  TaskList: # Running tasklist...
11-11 14:38 DEBUG  TaskList: ## Running reboot...
11-11 14:38 DEBUG  TaskList: ## Finished reboot
11-11 14:38 DEBUG  TaskList: # Finished tasklist
11-11 14:38 DEBUG  root: application.quit
11-11 14:38 DEBUG  WindowsFrontend: frontend.quit
11-11 14:38 DEBUG  WindowsFrontend: frontend.on_quit
11-11 14:38 DEBUG  root: application.on_quit
11-11 14:38 INFO   root: sys.exit
11-11 14:54 INFO   root: === wubi 10.10 rev197 ===
11-11 14:54 DEBUG  root: Logfile is c:\users\koojie~1\appdata\local\temp\wubi-10.10-rev197.log
11-11 14:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-11 14:54 DEBUG  CommonBackend: data_dir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp\data
11-11 14:54 DEBUG  WindowsBackend: 7z=C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp\bin\7z.exe
11-11 14:54 DEBUG  CommonBackend: Fetching basic info...
11-11 14:54 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-11 14:54 DEBUG  CommonBackend: platform=win32
11-11 14:54 DEBUG  CommonBackend: osname=nt
11-11 14:54 DEBUG  CommonBackend: language=en_SG
11-11 14:54 DEBUG  CommonBackend: encoding=cp1252
11-11 14:54 DEBUG  WindowsBackend: arch=amd64
11-11 14:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp\data\isolist.ini
11-11 14:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-11 14:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-11 14:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-11 14:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-11 14:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-11 14:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-11 14:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-11 14:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-11 14:54 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-11 14:54 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-11 14:54 DEBUG  WindowsBackend: Fetching host info...
11-11 14:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-11 14:54 DEBUG  WindowsBackend: windows version=vista
11-11 14:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Enterprise
11-11 14:54 DEBUG  WindowsBackend: windows_sp=None
11-11 14:54 DEBUG  WindowsBackend: windows_build=7600
11-11 14:54 DEBUG  WindowsBackend: gmt=8
11-11 14:54 DEBUG  WindowsBackend: country=SG
11-11 14:54 DEBUG  WindowsBackend: timezone=Asia/Singapore
11-11 14:54 DEBUG  WindowsBackend: windows_username=Koo Jie Hui
11-11 14:54 DEBUG  WindowsBackend: user_full_name=Koo Jie Hui
11-11 14:54 DEBUG  WindowsBackend: user_directory=C:\Users\Koo Jie Hui
11-11 14:54 DEBUG  WindowsBackend: windows_language_code=1033
11-11 14:54 DEBUG  WindowsBackend: windows_language=English
11-11 14:54 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
11-11 14:54 DEBUG  WindowsBackend: bootloader=vista
11-11 14:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 95591.4882813 mb free ntfs)
11-11 14:54 DEBUG  WindowsBackend: drive=Drive(C: hd 95591.4882813 mb free ntfs)
11-11 14:54 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-11 14:54 DEBUG  WindowsBackend: drive=Drive(F: hd 228240.300781 mb free ntfs)
11-11 14:54 DEBUG  WindowsBackend: drive=Drive(G: hd 15437.9765625 mb free fat32)
11-11 14:54 DEBUG  WindowsBackend: drive=Drive(H: hd 24841.125 mb free exfat)
11-11 14:54 DEBUG  WindowsBackend: drive=Drive(I: hd 20378.6210938 mb free ntfs)
11-11 14:54 DEBUG  WindowsBackend: uninstaller_path=None
11-11 14:54 DEBUG  WindowsBackend: previous_target_dir=None
11-11 14:54 DEBUG  WindowsBackend: previous_distro_name=None
11-11 14:54 DEBUG  WindowsBackend: keyboard_id=67699721
11-11 14:54 DEBUG  WindowsBackend: keyboard_layout=us
11-11 14:54 DEBUG  WindowsBackend: keyboard_variant=
11-11 14:54 DEBUG  CommonBackend: python locale=('en_SG', 'cp1252')
11-11 14:54 DEBUG  CommonBackend: locale=en_SG.UTF-8
11-11 14:54 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
11-11 14:54 DEBUG  CommonBackend: Searching ISOs on USB devices
11-11 14:54 DEBUG  Distro:   checking Ubuntu ISO H:\ubuntu-10.10-desktop-i386.iso
11-11 14:54 DEBUG  WindowsBackend:   extracting .disk\info from H:\ubuntu-10.10-desktop-i386.iso
11-11 14:54 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-11 14:54 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-11 14:54 INFO   Distro: Found a valid iso for Ubuntu: H:\ubuntu-10.10-desktop-i386.iso
11-11 14:54 DEBUG  CommonBackend: Searching for local CDs
11-11 14:54 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp is a valid Ubuntu CD
11-11 14:54 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp\casper\filesystem.squashfs
11-11 14:54 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp is a valid Ubuntu CD
11-11 14:54 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp\casper\filesystem.squashfs
11-11 14:54 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp is a valid Ubuntu Netbook CD
11-11 14:54 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp\casper\filesystem.squashfs
11-11 14:54 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp is a valid Kubuntu CD
11-11 14:54 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp\casper\filesystem.squashfs
11-11 14:54 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp is a valid Kubuntu CD
11-11 14:54 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp\casper\filesystem.squashfs
11-11 14:54 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp is a valid Kubuntu Netbook CD
11-11 14:54 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp\casper\filesystem.squashfs
11-11 14:54 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp is a valid Xubuntu CD
11-11 14:54 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp\casper\filesystem.squashfs
11-11 14:54 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp is a valid Xubuntu CD
11-11 14:54 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp\casper\filesystem.squashfs
11-11 14:54 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp is a valid Mythbuntu CD
11-11 14:54 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp\casper\filesystem.squashfs
11-11 14:54 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp is a valid Mythbuntu CD
11-11 14:54 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp\casper\filesystem.squashfs
11-11 14:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-11 14:54 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-11 14:54 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-11 14:54 INFO   Distro: Found a valid CD for Ubuntu: D:\
11-11 14:54 INFO   root: Running the CD menu...
11-11 14:54 DEBUG  WindowsFrontend: __init__...
11-11 14:54 DEBUG  WindowsFrontend: on_init...
11-11 14:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp\translations, languages=['en_SG', 'en']
11-11 14:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylC8E9.tmp\translations, languages=['en_SG', 'en']
11-11 14:57 INFO   WindowsFrontend: Operation cancelled
11-11 14:57 DEBUG  WindowsFrontend: frontend.quit
11-11 14:57 DEBUG  WindowsFrontend: frontend.on_quit
11-11 14:57 DEBUG  root: application.on_quit
11-11 14:57 INFO   root: sys.exit
11-11 14:58 INFO   root: === wubi 10.10 rev197 ===
11-11 14:58 DEBUG  root: Logfile is c:\users\koojie~1\appdata\local\temp\wubi-10.10-rev197.log
11-11 14:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-11 14:58 DEBUG  CommonBackend: data_dir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\data
11-11 14:58 DEBUG  WindowsBackend: 7z=C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\bin\7z.exe
11-11 14:58 DEBUG  CommonBackend: Fetching basic info...
11-11 14:58 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-11 14:58 DEBUG  CommonBackend: platform=win32
11-11 14:58 DEBUG  CommonBackend: osname=nt
11-11 14:58 DEBUG  CommonBackend: language=en_SG
11-11 14:58 DEBUG  CommonBackend: encoding=cp1252
11-11 14:58 DEBUG  WindowsBackend: arch=amd64
11-11 14:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\data\isolist.ini
11-11 14:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-11 14:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-11 14:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-11 14:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-11 14:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-11 14:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-11 14:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-11 14:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-11 14:58 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-11 14:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-11 14:58 DEBUG  WindowsBackend: Fetching host info...
11-11 14:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-11 14:58 DEBUG  WindowsBackend: windows version=vista
11-11 14:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Enterprise
11-11 14:58 DEBUG  WindowsBackend: windows_sp=None
11-11 14:58 DEBUG  WindowsBackend: windows_build=7600
11-11 14:58 DEBUG  WindowsBackend: gmt=8
11-11 14:58 DEBUG  WindowsBackend: country=SG
11-11 14:58 DEBUG  WindowsBackend: timezone=Asia/Singapore
11-11 14:58 DEBUG  WindowsBackend: windows_username=Koo Jie Hui
11-11 14:58 DEBUG  WindowsBackend: user_full_name=Koo Jie Hui
11-11 14:58 DEBUG  WindowsBackend: user_directory=C:\Users\Koo Jie Hui
11-11 14:58 DEBUG  WindowsBackend: windows_language_code=1033
11-11 14:58 DEBUG  WindowsBackend: windows_language=English
11-11 14:58 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
11-11 14:58 DEBUG  WindowsBackend: bootloader=vista
11-11 14:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 95559.25 mb free ntfs)
11-11 14:58 DEBUG  WindowsBackend: drive=Drive(C: hd 95559.25 mb free ntfs)
11-11 14:58 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-11 14:58 DEBUG  WindowsBackend: drive=Drive(F: hd 228240.300781 mb free ntfs)
11-11 14:58 DEBUG  WindowsBackend: drive=Drive(G: hd 15437.9765625 mb free fat32)
11-11 14:58 DEBUG  WindowsBackend: drive=Drive(H: hd 24841.125 mb free exfat)
11-11 14:58 DEBUG  WindowsBackend: drive=Drive(I: hd 20378.6210938 mb free ntfs)
11-11 14:58 DEBUG  WindowsBackend: uninstaller_path=None
11-11 14:58 DEBUG  WindowsBackend: previous_target_dir=None
11-11 14:58 DEBUG  WindowsBackend: previous_distro_name=None
11-11 14:58 DEBUG  WindowsBackend: keyboard_id=67699721
11-11 14:58 DEBUG  WindowsBackend: keyboard_layout=us
11-11 14:58 DEBUG  WindowsBackend: keyboard_variant=
11-11 14:58 DEBUG  CommonBackend: python locale=('en_SG', 'cp1252')
11-11 14:58 DEBUG  CommonBackend: locale=en_SG.UTF-8
11-11 14:58 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
11-11 14:58 DEBUG  CommonBackend: Searching ISOs on USB devices
11-11 14:58 DEBUG  Distro:   checking Ubuntu ISO H:\ubuntu-10.10-desktop-i386.iso
11-11 14:58 DEBUG  WindowsBackend:   extracting .disk\info from H:\ubuntu-10.10-desktop-i386.iso
11-11 14:58 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-11 14:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-11 14:58 INFO   Distro: Found a valid iso for Ubuntu: H:\ubuntu-10.10-desktop-i386.iso
11-11 14:58 DEBUG  CommonBackend: Searching for local CDs
11-11 14:58 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp is a valid Ubuntu CD
11-11 14:58 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\casper\filesystem.squashfs
11-11 14:58 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp is a valid Ubuntu CD
11-11 14:58 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\casper\filesystem.squashfs
11-11 14:58 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp is a valid Ubuntu Netbook CD
11-11 14:58 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\casper\filesystem.squashfs
11-11 14:58 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp is a valid Kubuntu CD
11-11 14:58 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\casper\filesystem.squashfs
11-11 14:58 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp is a valid Kubuntu CD
11-11 14:58 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\casper\filesystem.squashfs
11-11 14:58 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp is a valid Kubuntu Netbook CD
11-11 14:58 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\casper\filesystem.squashfs
11-11 14:58 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp is a valid Xubuntu CD
11-11 14:58 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\casper\filesystem.squashfs
11-11 14:58 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp is a valid Xubuntu CD
11-11 14:58 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\casper\filesystem.squashfs
11-11 14:58 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp is a valid Mythbuntu CD
11-11 14:58 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\casper\filesystem.squashfs
11-11 14:58 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp is a valid Mythbuntu CD
11-11 14:58 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\casper\filesystem.squashfs
11-11 14:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-11 14:58 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-11 14:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-11 14:58 INFO   Distro: Found a valid CD for Ubuntu: D:\
11-11 14:58 INFO   root: Running the CD menu...
11-11 14:58 DEBUG  WindowsFrontend: __init__...
11-11 14:58 DEBUG  WindowsFrontend: on_init...
11-11 14:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\translations, languages=['en_SG', 'en']
11-11 14:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\translations, languages=['en_SG', 'en']
11-11 14:58 INFO   root: CD menu finished
11-11 14:58 INFO   root: Running the installer...
11-11 14:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\translations, languages=['en_SG', 'en']
11-11 14:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylF6DC.tmp\translations, languages=['en_SG', 'en']
11-11 14:58 INFO   WindowsFrontend: Operation cancelled
11-11 14:58 DEBUG  WindowsFrontend: frontend.quit
11-11 14:58 DEBUG  WindowsFrontend: frontend.on_quit
11-11 14:58 DEBUG  root: application.on_quit
11-11 14:58 INFO   root: sys.exit
11-11 14:59 INFO   root: === wubi 10.10 rev197 ===
11-11 14:59 DEBUG  root: Logfile is c:\users\koojie~1\appdata\local\temp\wubi-10.10-rev197.log
11-11 14:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-11 14:59 DEBUG  CommonBackend: data_dir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\data
11-11 14:59 DEBUG  WindowsBackend: 7z=C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\bin\7z.exe
11-11 14:59 DEBUG  CommonBackend: Fetching basic info...
11-11 14:59 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-11 14:59 DEBUG  CommonBackend: platform=win32
11-11 14:59 DEBUG  CommonBackend: osname=nt
11-11 14:59 DEBUG  CommonBackend: language=en_SG
11-11 14:59 DEBUG  CommonBackend: encoding=cp1252
11-11 14:59 DEBUG  WindowsBackend: arch=amd64
11-11 14:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\data\isolist.ini
11-11 14:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-11 14:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-11 14:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-11 14:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-11 14:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-11 14:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-11 14:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-11 14:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-11 14:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-11 14:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-11 14:59 DEBUG  WindowsBackend: Fetching host info...
11-11 14:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-11 14:59 DEBUG  WindowsBackend: windows version=vista
11-11 14:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Enterprise
11-11 14:59 DEBUG  WindowsBackend: windows_sp=None
11-11 14:59 DEBUG  WindowsBackend: windows_build=7600
11-11 14:59 DEBUG  WindowsBackend: gmt=8
11-11 14:59 DEBUG  WindowsBackend: country=SG
11-11 14:59 DEBUG  WindowsBackend: timezone=Asia/Singapore
11-11 14:59 DEBUG  WindowsBackend: windows_username=Koo Jie Hui
11-11 14:59 DEBUG  WindowsBackend: user_full_name=Koo Jie Hui
11-11 14:59 DEBUG  WindowsBackend: user_directory=C:\Users\Koo Jie Hui
11-11 14:59 DEBUG  WindowsBackend: windows_language_code=1033
11-11 14:59 DEBUG  WindowsBackend: windows_language=English
11-11 14:59 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
11-11 14:59 DEBUG  WindowsBackend: bootloader=vista
11-11 14:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 95334.015625 mb free ntfs)
11-11 14:59 DEBUG  WindowsBackend: drive=Drive(C: hd 95334.015625 mb free ntfs)
11-11 14:59 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-11 14:59 DEBUG  WindowsBackend: drive=Drive(F: hd 228240.300781 mb free ntfs)
11-11 14:59 DEBUG  WindowsBackend: drive=Drive(G: hd 15437.9765625 mb free fat32)
11-11 14:59 DEBUG  WindowsBackend: drive=Drive(H: hd 24841.125 mb free exfat)
11-11 14:59 DEBUG  WindowsBackend: drive=Drive(I: hd 20378.6210938 mb free ntfs)
11-11 14:59 DEBUG  WindowsBackend: uninstaller_path=None
11-11 14:59 DEBUG  WindowsBackend: previous_target_dir=None
11-11 14:59 DEBUG  WindowsBackend: previous_distro_name=None
11-11 14:59 DEBUG  WindowsBackend: keyboard_id=67699721
11-11 14:59 DEBUG  WindowsBackend: keyboard_layout=us
11-11 14:59 DEBUG  WindowsBackend: keyboard_variant=
11-11 14:59 DEBUG  CommonBackend: python locale=('en_SG', 'cp1252')
11-11 14:59 DEBUG  CommonBackend: locale=en_SG.UTF-8
11-11 14:59 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
11-11 14:59 DEBUG  CommonBackend: Searching ISOs on USB devices
11-11 14:59 DEBUG  Distro:   checking Ubuntu ISO H:\ubuntu-10.10-desktop-i386.iso
11-11 14:59 DEBUG  WindowsBackend:   extracting .disk\info from H:\ubuntu-10.10-desktop-i386.iso
11-11 14:59 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-11 14:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-11 14:59 INFO   Distro: Found a valid iso for Ubuntu: H:\ubuntu-10.10-desktop-i386.iso
11-11 14:59 DEBUG  CommonBackend: Searching for local CDs
11-11 14:59 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp is a valid Ubuntu CD
11-11 14:59 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\casper\filesystem.squashfs
11-11 14:59 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp is a valid Ubuntu CD
11-11 14:59 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\casper\filesystem.squashfs
11-11 14:59 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp is a valid Ubuntu Netbook CD
11-11 14:59 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\casper\filesystem.squashfs
11-11 14:59 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp is a valid Kubuntu CD
11-11 14:59 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\casper\filesystem.squashfs
11-11 14:59 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp is a valid Kubuntu CD
11-11 14:59 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\casper\filesystem.squashfs
11-11 14:59 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp is a valid Kubuntu Netbook CD
11-11 14:59 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\casper\filesystem.squashfs
11-11 14:59 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp is a valid Xubuntu CD
11-11 14:59 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\casper\filesystem.squashfs
11-11 14:59 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp is a valid Xubuntu CD
11-11 14:59 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\casper\filesystem.squashfs
11-11 14:59 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp is a valid Mythbuntu CD
11-11 14:59 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\casper\filesystem.squashfs
11-11 14:59 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp is a valid Mythbuntu CD
11-11 14:59 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\casper\filesystem.squashfs
11-11 14:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-11 14:59 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-11 14:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-11 14:59 INFO   Distro: Found a valid CD for Ubuntu: D:\
11-11 14:59 INFO   root: Running the CD menu...
11-11 14:59 DEBUG  WindowsFrontend: __init__...
11-11 14:59 DEBUG  WindowsFrontend: on_init...
11-11 14:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\translations, languages=['en_SG', 'en']
11-11 14:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\translations, languages=['en_SG', 'en']
11-11 14:59 INFO   root: CD menu finished
11-11 14:59 INFO   root: Running the installer...
11-11 14:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\translations, languages=['en_SG', 'en']
11-11 14:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\translations, languages=['en_SG', 'en']
11-11 14:59 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=9000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jiehui
11-11 14:59 INFO   root: Received settings
11-11 14:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\translations, languages=['en_US', 'en']
11-11 14:59 DEBUG  TaskList: # Running tasklist...
11-11 14:59 DEBUG  TaskList: ## Running select_target_dir...
11-11 14:59 INFO   WindowsBackend: Installing into G:\ubuntu
11-11 14:59 DEBUG  TaskList: ## Finished select_target_dir
11-11 14:59 DEBUG  TaskList: ## Running create_dir_structure...
11-11 14:59 DEBUG  CommonBackend: Creating dir G:\ubuntu
11-11 14:59 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
11-11 14:59 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
11-11 14:59 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
11-11 14:59 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
11-11 14:59 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
11-11 14:59 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
11-11 14:59 DEBUG  TaskList: ## Finished create_dir_structure
11-11 14:59 DEBUG  TaskList: ## Running uncompress_target_dir...
11-11 14:59 DEBUG  TaskList: ## Finished uncompress_target_dir
11-11 14:59 DEBUG  TaskList: ## Running create_uninstaller...
11-11 14:59 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
11-11 14:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
11-11 14:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
11-11 14:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-11 14:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
11-11 14:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
11-11 14:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-11 14:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-11 14:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-11 14:59 DEBUG  TaskList: ## Finished create_uninstaller
11-11 14:59 DEBUG  TaskList: ## Running copy_installation_files...
11-11 14:59 DEBUG  WindowsBackend: Copying C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
11-11 14:59 DEBUG  WindowsBackend: Copying C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\winboot -> G:\ubuntu\winboot
11-11 14:59 DEBUG  WindowsBackend: Copying C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
11-11 14:59 DEBUG  TaskList: ## Finished copy_installation_files
11-11 14:59 DEBUG  TaskList: ## Running get_iso...
11-11 14:59 DEBUG  CommonBackend: Trying to use pre-specified ISO H:\ubuntu-10.10-desktop-i386.iso
11-11 14:59 DEBUG  TaskList: New task is_valid_iso
11-11 14:59 DEBUG  TaskList: ### Running is_valid_iso...
11-11 14:59 DEBUG  Distro:   checking Ubuntu ISO H:\ubuntu-10.10-desktop-i386.iso
11-11 14:59 INFO   Distro: Found a valid iso for Ubuntu: H:\ubuntu-10.10-desktop-i386.iso
11-11 14:59 DEBUG  TaskList: ### Finished is_valid_iso
11-11 14:59 DEBUG  TaskList: New task check_iso
11-11 14:59 DEBUG  TaskList: ### Running check_iso...
11-11 14:59 DEBUG  CommonBackend: Checking H:\ubuntu-10.10-desktop-i386.iso
11-11 14:59 DEBUG  Distro:   checking Ubuntu ISO H:\ubuntu-10.10-desktop-i386.iso
11-11 14:59 INFO   Distro: Found a valid iso for Ubuntu: H:\ubuntu-10.10-desktop-i386.iso
11-11 14:59 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
11-11 14:59 DEBUG  TaskList: New task get_metalink
11-11 14:59 DEBUG  TaskList: #### Running get_metalink...
11-11 14:59 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink) > G:\ubuntu\install
11-11 14:59 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-10.10-desktop-i386.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-i386.metalink, basename=ubuntu-10.10-desktop-i386.metalink, length=9071, text=None
11-11 14:59 DEBUG  downloader: download finished (read 9071 bytes)
11-11 14:59 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink](http://releases.ubuntu.com/10.10/MD5SUMS-metalink) > G:\ubuntu\install
11-11 14:59 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
11-11 14:59 DEBUG  downloader: download finished (read 488 bytes)
11-11 14:59 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg) > G:\ubuntu\install
11-11 14:59 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
11-11 14:59 DEBUG  downloader: download finished (read 198 bytes)
11-11 14:59 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
11-11 14:59 INFO   saplog: Checking block bindings..
11-11 14:59 INFO   saplog: Key verified successfully.
11-11 14:59 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

11-11 14:59 DEBUG  TaskList: #### Finished get_metalink
11-11 14:59 DEBUG  TaskList: New task get_file_md5
11-11 14:59 DEBUG  TaskList: #### Running get_file_md5...
11-11 14:59 DEBUG  TaskList: #### Finished get_file_md5
11-11 14:59 DEBUG  TaskList: ### Finished check_iso
11-11 14:59 DEBUG  TaskList: New task copy_file
11-11 14:59 DEBUG  CommonBackend: Copying H:\ubuntu-10.10-desktop-i386.iso > G:\ubuntu\install\installation.iso
11-11 14:59 DEBUG  TaskList: ### Running copy_file...
11-11 15:00 DEBUG  TaskList: ### Finished copy_file
11-11 15:00 DEBUG  TaskList: ## Finished get_iso
11-11 15:00 DEBUG  TaskList: ## Running extract_kernel...
11-11 15:00 DEBUG  CommonBackend: Extracting files from ISO G:\ubuntu\install\installation.iso
11-11 15:00 DEBUG  WindowsBackend:   extracting md5sum.txt from G:\ubuntu\install\installation.iso
11-11 15:00 DEBUG  WindowsBackend:   extracting casper\vmlinuz from G:\ubuntu\install\installation.iso
11-11 15:00 DEBUG  WindowsBackend:   extracting casper\initrd.lz from G:\ubuntu\install\installation.iso
11-11 15:00 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
11-11 15:00 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
11-11 15:00 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 50065155d2b4c37740b0e123cbfebc43 == 50065155d2b4c37740b0e123cbfebc43
11-11 15:00 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
11-11 15:00 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 8606bee30b5fc55cb9c9a8f997607552 == 8606bee30b5fc55cb9c9a8f997607552
11-11 15:00 DEBUG  TaskList: ## Finished extract_kernel
11-11 15:00 DEBUG  TaskList: ## Running choose_disk_sizes...
11-11 15:00 DEBUG  WindowsBackend: total size=9000
  root=4000
  swap=256
  home=744
  usr=4000
11-11 15:00 DEBUG  TaskList: ## Finished choose_disk_sizes
11-11 15:00 DEBUG  TaskList: ## Running create_preseed...
11-11 15:00 DEBUG  TaskList: ## Finished create_preseed
11-11 15:00 DEBUG  TaskList: ## Running modify_bootloader...
11-11 15:00 DEBUG  TaskList: New task modify_bcd
11-11 15:00 DEBUG  TaskList: ### Running modify_bcd...
11-11 15:00 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 95334.015625 mb free ntfs)
11-11 15:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {cea0b4ee-bdd9-11df-b973-b9b5d078ef58}
11-11 15:00 DEBUG  TaskList: ### Finished modify_bcd
11-11 15:00 DEBUG  TaskList: New task modify_bcd
11-11 15:00 DEBUG  TaskList: ### Running modify_bcd...
11-11 15:00 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 228240.300781 mb free ntfs)
11-11 15:00 DEBUG  WindowsBackend: BCD has already been modified
11-11 15:00 DEBUG  TaskList: ### Finished modify_bcd
11-11 15:00 DEBUG  TaskList: New task modify_bcd
11-11 15:00 DEBUG  TaskList: ### Running modify_bcd...
11-11 15:00 DEBUG  WindowsBackend: modify_bcd Drive(G: hd 15437.9765625 mb free fat32)
11-11 15:00 DEBUG  WindowsBackend: BCD has already been modified
11-11 15:00 DEBUG  TaskList: ### Finished modify_bcd
11-11 15:00 DEBUG  TaskList: New task modify_bcd
11-11 15:00 DEBUG  TaskList: ### Running modify_bcd...
11-11 15:00 DEBUG  WindowsBackend: modify_bcd Drive(H: hd 24841.125 mb free exfat)
11-11 15:00 DEBUG  WindowsBackend: BCD has already been modified
11-11 15:00 DEBUG  TaskList: ### Finished modify_bcd
11-11 15:00 DEBUG  TaskList: New task modify_bcd
11-11 15:00 DEBUG  TaskList: ### Running modify_bcd...
11-11 15:00 DEBUG  WindowsBackend: modify_bcd Drive(I: hd 20378.6210938 mb free ntfs)
11-11 15:00 DEBUG  WindowsBackend: BCD has already been modified
11-11 15:00 DEBUG  TaskList: ### Finished modify_bcd
11-11 15:00 DEBUG  TaskList: ## Finished modify_bootloader
11-11 15:00 DEBUG  TaskList: ## Running modify_grub_configuration...
11-11 15:00 DEBUG  TaskList: ## Finished modify_grub_configuration
11-11 15:00 DEBUG  TaskList: ## Running create_virtual_disks...
11-11 15:00 DEBUG  Virtualdisk:  Creating virtual disk G:\ubuntu\disks\root.disk of 4000MB
11-11 15:00 DEBUG  Virtualdisk:  Creating virtual disk G:\ubuntu\disks\home.disk of 744MB
11-11 15:00 DEBUG  Virtualdisk:  Creating virtual disk G:\ubuntu\disks\usr.disk of 4000MB
11-11 15:00 DEBUG  Virtualdisk:  Creating virtual disk G:\ubuntu\disks\swap.disk of 256MB
11-11 15:00 DEBUG  TaskList: ## Finished create_virtual_disks
11-11 15:00 DEBUG  TaskList: ## Running uncompress_files...
11-11 15:00 DEBUG  TaskList: ## Finished uncompress_files
11-11 15:00 DEBUG  TaskList: ## Running eject_cd...
11-11 15:00 DEBUG  TaskList: ## Finished eject_cd
11-11 15:00 DEBUG  TaskList: # Finished tasklist
11-11 15:00 INFO   root: Almost finished installing
11-11 15:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylA543.tmp\translations, languages=['en_US', 'en']
11-11 15:01 INFO   root: Finished installation
11-11 15:01 INFO   root: Rebooting
11-11 15:01 DEBUG  TaskList: # Running tasklist...
11-11 15:01 DEBUG  TaskList: ## Running reboot...
11-11 15:01 DEBUG  TaskList: ## Finished reboot
11-11 15:01 DEBUG  TaskList: # Finished tasklist
11-11 15:01 DEBUG  root: application.quit
11-11 15:01 DEBUG  WindowsFrontend: frontend.quit
11-11 15:01 DEBUG  WindowsFrontend: frontend.on_quit
11-11 15:01 DEBUG  root: application.on_quit
11-11 15:01 INFO   root: sys.exit
11-11 23:16 INFO   root: === wubi 10.10 rev197 ===
11-11 23:16 DEBUG  root: Logfile is c:\users\koojie~1\appdata\local\temp\wubi-10.10-rev197.log
11-11 23:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\ubuntu\\uninstall-wubi.exe"']
11-11 23:16 DEBUG  CommonBackend: data_dir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\data
11-11 23:16 DEBUG  WindowsBackend: 7z=C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\bin\7z.exe
11-11 23:16 DEBUG  CommonBackend: Fetching basic info...
11-11 23:16 DEBUG  CommonBackend: original_exe=G:\ubuntu\uninstall-wubi.exe
11-11 23:16 DEBUG  CommonBackend: platform=win32
11-11 23:16 DEBUG  CommonBackend: osname=nt
11-11 23:16 DEBUG  CommonBackend: language=en_SG
11-11 23:16 DEBUG  CommonBackend: encoding=cp1252
11-11 23:16 DEBUG  WindowsBackend: arch=amd64
11-11 23:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\data\isolist.ini
11-11 23:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-11 23:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-11 23:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-11 23:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-11 23:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-11 23:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-11 23:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-11 23:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-11 23:16 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-11 23:16 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-11 23:16 DEBUG  WindowsBackend: Fetching host info...
11-11 23:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-11 23:16 DEBUG  WindowsBackend: windows version=vista
11-11 23:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Enterprise
11-11 23:16 DEBUG  WindowsBackend: windows_sp=None
11-11 23:16 DEBUG  WindowsBackend: windows_build=7600
11-11 23:16 DEBUG  WindowsBackend: gmt=8
11-11 23:16 DEBUG  WindowsBackend: country=SG
11-11 23:16 DEBUG  WindowsBackend: timezone=Asia/Singapore
11-11 23:16 DEBUG  WindowsBackend: windows_username=Koo Jie Hui
11-11 23:16 DEBUG  WindowsBackend: user_full_name=Koo Jie Hui
11-11 23:16 DEBUG  WindowsBackend: user_directory=C:\Users\Koo Jie Hui
11-11 23:16 DEBUG  WindowsBackend: windows_language_code=1033
11-11 23:16 DEBUG  WindowsBackend: windows_language=English
11-11 23:16 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
11-11 23:16 DEBUG  WindowsBackend: bootloader=vista
11-11 23:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 95330.953125 mb free ntfs)
11-11 23:16 DEBUG  WindowsBackend: drive=Drive(C: hd 95330.953125 mb free ntfs)
11-11 23:16 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-11 23:16 DEBUG  WindowsBackend: drive=Drive(F: hd 228240.300781 mb free ntfs)
11-11 23:16 DEBUG  WindowsBackend: drive=Drive(G: hd 5743.171875 mb free fat32)
11-11 23:16 DEBUG  WindowsBackend: drive=Drive(H: hd 24841.125 mb free exfat)
11-11 23:16 DEBUG  WindowsBackend: drive=Drive(I: hd 20378.6210938 mb free ntfs)
11-11 23:16 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
11-11 23:16 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
11-11 23:16 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-11 23:16 DEBUG  WindowsBackend: keyboard_id=67699721
11-11 23:16 DEBUG  WindowsBackend: keyboard_layout=us
11-11 23:16 DEBUG  WindowsBackend: keyboard_variant=
11-11 23:16 DEBUG  CommonBackend: python locale=('en_SG', 'cp1252')
11-11 23:16 DEBUG  CommonBackend: locale=en_SG.UTF-8
11-11 23:16 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
11-11 23:16 DEBUG  CommonBackend: Searching ISOs on USB devices
11-11 23:16 DEBUG  Distro:   checking Ubuntu ISO H:\ubuntu-10.10-desktop-i386.iso
11-11 23:16 DEBUG  WindowsBackend:   extracting .disk\info from H:\ubuntu-10.10-desktop-i386.iso
11-11 23:16 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-11 23:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-11 23:16 INFO   Distro: Found a valid iso for Ubuntu: H:\ubuntu-10.10-desktop-i386.iso
11-11 23:16 DEBUG  CommonBackend: Searching for local CDs
11-11 23:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp is a valid Ubuntu CD
11-11 23:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
11-11 23:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp is a valid Ubuntu CD
11-11 23:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
11-11 23:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp is a valid Ubuntu Netbook CD
11-11 23:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
11-11 23:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp is a valid Kubuntu CD
11-11 23:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
11-11 23:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp is a valid Kubuntu CD
11-11 23:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
11-11 23:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp is a valid Kubuntu Netbook CD
11-11 23:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
11-11 23:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp is a valid Xubuntu CD
11-11 23:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
11-11 23:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp is a valid Xubuntu CD
11-11 23:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
11-11 23:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp is a valid Mythbuntu CD
11-11 23:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
11-11 23:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp is a valid Mythbuntu CD
11-11 23:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
11-11 23:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-11 23:16 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-11 23:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-11 23:16 INFO   Distro: Found a valid CD for Ubuntu: D:\
11-11 23:16 INFO   root: Running the uninstaller...
11-11 23:16 INFO   CommonBackend: This is the uninstaller running
11-11 23:16 DEBUG  WindowsFrontend: __init__...
11-11 23:16 DEBUG  WindowsFrontend: on_init...
11-11 23:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\translations, languages=['en_SG', 'en']
11-11 23:16 INFO   root: Received settings
11-11 23:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\translations, languages=['en_SG', 'en']
11-11 23:16 DEBUG  TaskList: # Running tasklist...
11-11 23:16 DEBUG  TaskList: ## Running Backup ISO...
11-11 23:16 DEBUG  TaskList: ## Finished Backup ISO
11-11 23:16 DEBUG  TaskList: ## Running Remove bootloader entry...
11-11 23:16 DEBUG  WindowsBackend: Removing bcd entry {cea0b4ee-bdd9-11df-b973-b9b5d078ef58}
11-11 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
11-11 23:16 DEBUG  WindowsBackend: undo_bootini C:
11-11 23:16 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 95330.953125 mb free ntfs)
11-11 23:16 DEBUG  WindowsBackend: undo_bootini F:
11-11 23:16 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 228240.300781 mb free ntfs)
11-11 23:16 DEBUG  WindowsBackend: undo_bootini G:
11-11 23:16 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 5743.171875 mb free fat32)
11-11 23:16 DEBUG  WindowsBackend: undo_bootini H:
11-11 23:16 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 24841.125 mb free exfat)
11-11 23:16 DEBUG  WindowsBackend: undo_bootini I:
11-11 23:16 DEBUG  WindowsBackend: undo_configsys Drive(I: hd 20378.6210938 mb free ntfs)
11-11 23:16 DEBUG  TaskList: ## Finished Remove bootloader entry
11-11 23:16 DEBUG  TaskList: ## Running Remove target dir...
11-11 23:16 DEBUG  CommonBackend: Deleting G:\ubuntu
11-11 23:16 DEBUG  TaskList: ## Finished Remove target dir
11-11 23:16 DEBUG  TaskList: ## Running Remove registry key...
11-11 23:16 DEBUG  TaskList: ## Finished Remove registry key
11-11 23:16 DEBUG  TaskList: # Finished tasklist
11-11 23:16 INFO   root: Almost finished uninstalling
11-11 23:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylEBF.tmp\translations, languages=['en_SG', 'en']
11-11 23:17 INFO   root: Finished uninstallation
11-11 23:17 DEBUG  root: application.quit
11-11 23:17 DEBUG  WindowsFrontend: frontend.quit
11-11 23:17 DEBUG  WindowsFrontend: frontend.on_quit
11-11 23:17 DEBUG  root: application.on_quit
11-11 23:17 INFO   root: sys.exit
11-11 15:30 INFO   root: === wubi 10.10 rev197 ===
11-11 15:30 DEBUG  root: Logfile is c:\users\koojie~1\appdata\local\temp\wubi-10.10-rev197.log
11-11 15:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-11 15:30 DEBUG  CommonBackend: data_dir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp\data
11-11 15:30 DEBUG  WindowsBackend: 7z=C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp\bin\7z.exe
11-11 15:30 DEBUG  CommonBackend: Fetching basic info...
11-11 15:30 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-11 15:30 DEBUG  CommonBackend: platform=win32
11-11 15:30 DEBUG  CommonBackend: osname=nt
11-11 15:30 DEBUG  CommonBackend: language=en_SG
11-11 15:30 DEBUG  CommonBackend: encoding=cp1252
11-11 15:30 DEBUG  WindowsBackend: arch=amd64
11-11 15:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp\data\isolist.ini
11-11 15:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-11 15:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-11 15:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-11 15:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-11 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-11 15:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-11 15:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-11 15:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-11 15:30 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-11 15:30 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-11 15:30 DEBUG  WindowsBackend: Fetching host info...
11-11 15:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-11 15:30 DEBUG  WindowsBackend: windows version=vista
11-11 15:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Enterprise
11-11 15:30 DEBUG  WindowsBackend: windows_sp=None
11-11 15:30 DEBUG  WindowsBackend: windows_build=7600
11-11 15:30 DEBUG  WindowsBackend: gmt=8
11-11 15:30 DEBUG  WindowsBackend: country=SG
11-11 15:30 DEBUG  WindowsBackend: timezone=Asia/Singapore
11-11 15:30 DEBUG  WindowsBackend: windows_username=Koo Jie Hui
11-11 15:30 DEBUG  WindowsBackend: user_full_name=Koo Jie Hui
11-11 15:30 DEBUG  WindowsBackend: user_directory=C:\Users\Koo Jie Hui
11-11 15:30 DEBUG  WindowsBackend: windows_language_code=1033
11-11 15:30 DEBUG  WindowsBackend: windows_language=English
11-11 15:30 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
11-11 15:30 DEBUG  WindowsBackend: bootloader=vista
11-11 15:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 95293.9257813 mb free ntfs)
11-11 15:30 DEBUG  WindowsBackend: drive=Drive(C: hd 95293.9257813 mb free ntfs)
11-11 15:30 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-11 15:30 DEBUG  WindowsBackend: drive=Drive(F: hd 228240.300781 mb free ntfs)
11-11 15:30 DEBUG  WindowsBackend: drive=Drive(G: hd 15437.9921875 mb free fat32)
11-11 15:30 DEBUG  WindowsBackend: drive=Drive(H: hd 24841.125 mb free exfat)
11-11 15:30 DEBUG  WindowsBackend: drive=Drive(I: hd 20378.6210938 mb free ntfs)
11-11 15:30 DEBUG  WindowsBackend: uninstaller_path=None
11-11 15:30 DEBUG  WindowsBackend: previous_target_dir=None
11-11 15:30 DEBUG  WindowsBackend: previous_distro_name=None
11-11 15:30 DEBUG  WindowsBackend: keyboard_id=67699721
11-11 15:30 DEBUG  WindowsBackend: keyboard_layout=us
11-11 15:30 DEBUG  WindowsBackend: keyboard_variant=
11-11 15:30 DEBUG  CommonBackend: python locale=('en_SG', 'cp1252')
11-11 15:30 DEBUG  CommonBackend: locale=en_SG.UTF-8
11-11 15:30 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
11-11 15:30 DEBUG  CommonBackend: Searching ISOs on USB devices
11-11 15:30 DEBUG  Distro:   checking Ubuntu ISO H:\ubuntu-10.10-desktop-i386.iso
11-11 15:30 DEBUG  WindowsBackend:   extracting .disk\info from H:\ubuntu-10.10-desktop-i386.iso
11-11 15:30 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-11 15:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-11 15:30 INFO   Distro: Found a valid iso for Ubuntu: H:\ubuntu-10.10-desktop-i386.iso
11-11 15:30 DEBUG  CommonBackend: Searching for local CDs
11-11 15:30 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp is a valid Ubuntu CD
11-11 15:30 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp\casper\filesystem.squashfs
11-11 15:30 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp is a valid Ubuntu CD
11-11 15:30 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp\casper\filesystem.squashfs
11-11 15:30 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp is a valid Ubuntu Netbook CD
11-11 15:30 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp\casper\filesystem.squashfs
11-11 15:30 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp is a valid Kubuntu CD
11-11 15:30 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp\casper\filesystem.squashfs
11-11 15:30 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp is a valid Kubuntu CD
11-11 15:30 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp\casper\filesystem.squashfs
11-11 15:30 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp is a valid Kubuntu Netbook CD
11-11 15:30 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp\casper\filesystem.squashfs
11-11 15:30 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp is a valid Xubuntu CD
11-11 15:30 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp\casper\filesystem.squashfs
11-11 15:30 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp is a valid Xubuntu CD
11-11 15:30 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp\casper\filesystem.squashfs
11-11 15:30 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp is a valid Mythbuntu CD
11-11 15:30 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp\casper\filesystem.squashfs
11-11 15:30 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp is a valid Mythbuntu CD
11-11 15:30 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp\casper\filesystem.squashfs
11-11 15:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-11 15:30 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-11 15:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-11 15:30 INFO   Distro: Found a valid CD for Ubuntu: D:\
11-11 15:30 INFO   root: Running the CD menu...
11-11 15:30 DEBUG  WindowsFrontend: __init__...
11-11 15:30 DEBUG  WindowsFrontend: on_init...
11-11 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp\translations, languages=['en_SG', 'en']
11-11 15:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylA082.tmp\translations, languages=['en_SG', 'en']
11-11 15:30 DEBUG  root: application.quit
11-11 15:30 DEBUG  WindowsFrontend: frontend.quit
11-11 15:30 DEBUG  WindowsFrontend: frontend.on_quit
11-11 15:30 DEBUG  root: application.on_quit
11-11 15:30 INFO   root: sys.exit
11-11 15:31 INFO   root: === wubi 10.10 rev197 ===
11-11 15:31 DEBUG  root: Logfile is c:\users\koojie~1\appdata\local\temp\wubi-10.10-rev197.log
11-11 15:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-11 15:31 DEBUG  CommonBackend: data_dir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp\data
11-11 15:31 DEBUG  WindowsBackend: 7z=C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp\bin\7z.exe
11-11 15:31 DEBUG  CommonBackend: Fetching basic info...
11-11 15:31 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-11 15:31 DEBUG  CommonBackend: platform=win32
11-11 15:31 DEBUG  CommonBackend: osname=nt
11-11 15:31 DEBUG  CommonBackend: language=en_SG
11-11 15:31 DEBUG  CommonBackend: encoding=cp1252
11-11 15:31 DEBUG  WindowsBackend: arch=amd64
11-11 15:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp\data\isolist.ini
11-11 15:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-11 15:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-11 15:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-11 15:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-11 15:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-11 15:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-11 15:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-11 15:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-11 15:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-11 15:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-11 15:31 DEBUG  WindowsBackend: Fetching host info...
11-11 15:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-11 15:31 DEBUG  WindowsBackend: windows version=vista
11-11 15:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Enterprise
11-11 15:31 DEBUG  WindowsBackend: windows_sp=None
11-11 15:31 DEBUG  WindowsBackend: windows_build=7600
11-11 15:31 DEBUG  WindowsBackend: gmt=8
11-11 15:31 DEBUG  WindowsBackend: country=SG
11-11 15:31 DEBUG  WindowsBackend: timezone=Asia/Singapore
11-11 15:31 DEBUG  WindowsBackend: windows_username=Koo Jie Hui
11-11 15:31 DEBUG  WindowsBackend: user_full_name=Koo Jie Hui
11-11 15:31 DEBUG  WindowsBackend: user_directory=C:\Users\Koo Jie Hui
11-11 15:31 DEBUG  WindowsBackend: windows_language_code=1033
11-11 15:31 DEBUG  WindowsBackend: windows_language=English
11-11 15:31 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
11-11 15:31 DEBUG  WindowsBackend: bootloader=vista
11-11 15:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 95293.375 mb free ntfs)
11-11 15:31 DEBUG  WindowsBackend: drive=Drive(C: hd 95293.375 mb free ntfs)
11-11 15:31 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-11 15:31 DEBUG  WindowsBackend: drive=Drive(F: hd 228240.300781 mb free ntfs)
11-11 15:31 DEBUG  WindowsBackend: drive=Drive(G: hd 15437.9921875 mb free fat32)
11-11 15:31 DEBUG  WindowsBackend: drive=Drive(H: hd 24841.125 mb free exfat)
11-11 15:31 DEBUG  WindowsBackend: drive=Drive(I: hd 20378.6210938 mb free ntfs)
11-11 15:31 DEBUG  WindowsBackend: uninstaller_path=None
11-11 15:31 DEBUG  WindowsBackend: previous_target_dir=None
11-11 15:31 DEBUG  WindowsBackend: previous_distro_name=None
11-11 15:31 DEBUG  WindowsBackend: keyboard_id=67699721
11-11 15:31 DEBUG  WindowsBackend: keyboard_layout=us
11-11 15:31 DEBUG  WindowsBackend: keyboard_variant=
11-11 15:31 DEBUG  CommonBackend: python locale=('en_SG', 'cp1252')
11-11 15:31 DEBUG  CommonBackend: locale=en_SG.UTF-8
11-11 15:31 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
11-11 15:31 DEBUG  CommonBackend: Searching ISOs on USB devices
11-11 15:31 DEBUG  Distro:   checking Ubuntu ISO H:\ubuntu-10.10-desktop-i386.iso
11-11 15:31 DEBUG  WindowsBackend:   extracting .disk\info from H:\ubuntu-10.10-desktop-i386.iso
11-11 15:31 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-11 15:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-11 15:31 INFO   Distro: Found a valid iso for Ubuntu: H:\ubuntu-10.10-desktop-i386.iso
11-11 15:31 DEBUG  CommonBackend: Searching for local CDs
11-11 15:31 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp is a valid Ubuntu CD
11-11 15:31 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp\casper\filesystem.squashfs
11-11 15:31 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp is a valid Ubuntu CD
11-11 15:31 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp\casper\filesystem.squashfs
11-11 15:31 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp is a valid Ubuntu Netbook CD
11-11 15:31 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp\casper\filesystem.squashfs
11-11 15:31 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp is a valid Kubuntu CD
11-11 15:31 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp\casper\filesystem.squashfs
11-11 15:31 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp is a valid Kubuntu CD
11-11 15:31 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp\casper\filesystem.squashfs
11-11 15:31 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp is a valid Kubuntu Netbook CD
11-11 15:31 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp\casper\filesystem.squashfs
11-11 15:31 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp is a valid Xubuntu CD
11-11 15:31 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp\casper\filesystem.squashfs
11-11 15:31 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp is a valid Xubuntu CD
11-11 15:31 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp\casper\filesystem.squashfs
11-11 15:31 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp is a valid Mythbuntu CD
11-11 15:31 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp\casper\filesystem.squashfs
11-11 15:31 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp is a valid Mythbuntu CD
11-11 15:31 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp\casper\filesystem.squashfs
11-11 15:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-11 15:31 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-11 15:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-11 15:31 INFO   Distro: Found a valid CD for Ubuntu: D:\
11-11 15:31 INFO   root: Running the CD menu...
11-11 15:31 DEBUG  WindowsFrontend: __init__...
11-11 15:31 DEBUG  WindowsFrontend: on_init...
11-11 15:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp\translations, languages=['en_SG', 'en']
11-11 15:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pylC84D.tmp\translations, languages=['en_SG', 'en']
11-11 15:32 INFO   root: CD menu finished
11-11 15:32 INFO   root: Rebooting
11-11 15:32 DEBUG  TaskList: # Running tasklist...
11-11 15:32 DEBUG  TaskList: ## Running reboot...
11-11 15:32 DEBUG  TaskList: ## Finished reboot
11-11 15:32 DEBUG  TaskList: # Finished tasklist
11-11 15:32 DEBUG  root: application.quit
11-11 15:32 DEBUG  WindowsFrontend: frontend.quit
11-11 15:32 DEBUG  WindowsFrontend: frontend.on_quit
11-11 15:32 DEBUG  root: application.on_quit
11-11 15:32 INFO   root: sys.exit
11-13 08:05 INFO   root: === wubi 10.10 rev197 ===
11-13 08:05 DEBUG  root: Logfile is c:\users\koojie~1\appdata\local\temp\wubi-10.10-rev197.log
11-13 08:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-13 08:05 DEBUG  CommonBackend: data_dir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\data
11-13 08:05 DEBUG  WindowsBackend: 7z=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\bin\7z.exe
11-13 08:05 DEBUG  CommonBackend: Fetching basic info...
11-13 08:05 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-13 08:05 DEBUG  CommonBackend: platform=win32
11-13 08:05 DEBUG  CommonBackend: osname=nt
11-13 08:05 DEBUG  CommonBackend: language=en_SG
11-13 08:05 DEBUG  CommonBackend: encoding=cp1252
11-13 08:05 DEBUG  WindowsBackend: arch=amd64
11-13 08:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\data\isolist.ini
11-13 08:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-13 08:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-13 08:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-13 08:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-13 08:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-13 08:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-13 08:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-13 08:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-13 08:05 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-13 08:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-13 08:05 DEBUG  WindowsBackend: Fetching host info...
11-13 08:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-13 08:05 DEBUG  WindowsBackend: windows version=vista
11-13 08:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Enterprise
11-13 08:05 DEBUG  WindowsBackend: windows_sp=None
11-13 08:05 DEBUG  WindowsBackend: windows_build=7600
11-13 08:05 DEBUG  WindowsBackend: gmt=8
11-13 08:05 DEBUG  WindowsBackend: country=SG
11-13 08:05 DEBUG  WindowsBackend: timezone=Asia/Singapore
11-13 08:05 DEBUG  WindowsBackend: windows_username=Koo Jie Hui
11-13 08:05 DEBUG  WindowsBackend: user_full_name=Koo Jie Hui
11-13 08:05 DEBUG  WindowsBackend: user_directory=C:\Users\Koo Jie Hui
11-13 08:05 DEBUG  WindowsBackend: windows_language_code=1033
11-13 08:05 DEBUG  WindowsBackend: windows_language=English
11-13 08:05 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
11-13 08:05 DEBUG  WindowsBackend: bootloader=vista
11-13 08:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 90076.3789063 mb free ntfs)
11-13 08:05 DEBUG  WindowsBackend: drive=Drive(C: hd 90076.3789063 mb free ntfs)
11-13 08:05 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-13 08:05 DEBUG  WindowsBackend: uninstaller_path=None
11-13 08:05 DEBUG  WindowsBackend: previous_target_dir=None
11-13 08:05 DEBUG  WindowsBackend: previous_distro_name=None
11-13 08:05 DEBUG  WindowsBackend: keyboard_id=67699721
11-13 08:05 DEBUG  WindowsBackend: keyboard_layout=us
11-13 08:05 DEBUG  WindowsBackend: keyboard_variant=
11-13 08:05 DEBUG  CommonBackend: python locale=('en_SG', 'cp1252')
11-13 08:05 DEBUG  CommonBackend: locale=en_SG.UTF-8
11-13 08:05 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
11-13 08:05 DEBUG  CommonBackend: Searching ISOs on USB devices
11-13 08:05 DEBUG  CommonBackend: Searching for local CDs
11-13 08:05 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp is a valid Ubuntu CD
11-13 08:05 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\casper\filesystem.squashfs
11-13 08:05 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp is a valid Ubuntu CD
11-13 08:05 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\casper\filesystem.squashfs
11-13 08:05 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp is a valid Ubuntu Netbook CD
11-13 08:05 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\casper\filesystem.squashfs
11-13 08:05 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp is a valid Kubuntu CD
11-13 08:05 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\casper\filesystem.squashfs
11-13 08:05 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp is a valid Kubuntu CD
11-13 08:05 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\casper\filesystem.squashfs
11-13 08:05 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp is a valid Kubuntu Netbook CD
11-13 08:05 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\casper\filesystem.squashfs
11-13 08:05 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp is a valid Xubuntu CD
11-13 08:05 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\casper\filesystem.squashfs
11-13 08:05 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp is a valid Xubuntu CD
11-13 08:05 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\casper\filesystem.squashfs
11-13 08:05 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp is a valid Mythbuntu CD
11-13 08:05 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\casper\filesystem.squashfs
11-13 08:05 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp is a valid Mythbuntu CD
11-13 08:05 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\casper\filesystem.squashfs
11-13 08:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 08:05 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-13 08:05 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-13 08:05 INFO   Distro: Found a valid CD for Ubuntu: D:\
11-13 08:05 INFO   root: Running the CD menu...
11-13 08:05 DEBUG  WindowsFrontend: __init__...
11-13 08:05 DEBUG  WindowsFrontend: on_init...
11-13 08:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\translations, languages=['en_SG', 'en']
11-13 08:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\translations, languages=['en_SG', 'en']
11-13 08:05 INFO   root: CD menu finished
11-13 08:05 INFO   root: Running the installer...
11-13 08:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\translations, languages=['en_SG', 'en']
11-13 08:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\translations, languages=['en_SG', 'en']
11-13 08:05 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=koojiehui
11-13 08:05 INFO   root: Received settings
11-13 08:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\translations, languages=['en_GB', 'en']
11-13 08:05 DEBUG  TaskList: # Running tasklist...
11-13 08:05 DEBUG  TaskList: ## Running select_target_dir...
11-13 08:05 INFO   WindowsBackend: Installing into C:\ubuntu
11-13 08:05 DEBUG  TaskList: ## Finished select_target_dir
11-13 08:05 DEBUG  TaskList: ## Running create_dir_structure...
11-13 08:05 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-13 08:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-13 08:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-13 08:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-13 08:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-13 08:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-13 08:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-13 08:05 DEBUG  TaskList: ## Finished create_dir_structure
11-13 08:05 DEBUG  TaskList: ## Running uncompress_target_dir...
11-13 08:05 DEBUG  TaskList: ## Finished uncompress_target_dir
11-13 08:05 DEBUG  TaskList: ## Running create_uninstaller...
11-13 08:05 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-13 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-13 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-13 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-13 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-13 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
11-13 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-13 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-13 08:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-13 08:05 DEBUG  TaskList: ## Finished create_uninstaller
11-13 08:05 DEBUG  TaskList: ## Running copy_installation_files...
11-13 08:05 DEBUG  WindowsBackend: Copying C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-13 08:05 DEBUG  WindowsBackend: Copying C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\winboot -> C:\ubuntu\winboot
11-13 08:05 DEBUG  WindowsBackend: Copying C:\Users\KOOJIE~1\AppData\Local\Temp\pyl426C.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-13 08:05 DEBUG  TaskList: ## Finished copy_installation_files
11-13 08:05 DEBUG  TaskList: ## Running get_iso...
11-13 08:05 DEBUG  TaskList: New task copy_file
11-13 08:05 DEBUG  TaskList: ### Running copy_file...
11-13 08:07 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-13 08:07 DEBUG  TaskList: # Cancelling tasklist
11-13 08:07 DEBUG  TaskList: New task check_iso
11-13 08:07 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-13 08:07 DEBUG  CommonBackend: Searching for local ISO
11-13 08:07 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-13 08:07 DEBUG  TaskList: New task get_metalink
11-13 08:07 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-13 08:07 DEBUG  TaskList: # Cancelling tasklist
11-13 08:07 DEBUG  TaskList: # Finished tasklist
11-13 08:15 INFO   root: === wubi 10.10 rev197 ===
11-13 08:15 DEBUG  root: Logfile is c:\users\koojie~1\appdata\local\temp\wubi-10.10-rev197.log
11-13 08:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
11-13 08:15 DEBUG  CommonBackend: data_dir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\data
11-13 08:15 DEBUG  WindowsBackend: 7z=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\bin\7z.exe
11-13 08:15 DEBUG  CommonBackend: Fetching basic info...
11-13 08:15 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
11-13 08:15 DEBUG  CommonBackend: platform=win32
11-13 08:15 DEBUG  CommonBackend: osname=nt
11-13 08:15 DEBUG  CommonBackend: language=en_SG
11-13 08:15 DEBUG  CommonBackend: encoding=cp1252
11-13 08:15 DEBUG  WindowsBackend: arch=amd64
11-13 08:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\data\isolist.ini
11-13 08:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-13 08:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-13 08:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-13 08:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-13 08:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-13 08:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-13 08:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-13 08:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-13 08:15 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-13 08:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-13 08:15 DEBUG  WindowsBackend: Fetching host info...
11-13 08:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-13 08:15 DEBUG  WindowsBackend: windows version=vista
11-13 08:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Enterprise
11-13 08:15 DEBUG  WindowsBackend: windows_sp=None
11-13 08:15 DEBUG  WindowsBackend: windows_build=7600
11-13 08:15 DEBUG  WindowsBackend: gmt=8
11-13 08:15 DEBUG  WindowsBackend: country=SG
11-13 08:15 DEBUG  WindowsBackend: timezone=Asia/Singapore
11-13 08:15 DEBUG  WindowsBackend: windows_username=Koo Jie Hui
11-13 08:15 DEBUG  WindowsBackend: user_full_name=Koo Jie Hui
11-13 08:15 DEBUG  WindowsBackend: user_directory=C:\Users\Koo Jie Hui
11-13 08:15 DEBUG  WindowsBackend: windows_language_code=1033
11-13 08:15 DEBUG  WindowsBackend: windows_language=English
11-13 08:15 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
11-13 08:15 DEBUG  WindowsBackend: bootloader=vista
11-13 08:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 89098.7851563 mb free ntfs)
11-13 08:15 DEBUG  WindowsBackend: drive=Drive(C: hd 89098.7851563 mb free ntfs)
11-13 08:15 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-13 08:15 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-13 08:15 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-13 08:15 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-13 08:15 DEBUG  WindowsBackend: keyboard_id=67699721
11-13 08:15 DEBUG  WindowsBackend: keyboard_layout=us
11-13 08:15 DEBUG  WindowsBackend: keyboard_variant=
11-13 08:15 DEBUG  CommonBackend: python locale=('en_SG', 'cp1252')
11-13 08:15 DEBUG  CommonBackend: locale=en_SG.UTF-8
11-13 08:15 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
11-13 08:15 DEBUG  CommonBackend: Searching ISOs on USB devices
11-13 08:15 DEBUG  CommonBackend: Searching for local CDs
11-13 08:15 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp is a valid Ubuntu CD
11-13 08:15 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\casper\filesystem.squashfs
11-13 08:15 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp is a valid Ubuntu CD
11-13 08:15 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\casper\filesystem.squashfs
11-13 08:15 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp is a valid Ubuntu Netbook CD
11-13 08:15 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\casper\filesystem.squashfs
11-13 08:15 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp is a valid Kubuntu CD
11-13 08:15 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\casper\filesystem.squashfs
11-13 08:15 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp is a valid Kubuntu CD
11-13 08:15 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\casper\filesystem.squashfs
11-13 08:15 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp is a valid Kubuntu Netbook CD
11-13 08:15 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\casper\filesystem.squashfs
11-13 08:15 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp is a valid Xubuntu CD
11-13 08:15 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\casper\filesystem.squashfs
11-13 08:15 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp is a valid Xubuntu CD
11-13 08:15 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\casper\filesystem.squashfs
11-13 08:15 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp is a valid Mythbuntu CD
11-13 08:15 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\casper\filesystem.squashfs
11-13 08:15 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp is a valid Mythbuntu CD
11-13 08:15 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\casper\filesystem.squashfs
11-13 08:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 08:15 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-13 08:15 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-13 08:15 INFO   Distro: Found a valid CD for Ubuntu: D:\
11-13 08:15 INFO   root: Running the uninstaller...
11-13 08:15 INFO   CommonBackend: This is the uninstaller running
11-13 08:15 DEBUG  WindowsFrontend: __init__...
11-13 08:15 DEBUG  WindowsFrontend: on_init...
11-13 08:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\translations, languages=['en_SG', 'en']
11-13 08:15 INFO   root: Received settings
11-13 08:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\translations, languages=['en_SG', 'en']
11-13 08:15 DEBUG  TaskList: # Running tasklist...
11-13 08:15 DEBUG  TaskList: ## Running Backup ISO...
11-13 08:15 DEBUG  TaskList: ## Finished Backup ISO
11-13 08:15 DEBUG  TaskList: ## Running Remove bootloader entry...
11-13 08:15 DEBUG  WindowsBackend: Could not find bcd id
11-13 08:15 DEBUG  WindowsBackend: undo_bootini C:
11-13 08:15 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 89098.7851563 mb free ntfs)
11-13 08:15 DEBUG  TaskList: ## Finished Remove bootloader entry
11-13 08:15 DEBUG  TaskList: ## Running Remove target dir...
11-13 08:15 DEBUG  CommonBackend: Deleting C:\ubuntu
11-13 08:15 DEBUG  TaskList: ## Finished Remove target dir
11-13 08:15 DEBUG  TaskList: ## Running Remove registry key...
11-13 08:15 DEBUG  TaskList: ## Finished Remove registry key
11-13 08:15 DEBUG  TaskList: # Finished tasklist
11-13 08:15 INFO   root: Almost finished uninstalling
11-13 08:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5C80.tmp\translations, languages=['en_SG', 'en']
11-13 08:15 INFO   root: Finished uninstallation
11-13 08:15 DEBUG  root: application.quit
11-13 08:15 DEBUG  WindowsFrontend: frontend.quit
11-13 08:15 DEBUG  WindowsFrontend: frontend.on_quit
11-13 08:15 DEBUG  root: application.on_quit
11-13 08:15 INFO   root: sys.exit
11-13 08:16 INFO   root: === wubi 10.10 rev197 ===
11-13 08:16 DEBUG  root: Logfile is c:\users\koojie~1\appdata\local\temp\wubi-10.10-rev197.log
11-13 08:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-13 08:16 DEBUG  CommonBackend: data_dir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\data
11-13 08:16 DEBUG  WindowsBackend: 7z=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\bin\7z.exe
11-13 08:16 DEBUG  CommonBackend: Fetching basic info...
11-13 08:16 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-13 08:16 DEBUG  CommonBackend: platform=win32
11-13 08:16 DEBUG  CommonBackend: osname=nt
11-13 08:16 DEBUG  CommonBackend: language=en_SG
11-13 08:16 DEBUG  CommonBackend: encoding=cp1252
11-13 08:16 DEBUG  WindowsBackend: arch=amd64
11-13 08:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\data\isolist.ini
11-13 08:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-13 08:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-13 08:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-13 08:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-13 08:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-13 08:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-13 08:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-13 08:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-13 08:16 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-13 08:16 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-13 08:16 DEBUG  WindowsBackend: Fetching host info...
11-13 08:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-13 08:16 DEBUG  WindowsBackend: windows version=vista
11-13 08:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Enterprise
11-13 08:16 DEBUG  WindowsBackend: windows_sp=None
11-13 08:16 DEBUG  WindowsBackend: windows_build=7600
11-13 08:16 DEBUG  WindowsBackend: gmt=8
11-13 08:16 DEBUG  WindowsBackend: country=SG
11-13 08:16 DEBUG  WindowsBackend: timezone=Asia/Singapore
11-13 08:16 DEBUG  WindowsBackend: windows_username=Koo Jie Hui
11-13 08:16 DEBUG  WindowsBackend: user_full_name=Koo Jie Hui
11-13 08:16 DEBUG  WindowsBackend: user_directory=C:\Users\Koo Jie Hui
11-13 08:16 DEBUG  WindowsBackend: windows_language_code=1033
11-13 08:16 DEBUG  WindowsBackend: windows_language=English
11-13 08:16 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
11-13 08:16 DEBUG  WindowsBackend: bootloader=vista
11-13 08:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 91738.0117188 mb free ntfs)
11-13 08:16 DEBUG  WindowsBackend: drive=Drive(C: hd 91738.0117188 mb free ntfs)
11-13 08:16 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
11-13 08:16 DEBUG  WindowsBackend: uninstaller_path=None
11-13 08:16 DEBUG  WindowsBackend: previous_target_dir=None
11-13 08:16 DEBUG  WindowsBackend: previous_distro_name=None
11-13 08:16 DEBUG  WindowsBackend: keyboard_id=67699721
11-13 08:16 DEBUG  WindowsBackend: keyboard_layout=us
11-13 08:16 DEBUG  WindowsBackend: keyboard_variant=
11-13 08:16 DEBUG  CommonBackend: python locale=('en_SG', 'cp1252')
11-13 08:16 DEBUG  CommonBackend: locale=en_SG.UTF-8
11-13 08:16 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
11-13 08:16 DEBUG  CommonBackend: Searching ISOs on USB devices
11-13 08:16 DEBUG  CommonBackend: Searching for local CDs
11-13 08:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp is a valid Ubuntu CD
11-13 08:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\casper\filesystem.squashfs
11-13 08:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp is a valid Ubuntu CD
11-13 08:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\casper\filesystem.squashfs
11-13 08:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp is a valid Ubuntu Netbook CD
11-13 08:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\casper\filesystem.squashfs
11-13 08:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp is a valid Kubuntu CD
11-13 08:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\casper\filesystem.squashfs
11-13 08:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp is a valid Kubuntu CD
11-13 08:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\casper\filesystem.squashfs
11-13 08:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp is a valid Kubuntu Netbook CD
11-13 08:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\casper\filesystem.squashfs
11-13 08:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp is a valid Xubuntu CD
11-13 08:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\casper\filesystem.squashfs
11-13 08:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp is a valid Xubuntu CD
11-13 08:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\casper\filesystem.squashfs
11-13 08:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp is a valid Mythbuntu CD
11-13 08:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\casper\filesystem.squashfs
11-13 08:16 DEBUG  Distro:   checking whether C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp is a valid Mythbuntu CD
11-13 08:16 DEBUG  Distro:     does not contain C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\casper\filesystem.squashfs
11-13 08:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 08:16 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
11-13 08:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
11-13 08:16 INFO   Distro: Found a valid CD for Ubuntu: D:\
11-13 08:16 INFO   root: Running the CD menu...
11-13 08:16 DEBUG  WindowsFrontend: __init__...
11-13 08:16 DEBUG  WindowsFrontend: on_init...
11-13 08:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\translations, languages=['en_SG', 'en']
11-13 08:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\translations, languages=['en_SG', 'en']
11-13 08:16 INFO   root: CD menu finished
11-13 08:16 INFO   root: Running the installer...
11-13 08:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\translations, languages=['en_SG', 'en']
11-13 08:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\translations, languages=['en_SG', 'en']
11-13 08:16 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=koojiehui
11-13 08:16 INFO   root: Received settings
11-13 08:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\translations, languages=['en_US', 'en']
11-13 08:16 DEBUG  TaskList: # Running tasklist...
11-13 08:16 DEBUG  TaskList: ## Running select_target_dir...
11-13 08:16 INFO   WindowsBackend: Installing into C:\ubuntu
11-13 08:16 DEBUG  TaskList: ## Finished select_target_dir
11-13 08:16 DEBUG  TaskList: ## Running create_dir_structure...
11-13 08:16 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-13 08:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-13 08:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-13 08:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-13 08:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-13 08:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-13 08:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-13 08:16 DEBUG  TaskList: ## Finished create_dir_structure
11-13 08:16 DEBUG  TaskList: ## Running uncompress_target_dir...
11-13 08:16 DEBUG  TaskList: ## Finished uncompress_target_dir
11-13 08:16 DEBUG  TaskList: ## Running create_uninstaller...
11-13 08:16 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-13 08:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-13 08:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-13 08:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-13 08:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-13 08:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
11-13 08:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-13 08:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-13 08:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-13 08:16 DEBUG  TaskList: ## Finished create_uninstaller
11-13 08:16 DEBUG  TaskList: ## Running copy_installation_files...
11-13 08:16 DEBUG  WindowsBackend: Copying C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-13 08:16 DEBUG  WindowsBackend: Copying C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\winboot -> C:\ubuntu\winboot
11-13 08:16 DEBUG  WindowsBackend: Copying C:\Users\KOOJIE~1\AppData\Local\Temp\pyl5CA.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-13 08:16 DEBUG  TaskList: ## Finished copy_installation_files
11-13 08:16 DEBUG  TaskList: ## Running get_iso...
11-13 08:16 DEBUG  TaskList: New task copy_file
11-13 08:16 DEBUG  TaskList: ### Running copy_file...
11-13 08:18 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-13 08:18 DEBUG  TaskList: # Cancelling tasklist
11-13 08:18 DEBUG  TaskList: New task check_iso
11-13 08:18 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
11-13 08:18 DEBUG  CommonBackend: Searching for local ISO
11-13 08:18 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-13 08:18 DEBUG  TaskList: New task get_metalink
11-13 08:18 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-13 08:18 DEBUG  TaskList: # Cancelling tasklist
11-13 08:18 DEBUG  TaskList: # Finished tasklist"



above was the whole log file... again sorry for my inexperience XD

---

### Post by bcbc on 2010-11-12
It seems like it ran successfully when the .iso was on H: but now you are getting a error installing from the CD/DVD drive. Some CD/DVD drives have issues apparently.

Try running wubi.exe with the downloaded .iso in the same folder.

---

