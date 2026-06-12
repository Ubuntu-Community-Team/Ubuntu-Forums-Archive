---
title: "Installation error - please help!!"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by journeyousglory on 2011-01-18
I am having trouble installing ubuntu netbook edition onto my ASUS Eee PC 1015PEM-PU17-RD. I used a usb drive and when I choose Demo and Install, the program that helps me to do that comes up, loads, then halfway through stops with this message:
 
An error occurred:
 
Could not retrieve the required installation files
 
For more information, please see the log file: c:\users\username\appdata\local\temp\wubi-10.10-rev197
 
the log file includes the following:
 
```
01-14 23:42 INFO   root: === wubi 10.10 rev197 ===
01-14 23:42 DEBUG  root: Logfile is c:\users\journe~1\appdata\local\temp\wubi-10.10-rev197.log
01-14 23:42 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
01-14 23:42 DEBUG  CommonBackend: data_dir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp\data
01-14 23:42 DEBUG  WindowsBackend: 7z=C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp\bin\7z.exe
01-14 23:42 DEBUG  CommonBackend: Fetching basic info...
01-14 23:42 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-14 23:42 DEBUG  CommonBackend: platform=win32
01-14 23:42 DEBUG  CommonBackend: osname=nt
01-14 23:42 DEBUG  CommonBackend: language=en_US
01-14 23:42 DEBUG  CommonBackend: encoding=cp1252
01-14 23:42 DEBUG  WindowsBackend: arch=amd64
01-14 23:42 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp\data\isolist.ini
01-14 23:42 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-14 23:42 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-14 23:42 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-14 23:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-14 23:42 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-14 23:42 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-14 23:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-14 23:42 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-14 23:42 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-14 23:42 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-14 23:42 DEBUG  WindowsBackend: Fetching host info...
01-14 23:42 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-14 23:42 DEBUG  WindowsBackend: windows version=vista
01-14 23:42 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-14 23:42 DEBUG  WindowsBackend: windows_sp=None
01-14 23:42 DEBUG  WindowsBackend: windows_build=7600
01-14 23:42 DEBUG  WindowsBackend: gmt=-8
01-14 23:42 DEBUG  WindowsBackend: country=US
01-14 23:42 DEBUG  WindowsBackend: timezone=America/Los_Angeles
01-14 23:42 DEBUG  WindowsBackend: windows_username=journeyous glory
01-14 23:42 DEBUG  WindowsBackend: user_full_name=journeyous glory
01-14 23:42 DEBUG  WindowsBackend: user_directory=C:\Users\journeyous glory
01-14 23:42 DEBUG  WindowsBackend: windows_language_code=1033
01-14 23:42 DEBUG  WindowsBackend: windows_language=English
01-14 23:42 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N550   @ 1.50GHz
01-14 23:42 DEBUG  WindowsBackend: bootloader=vista
01-14 23:42 DEBUG  WindowsBackend: system_drive=Drive(C: hd 81009.9335938 mb free ntfs)
01-14 23:42 DEBUG  WindowsBackend: drive=Drive(C: hd 81009.9335938 mb free ntfs)
01-14 23:42 DEBUG  WindowsBackend: drive=Drive(D: hd 120599.035156 mb free ntfs)
01-14 23:42 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
01-14 23:42 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-14 23:42 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-14 23:42 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-14 23:42 DEBUG  WindowsBackend: keyboard_id=67699721
01-14 23:42 DEBUG  WindowsBackend: keyboard_layout=us
01-14 23:42 DEBUG  WindowsBackend: keyboard_variant=
01-14 23:42 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-14 23:42 DEBUG  CommonBackend: locale=en_US.UTF-8
01-14 23:42 DEBUG  WindowsBackend: total_memory_mb=2038.1171875
01-14 23:42 DEBUG  CommonBackend: Searching ISOs on USB devices
01-14 23:42 DEBUG  CommonBackend: Searching for local CDs
01-14 23:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp is a valid Ubuntu CD
01-14 23:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp is a valid Ubuntu CD
01-14 23:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp is a valid Ubuntu Netbook CD
01-14 23:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp is a valid Kubuntu CD
01-14 23:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp is a valid Kubuntu CD
01-14 23:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp is a valid Kubuntu Netbook CD
01-14 23:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp is a valid Xubuntu CD
01-14 23:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp is a valid Xubuntu CD
01-14 23:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp is a valid Mythbuntu CD
01-14 23:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp is a valid Mythbuntu CD
01-14 23:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 23:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 23:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-14 23:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 23:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 23:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-14 23:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 23:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 23:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 23:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 23:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 23:42 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
01-14 23:42 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
01-14 23:42 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-14 23:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 23:42 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-14 23:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-14 23:42 INFO   Distro: Found a valid CD for Ubuntu Netbook: E:\
01-14 23:42 INFO   root: Running the CD menu...
01-14 23:42 DEBUG  WindowsFrontend: __init__...
01-14 23:42 DEBUG  WindowsFrontend: on_init...
01-14 23:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp\translations, languages=['en_US', 'en']
01-14 23:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl9F81.tmp\translations, languages=['en_US', 'en']
01-14 23:43 INFO   root: CD menu finished
01-14 23:43 INFO   root: Rebooting
01-14 23:43 DEBUG  TaskList: # Running tasklist...
01-14 23:43 DEBUG  TaskList: ## Running reboot...
01-14 23:43 DEBUG  TaskList: ## Finished reboot
01-14 23:43 DEBUG  TaskList: # Finished tasklist
01-14 23:43 DEBUG  root: application.quit
01-14 23:43 DEBUG  WindowsFrontend: frontend.quit
01-14 23:43 DEBUG  WindowsFrontend: frontend.on_quit
01-14 23:43 DEBUG  root: application.on_quit
01-14 23:43 INFO   root: sys.exit
01-14 23:46 INFO   root: === wubi 10.10 rev197 ===
01-14 23:46 DEBUG  root: Logfile is c:\users\journe~1\appdata\local\temp\wubi-10.10-rev197.log
01-14 23:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
01-14 23:46 DEBUG  CommonBackend: data_dir=C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp\data
01-14 23:46 DEBUG  WindowsBackend: 7z=C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp\bin\7z.exe
01-14 23:46 DEBUG  CommonBackend: Fetching basic info...
01-14 23:46 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-14 23:46 DEBUG  CommonBackend: platform=win32
01-14 23:46 DEBUG  CommonBackend: osname=nt
01-14 23:46 DEBUG  CommonBackend: language=en_US
01-14 23:46 DEBUG  CommonBackend: encoding=cp1252
01-14 23:46 DEBUG  WindowsBackend: arch=amd64
01-14 23:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp\data\isolist.ini
01-14 23:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-14 23:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-14 23:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-14 23:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-14 23:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-14 23:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-14 23:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-14 23:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-14 23:46 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-14 23:46 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-14 23:46 DEBUG  WindowsBackend: Fetching host info...
01-14 23:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-14 23:46 DEBUG  WindowsBackend: windows version=vista
01-14 23:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-14 23:46 DEBUG  WindowsBackend: windows_sp=None
01-14 23:46 DEBUG  WindowsBackend: windows_build=7600
01-14 23:46 DEBUG  WindowsBackend: gmt=-8
01-14 23:46 DEBUG  WindowsBackend: country=US
01-14 23:46 DEBUG  WindowsBackend: timezone=America/Los_Angeles
01-14 23:46 DEBUG  WindowsBackend: windows_username=journeyous glory
01-14 23:46 DEBUG  WindowsBackend: user_full_name=journeyous glory
01-14 23:46 DEBUG  WindowsBackend: user_directory=C:\Users\journeyous glory
01-14 23:46 DEBUG  WindowsBackend: windows_language_code=1033
01-14 23:46 DEBUG  WindowsBackend: windows_language=English
01-14 23:46 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N550   @ 1.50GHz
01-14 23:46 DEBUG  WindowsBackend: bootloader=vista
01-14 23:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 81081.7734375 mb free ntfs)
01-14 23:46 DEBUG  WindowsBackend: drive=Drive(C: hd 81081.7734375 mb free ntfs)
01-14 23:46 DEBUG  WindowsBackend: drive=Drive(D: hd 120599.035156 mb free ntfs)
01-14 23:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
01-14 23:46 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-14 23:46 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-14 23:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-14 23:46 DEBUG  WindowsBackend: keyboard_id=67699721
01-14 23:46 DEBUG  WindowsBackend: keyboard_layout=us
01-14 23:46 DEBUG  WindowsBackend: keyboard_variant=
01-14 23:46 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-14 23:46 DEBUG  CommonBackend: locale=en_US.UTF-8
01-14 23:46 DEBUG  WindowsBackend: total_memory_mb=2038.1171875
01-14 23:46 DEBUG  CommonBackend: Searching ISOs on USB devices
01-14 23:46 DEBUG  CommonBackend: Searching for local CDs
01-14 23:46 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp is a valid Ubuntu CD
01-14 23:46 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp is a valid Ubuntu CD
01-14 23:46 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp is a valid Ubuntu Netbook CD
01-14 23:46 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp is a valid Kubuntu CD
01-14 23:46 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp is a valid Kubuntu CD
01-14 23:46 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp is a valid Kubuntu Netbook CD
01-14 23:46 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp is a valid Xubuntu CD
01-14 23:46 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp is a valid Xubuntu CD
01-14 23:46 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp is a valid Mythbuntu CD
01-14 23:46 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp is a valid Mythbuntu CD
01-14 23:46 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 23:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 23:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-14 23:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 23:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 23:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-14 23:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 23:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 23:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 23:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 23:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 23:46 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
01-14 23:46 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
01-14 23:46 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-14 23:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 23:46 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-14 23:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-14 23:46 INFO   Distro: Found a valid CD for Ubuntu Netbook: E:\
01-14 23:46 INFO   root: Running the CD menu...
01-14 23:46 DEBUG  WindowsFrontend: __init__...
01-14 23:46 DEBUG  WindowsFrontend: on_init...
01-14 23:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp\translations, languages=['en_US', 'en']
01-14 23:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pylA5CF.tmp\translations, languages=['en_US', 'en']
01-14 23:46 INFO   root: CD menu finished
01-14 23:46 INFO   root: Already installed, running the uninstaller...
01-14 23:46 INFO   root: Running the uninstaller...
01-14 23:46 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
01-14 23:46 DEBUG  root: application.quit
01-14 23:46 DEBUG  WindowsFrontend: frontend.quit
01-14 23:46 DEBUG  WindowsFrontend: frontend.on_quit
01-14 23:46 DEBUG  root: application.on_quit
01-14 23:46 INFO   root: sys.exit
01-14 23:47 INFO   root: === wubi 10.10 rev197 ===
01-14 23:47 DEBUG  root: Logfile is c:\users\journe~1\appdata\local\temp\wubi-10.10-rev197.log
01-14 23:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
01-14 23:47 DEBUG  CommonBackend: data_dir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp\data
01-14 23:47 DEBUG  WindowsBackend: 7z=C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp\bin\7z.exe
01-14 23:47 DEBUG  CommonBackend: Fetching basic info...
01-14 23:47 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-14 23:47 DEBUG  CommonBackend: platform=win32
01-14 23:47 DEBUG  CommonBackend: osname=nt
01-14 23:47 DEBUG  CommonBackend: language=en_US
01-14 23:47 DEBUG  CommonBackend: encoding=cp1252
01-14 23:47 DEBUG  WindowsBackend: arch=amd64
01-14 23:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp\data\isolist.ini
01-14 23:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-14 23:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-14 23:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-14 23:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-14 23:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-14 23:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-14 23:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-14 23:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-14 23:47 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-14 23:47 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-14 23:47 DEBUG  WindowsBackend: Fetching host info...
01-14 23:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-14 23:47 DEBUG  WindowsBackend: windows version=vista
01-14 23:47 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-14 23:47 DEBUG  WindowsBackend: windows_sp=None
01-14 23:47 DEBUG  WindowsBackend: windows_build=7600
01-14 23:47 DEBUG  WindowsBackend: gmt=-8
01-14 23:47 DEBUG  WindowsBackend: country=US
01-14 23:47 DEBUG  WindowsBackend: timezone=America/Los_Angeles
01-14 23:47 DEBUG  WindowsBackend: windows_username=journeyous glory
01-14 23:47 DEBUG  WindowsBackend: user_full_name=journeyous glory
01-14 23:47 DEBUG  WindowsBackend: user_directory=C:\Users\journeyous glory
01-14 23:47 DEBUG  WindowsBackend: windows_language_code=1033
01-14 23:47 DEBUG  WindowsBackend: windows_language=English
01-14 23:47 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N550   @ 1.50GHz
01-14 23:47 DEBUG  WindowsBackend: bootloader=vista
01-14 23:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 81078.1914063 mb free ntfs)
01-14 23:47 DEBUG  WindowsBackend: drive=Drive(C: hd 81078.1914063 mb free ntfs)
01-14 23:47 DEBUG  WindowsBackend: drive=Drive(D: hd 120599.035156 mb free ntfs)
01-14 23:47 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
01-14 23:47 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-14 23:47 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-14 23:47 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-14 23:47 DEBUG  WindowsBackend: keyboard_id=67699721
01-14 23:47 DEBUG  WindowsBackend: keyboard_layout=us
01-14 23:47 DEBUG  WindowsBackend: keyboard_variant=
01-14 23:47 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-14 23:47 DEBUG  CommonBackend: locale=en_US.UTF-8
01-14 23:47 DEBUG  WindowsBackend: total_memory_mb=2038.1171875
01-14 23:47 DEBUG  CommonBackend: Searching ISOs on USB devices
01-14 23:47 DEBUG  CommonBackend: Searching for local CDs
01-14 23:47 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp is a valid Ubuntu CD
01-14 23:47 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp is a valid Ubuntu CD
01-14 23:47 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp is a valid Ubuntu Netbook CD
01-14 23:47 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp is a valid Kubuntu CD
01-14 23:47 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp is a valid Kubuntu CD
01-14 23:47 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp is a valid Kubuntu Netbook CD
01-14 23:47 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp is a valid Xubuntu CD
01-14 23:47 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp is a valid Xubuntu CD
01-14 23:47 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp is a valid Mythbuntu CD
01-14 23:47 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp is a valid Mythbuntu CD
01-14 23:47 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-14 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-14 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 23:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 23:47 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
01-14 23:47 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
01-14 23:47 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-14 23:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 23:47 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-14 23:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-14 23:47 INFO   Distro: Found a valid CD for Ubuntu Netbook: E:\
01-14 23:47 INFO   root: Running the CD menu...
01-14 23:47 DEBUG  WindowsFrontend: __init__...
01-14 23:47 DEBUG  WindowsFrontend: on_init...
01-14 23:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp\translations, languages=['en_US', 'en']
01-14 23:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl78E6.tmp\translations, languages=['en_US', 'en']
01-14 23:47 INFO   root: CD menu finished
01-14 23:47 INFO   root: Already installed, running the uninstaller...
01-14 23:47 INFO   root: Running the uninstaller...
01-14 23:47 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
01-14 23:47 DEBUG  root: application.quit
01-14 23:47 DEBUG  WindowsFrontend: frontend.quit
01-14 23:47 DEBUG  WindowsFrontend: frontend.on_quit
01-14 23:47 DEBUG  root: application.on_quit
01-14 23:47 INFO   root: sys.exit
01-14 23:48 INFO   root: === wubi 10.10 rev197 ===
01-14 23:48 DEBUG  root: Logfile is c:\users\journe~1\appdata\local\temp\wubi-10.10-rev197.log
01-14 23:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
01-14 23:48 DEBUG  CommonBackend: data_dir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp\data
01-14 23:48 DEBUG  WindowsBackend: 7z=C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp\bin\7z.exe
01-14 23:48 DEBUG  CommonBackend: Fetching basic info...
01-14 23:48 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-14 23:48 DEBUG  CommonBackend: platform=win32
01-14 23:48 DEBUG  CommonBackend: osname=nt
01-14 23:48 DEBUG  CommonBackend: language=en_US
01-14 23:48 DEBUG  CommonBackend: encoding=cp1252
01-14 23:48 DEBUG  WindowsBackend: arch=amd64
01-14 23:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp\data\isolist.ini
01-14 23:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-14 23:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-14 23:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-14 23:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-14 23:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-14 23:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-14 23:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-14 23:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-14 23:48 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-14 23:48 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-14 23:48 DEBUG  WindowsBackend: Fetching host info...
01-14 23:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-14 23:48 DEBUG  WindowsBackend: windows version=vista
01-14 23:48 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-14 23:48 DEBUG  WindowsBackend: windows_sp=None
01-14 23:48 DEBUG  WindowsBackend: windows_build=7600
01-14 23:48 DEBUG  WindowsBackend: gmt=-8
01-14 23:48 DEBUG  WindowsBackend: country=US
01-14 23:48 DEBUG  WindowsBackend: timezone=America/Los_Angeles
01-14 23:48 DEBUG  WindowsBackend: windows_username=journeyous glory
01-14 23:48 DEBUG  WindowsBackend: user_full_name=journeyous glory
01-14 23:48 DEBUG  WindowsBackend: user_directory=C:\Users\journeyous glory
01-14 23:48 DEBUG  WindowsBackend: windows_language_code=1033
01-14 23:48 DEBUG  WindowsBackend: windows_language=English
01-14 23:48 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N550   @ 1.50GHz
01-14 23:48 DEBUG  WindowsBackend: bootloader=vista
01-14 23:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 81077.4023438 mb free ntfs)
01-14 23:48 DEBUG  WindowsBackend: drive=Drive(C: hd 81077.4023438 mb free ntfs)
01-14 23:48 DEBUG  WindowsBackend: drive=Drive(D: hd 120599.035156 mb free ntfs)
01-14 23:48 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
01-14 23:48 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-14 23:48 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-14 23:48 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-14 23:48 DEBUG  WindowsBackend: keyboard_id=67699721
01-14 23:48 DEBUG  WindowsBackend: keyboard_layout=us
01-14 23:48 DEBUG  WindowsBackend: keyboard_variant=
01-14 23:48 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-14 23:48 DEBUG  CommonBackend: locale=en_US.UTF-8
01-14 23:48 DEBUG  WindowsBackend: total_memory_mb=2038.1171875
01-14 23:48 DEBUG  CommonBackend: Searching ISOs on USB devices
01-14 23:48 DEBUG  CommonBackend: Searching for local CDs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp is a valid Ubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp is a valid Ubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp is a valid Ubuntu Netbook CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp is a valid Kubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp is a valid Kubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp is a valid Kubuntu Netbook CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp is a valid Xubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp is a valid Xubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp is a valid Mythbuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp is a valid Mythbuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 23:48 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
01-14 23:48 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
01-14 23:48 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-14 23:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 23:48 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-14 23:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-14 23:48 INFO   Distro: Found a valid CD for Ubuntu Netbook: E:\
01-14 23:48 INFO   root: Running the CD menu...
01-14 23:48 DEBUG  WindowsFrontend: __init__...
01-14 23:48 DEBUG  WindowsFrontend: on_init...
01-14 23:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp\translations, languages=['en_US', 'en']
01-14 23:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl428B.tmp\translations, languages=['en_US', 'en']
01-14 23:48 INFO   root: CD menu finished
01-14 23:48 INFO   root: Already installed, running the uninstaller...
01-14 23:48 INFO   root: Running the uninstaller...
01-14 23:48 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
01-14 23:48 DEBUG  root: application.quit
01-14 23:48 DEBUG  WindowsFrontend: frontend.quit
01-14 23:48 DEBUG  WindowsFrontend: frontend.on_quit
01-14 23:48 DEBUG  root: application.on_quit
01-14 23:48 INFO   root: sys.exit
01-14 23:48 INFO   root: === wubi 10.10 rev197 ===
01-14 23:48 DEBUG  root: Logfile is c:\users\journe~1\appdata\local\temp\wubi-10.10-rev197.log
01-14 23:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
01-14 23:48 DEBUG  CommonBackend: data_dir=C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\data
01-14 23:48 DEBUG  WindowsBackend: 7z=C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\bin\7z.exe
01-14 23:48 DEBUG  CommonBackend: Fetching basic info...
01-14 23:48 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-14 23:48 DEBUG  CommonBackend: platform=win32
01-14 23:48 DEBUG  CommonBackend: osname=nt
01-14 23:48 DEBUG  CommonBackend: language=en_US
01-14 23:48 DEBUG  CommonBackend: encoding=cp1252
01-14 23:48 DEBUG  WindowsBackend: arch=amd64
01-14 23:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\data\isolist.ini
01-14 23:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-14 23:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-14 23:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-14 23:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-14 23:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-14 23:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-14 23:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-14 23:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-14 23:48 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-14 23:48 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-14 23:48 DEBUG  WindowsBackend: Fetching host info...
01-14 23:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-14 23:48 DEBUG  WindowsBackend: windows version=vista
01-14 23:48 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-14 23:48 DEBUG  WindowsBackend: windows_sp=None
01-14 23:48 DEBUG  WindowsBackend: windows_build=7600
01-14 23:48 DEBUG  WindowsBackend: gmt=-8
01-14 23:48 DEBUG  WindowsBackend: country=US
01-14 23:48 DEBUG  WindowsBackend: timezone=America/Los_Angeles
01-14 23:48 DEBUG  WindowsBackend: windows_username=journeyous glory
01-14 23:48 DEBUG  WindowsBackend: user_full_name=journeyous glory
01-14 23:48 DEBUG  WindowsBackend: user_directory=C:\Users\journeyous glory
01-14 23:48 DEBUG  WindowsBackend: windows_language_code=1033
01-14 23:48 DEBUG  WindowsBackend: windows_language=English
01-14 23:48 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N550   @ 1.50GHz
01-14 23:48 DEBUG  WindowsBackend: bootloader=vista
01-14 23:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 81187.6445313 mb free ntfs)
01-14 23:48 DEBUG  WindowsBackend: drive=Drive(C: hd 81187.6445313 mb free ntfs)
01-14 23:48 DEBUG  WindowsBackend: drive=Drive(D: hd 120599.035156 mb free ntfs)
01-14 23:48 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
01-14 23:48 DEBUG  WindowsBackend: uninstaller_path=None
01-14 23:48 DEBUG  WindowsBackend: previous_target_dir=None
01-14 23:48 DEBUG  WindowsBackend: previous_distro_name=None
01-14 23:48 DEBUG  WindowsBackend: keyboard_id=67699721
01-14 23:48 DEBUG  WindowsBackend: keyboard_layout=us
01-14 23:48 DEBUG  WindowsBackend: keyboard_variant=
01-14 23:48 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-14 23:48 DEBUG  CommonBackend: locale=en_US.UTF-8
01-14 23:48 DEBUG  WindowsBackend: total_memory_mb=2038.1171875
01-14 23:48 DEBUG  CommonBackend: Searching ISOs on USB devices
01-14 23:48 DEBUG  CommonBackend: Searching for local CDs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp is a valid Ubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp is a valid Ubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp is a valid Ubuntu Netbook CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp is a valid Kubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp is a valid Kubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp is a valid Kubuntu Netbook CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp is a valid Xubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp is a valid Xubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp is a valid Mythbuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp is a valid Mythbuntu CD
01-14 23:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-14 23:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-14 23:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 23:48 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
01-14 23:48 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
01-14 23:48 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-14 23:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-14 23:48 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-14 23:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-14 23:48 INFO   Distro: Found a valid CD for Ubuntu Netbook: E:\
01-14 23:48 INFO   root: Running the CD menu...
01-14 23:48 DEBUG  WindowsFrontend: __init__...
01-14 23:48 DEBUG  WindowsFrontend: on_init...
01-14 23:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\translations, languages=['en_US', 'en']
01-14 23:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\translations, languages=['en_US', 'en']
01-14 23:48 INFO   root: CD menu finished
01-14 23:48 INFO   root: Running the CD boot helper...
01-14 23:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\translations, languages=['en_US', 'en']
01-14 23:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\translations, languages=['en_US', 'en']
01-14 23:48 INFO   root: CD boot helper confirmed
01-14 23:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\translations, languages=['en_US', 'en']
01-14 23:48 DEBUG  TaskList: # Running tasklist...
01-14 23:48 DEBUG  TaskList: ## Running select_target_dir...
01-14 23:48 INFO   WindowsBackend: Installing into C:\ubuntu
01-14 23:48 DEBUG  TaskList: ## Finished select_target_dir
01-14 23:48 DEBUG  TaskList: ## Running create_dir_structure...
01-14 23:48 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-14 23:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-14 23:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-14 23:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-14 23:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-14 23:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-14 23:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-14 23:48 DEBUG  TaskList: ## Finished create_dir_structure
01-14 23:48 DEBUG  TaskList: ## Running uncompress_target_dir...
01-14 23:48 DEBUG  TaskList: ## Finished uncompress_target_dir
01-14 23:48 DEBUG  TaskList: ## Running create_uninstaller...
01-14 23:48 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-14 23:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-14 23:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-14 23:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
01-14 23:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
01-14 23:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
01-14 23:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
01-14 23:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-14 23:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-14 23:48 DEBUG  TaskList: ## Finished create_uninstaller
01-14 23:48 DEBUG  TaskList: ## Running copy_installation_files...
01-14 23:48 DEBUG  WindowsBackend: Copying C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-14 23:48 DEBUG  WindowsBackend: Copying C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\winboot -> C:\ubuntu\winboot
01-14 23:48 DEBUG  WindowsBackend: Copying C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
01-14 23:48 DEBUG  TaskList: ## Finished copy_installation_files
01-14 23:48 DEBUG  TaskList: ## Running use_cd...
01-14 23:48 DEBUG  TaskList: New task copy_file
01-14 23:48 DEBUG  TaskList: ### Running copy_file...
01-14 23:53 DEBUG  TaskList: ### Finished copy_file
01-14 23:53 DEBUG  TaskList: New task check_iso
01-14 23:53 DEBUG  TaskList: ### Running check_iso...
01-14 23:53 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
01-14 23:53 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\installation.iso
01-14 23:53 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
01-14 23:53 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
01-14 23:53 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
01-14 23:53 INFO   Distro: Found a valid iso for Ubuntu Netbook: C:\ubuntu\install\installation.iso
01-14 23:53 DEBUG  TaskList: New task get_metalink
01-14 23:53 DEBUG  TaskList: #### Running get_metalink...
01-14 23:53 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-netbook-i386.metalink](http://releases.ubuntu.com/10.10/ubuntu-10.10-netbook-i386.metalink) > C:\ubuntu\install
01-14 23:53 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.10-netbook-i386.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-netbook-i386.metalink, basename=ubuntu-10.10-netbook-i386.metalink, length=9071, text=None
01-14 23:53 DEBUG  downloader: download finished (read 9071 bytes)
01-14 23:53 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink](http://releases.ubuntu.com/10.10/MD5SUMS-metalink) > C:\ubuntu\install
01-14 23:53 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
01-14 23:53 DEBUG  downloader: download finished (read 488 bytes)
01-14 23:53 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
01-14 23:53 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
01-14 23:53 DEBUG  downloader: download finished (read 198 bytes)
01-14 23:53 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
01-14 23:53 INFO   saplog: Checking block bindings..
01-14 23:53 INFO   saplog: Key verified successfully.
01-14 23:53 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink
01-14 23:53 DEBUG  TaskList: #### Finished get_metalink
01-14 23:53 DEBUG  TaskList: New task get_file_md5
01-14 23:53 DEBUG  TaskList: #### Running get_file_md5...
01-14 23:53 DEBUG  TaskList: #### Finished get_file_md5
01-14 23:53 DEBUG  TaskList: ### Finished check_iso
01-14 23:53 DEBUG  TaskList: ## Finished use_cd
01-14 23:53 DEBUG  TaskList: ## Running extract_kernel...
01-14 23:53 DEBUG  CommonBackend: Copying files from CD E:\
01-14 23:53 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
01-14 23:53 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
01-14 23:53 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 50065155d2b4c37740b0e123cbfebc43 == 50065155d2b4c37740b0e123cbfebc43
01-14 23:53 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
01-14 23:53 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 27cfb218196cea72593d207de0cb30a2 == 27cfb218196cea72593d207de0cb30a2
01-14 23:53 DEBUG  TaskList: ## Finished extract_kernel
01-14 23:53 DEBUG  TaskList: ## Running create_preseed_cdboot...
01-14 23:53 DEBUG  TaskList: ## Finished create_preseed_cdboot
01-14 23:53 DEBUG  TaskList: ## Running modify_bootloader...
01-14 23:53 DEBUG  TaskList: New task modify_bcd
01-14 23:53 DEBUG  TaskList: ### Running modify_bcd...
01-14 23:53 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 81187.6445313 mb free ntfs)
01-14 23:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {a2decfdf-6352-11f5-87b1-be15d4eb8289}
01-14 23:53 DEBUG  TaskList: ### Finished modify_bcd
01-14 23:53 DEBUG  TaskList: New task modify_bcd
01-14 23:53 DEBUG  TaskList: ### Running modify_bcd...
01-14 23:53 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 120599.035156 mb free ntfs)
01-14 23:53 DEBUG  WindowsBackend: BCD has already been modified
01-14 23:53 DEBUG  TaskList: ### Finished modify_bcd
01-14 23:53 DEBUG  TaskList: ## Finished modify_bootloader
01-14 23:53 DEBUG  TaskList: ## Running modify_grub_configuration...
01-14 23:53 DEBUG  TaskList: ## Finished modify_grub_configuration
01-14 23:53 DEBUG  TaskList: ## Running uncompress_files...
01-14 23:53 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
01-14 23:53 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
01-14 23:53 DEBUG  TaskList: ## Finished uncompress_files
01-14 23:53 DEBUG  TaskList: ## Running eject_cd...
01-14 23:53 DEBUG  TaskList: ## Finished eject_cd
01-14 23:53 DEBUG  TaskList: # Finished tasklist
01-14 23:53 INFO   root: Almost finished installing
01-14 23:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pylB48F.tmp\translations, languages=['en_US', 'en']
01-14 23:55 INFO   root: Finished installation
01-14 23:55 INFO   root: Rebooting
01-14 23:55 DEBUG  TaskList: # Running tasklist...
01-14 23:55 DEBUG  TaskList: ## Running reboot...
01-14 23:55 DEBUG  TaskList: ## Finished reboot
01-14 23:55 DEBUG  TaskList: # Finished tasklist
01-14 23:55 DEBUG  root: application.quit
01-14 23:55 DEBUG  WindowsFrontend: frontend.quit
01-14 23:55 DEBUG  WindowsFrontend: frontend.on_quit
01-14 23:55 DEBUG  root: application.on_quit
01-14 23:55 INFO   root: sys.exit
01-17 10:17 INFO   root: === wubi 10.10 rev197 ===
01-17 10:17 DEBUG  root: Logfile is c:\users\journe~1\appdata\local\temp\wubi-10.10-rev197.log
01-17 10:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
01-17 10:17 DEBUG  CommonBackend: data_dir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\data
01-17 10:17 DEBUG  WindowsBackend: 7z=C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\bin\7z.exe
01-17 10:17 DEBUG  CommonBackend: Fetching basic info...
01-17 10:17 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
01-17 10:17 DEBUG  CommonBackend: platform=win32
01-17 10:17 DEBUG  CommonBackend: osname=nt
01-17 10:17 DEBUG  CommonBackend: language=en_US
01-17 10:17 DEBUG  CommonBackend: encoding=cp1252
01-17 10:17 DEBUG  WindowsBackend: arch=amd64
01-17 10:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\data\isolist.ini
01-17 10:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-17 10:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-17 10:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-17 10:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-17 10:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-17 10:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-17 10:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-17 10:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-17 10:17 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-17 10:17 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-17 10:17 DEBUG  WindowsBackend: Fetching host info...
01-17 10:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-17 10:17 DEBUG  WindowsBackend: windows version=vista
01-17 10:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-17 10:17 DEBUG  WindowsBackend: windows_sp=None
01-17 10:17 DEBUG  WindowsBackend: windows_build=7600
01-17 10:17 DEBUG  WindowsBackend: gmt=-8
01-17 10:17 DEBUG  WindowsBackend: country=US
01-17 10:17 DEBUG  WindowsBackend: timezone=America/Los_Angeles
01-17 10:17 DEBUG  WindowsBackend: windows_username=journeyous glory
01-17 10:17 DEBUG  WindowsBackend: user_full_name=journeyous glory
01-17 10:17 DEBUG  WindowsBackend: user_directory=C:\Users\journeyous glory
01-17 10:17 DEBUG  WindowsBackend: windows_language_code=1033
01-17 10:17 DEBUG  WindowsBackend: windows_language=English
01-17 10:17 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N550   @ 1.50GHz
01-17 10:17 DEBUG  WindowsBackend: bootloader=vista
01-17 10:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 77443.7695313 mb free ntfs)
01-17 10:17 DEBUG  WindowsBackend: drive=Drive(C: hd 77443.7695313 mb free ntfs)
01-17 10:17 DEBUG  WindowsBackend: drive=Drive(D: hd 120599.03125 mb free ntfs)
01-17 10:17 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-17 10:17 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-17 10:17 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
01-17 10:17 DEBUG  WindowsBackend: keyboard_id=67699721
01-17 10:17 DEBUG  WindowsBackend: keyboard_layout=us
01-17 10:17 DEBUG  WindowsBackend: keyboard_variant=
01-17 10:17 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-17 10:17 DEBUG  CommonBackend: locale=en_US.UTF-8
01-17 10:17 DEBUG  WindowsBackend: total_memory_mb=2038.1171875
01-17 10:17 DEBUG  CommonBackend: Searching ISOs on USB devices
01-17 10:17 DEBUG  CommonBackend: Searching for local CDs
01-17 10:17 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp is a valid Ubuntu CD
01-17 10:17 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp is a valid Ubuntu CD
01-17 10:17 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp is a valid Ubuntu Netbook CD
01-17 10:17 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp is a valid Kubuntu CD
01-17 10:17 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp is a valid Kubuntu CD
01-17 10:17 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp is a valid Kubuntu Netbook CD
01-17 10:17 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp is a valid Xubuntu CD
01-17 10:17 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp is a valid Xubuntu CD
01-17 10:17 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp is a valid Mythbuntu CD
01-17 10:17 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp is a valid Mythbuntu CD
01-17 10:17 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 10:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 10:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-17 10:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 10:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 10:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-17 10:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 10:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 10:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 10:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 10:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 10:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 10:17 INFO   root: Running the uninstaller...
01-17 10:17 INFO   CommonBackend: This is the uninstaller running
01-17 10:17 DEBUG  WindowsFrontend: __init__...
01-17 10:17 DEBUG  WindowsFrontend: on_init...
01-17 10:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\translations, languages=['en_US', 'en']
01-17 10:17 INFO   root: Received settings
01-17 10:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\translations, languages=['en_US', 'en']
01-17 10:17 DEBUG  TaskList: # Running tasklist...
01-17 10:17 DEBUG  TaskList: ## Running Backup ISO...
01-17 10:17 DEBUG  TaskList: ## Finished Backup ISO
01-17 10:17 DEBUG  TaskList: ## Running Remove bootloader entry...
01-17 10:17 DEBUG  WindowsBackend: Removing bcd entry {a2decfdf-6352-11f5-87b1-be15d4eb8289}
01-17 10:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
01-17 10:17 DEBUG  WindowsBackend: undo_bootini C:
01-17 10:17 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 77443.7695313 mb free ntfs)
01-17 10:17 DEBUG  WindowsBackend: undo_bootini D:
01-17 10:17 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 120599.03125 mb free ntfs)
01-17 10:17 DEBUG  TaskList: ## Finished Remove bootloader entry
01-17 10:17 DEBUG  TaskList: ## Running Remove target dir...
01-17 10:17 DEBUG  CommonBackend: Deleting C:\ubuntu
01-17 10:17 DEBUG  TaskList: ## Finished Remove target dir
01-17 10:17 DEBUG  TaskList: ## Running Remove registry key...
01-17 10:17 DEBUG  TaskList: ## Finished Remove registry key
01-17 10:17 DEBUG  TaskList: # Finished tasklist
01-17 10:17 INFO   root: Almost finished uninstalling
01-17 10:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl693D.tmp\translations, languages=['en_US', 'en']
01-17 10:17 INFO   root: Finished uninstallation
01-17 10:17 DEBUG  root: application.quit
01-17 10:17 DEBUG  WindowsFrontend: frontend.quit
01-17 10:17 DEBUG  WindowsFrontend: frontend.on_quit
01-17 10:17 DEBUG  root: application.on_quit
01-17 10:17 INFO   root: sys.exit
01-17 17:41 INFO   root: === wubi 10.10 rev197 ===
01-17 17:41 DEBUG  root: Logfile is c:\users\journe~1\appdata\local\temp\wubi-10.10-rev197.log
01-17 17:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
01-17 17:41 DEBUG  CommonBackend: data_dir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp\data
01-17 17:41 DEBUG  WindowsBackend: 7z=C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp\bin\7z.exe
01-17 17:41 DEBUG  CommonBackend: Fetching basic info...
01-17 17:41 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-17 17:41 DEBUG  CommonBackend: platform=win32
01-17 17:41 DEBUG  CommonBackend: osname=nt
01-17 17:41 DEBUG  CommonBackend: language=en_US
01-17 17:41 DEBUG  CommonBackend: encoding=cp1252
01-17 17:41 DEBUG  WindowsBackend: arch=amd64
01-17 17:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp\data\isolist.ini
01-17 17:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-17 17:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-17 17:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-17 17:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-17 17:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-17 17:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-17 17:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-17 17:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-17 17:41 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-17 17:41 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-17 17:41 DEBUG  WindowsBackend: Fetching host info...
01-17 17:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-17 17:41 DEBUG  WindowsBackend: windows version=vista
01-17 17:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-17 17:41 DEBUG  WindowsBackend: windows_sp=None
01-17 17:41 DEBUG  WindowsBackend: windows_build=7600
01-17 17:41 DEBUG  WindowsBackend: gmt=-8
01-17 17:41 DEBUG  WindowsBackend: country=US
01-17 17:41 DEBUG  WindowsBackend: timezone=America/Los_Angeles
01-17 17:41 DEBUG  WindowsBackend: windows_username=journeyous glory
01-17 17:41 DEBUG  WindowsBackend: user_full_name=journeyous glory
01-17 17:41 DEBUG  WindowsBackend: user_directory=C:\Users\journeyous glory
01-17 17:41 DEBUG  WindowsBackend: windows_language_code=1033
01-17 17:41 DEBUG  WindowsBackend: windows_language=English
01-17 17:41 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N550   @ 1.50GHz
01-17 17:41 DEBUG  WindowsBackend: bootloader=vista
01-17 17:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 79005.3789063 mb free ntfs)
01-17 17:41 DEBUG  WindowsBackend: drive=Drive(C: hd 79005.3789063 mb free ntfs)
01-17 17:41 DEBUG  WindowsBackend: drive=Drive(D: hd 120599.03125 mb free ntfs)
01-17 17:41 DEBUG  WindowsBackend: drive=Drive(E: removable 265.390625 mb free fat)
01-17 17:41 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-17 17:41 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-17 17:41 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-17 17:41 DEBUG  WindowsBackend: keyboard_id=67699721
01-17 17:41 DEBUG  WindowsBackend: keyboard_layout=us
01-17 17:41 DEBUG  WindowsBackend: keyboard_variant=
01-17 17:41 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-17 17:41 DEBUG  CommonBackend: locale=en_US.UTF-8
01-17 17:41 DEBUG  WindowsBackend: total_memory_mb=2038.1171875
01-17 17:41 DEBUG  CommonBackend: Searching ISOs on USB devices
01-17 17:41 DEBUG  CommonBackend: Searching for local CDs
01-17 17:41 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp is a valid Ubuntu CD
01-17 17:41 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp is a valid Ubuntu CD
01-17 17:41 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp is a valid Ubuntu Netbook CD
01-17 17:41 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp is a valid Kubuntu CD
01-17 17:41 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp is a valid Kubuntu CD
01-17 17:41 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp is a valid Kubuntu Netbook CD
01-17 17:41 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp is a valid Xubuntu CD
01-17 17:41 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp is a valid Xubuntu CD
01-17 17:41 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp is a valid Mythbuntu CD
01-17 17:41 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp is a valid Mythbuntu CD
01-17 17:41 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-17 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-17 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 17:41 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
01-17 17:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
01-17 17:41 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-17 17:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 17:41 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-17 17:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-17 17:41 INFO   Distro: Found a valid CD for Ubuntu Netbook: E:\
01-17 17:41 INFO   root: Running the CD menu...
01-17 17:41 DEBUG  WindowsFrontend: __init__...
01-17 17:41 DEBUG  WindowsFrontend: on_init...
01-17 17:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp\translations, languages=['en_US', 'en']
01-17 17:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl452A.tmp\translations, languages=['en_US', 'en']
01-17 17:42 INFO   root: CD menu finished
01-17 17:42 INFO   root: Already installed, running the uninstaller...
01-17 17:42 INFO   root: Running the uninstaller...
01-17 17:42 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
01-17 17:42 DEBUG  root: application.quit
01-17 17:42 DEBUG  WindowsFrontend: frontend.quit
01-17 17:42 DEBUG  WindowsFrontend: frontend.on_quit
01-17 17:42 DEBUG  root: application.on_quit
01-17 17:42 INFO   root: sys.exit
01-17 17:42 INFO   root: === wubi 10.10 rev197 ===
01-17 17:42 DEBUG  root: Logfile is c:\users\journe~1\appdata\local\temp\wubi-10.10-rev197.log
01-17 17:42 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
01-17 17:42 DEBUG  CommonBackend: data_dir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp\data
01-17 17:42 DEBUG  WindowsBackend: 7z=C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp\bin\7z.exe
01-17 17:42 DEBUG  CommonBackend: Fetching basic info...
01-17 17:42 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-17 17:42 DEBUG  CommonBackend: platform=win32
01-17 17:42 DEBUG  CommonBackend: osname=nt
01-17 17:42 DEBUG  CommonBackend: language=en_US
01-17 17:42 DEBUG  CommonBackend: encoding=cp1252
01-17 17:42 DEBUG  WindowsBackend: arch=amd64
01-17 17:42 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp\data\isolist.ini
01-17 17:42 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-17 17:42 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-17 17:42 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-17 17:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-17 17:42 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-17 17:42 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-17 17:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-17 17:42 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-17 17:42 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-17 17:42 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-17 17:42 DEBUG  WindowsBackend: Fetching host info...
01-17 17:42 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-17 17:42 DEBUG  WindowsBackend: windows version=vista
01-17 17:42 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-17 17:42 DEBUG  WindowsBackend: windows_sp=None
01-17 17:42 DEBUG  WindowsBackend: windows_build=7600
01-17 17:42 DEBUG  WindowsBackend: gmt=-8
01-17 17:42 DEBUG  WindowsBackend: country=US
01-17 17:42 DEBUG  WindowsBackend: timezone=America/Los_Angeles
01-17 17:42 DEBUG  WindowsBackend: windows_username=journeyous glory
01-17 17:42 DEBUG  WindowsBackend: user_full_name=journeyous glory
01-17 17:42 DEBUG  WindowsBackend: user_directory=C:\Users\journeyous glory
01-17 17:42 DEBUG  WindowsBackend: windows_language_code=1033
01-17 17:42 DEBUG  WindowsBackend: windows_language=English
01-17 17:42 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N550   @ 1.50GHz
01-17 17:42 DEBUG  WindowsBackend: bootloader=vista
01-17 17:42 DEBUG  WindowsBackend: system_drive=Drive(C: hd 78993.3515625 mb free ntfs)
01-17 17:42 DEBUG  WindowsBackend: drive=Drive(C: hd 78993.3515625 mb free ntfs)
01-17 17:42 DEBUG  WindowsBackend: drive=Drive(D: hd 120599.03125 mb free ntfs)
01-17 17:42 DEBUG  WindowsBackend: drive=Drive(E: removable 265.390625 mb free fat)
01-17 17:42 DEBUG  WindowsBackend: uninstaller_path=None
01-17 17:42 DEBUG  WindowsBackend: previous_target_dir=None
01-17 17:42 DEBUG  WindowsBackend: previous_distro_name=None
01-17 17:42 DEBUG  WindowsBackend: keyboard_id=67699721
01-17 17:42 DEBUG  WindowsBackend: keyboard_layout=us
01-17 17:42 DEBUG  WindowsBackend: keyboard_variant=
01-17 17:42 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-17 17:42 DEBUG  CommonBackend: locale=en_US.UTF-8
01-17 17:42 DEBUG  WindowsBackend: total_memory_mb=2038.1171875
01-17 17:42 DEBUG  CommonBackend: Searching ISOs on USB devices
01-17 17:42 DEBUG  CommonBackend: Searching for local CDs
01-17 17:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp is a valid Ubuntu CD
01-17 17:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp is a valid Ubuntu CD
01-17 17:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp is a valid Ubuntu Netbook CD
01-17 17:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp is a valid Kubuntu CD
01-17 17:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp is a valid Kubuntu CD
01-17 17:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp is a valid Kubuntu Netbook CD
01-17 17:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp is a valid Xubuntu CD
01-17 17:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp is a valid Xubuntu CD
01-17 17:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp is a valid Mythbuntu CD
01-17 17:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp is a valid Mythbuntu CD
01-17 17:42 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-17 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-17 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 17:42 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
01-17 17:42 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
01-17 17:42 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-17 17:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 17:42 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-17 17:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-17 17:42 INFO   Distro: Found a valid CD for Ubuntu Netbook: E:\
01-17 17:42 INFO   root: Running the CD menu...
01-17 17:42 DEBUG  WindowsFrontend: __init__...
01-17 17:42 DEBUG  WindowsFrontend: on_init...
01-17 17:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp\translations, languages=['en_US', 'en']
01-17 17:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl59A3.tmp\translations, languages=['en_US', 'en']
01-17 17:42 INFO   root: CD menu finished
01-17 17:42 INFO   root: Rebooting
01-17 17:42 DEBUG  TaskList: # Running tasklist...
01-17 17:42 DEBUG  TaskList: ## Running reboot...
01-17 17:42 DEBUG  TaskList: ## Finished reboot
01-17 17:42 DEBUG  TaskList: # Finished tasklist
01-17 17:42 DEBUG  root: application.quit
01-17 17:42 DEBUG  WindowsFrontend: frontend.quit
01-17 17:42 DEBUG  WindowsFrontend: frontend.on_quit
01-17 17:42 DEBUG  root: application.on_quit
01-17 17:42 INFO   root: sys.exit
01-17 17:44 INFO   root: === wubi 10.10 rev197 ===
01-17 17:44 DEBUG  root: Logfile is c:\users\journe~1\appdata\local\temp\wubi-10.10-rev197.log
01-17 17:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
01-17 17:44 DEBUG  CommonBackend: data_dir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\data
01-17 17:44 DEBUG  WindowsBackend: 7z=C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\bin\7z.exe
01-17 17:44 DEBUG  CommonBackend: Fetching basic info...
01-17 17:44 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-17 17:44 DEBUG  CommonBackend: platform=win32
01-17 17:44 DEBUG  CommonBackend: osname=nt
01-17 17:44 DEBUG  CommonBackend: language=en_US
01-17 17:44 DEBUG  CommonBackend: encoding=cp1252
01-17 17:44 DEBUG  WindowsBackend: arch=amd64
01-17 17:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\data\isolist.ini
01-17 17:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-17 17:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-17 17:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-17 17:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-17 17:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-17 17:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-17 17:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-17 17:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-17 17:44 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-17 17:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-17 17:44 DEBUG  WindowsBackend: Fetching host info...
01-17 17:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-17 17:44 DEBUG  WindowsBackend: windows version=vista
01-17 17:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-17 17:44 DEBUG  WindowsBackend: windows_sp=None
01-17 17:44 DEBUG  WindowsBackend: windows_build=7600
01-17 17:44 DEBUG  WindowsBackend: gmt=-8
01-17 17:44 DEBUG  WindowsBackend: country=US
01-17 17:44 DEBUG  WindowsBackend: timezone=America/Los_Angeles
01-17 17:44 DEBUG  WindowsBackend: windows_username=journeyous glory
01-17 17:44 DEBUG  WindowsBackend: user_full_name=journeyous glory
01-17 17:44 DEBUG  WindowsBackend: user_directory=C:\Users\journeyous glory
01-17 17:44 DEBUG  WindowsBackend: windows_language_code=1033
01-17 17:44 DEBUG  WindowsBackend: windows_language=English
01-17 17:44 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N550   @ 1.50GHz
01-17 17:44 DEBUG  WindowsBackend: bootloader=vista
01-17 17:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 78997.4023438 mb free ntfs)
01-17 17:44 DEBUG  WindowsBackend: drive=Drive(C: hd 78997.4023438 mb free ntfs)
01-17 17:44 DEBUG  WindowsBackend: drive=Drive(D: hd 120599.03125 mb free ntfs)
01-17 17:44 DEBUG  WindowsBackend: drive=Drive(E: removable 265.390625 mb free fat)
01-17 17:44 DEBUG  WindowsBackend: uninstaller_path=None
01-17 17:44 DEBUG  WindowsBackend: previous_target_dir=None
01-17 17:44 DEBUG  WindowsBackend: previous_distro_name=None
01-17 17:44 DEBUG  WindowsBackend: keyboard_id=67699721
01-17 17:44 DEBUG  WindowsBackend: keyboard_layout=us
01-17 17:44 DEBUG  WindowsBackend: keyboard_variant=
01-17 17:44 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-17 17:44 DEBUG  CommonBackend: locale=en_US.UTF-8
01-17 17:44 DEBUG  WindowsBackend: total_memory_mb=2038.1171875
01-17 17:44 DEBUG  CommonBackend: Searching ISOs on USB devices
01-17 17:44 DEBUG  CommonBackend: Searching for local CDs
01-17 17:44 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp is a valid Ubuntu CD
01-17 17:44 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp is a valid Ubuntu CD
01-17 17:44 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp is a valid Ubuntu Netbook CD
01-17 17:44 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp is a valid Kubuntu CD
01-17 17:44 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp is a valid Kubuntu CD
01-17 17:44 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp is a valid Kubuntu Netbook CD
01-17 17:44 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp is a valid Xubuntu CD
01-17 17:44 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp is a valid Xubuntu CD
01-17 17:44 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp is a valid Mythbuntu CD
01-17 17:44 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp is a valid Mythbuntu CD
01-17 17:44 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 17:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 17:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-17 17:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 17:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 17:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-17 17:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 17:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 17:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 17:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 17:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 17:44 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
01-17 17:44 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
01-17 17:44 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-17 17:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 17:44 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-17 17:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-17 17:44 INFO   Distro: Found a valid CD for Ubuntu Netbook: E:\
01-17 17:44 INFO   root: Running the CD menu...
01-17 17:44 DEBUG  WindowsFrontend: __init__...
01-17 17:44 DEBUG  WindowsFrontend: on_init...
01-17 17:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\translations, languages=['en_US', 'en']
01-17 17:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\translations, languages=['en_US', 'en']
01-17 17:45 INFO   root: CD menu finished
01-17 17:45 INFO   root: Running the CD boot helper...
01-17 17:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\translations, languages=['en_US', 'en']
01-17 17:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\translations, languages=['en_US', 'en']
01-17 17:45 INFO   root: CD boot helper confirmed
01-17 17:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\translations, languages=['en_US', 'en']
01-17 17:45 DEBUG  TaskList: # Running tasklist...
01-17 17:45 DEBUG  TaskList: ## Running select_target_dir...
01-17 17:45 INFO   WindowsBackend: Installing into C:\ubuntu
01-17 17:45 DEBUG  TaskList: ## Finished select_target_dir
01-17 17:45 DEBUG  TaskList: ## Running create_dir_structure...
01-17 17:45 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-17 17:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-17 17:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-17 17:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-17 17:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-17 17:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-17 17:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-17 17:45 DEBUG  TaskList: ## Finished create_dir_structure
01-17 17:45 DEBUG  TaskList: ## Running uncompress_target_dir...
01-17 17:45 DEBUG  TaskList: ## Finished uncompress_target_dir
01-17 17:45 DEBUG  TaskList: ## Running create_uninstaller...
01-17 17:45 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-17 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-17 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-17 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
01-17 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
01-17 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
01-17 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
01-17 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-17 17:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-17 17:45 DEBUG  TaskList: ## Finished create_uninstaller
01-17 17:45 DEBUG  TaskList: ## Running copy_installation_files...
01-17 17:45 DEBUG  WindowsBackend: Copying C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-17 17:45 DEBUG  WindowsBackend: Copying C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\winboot -> C:\ubuntu\winboot
01-17 17:45 DEBUG  WindowsBackend: Copying C:\Users\JOURNE~1\AppData\Local\Temp\pyl7D1B.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
01-17 17:45 DEBUG  TaskList: ## Finished copy_installation_files
01-17 17:45 DEBUG  TaskList: ## Running use_cd...
01-17 17:45 DEBUG  TaskList: New task copy_file
01-17 17:45 DEBUG  TaskList: ### Running copy_file...
01-17 17:46 DEBUG  TaskList: ### Finished copy_file
01-17 17:46 DEBUG  TaskList: New task check_iso
01-17 17:46 DEBUG  TaskList: ### Running check_iso...
01-17 17:46 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
01-17 17:46 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\installation.iso
01-17 17:46 DEBUG  Distro:     wrong size: 1010827264 > 900000000
01-17 17:46 DEBUG  TaskList: ### Finished check_iso
01-17 17:46 DEBUG  TaskList: ## Finished use_cd
01-17 17:46 DEBUG  TaskList: ## Running extract_kernel...
01-17 17:46 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
01-17 17:46 DEBUG  TaskList: # Cancelling tasklist
01-17 17:46 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
01-17 17:46 DEBUG  TaskList: # Finished tasklist
01-17 17:49 INFO   root: === wubi 10.10 rev197 ===
01-17 17:49 DEBUG  root: Logfile is c:\users\journe~1\appdata\local\temp\wubi-10.10-rev197.log
01-17 17:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
01-17 17:49 DEBUG  CommonBackend: data_dir=C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\data
01-17 17:49 DEBUG  WindowsBackend: 7z=C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\bin\7z.exe
01-17 17:49 DEBUG  CommonBackend: Fetching basic info...
01-17 17:49 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-17 17:49 DEBUG  CommonBackend: platform=win32
01-17 17:49 DEBUG  CommonBackend: osname=nt
01-17 17:49 DEBUG  CommonBackend: language=en_US
01-17 17:49 DEBUG  CommonBackend: encoding=cp1252
01-17 17:49 DEBUG  WindowsBackend: arch=amd64
01-17 17:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\data\isolist.ini
01-17 17:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-17 17:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-17 17:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-17 17:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-17 17:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-17 17:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-17 17:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-17 17:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-17 17:49 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-17 17:49 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-17 17:49 DEBUG  WindowsBackend: Fetching host info...
01-17 17:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-17 17:49 DEBUG  WindowsBackend: windows version=vista
01-17 17:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-17 17:49 DEBUG  WindowsBackend: windows_sp=None
01-17 17:49 DEBUG  WindowsBackend: windows_build=7600
01-17 17:49 DEBUG  WindowsBackend: gmt=-8
01-17 17:49 DEBUG  WindowsBackend: country=US
01-17 17:49 DEBUG  WindowsBackend: timezone=America/Los_Angeles
01-17 17:49 DEBUG  WindowsBackend: windows_username=journeyous glory
01-17 17:49 DEBUG  WindowsBackend: user_full_name=journeyous glory
01-17 17:49 DEBUG  WindowsBackend: user_directory=C:\Users\journeyous glory
01-17 17:49 DEBUG  WindowsBackend: windows_language_code=1033
01-17 17:49 DEBUG  WindowsBackend: windows_language=English
01-17 17:49 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N550   @ 1.50GHz
01-17 17:49 DEBUG  WindowsBackend: bootloader=vista
01-17 17:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 77837.828125 mb free ntfs)
01-17 17:49 DEBUG  WindowsBackend: drive=Drive(C: hd 77837.828125 mb free ntfs)
01-17 17:49 DEBUG  WindowsBackend: drive=Drive(D: hd 120599.03125 mb free ntfs)
01-17 17:49 DEBUG  WindowsBackend: drive=Drive(E: removable 265.390625 mb free fat)
01-17 17:49 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-17 17:49 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-17 17:49 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
01-17 17:49 DEBUG  WindowsBackend: keyboard_id=67699721
01-17 17:49 DEBUG  WindowsBackend: keyboard_layout=us
01-17 17:49 DEBUG  WindowsBackend: keyboard_variant=
01-17 17:49 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-17 17:49 DEBUG  CommonBackend: locale=en_US.UTF-8
01-17 17:49 DEBUG  WindowsBackend: total_memory_mb=2038.1171875
01-17 17:49 DEBUG  CommonBackend: Searching ISOs on USB devices
01-17 17:49 DEBUG  CommonBackend: Searching for local CDs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Ubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Ubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Ubuntu Netbook CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Kubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Kubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Kubuntu Netbook CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Xubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Xubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Mythbuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Mythbuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 17:49 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
01-17 17:49 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
01-17 17:49 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-17 17:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 17:49 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-17 17:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-17 17:49 INFO   Distro: Found a valid CD for Ubuntu Netbook: E:\
01-17 17:49 INFO   root: Running the CD menu...
01-17 17:49 DEBUG  WindowsFrontend: __init__...
01-17 17:49 DEBUG  WindowsFrontend: on_init...
01-17 17:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\translations, languages=['en_US', 'en']
01-17 17:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\translations, languages=['en_US', 'en']
01-17 17:49 INFO   root: CD menu finished
01-17 17:49 INFO   root: Already installed, running the uninstaller...
01-17 17:49 INFO   root: Running the uninstaller...
01-17 17:49 INFO   CommonBackend: This is the uninstaller running
01-17 17:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\translations, languages=['en_US', 'en']
01-17 17:49 INFO   root: Received settings
01-17 17:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\translations, languages=['en_US', 'en']
01-17 17:49 DEBUG  TaskList: # Running tasklist...
01-17 17:49 DEBUG  TaskList: ## Running Backup ISO...
01-17 17:49 DEBUG  TaskList: ## Finished Backup ISO
01-17 17:49 DEBUG  TaskList: ## Running Remove bootloader entry...
01-17 17:49 DEBUG  WindowsBackend: Could not find bcd id
01-17 17:49 DEBUG  WindowsBackend: undo_bootini C:
01-17 17:49 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 77837.828125 mb free ntfs)
01-17 17:49 DEBUG  WindowsBackend: undo_bootini D:
01-17 17:49 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 120599.03125 mb free ntfs)
01-17 17:49 DEBUG  WindowsBackend: undo_bootini E:
01-17 17:49 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 265.390625 mb free fat)
01-17 17:49 DEBUG  TaskList: ## Finished Remove bootloader entry
01-17 17:49 DEBUG  TaskList: ## Running Remove target dir...
01-17 17:49 DEBUG  CommonBackend: Deleting C:\ubuntu
01-17 17:49 DEBUG  TaskList: ## Finished Remove target dir
01-17 17:49 DEBUG  TaskList: ## Running Remove registry key...
01-17 17:49 DEBUG  TaskList: ## Finished Remove registry key
01-17 17:49 DEBUG  TaskList: # Finished tasklist
01-17 17:49 INFO   root: Almost finished uninstalling
01-17 17:49 INFO   root: Finished uninstallation
01-17 17:49 DEBUG  CommonBackend: Fetching basic info...
01-17 17:49 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-17 17:49 DEBUG  CommonBackend: platform=win32
01-17 17:49 DEBUG  CommonBackend: osname=nt
01-17 17:49 DEBUG  WindowsBackend: arch=amd64
01-17 17:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\data\isolist.ini
01-17 17:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-17 17:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-17 17:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-17 17:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-17 17:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-17 17:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-17 17:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-17 17:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-17 17:49 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-17 17:49 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-17 17:49 DEBUG  WindowsBackend: Fetching host info...
01-17 17:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-17 17:49 DEBUG  WindowsBackend: windows version=vista
01-17 17:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-17 17:49 DEBUG  WindowsBackend: windows_sp=None
01-17 17:49 DEBUG  WindowsBackend: windows_build=7600
01-17 17:49 DEBUG  WindowsBackend: gmt=-8
01-17 17:49 DEBUG  WindowsBackend: country=US
01-17 17:49 DEBUG  WindowsBackend: timezone=America/Los_Angeles
01-17 17:49 DEBUG  WindowsBackend: windows_username=journeyous glory
01-17 17:49 DEBUG  WindowsBackend: user_full_name=journeyous glory
01-17 17:49 DEBUG  WindowsBackend: user_directory=C:\Users\journeyous glory
01-17 17:49 DEBUG  WindowsBackend: windows_language_code=1033
01-17 17:49 DEBUG  WindowsBackend: windows_language=English
01-17 17:49 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N550   @ 1.50GHz
01-17 17:49 DEBUG  WindowsBackend: bootloader=vista
01-17 17:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 78803.4101563 mb free ntfs)
01-17 17:49 DEBUG  WindowsBackend: drive=Drive(C: hd 78803.4101563 mb free ntfs)
01-17 17:49 DEBUG  WindowsBackend: drive=Drive(D: hd 120599.03125 mb free ntfs)
01-17 17:49 DEBUG  WindowsBackend: drive=Drive(E: removable 265.390625 mb free fat)
01-17 17:49 DEBUG  WindowsBackend: uninstaller_path=None
01-17 17:49 DEBUG  WindowsBackend: previous_target_dir=None
01-17 17:49 DEBUG  WindowsBackend: previous_distro_name=None
01-17 17:49 DEBUG  WindowsBackend: keyboard_id=67699721
01-17 17:49 DEBUG  WindowsBackend: keyboard_layout=us
01-17 17:49 DEBUG  WindowsBackend: keyboard_variant=
01-17 17:49 DEBUG  WindowsBackend: total_memory_mb=2038.1171875
01-17 17:49 DEBUG  CommonBackend: Searching ISOs on USB devices
01-17 17:49 DEBUG  CommonBackend: Searching for local CDs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Ubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Ubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Ubuntu Netbook CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Kubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Kubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Kubuntu Netbook CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Xubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Xubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Mythbuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp is a valid Mythbuntu CD
01-17 17:49 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 17:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 17:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 17:49 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-17 17:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 17:49 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-17 17:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-17 17:49 INFO   Distro: Found a valid CD for Ubuntu Netbook: E:\
01-17 17:49 INFO   root: Running the CD boot helper...
01-17 17:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\translations, languages=['en_US', 'en']
01-17 17:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\translations, languages=['en_US', 'en']
01-17 17:49 INFO   root: CD boot helper confirmed
01-17 17:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\translations, languages=['en_US', 'en']
01-17 17:49 DEBUG  TaskList: # Running tasklist...
01-17 17:49 DEBUG  TaskList: ## Running select_target_dir...
01-17 17:49 INFO   WindowsBackend: Installing into C:\ubuntu
01-17 17:49 DEBUG  TaskList: ## Finished select_target_dir
01-17 17:50 DEBUG  TaskList: ## Running create_dir_structure...
01-17 17:50 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-17 17:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-17 17:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-17 17:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-17 17:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-17 17:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-17 17:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-17 17:50 DEBUG  TaskList: ## Finished create_dir_structure
01-17 17:50 DEBUG  TaskList: ## Running uncompress_target_dir...
01-17 17:50 DEBUG  TaskList: ## Finished uncompress_target_dir
01-17 17:50 DEBUG  TaskList: ## Running create_uninstaller...
01-17 17:50 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-17 17:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-17 17:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-17 17:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
01-17 17:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
01-17 17:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
01-17 17:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
01-17 17:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-17 17:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-17 17:50 DEBUG  TaskList: ## Finished create_uninstaller
01-17 17:50 DEBUG  TaskList: ## Running copy_installation_files...
01-17 17:50 DEBUG  WindowsBackend: Copying C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-17 17:50 DEBUG  WindowsBackend: Copying C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\winboot -> C:\ubuntu\winboot
01-17 17:50 DEBUG  WindowsBackend: Copying C:\Users\JOURNE~1\AppData\Local\Temp\pylD00A.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
01-17 17:50 DEBUG  TaskList: ## Finished copy_installation_files
01-17 17:50 DEBUG  TaskList: ## Running use_cd...
01-17 17:50 DEBUG  TaskList: New task copy_file
01-17 17:50 DEBUG  TaskList: ### Running copy_file...
01-17 17:51 DEBUG  TaskList: ### Finished copy_file
01-17 17:51 DEBUG  TaskList: New task check_iso
01-17 17:51 DEBUG  TaskList: ### Running check_iso...
01-17 17:51 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
01-17 17:51 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\installation.iso
01-17 17:51 DEBUG  Distro:     wrong size: 1010827264 > 900000000
01-17 17:51 DEBUG  TaskList: ### Finished check_iso
01-17 17:51 DEBUG  TaskList: ## Finished use_cd
01-17 17:51 DEBUG  TaskList: ## Running extract_kernel...
01-17 17:51 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
01-17 17:51 DEBUG  TaskList: # Cancelling tasklist
01-17 17:51 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
01-17 17:51 DEBUG  TaskList: # Finished tasklist
01-17 18:04 INFO   root: === wubi 10.10 rev197 ===
01-17 18:04 DEBUG  root: Logfile is c:\users\journe~1\appdata\local\temp\wubi-10.10-rev197.log
01-17 18:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
01-17 18:04 DEBUG  CommonBackend: data_dir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\data
01-17 18:04 DEBUG  WindowsBackend: 7z=C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\bin\7z.exe
01-17 18:04 DEBUG  CommonBackend: Fetching basic info...
01-17 18:04 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-17 18:04 DEBUG  CommonBackend: platform=win32
01-17 18:04 DEBUG  CommonBackend: osname=nt
01-17 18:04 DEBUG  CommonBackend: language=en_US
01-17 18:04 DEBUG  CommonBackend: encoding=cp1252
01-17 18:04 DEBUG  WindowsBackend: arch=amd64
01-17 18:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\data\isolist.ini
01-17 18:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-17 18:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-17 18:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-17 18:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-17 18:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-17 18:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-17 18:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-17 18:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-17 18:04 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-17 18:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-17 18:04 DEBUG  WindowsBackend: Fetching host info...
01-17 18:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-17 18:04 DEBUG  WindowsBackend: windows version=vista
01-17 18:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-17 18:04 DEBUG  WindowsBackend: windows_sp=None
01-17 18:04 DEBUG  WindowsBackend: windows_build=7600
01-17 18:04 DEBUG  WindowsBackend: gmt=-8
01-17 18:04 DEBUG  WindowsBackend: country=US
01-17 18:04 DEBUG  WindowsBackend: timezone=America/Los_Angeles
01-17 18:04 DEBUG  WindowsBackend: windows_username=journeyous glory
01-17 18:04 DEBUG  WindowsBackend: user_full_name=journeyous glory
01-17 18:04 DEBUG  WindowsBackend: user_directory=C:\Users\journeyous glory
01-17 18:04 DEBUG  WindowsBackend: windows_language_code=1033
01-17 18:04 DEBUG  WindowsBackend: windows_language=English
01-17 18:04 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N550   @ 1.50GHz
01-17 18:04 DEBUG  WindowsBackend: bootloader=vista
01-17 18:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 77854.015625 mb free ntfs)
01-17 18:04 DEBUG  WindowsBackend: drive=Drive(C: hd 77854.015625 mb free ntfs)
01-17 18:04 DEBUG  WindowsBackend: drive=Drive(D: hd 120599.03125 mb free ntfs)
01-17 18:04 DEBUG  WindowsBackend: drive=Drive(E: removable 265.390625 mb free fat)
01-17 18:04 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-17 18:04 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-17 18:04 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
01-17 18:04 DEBUG  WindowsBackend: keyboard_id=67699721
01-17 18:04 DEBUG  WindowsBackend: keyboard_layout=us
01-17 18:04 DEBUG  WindowsBackend: keyboard_variant=
01-17 18:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-17 18:04 DEBUG  CommonBackend: locale=en_US.UTF-8
01-17 18:04 DEBUG  WindowsBackend: total_memory_mb=2038.1171875
01-17 18:04 DEBUG  CommonBackend: Searching ISOs on USB devices
01-17 18:04 DEBUG  CommonBackend: Searching for local CDs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Ubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Ubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Ubuntu Netbook CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Kubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Kubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Kubuntu Netbook CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Xubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Xubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Mythbuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Mythbuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 18:04 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
01-17 18:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
01-17 18:04 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-17 18:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 18:04 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-17 18:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-17 18:04 INFO   Distro: Found a valid CD for Ubuntu Netbook: E:\
01-17 18:04 INFO   root: Running the CD menu...
01-17 18:04 DEBUG  WindowsFrontend: __init__...
01-17 18:04 DEBUG  WindowsFrontend: on_init...
01-17 18:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\translations, languages=['en_US', 'en']
01-17 18:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\translations, languages=['en_US', 'en']
01-17 18:04 INFO   root: CD menu finished
01-17 18:04 INFO   root: Already installed, running the uninstaller...
01-17 18:04 INFO   root: Running the uninstaller...
01-17 18:04 INFO   CommonBackend: This is the uninstaller running
01-17 18:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\translations, languages=['en_US', 'en']
01-17 18:04 INFO   root: Received settings
01-17 18:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\translations, languages=['en_US', 'en']
01-17 18:04 DEBUG  TaskList: # Running tasklist...
01-17 18:04 DEBUG  TaskList: ## Running Backup ISO...
01-17 18:04 DEBUG  TaskList: ## Finished Backup ISO
01-17 18:04 DEBUG  TaskList: ## Running Remove bootloader entry...
01-17 18:04 DEBUG  WindowsBackend: Could not find bcd id
01-17 18:04 DEBUG  WindowsBackend: undo_bootini C:
01-17 18:04 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 77854.015625 mb free ntfs)
01-17 18:04 DEBUG  WindowsBackend: undo_bootini D:
01-17 18:04 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 120599.03125 mb free ntfs)
01-17 18:04 DEBUG  WindowsBackend: undo_bootini E:
01-17 18:04 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 265.390625 mb free fat)
01-17 18:04 DEBUG  TaskList: ## Finished Remove bootloader entry
01-17 18:04 DEBUG  TaskList: ## Running Remove target dir...
01-17 18:04 DEBUG  CommonBackend: Deleting C:\ubuntu
01-17 18:04 DEBUG  TaskList: ## Finished Remove target dir
01-17 18:04 DEBUG  TaskList: ## Running Remove registry key...
01-17 18:04 DEBUG  TaskList: ## Finished Remove registry key
01-17 18:04 DEBUG  TaskList: # Finished tasklist
01-17 18:04 INFO   root: Almost finished uninstalling
01-17 18:04 INFO   root: Finished uninstallation
01-17 18:04 DEBUG  CommonBackend: Fetching basic info...
01-17 18:04 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-17 18:04 DEBUG  CommonBackend: platform=win32
01-17 18:04 DEBUG  CommonBackend: osname=nt
01-17 18:04 DEBUG  WindowsBackend: arch=amd64
01-17 18:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\data\isolist.ini
01-17 18:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-17 18:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-17 18:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-17 18:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-17 18:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-17 18:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-17 18:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-17 18:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-17 18:04 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-17 18:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-17 18:04 DEBUG  WindowsBackend: Fetching host info...
01-17 18:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-17 18:04 DEBUG  WindowsBackend: windows version=vista
01-17 18:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-17 18:04 DEBUG  WindowsBackend: windows_sp=None
01-17 18:04 DEBUG  WindowsBackend: windows_build=7600
01-17 18:04 DEBUG  WindowsBackend: gmt=-8
01-17 18:04 DEBUG  WindowsBackend: country=US
01-17 18:04 DEBUG  WindowsBackend: timezone=America/Los_Angeles
01-17 18:04 DEBUG  WindowsBackend: windows_username=journeyous glory
01-17 18:04 DEBUG  WindowsBackend: user_full_name=journeyous glory
01-17 18:04 DEBUG  WindowsBackend: user_directory=C:\Users\journeyous glory
01-17 18:04 DEBUG  WindowsBackend: windows_language_code=1033
01-17 18:04 DEBUG  WindowsBackend: windows_language=English
01-17 18:04 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N550   @ 1.50GHz
01-17 18:04 DEBUG  WindowsBackend: bootloader=vista
01-17 18:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 78819.5976563 mb free ntfs)
01-17 18:04 DEBUG  WindowsBackend: drive=Drive(C: hd 78819.5976563 mb free ntfs)
01-17 18:04 DEBUG  WindowsBackend: drive=Drive(D: hd 120599.03125 mb free ntfs)
01-17 18:04 DEBUG  WindowsBackend: drive=Drive(E: removable 265.390625 mb free fat)
01-17 18:04 DEBUG  WindowsBackend: uninstaller_path=None
01-17 18:04 DEBUG  WindowsBackend: previous_target_dir=None
01-17 18:04 DEBUG  WindowsBackend: previous_distro_name=None
01-17 18:04 DEBUG  WindowsBackend: keyboard_id=67699721
01-17 18:04 DEBUG  WindowsBackend: keyboard_layout=us
01-17 18:04 DEBUG  WindowsBackend: keyboard_variant=
01-17 18:04 DEBUG  WindowsBackend: total_memory_mb=2038.1171875
01-17 18:04 DEBUG  CommonBackend: Searching ISOs on USB devices
01-17 18:04 DEBUG  CommonBackend: Searching for local CDs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Ubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Ubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Ubuntu Netbook CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Kubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Kubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Kubuntu Netbook CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Xubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Xubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Mythbuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp is a valid Mythbuntu CD
01-17 18:04 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 18:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 18:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 18:04 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-17 18:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 18:04 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-17 18:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-17 18:04 INFO   Distro: Found a valid CD for Ubuntu Netbook: E:\
01-17 18:04 INFO   root: Running the installer...
01-17 18:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\translations, languages=['en_US', 'en']
01-17 18:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\translations, languages=['en_US', 'en']
01-17 18:04 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_US, locale=en_US.UTF-8, username=journeyousglory
01-17 18:04 INFO   root: Received settings
01-17 18:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\translations, languages=['en_US', 'en']
01-17 18:04 DEBUG  TaskList: # Running tasklist...
01-17 18:04 DEBUG  TaskList: ## Running select_target_dir...
01-17 18:04 INFO   WindowsBackend: Installing into C:\ubuntu
01-17 18:04 DEBUG  TaskList: ## Finished select_target_dir
01-17 18:04 DEBUG  TaskList: ## Running create_dir_structure...
01-17 18:04 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-17 18:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-17 18:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-17 18:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-17 18:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-17 18:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-17 18:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-17 18:04 DEBUG  TaskList: ## Finished create_dir_structure
01-17 18:04 DEBUG  TaskList: ## Running uncompress_target_dir...
01-17 18:04 DEBUG  TaskList: ## Finished uncompress_target_dir
01-17 18:04 DEBUG  TaskList: ## Running create_uninstaller...
01-17 18:04 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-17 18:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-17 18:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-17 18:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
01-17 18:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
01-17 18:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
01-17 18:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
01-17 18:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-17 18:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-17 18:04 DEBUG  TaskList: ## Finished create_uninstaller
01-17 18:04 DEBUG  TaskList: ## Running copy_installation_files...
01-17 18:04 DEBUG  WindowsBackend: Copying C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-17 18:04 DEBUG  WindowsBackend: Copying C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\winboot -> C:\ubuntu\winboot
01-17 18:04 DEBUG  WindowsBackend: Copying C:\Users\JOURNE~1\AppData\Local\Temp\pyl696C.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
01-17 18:04 DEBUG  TaskList: ## Finished copy_installation_files
01-17 18:04 DEBUG  TaskList: ## Running get_iso...
01-17 18:04 DEBUG  TaskList: New task copy_file
01-17 18:04 DEBUG  TaskList: ### Running copy_file...
01-17 18:05 DEBUG  TaskList: ### Finished copy_file
01-17 18:05 DEBUG  TaskList: New task check_iso
01-17 18:05 DEBUG  TaskList: ### Running check_iso...
01-17 18:05 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
01-17 18:05 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\installation.iso
01-17 18:05 DEBUG  Distro:     wrong size: 1010827264 > 900000000
01-17 18:05 DEBUG  TaskList: ### Finished check_iso
01-17 18:05 DEBUG  CommonBackend: Searching for local ISO
01-17 18:05 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-17 18:05 DEBUG  TaskList: New task get_metalink
01-17 18:05 DEBUG  TaskList: ### Running get_metalink...
01-17 18:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-netbook-i386.metalink](http://releases.ubuntu.com/10.10/ubuntu-10.10-netbook-i386.metalink) > C:\ubuntu\install
01-17 18:05 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.10-netbook-i386.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-netbook-i386.metalink, basename=ubuntu-10.10-netbook-i386.metalink, length=9071, text=None
01-17 18:05 DEBUG  downloader: download finished (read 9071 bytes)
01-17 18:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink](http://releases.ubuntu.com/10.10/MD5SUMS-metalink) > C:\ubuntu\install
01-17 18:05 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
01-17 18:05 DEBUG  downloader: download finished (read 488 bytes)
01-17 18:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
01-17 18:05 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
01-17 18:05 DEBUG  downloader: download finished (read 198 bytes)
01-17 18:05 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
01-17 18:05 INFO   saplog: Checking block bindings..
01-17 18:05 INFO   saplog: Key verified successfully.
01-17 18:05 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink
01-17 18:05 DEBUG  TaskList: ### Finished get_metalink
01-17 18:05 DEBUG  TaskList: New task download
01-17 18:05 DEBUG  TaskList: ### Running download...
01-17 18:05 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-netbook-i386.iso.torrent](http://releases.ubuntu.com/10.10/ubuntu-10.10-netbook-i386.iso.torrent) > C:\ubuntu\install\ubuntu-10.10-netbook-i386.iso
01-17 19:26 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request
 
01-17 19:26 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request
 in task download
01-17 19:26 DEBUG  TaskList: ### Finished download
01-17 19:26 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-netbook-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-netbook-i386.iso'
01-17 19:26 DEBUG  TaskList: # Cancelling tasklist
01-17 19:26 DEBUG  TaskList: # Finished tasklist
01-17 19:26 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-netbook-i386.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-netbook-i386.iso'
01-18 13:48 INFO   root: === wubi 10.10 rev197 ===
01-18 13:48 DEBUG  root: Logfile is c:\users\journe~1\appdata\local\temp\wubi-10.10-rev197.log
01-18 13:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
01-18 13:48 DEBUG  CommonBackend: data_dir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\data
01-18 13:48 DEBUG  WindowsBackend: 7z=C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\bin\7z.exe
01-18 13:48 DEBUG  CommonBackend: Fetching basic info...
01-18 13:48 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-18 13:48 DEBUG  CommonBackend: platform=win32
01-18 13:48 DEBUG  CommonBackend: osname=nt
01-18 13:48 DEBUG  CommonBackend: language=en_US
01-18 13:48 DEBUG  CommonBackend: encoding=cp1252
01-18 13:48 DEBUG  WindowsBackend: arch=amd64
01-18 13:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\data\isolist.ini
01-18 13:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-18 13:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-18 13:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-18 13:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-18 13:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-18 13:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-18 13:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-18 13:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-18 13:48 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-18 13:48 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-18 13:48 DEBUG  WindowsBackend: Fetching host info...
01-18 13:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-18 13:48 DEBUG  WindowsBackend: windows version=vista
01-18 13:48 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-18 13:48 DEBUG  WindowsBackend: windows_sp=None
01-18 13:48 DEBUG  WindowsBackend: windows_build=7600
01-18 13:48 DEBUG  WindowsBackend: gmt=-8
01-18 13:48 DEBUG  WindowsBackend: country=US
01-18 13:48 DEBUG  WindowsBackend: timezone=America/Los_Angeles
01-18 13:48 DEBUG  WindowsBackend: windows_username=journeyous glory
01-18 13:48 DEBUG  WindowsBackend: user_full_name=journeyous glory
01-18 13:48 DEBUG  WindowsBackend: user_directory=C:\Users\journeyous glory
01-18 13:48 DEBUG  WindowsBackend: windows_language_code=1033
01-18 13:48 DEBUG  WindowsBackend: windows_language=English
01-18 13:48 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N550   @ 1.50GHz
01-18 13:48 DEBUG  WindowsBackend: bootloader=vista
01-18 13:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 76108.359375 mb free ntfs)
01-18 13:48 DEBUG  WindowsBackend: drive=Drive(C: hd 76108.359375 mb free ntfs)
01-18 13:48 DEBUG  WindowsBackend: drive=Drive(D: hd 120478.375 mb free ntfs)
01-18 13:48 DEBUG  WindowsBackend: drive=Drive(E: removable 266.2890625 mb free fat32)
01-18 13:48 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-18 13:48 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-18 13:48 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
01-18 13:48 DEBUG  WindowsBackend: keyboard_id=67699721
01-18 13:48 DEBUG  WindowsBackend: keyboard_layout=us
01-18 13:48 DEBUG  WindowsBackend: keyboard_variant=
01-18 13:48 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-18 13:48 DEBUG  CommonBackend: locale=en_US.UTF-8
01-18 13:48 DEBUG  WindowsBackend: total_memory_mb=2038.1171875
01-18 13:48 DEBUG  CommonBackend: Searching ISOs on USB devices
01-18 13:48 DEBUG  CommonBackend: Searching for local CDs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Ubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Ubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Ubuntu Netbook CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Kubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Kubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Kubuntu Netbook CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Xubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Xubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Mythbuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Mythbuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-18 13:48 DEBUG  Distro:   parsing info from str=Ubuntu-Netbook 10.10 "Maverick Meerkat" - Release i386 (20101007)
01-18 13:48 DEBUG  Distro:   parsed info={'name': 'Ubuntu-Netbook', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
01-18 13:48 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-18 13:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-18 13:48 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-18 13:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-18 13:48 INFO   Distro: Found a valid CD for Ubuntu Netbook: E:\
01-18 13:48 INFO   root: Running the CD menu...
01-18 13:48 DEBUG  WindowsFrontend: __init__...
01-18 13:48 DEBUG  WindowsFrontend: on_init...
01-18 13:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\translations, languages=['en_US', 'en']
01-18 13:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\translations, languages=['en_US', 'en']
01-18 13:48 INFO   root: CD menu finished
01-18 13:48 INFO   root: Already installed, running the uninstaller...
01-18 13:48 INFO   root: Running the uninstaller...
01-18 13:48 INFO   CommonBackend: This is the uninstaller running
01-18 13:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\translations, languages=['en_US', 'en']
01-18 13:48 INFO   root: Received settings
01-18 13:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\translations, languages=['en_US', 'en']
01-18 13:48 DEBUG  TaskList: # Running tasklist...
01-18 13:48 DEBUG  TaskList: ## Running Backup ISO...
01-18 13:48 DEBUG  TaskList: ## Finished Backup ISO
01-18 13:48 DEBUG  TaskList: ## Running Remove bootloader entry...
01-18 13:48 DEBUG  WindowsBackend: Could not find bcd id
01-18 13:48 DEBUG  WindowsBackend: undo_bootini C:
01-18 13:48 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 76108.359375 mb free ntfs)
01-18 13:48 DEBUG  WindowsBackend: undo_bootini D:
01-18 13:48 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 120478.375 mb free ntfs)
01-18 13:48 DEBUG  WindowsBackend: undo_bootini E:
01-18 13:48 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 266.2890625 mb free fat32)
01-18 13:48 DEBUG  TaskList: ## Finished Remove bootloader entry
01-18 13:48 DEBUG  TaskList: ## Running Remove target dir...
01-18 13:48 DEBUG  CommonBackend: Deleting C:\ubuntu
01-18 13:48 DEBUG  TaskList: ## Finished Remove target dir
01-18 13:48 DEBUG  TaskList: ## Running Remove registry key...
01-18 13:48 DEBUG  TaskList: ## Finished Remove registry key
01-18 13:48 DEBUG  TaskList: # Finished tasklist
01-18 13:48 INFO   root: Almost finished uninstalling
01-18 13:48 INFO   root: Finished uninstallation
01-18 13:48 DEBUG  CommonBackend: Fetching basic info...
01-18 13:48 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-18 13:48 DEBUG  CommonBackend: platform=win32
01-18 13:48 DEBUG  CommonBackend: osname=nt
01-18 13:48 DEBUG  WindowsBackend: arch=amd64
01-18 13:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\data\isolist.ini
01-18 13:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-18 13:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-18 13:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-18 13:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-18 13:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-18 13:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-18 13:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-18 13:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-18 13:48 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-18 13:48 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-18 13:48 DEBUG  WindowsBackend: Fetching host info...
01-18 13:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-18 13:48 DEBUG  WindowsBackend: windows version=vista
01-18 13:48 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-18 13:48 DEBUG  WindowsBackend: windows_sp=None
01-18 13:48 DEBUG  WindowsBackend: windows_build=7600
01-18 13:48 DEBUG  WindowsBackend: gmt=-8
01-18 13:48 DEBUG  WindowsBackend: country=US
01-18 13:48 DEBUG  WindowsBackend: timezone=America/Los_Angeles
01-18 13:48 DEBUG  WindowsBackend: windows_username=journeyous glory
01-18 13:48 DEBUG  WindowsBackend: user_full_name=journeyous glory
01-18 13:48 DEBUG  WindowsBackend: user_directory=C:\Users\journeyous glory
01-18 13:48 DEBUG  WindowsBackend: windows_language_code=1033
01-18 13:48 DEBUG  WindowsBackend: windows_language=English
01-18 13:48 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N550   @ 1.50GHz
01-18 13:48 DEBUG  WindowsBackend: bootloader=vista
01-18 13:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 77347.8710938 mb free ntfs)
01-18 13:48 DEBUG  WindowsBackend: drive=Drive(C: hd 77347.8710938 mb free ntfs)
01-18 13:48 DEBUG  WindowsBackend: drive=Drive(D: hd 120478.375 mb free ntfs)
01-18 13:48 DEBUG  WindowsBackend: drive=Drive(E: removable 266.2890625 mb free fat32)
01-18 13:48 DEBUG  WindowsBackend: uninstaller_path=None
01-18 13:48 DEBUG  WindowsBackend: previous_target_dir=None
01-18 13:48 DEBUG  WindowsBackend: previous_distro_name=None
01-18 13:48 DEBUG  WindowsBackend: keyboard_id=67699721
01-18 13:48 DEBUG  WindowsBackend: keyboard_layout=us
01-18 13:48 DEBUG  WindowsBackend: keyboard_variant=
01-18 13:48 DEBUG  WindowsBackend: total_memory_mb=2038.1171875
01-18 13:48 DEBUG  CommonBackend: Searching ISOs on USB devices
01-18 13:48 DEBUG  CommonBackend: Searching for local CDs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Ubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Ubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Ubuntu Netbook CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Kubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Kubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Kubuntu Netbook CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Xubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Xubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Mythbuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp is a valid Mythbuntu CD
01-18 13:48 DEBUG  Distro:     does not contain C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-18 13:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-18 13:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-18 13:48 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-18 13:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-18 13:48 DEBUG  Distro: wrong name: Ubuntu Netbook != Ubuntu
01-18 13:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-18 13:48 INFO   Distro: Found a valid CD for Ubuntu Netbook: E:\
01-18 13:48 INFO   root: Running the CD boot helper...
01-18 13:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\translations, languages=['en_US', 'en']
01-18 13:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\translations, languages=['en_US', 'en']
01-18 13:48 INFO   root: CD boot helper confirmed
01-18 13:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\translations, languages=['en_US', 'en']
01-18 13:48 DEBUG  TaskList: # Running tasklist...
01-18 13:48 DEBUG  TaskList: ## Running select_target_dir...
01-18 13:48 INFO   WindowsBackend: Installing into C:\ubuntu
01-18 13:48 DEBUG  TaskList: ## Finished select_target_dir
01-18 13:48 DEBUG  TaskList: ## Running create_dir_structure...
01-18 13:48 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-18 13:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-18 13:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-18 13:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-18 13:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-18 13:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-18 13:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-18 13:48 DEBUG  TaskList: ## Finished create_dir_structure
01-18 13:48 DEBUG  TaskList: ## Running uncompress_target_dir...
01-18 13:48 DEBUG  TaskList: ## Finished uncompress_target_dir
01-18 13:48 DEBUG  TaskList: ## Running create_uninstaller...
01-18 13:48 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-18 13:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-18 13:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-18 13:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
01-18 13:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
01-18 13:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
01-18 13:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
01-18 13:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-18 13:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-18 13:48 DEBUG  TaskList: ## Finished create_uninstaller
01-18 13:48 DEBUG  TaskList: ## Running copy_installation_files...
01-18 13:48 DEBUG  WindowsBackend: Copying C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-18 13:48 DEBUG  WindowsBackend: Copying C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\winboot -> C:\ubuntu\winboot
01-18 13:48 DEBUG  WindowsBackend: Copying C:\Users\JOURNE~1\AppData\Local\Temp\pyl1B41.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
01-18 13:48 DEBUG  TaskList: ## Finished copy_installation_files
01-18 13:48 DEBUG  TaskList: ## Running use_cd...
01-18 13:48 DEBUG  TaskList: New task copy_file
01-18 13:48 DEBUG  TaskList: ### Running copy_file...
01-18 13:49 DEBUG  TaskList: ### Finished copy_file
01-18 13:49 DEBUG  TaskList: New task check_iso
01-18 13:49 DEBUG  TaskList: ### Running check_iso...
01-18 13:49 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
01-18 13:49 DEBUG  Distro:   checking Ubuntu Netbook ISO C:\ubuntu\install\installation.iso
01-18 13:49 DEBUG  Distro:     wrong size: 1010827264 > 900000000
01-18 13:49 DEBUG  TaskList: ### Finished check_iso
01-18 13:49 DEBUG  TaskList: ## Finished use_cd
01-18 13:49 DEBUG  TaskList: ## Running extract_kernel...
01-18 13:49 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
01-18 13:49 DEBUG  TaskList: # Cancelling tasklist
01-18 13:49 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 515, in extract_kernel
Exception: Could not retrieve the required installation files
01-18 13:49 DEBUG  TaskList: # Finished tasklist

```
 
I tried evading the problem out of ignorance by just installing it directly, no demo, and received the same error message.
 
Any help would be enormously appreciated!!! I am stuck and don't know what to do!

---

### Post by journeyousglory on 2011-01-19
Perhaps this time around?

---

### Post by journeyousglory on 2011-01-19
Perhaps this time around?

---

### Post by journeyousglory on 2011-01-19
Perhaps this time around?

---

