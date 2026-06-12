---
title: "Can't install Ubuntu-11.04"
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by kay1234 on 2011-07-30
Hello,
I have two windows installed in my com, window 7 and window XP. I am trying to install wubi in my window 7 but it gives me an error after i have finished installing wubi.
The error message is as follow :
An error occurred :
Permission denied:
For more information, please see the log file:

Here is my log file:


07-29 08:07 INFO   root: === wubi 11.04 rev211 ===
07-29 08:07 DEBUG  root: Logfile is c:\users\kay\appdata\local\temp\wubi-11.04-rev211.log
07-29 08:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kay\\Downloads\\wubi.exe"']
07-29 08:07 DEBUG  CommonBackend: data_dir=C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp\data
07-29 08:07 DEBUG  WindowsBackend: 7z=C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp\bin\7z.exe
07-29 08:07 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-29 08:07 DEBUG  CommonBackend: Fetching basic info...
07-29 08:07 DEBUG  CommonBackend: original_exe=C:\Users\Kay\Downloads\wubi.exe
07-29 08:07 DEBUG  CommonBackend: platform=win32
07-29 08:07 DEBUG  CommonBackend: osname=nt
07-29 08:07 DEBUG  CommonBackend: language=en_US
07-29 08:07 DEBUG  CommonBackend: encoding=cp936
07-29 08:07 DEBUG  WindowsBackend: arch=amd64
07-29 08:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp\data\isolist.ini
07-29 08:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-29 08:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-29 08:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-29 08:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-29 08:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-29 08:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-29 08:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-29 08:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-29 08:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-29 08:07 DEBUG  WindowsBackend: Fetching host info...
07-29 08:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-29 08:07 DEBUG  WindowsBackend: windows version=vista
07-29 08:07 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
07-29 08:07 DEBUG  WindowsBackend: windows_sp=Service Pack 1
07-29 08:07 DEBUG  WindowsBackend: windows_build=7601
07-29 08:07 DEBUG  WindowsBackend: gmt=8
07-29 08:07 DEBUG  WindowsBackend: country=US
07-29 08:07 DEBUG  WindowsBackend: timezone=America/New_York
07-29 08:07 DEBUG  WindowsBackend: windows_username=Kay
07-29 08:07 DEBUG  WindowsBackend: user_full_name=Kay
07-29 08:07 DEBUG  WindowsBackend: user_directory=C:\Users\Kay
07-29 08:07 DEBUG  WindowsBackend: windows_language_code=1033
07-29 08:07 DEBUG  WindowsBackend: windows_language=English
07-29 08:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz
07-29 08:07 DEBUG  WindowsBackend: bootloader=vista
07-29 08:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 138433.199219 mb free ntfs)
07-29 08:07 DEBUG  WindowsBackend: drive=Drive(C: hd 138433.199219 mb free ntfs)
07-29 08:07 DEBUG  WindowsBackend: drive=Drive(D: hd 136774.441406 mb free ntfs)
07-29 08:07 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-29 08:07 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-29 08:07 DEBUG  WindowsBackend: drive=Drive(H: removable 12.09375 mb free fat)
07-29 08:07 DEBUG  WindowsBackend: uninstaller_path=None
07-29 08:07 DEBUG  WindowsBackend: previous_target_dir=None
07-29 08:07 DEBUG  WindowsBackend: previous_distro_name=None
07-29 08:07 DEBUG  WindowsBackend: keyboard_id=67699721
07-29 08:07 DEBUG  WindowsBackend: keyboard_layout=us
07-29 08:07 DEBUG  WindowsBackend: keyboard_variant=
07-29 08:07 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
07-29 08:07 DEBUG  CommonBackend: locale=en_US.UTF-8
07-29 08:07 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-29 08:07 DEBUG  CommonBackend: Searching ISOs on USB devices
07-29 08:07 DEBUG  CommonBackend: Searching for local CDs
07-29 08:07 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp is a valid Ubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp is a valid Ubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp is a valid Ubuntu Netbook CD
07-29 08:07 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp is a valid Kubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp is a valid Kubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp is a valid Xubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp is a valid Xubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp is a valid Mythbuntu CD
07-29 08:07 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp is a valid Mythbuntu CD
07-29 08:07 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-29 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-29 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-29 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-29 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-29 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-29 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
07-29 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-29 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 08:07 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-29 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-29 08:07 INFO   root: Running the installer...
07-29 08:07 DEBUG  WindowsFrontend: __init__...
07-29 08:07 DEBUG  WindowsFrontend: on_init...
07-29 08:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp\translations, languages=['en_US', 'en']
07-29 08:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pyl1A45.tmp\translations, languages=['en_US', 'en']
07-29 08:08 INFO   WindowsFrontend: Operation cancelled
07-29 08:08 DEBUG  WindowsFrontend: frontend.quit
07-29 08:08 DEBUG  WindowsFrontend: frontend.on_quit
07-29 08:08 DEBUG  root: application.on_quit
07-29 08:08 INFO   root: sys.exit
07-30 13:53 INFO   root: === wubi 11.04 rev211 ===
07-30 13:53 DEBUG  root: Logfile is c:\users\kay\appdata\local\temp\wubi-11.04-rev211.log
07-30 13:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\school\\year 3\\FYP\\Ubuntu\\wubi.exe"']
07-30 13:53 DEBUG  CommonBackend: data_dir=C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\data
07-30 13:53 DEBUG  WindowsBackend: 7z=C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\bin\7z.exe
07-30 13:53 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-30 13:53 DEBUG  CommonBackend: Fetching basic info...
07-30 13:53 DEBUG  CommonBackend: original_exe=C:\school\year 3\FYP\Ubuntu\wubi.exe
07-30 13:53 DEBUG  CommonBackend: platform=win32
07-30 13:53 DEBUG  CommonBackend: osname=nt
07-30 13:53 DEBUG  CommonBackend: language=en_US
07-30 13:53 DEBUG  CommonBackend: encoding=cp936
07-30 13:53 DEBUG  WindowsBackend: arch=amd64
07-30 13:53 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\data\isolist.ini
07-30 13:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-30 13:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-30 13:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-30 13:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-30 13:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-30 13:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-30 13:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-30 13:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-30 13:53 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-30 13:53 DEBUG  WindowsBackend: Fetching host info...
07-30 13:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-30 13:53 DEBUG  WindowsBackend: windows version=vista
07-30 13:53 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
07-30 13:53 DEBUG  WindowsBackend: windows_sp=Service Pack 1
07-30 13:53 DEBUG  WindowsBackend: windows_build=7601
07-30 13:53 DEBUG  WindowsBackend: gmt=8
07-30 13:53 DEBUG  WindowsBackend: country=US
07-30 13:53 DEBUG  WindowsBackend: timezone=America/New_York
07-30 13:53 DEBUG  WindowsBackend: windows_username=Kay
07-30 13:53 DEBUG  WindowsBackend: user_full_name=Kay
07-30 13:53 DEBUG  WindowsBackend: user_directory=C:\Users\Kay
07-30 13:53 DEBUG  WindowsBackend: windows_language_code=1033
07-30 13:53 DEBUG  WindowsBackend: windows_language=English
07-30 13:53 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz
07-30 13:53 DEBUG  WindowsBackend: bootloader=vista
07-30 13:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 135104.835938 mb free ntfs)
07-30 13:53 DEBUG  WindowsBackend: drive=Drive(C: hd 135104.835938 mb free ntfs)
07-30 13:53 DEBUG  WindowsBackend: drive=Drive(D: hd 136774.441406 mb free ntfs)
07-30 13:53 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-30 13:53 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-30 13:53 DEBUG  WindowsBackend: drive=Drive(H: removable 12.09375 mb free fat)
07-30 13:53 DEBUG  WindowsBackend: uninstaller_path=None
07-30 13:53 DEBUG  WindowsBackend: previous_target_dir=None
07-30 13:53 DEBUG  WindowsBackend: previous_distro_name=None
07-30 13:53 DEBUG  WindowsBackend: keyboard_id=67699721
07-30 13:53 DEBUG  WindowsBackend: keyboard_layout=us
07-30 13:53 DEBUG  WindowsBackend: keyboard_variant=
07-30 13:53 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
07-30 13:53 DEBUG  CommonBackend: locale=en_US.UTF-8
07-30 13:53 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-30 13:53 DEBUG  CommonBackend: Searching ISOs on USB devices
07-30 13:53 DEBUG  CommonBackend: Searching for local CDs
07-30 13:53 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylC768.tmp is a valid Ubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylC768.tmp is a valid Ubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylC768.tmp is a valid Ubuntu Netbook CD
07-30 13:53 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylC768.tmp is a valid Kubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylC768.tmp is a valid Kubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylC768.tmp is a valid Xubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylC768.tmp is a valid Xubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylC768.tmp is a valid Mythbuntu CD
07-30 13:53 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylC768.tmp is a valid Mythbuntu CD
07-30 13:53 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-30 13:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 13:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 13:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-30 13:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 13:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 13:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-30 13:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 13:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 13:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
07-30 13:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 13:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 13:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 13:53 INFO   root: Running the installer...
07-30 13:53 DEBUG  WindowsFrontend: __init__...
07-30 13:53 DEBUG  WindowsFrontend: on_init...
07-30 13:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\translations, languages=['en_US', 'en']
07-30 13:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\translations, languages=['en_US', 'en']
07-30 13:53 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=kay
07-30 13:53 INFO   root: Received settings
07-30 13:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\translations, languages=['en_US', 'en']
07-30 13:53 DEBUG  TaskList: # Running tasklist...
07-30 13:53 DEBUG  TaskList: ## Running select_target_dir...
07-30 13:53 INFO   WindowsBackend: Installing into C:\ubuntu
07-30 13:53 DEBUG  TaskList: ## Finished select_target_dir
07-30 13:53 DEBUG  TaskList: ## Running create_dir_structure...
07-30 13:53 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-30 13:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-30 13:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-30 13:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-30 13:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-30 13:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-30 13:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-30 13:53 DEBUG  TaskList: ## Finished create_dir_structure
07-30 13:53 DEBUG  TaskList: ## Running uncompress_target_dir...
07-30 13:53 DEBUG  TaskList: ## Finished uncompress_target_dir
07-30 13:53 DEBUG  TaskList: ## Running create_uninstaller...
07-30 13:53 DEBUG  WindowsBackend: Copying uninstaller C:\school\year 3\FYP\Ubuntu\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-30 13:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-30 13:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-30 13:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-30 13:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-30 13:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
07-30 13:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-30 13:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-30 13:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-30 13:53 DEBUG  TaskList: ## Finished create_uninstaller
07-30 13:53 DEBUG  TaskList: ## Running copy_installation_files...
07-30 13:53 DEBUG  WindowsBackend: Copying C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-30 13:53 DEBUG  WindowsBackend: Copying C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\winboot -> C:\ubuntu\winboot
07-30 13:53 DEBUG  WindowsBackend: Copying C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-30 13:53 DEBUG  TaskList: ## Finished copy_installation_files
07-30 13:53 DEBUG  TaskList: ## Running get_iso...
07-30 13:53 DEBUG  CommonBackend: Searching for local CD
07-30 13:53 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylC768.tmp is a valid Ubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylC768.tmp\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 13:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 13:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 13:53 DEBUG  CommonBackend: Searching for local ISO
07-30 13:53 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-30 13:53 DEBUG  TaskList: New task get_metalink
07-30 13:53 DEBUG  TaskList: ### Running get_metalink...
07-30 13:53 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
07-30 13:54 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
07-30 13:54 DEBUG  downloader: download finished (read 28363 bytes)
07-30 13:54 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
07-30 13:54 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
07-30 13:54 DEBUG  downloader: download finished (read 874 bytes)
07-30 13:54 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
07-30 13:54 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
07-30 13:54 DEBUG  downloader: download finished (read 198 bytes)
07-30 13:54 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-30 13:54 INFO   saplog: Checking block bindings..
07-30 13:54 INFO   saplog: Key verified successfully.
07-30 13:54 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

07-30 13:54 DEBUG  TaskList: ### Finished get_metalink
07-30 13:54 DEBUG  TaskList: New task download
07-30 13:54 DEBUG  TaskList: ### Running download...
07-30 13:54 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-30 13:54 INFO   WindowsFrontend: Operation cancelled
07-30 13:54 DEBUG  WindowsFrontend: frontend.quit
07-30 13:54 DEBUG  WindowsFrontend: frontend.on_quit
07-30 13:54 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
07-30 13:54 DEBUG  TaskList: # Cancelling tasklist
07-30 13:54 DEBUG  TaskList: ### Finished download
07-30 13:54 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
07-30 13:54 DEBUG  root: application.on_quit
07-30 13:54 DEBUG  root: Forceful exit
07-30 13:54 INFO   root: sys.exit
07-30 15:20 INFO   root: === wubi 11.04 rev211 ===
07-30 15:20 DEBUG  root: Logfile is c:\users\kay\appdata\local\temp\wubi-11.04-rev211.log
07-30 15:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\school\\year 3\\FYP\\Ubuntu\\wubi.exe"']
07-30 15:20 DEBUG  CommonBackend: data_dir=C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\data
07-30 15:20 DEBUG  WindowsBackend: 7z=C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\bin\7z.exe
07-30 15:20 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-30 15:20 DEBUG  CommonBackend: Fetching basic info...
07-30 15:20 DEBUG  CommonBackend: original_exe=C:\school\year 3\FYP\Ubuntu\wubi.exe
07-30 15:20 DEBUG  CommonBackend: platform=win32
07-30 15:20 DEBUG  CommonBackend: osname=nt
07-30 15:20 DEBUG  CommonBackend: language=en_US
07-30 15:20 DEBUG  CommonBackend: encoding=cp936
07-30 15:20 DEBUG  WindowsBackend: arch=amd64
07-30 15:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\data\isolist.ini
07-30 15:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-30 15:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-30 15:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-30 15:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-30 15:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-30 15:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-30 15:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-30 15:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-30 15:20 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-30 15:20 DEBUG  WindowsBackend: Fetching host info...
07-30 15:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-30 15:20 DEBUG  WindowsBackend: windows version=vista
07-30 15:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
07-30 15:20 DEBUG  WindowsBackend: windows_sp=Service Pack 1
07-30 15:20 DEBUG  WindowsBackend: windows_build=7601
07-30 15:20 DEBUG  WindowsBackend: gmt=8
07-30 15:20 DEBUG  WindowsBackend: country=US
07-30 15:20 DEBUG  WindowsBackend: timezone=America/New_York
07-30 15:20 DEBUG  WindowsBackend: windows_username=Kay
07-30 15:20 DEBUG  WindowsBackend: user_full_name=Kay
07-30 15:20 DEBUG  WindowsBackend: user_directory=C:\Users\Kay
07-30 15:20 DEBUG  WindowsBackend: windows_language_code=1033
07-30 15:20 DEBUG  WindowsBackend: windows_language=English
07-30 15:20 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz
07-30 15:20 DEBUG  WindowsBackend: bootloader=vista
07-30 15:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 135111.6875 mb free ntfs)
07-30 15:20 DEBUG  WindowsBackend: drive=Drive(C: hd 135111.6875 mb free ntfs)
07-30 15:20 DEBUG  WindowsBackend: drive=Drive(D: hd 136774.441406 mb free ntfs)
07-30 15:20 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-30 15:20 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-30 15:20 DEBUG  WindowsBackend: drive=Drive(H: removable 12.09375 mb free fat)
07-30 15:20 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-30 15:20 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-30 15:20 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-30 15:20 DEBUG  WindowsBackend: keyboard_id=67699721
07-30 15:20 DEBUG  WindowsBackend: keyboard_layout=us
07-30 15:20 DEBUG  WindowsBackend: keyboard_variant=
07-30 15:20 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
07-30 15:20 DEBUG  CommonBackend: locale=en_US.UTF-8
07-30 15:20 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-30 15:20 DEBUG  CommonBackend: Searching ISOs on USB devices
07-30 15:20 DEBUG  CommonBackend: Searching for local CDs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Ubuntu Netbook CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 INFO   root: Already installed, running the uninstaller...
07-30 15:20 INFO   root: Running the uninstaller...
07-30 15:20 INFO   CommonBackend: This is the uninstaller running
07-30 15:20 DEBUG  WindowsFrontend: __init__...
07-30 15:20 DEBUG  WindowsFrontend: on_init...
07-30 15:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\translations, languages=['en_US', 'en']
07-30 15:20 INFO   root: Received settings
07-30 15:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\translations, languages=['en_US', 'en']
07-30 15:20 DEBUG  TaskList: # Running tasklist...
07-30 15:20 DEBUG  TaskList: ## Running Backup ISO...
07-30 15:20 DEBUG  TaskList: ## Finished Backup ISO
07-30 15:20 DEBUG  TaskList: ## Running Remove bootloader entry...
07-30 15:20 DEBUG  WindowsBackend: Could not find bcd id
07-30 15:20 DEBUG  WindowsBackend: undo_bootini C:
07-30 15:20 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 135111.6875 mb free ntfs)
07-30 15:20 DEBUG  WindowsBackend: undo_bootini D:
07-30 15:20 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 136774.441406 mb free ntfs)
07-30 15:20 DEBUG  WindowsBackend: undo_bootini H:
07-30 15:20 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 12.09375 mb free fat)
07-30 15:20 DEBUG  TaskList: ## Finished Remove bootloader entry
07-30 15:20 DEBUG  TaskList: ## Running Remove target dir...
07-30 15:20 DEBUG  CommonBackend: Deleting C:\ubuntu
07-30 15:20 DEBUG  TaskList: ## Finished Remove target dir
07-30 15:20 DEBUG  TaskList: ## Running Remove registry key...
07-30 15:20 DEBUG  TaskList: ## Finished Remove registry key
07-30 15:20 DEBUG  TaskList: # Finished tasklist
07-30 15:20 INFO   root: Almost finished uninstalling
07-30 15:20 INFO   root: Finished uninstallation
07-30 15:20 DEBUG  CommonBackend: Fetching basic info...
07-30 15:20 DEBUG  CommonBackend: original_exe=C:\school\year 3\FYP\Ubuntu\wubi.exe
07-30 15:20 DEBUG  CommonBackend: platform=win32
07-30 15:20 DEBUG  CommonBackend: osname=nt
07-30 15:20 DEBUG  WindowsBackend: arch=amd64
07-30 15:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\data\isolist.ini
07-30 15:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-30 15:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-30 15:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-30 15:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-30 15:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-30 15:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-30 15:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-30 15:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-30 15:20 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-30 15:20 DEBUG  WindowsBackend: Fetching host info...
07-30 15:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-30 15:20 DEBUG  WindowsBackend: windows version=vista
07-30 15:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
07-30 15:20 DEBUG  WindowsBackend: windows_sp=Service Pack 1
07-30 15:20 DEBUG  WindowsBackend: windows_build=7601
07-30 15:20 DEBUG  WindowsBackend: gmt=8
07-30 15:20 DEBUG  WindowsBackend: country=US
07-30 15:20 DEBUG  WindowsBackend: timezone=America/New_York
07-30 15:20 DEBUG  WindowsBackend: windows_username=Kay
07-30 15:20 DEBUG  WindowsBackend: user_full_name=Kay
07-30 15:20 DEBUG  WindowsBackend: user_directory=C:\Users\Kay
07-30 15:20 DEBUG  WindowsBackend: windows_language_code=1033
07-30 15:20 DEBUG  WindowsBackend: windows_language=English
07-30 15:20 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz
07-30 15:20 DEBUG  WindowsBackend: bootloader=vista
07-30 15:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 135115.226563 mb free ntfs)
07-30 15:20 DEBUG  WindowsBackend: drive=Drive(C: hd 135115.226563 mb free ntfs)
07-30 15:20 DEBUG  WindowsBackend: drive=Drive(D: hd 136774.441406 mb free ntfs)
07-30 15:20 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-30 15:20 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-30 15:20 DEBUG  WindowsBackend: drive=Drive(H: removable 12.09375 mb free fat)
07-30 15:20 DEBUG  WindowsBackend: uninstaller_path=None
07-30 15:20 DEBUG  WindowsBackend: previous_target_dir=None
07-30 15:20 DEBUG  WindowsBackend: previous_distro_name=None
07-30 15:20 DEBUG  WindowsBackend: keyboard_id=67699721
07-30 15:20 DEBUG  WindowsBackend: keyboard_layout=us
07-30 15:20 DEBUG  WindowsBackend: keyboard_variant=
07-30 15:20 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-30 15:20 DEBUG  CommonBackend: Searching ISOs on USB devices
07-30 15:20 DEBUG  CommonBackend: Searching for local CDs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Ubuntu Netbook CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 INFO   root: Running the installer...
07-30 15:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\translations, languages=['en_US', 'en']
07-30 15:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\translations, languages=['en_US', 'en']
07-30 15:20 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=kay
07-30 15:20 INFO   root: Received settings
07-30 15:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\translations, languages=['en_US', 'en']
07-30 15:20 DEBUG  TaskList: # Running tasklist...
07-30 15:20 DEBUG  TaskList: ## Running select_target_dir...
07-30 15:20 INFO   WindowsBackend: Installing into C:\ubuntu
07-30 15:20 DEBUG  TaskList: ## Finished select_target_dir
07-30 15:20 DEBUG  TaskList: ## Running create_dir_structure...
07-30 15:20 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-30 15:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-30 15:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-30 15:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-30 15:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-30 15:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-30 15:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-30 15:20 DEBUG  TaskList: ## Finished create_dir_structure
07-30 15:20 DEBUG  TaskList: ## Running uncompress_target_dir...
07-30 15:20 DEBUG  TaskList: ## Finished uncompress_target_dir
07-30 15:20 DEBUG  TaskList: ## Running create_uninstaller...
07-30 15:20 DEBUG  WindowsBackend: Copying uninstaller C:\school\year 3\FYP\Ubuntu\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-30 15:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-30 15:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-30 15:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-30 15:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-30 15:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
07-30 15:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-30 15:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-30 15:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-30 15:20 DEBUG  TaskList: ## Finished create_uninstaller
07-30 15:20 DEBUG  TaskList: ## Running copy_installation_files...
07-30 15:20 DEBUG  WindowsBackend: Copying C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-30 15:20 DEBUG  WindowsBackend: Copying C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\winboot -> C:\ubuntu\winboot
07-30 15:20 DEBUG  WindowsBackend: Copying C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-30 15:20 DEBUG  TaskList: ## Finished copy_installation_files
07-30 15:20 DEBUG  TaskList: ## Running get_iso...
07-30 15:20 DEBUG  CommonBackend: Searching for local CD
07-30 15:20 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylB1B2.tmp\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 15:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 15:20 DEBUG  CommonBackend: Searching for local ISO
07-30 15:20 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-30 15:20 DEBUG  TaskList: New task get_metalink
07-30 15:20 DEBUG  TaskList: ### Running get_metalink...
07-30 15:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
07-30 15:20 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
07-30 15:20 DEBUG  downloader: download finished (read 28363 bytes)
07-30 15:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
07-30 15:20 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
07-30 15:20 DEBUG  downloader: download finished (read 874 bytes)
07-30 15:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
07-30 15:20 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
07-30 15:20 DEBUG  downloader: download finished (read 198 bytes)
07-30 15:20 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-30 15:20 INFO   saplog: Checking block bindings..
07-30 15:20 INFO   saplog: Key verified successfully.
07-30 15:20 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

07-30 15:20 DEBUG  TaskList: ### Finished get_metalink
07-30 15:20 DEBUG  TaskList: New task download
07-30 15:20 DEBUG  TaskList: ### Running download...
07-30 15:20 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-30 16:31 ERROR  TaskList: Traceback (most recent call last):
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


07-30 16:31 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
07-30 16:31 DEBUG  TaskList: ### Finished download
07-30 16:31 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
07-30 16:31 DEBUG  TaskList: # Cancelling tasklist
07-30 16:31 DEBUG  TaskList: # Finished tasklist
07-30 16:31 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
07-30 16:34 INFO   root: === wubi 11.04 rev211 ===
07-30 16:34 DEBUG  root: Logfile is c:\users\kay\appdata\local\temp\wubi-11.04-rev211.log
07-30 16:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
07-30 16:34 DEBUG  CommonBackend: data_dir=C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp\data
07-30 16:34 DEBUG  WindowsBackend: 7z=C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp\bin\7z.exe
07-30 16:34 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-30 16:34 DEBUG  CommonBackend: Fetching basic info...
07-30 16:34 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
07-30 16:34 DEBUG  CommonBackend: platform=win32
07-30 16:34 DEBUG  CommonBackend: osname=nt
07-30 16:34 DEBUG  CommonBackend: language=en_US
07-30 16:34 DEBUG  CommonBackend: encoding=cp936
07-30 16:34 DEBUG  WindowsBackend: arch=amd64
07-30 16:34 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp\data\isolist.ini
07-30 16:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-30 16:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-30 16:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-30 16:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-30 16:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-30 16:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-30 16:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-30 16:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-30 16:34 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-30 16:34 DEBUG  WindowsBackend: Fetching host info...
07-30 16:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-30 16:34 DEBUG  WindowsBackend: windows version=vista
07-30 16:34 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
07-30 16:34 DEBUG  WindowsBackend: windows_sp=Service Pack 1
07-30 16:34 DEBUG  WindowsBackend: windows_build=7601
07-30 16:34 DEBUG  WindowsBackend: gmt=8
07-30 16:34 DEBUG  WindowsBackend: country=US
07-30 16:34 DEBUG  WindowsBackend: timezone=America/New_York
07-30 16:34 DEBUG  WindowsBackend: windows_username=Kay
07-30 16:34 DEBUG  WindowsBackend: user_full_name=Kay
07-30 16:34 DEBUG  WindowsBackend: user_directory=C:\Users\Kay
07-30 16:34 DEBUG  WindowsBackend: windows_language_code=1033
07-30 16:34 DEBUG  WindowsBackend: windows_language=English
07-30 16:34 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz
07-30 16:34 DEBUG  WindowsBackend: bootloader=vista
07-30 16:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 134785.035156 mb free ntfs)
07-30 16:34 DEBUG  WindowsBackend: drive=Drive(C: hd 134785.035156 mb free ntfs)
07-30 16:34 DEBUG  WindowsBackend: drive=Drive(D: hd 136774.441406 mb free ntfs)
07-30 16:34 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-30 16:34 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-30 16:34 DEBUG  WindowsBackend: drive=Drive(H: removable 12.09375 mb free fat)
07-30 16:34 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-30 16:34 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-30 16:34 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-30 16:34 DEBUG  WindowsBackend: keyboard_id=67699721
07-30 16:34 DEBUG  WindowsBackend: keyboard_layout=us
07-30 16:34 DEBUG  WindowsBackend: keyboard_variant=
07-30 16:34 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
07-30 16:34 DEBUG  CommonBackend: locale=en_US.UTF-8
07-30 16:34 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-30 16:34 DEBUG  CommonBackend: Searching ISOs on USB devices
07-30 16:34 DEBUG  CommonBackend: Searching for local CDs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp is a valid Ubuntu Netbook CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 INFO   root: Running the uninstaller...
07-30 16:34 INFO   CommonBackend: This is the uninstaller running
07-30 16:34 DEBUG  WindowsFrontend: __init__...
07-30 16:34 DEBUG  WindowsFrontend: on_init...
07-30 16:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp\translations, languages=['en_US', 'en']
07-30 16:34 INFO   root: Received settings
07-30 16:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp\translations, languages=['en_US', 'en']
07-30 16:34 DEBUG  TaskList: # Running tasklist...
07-30 16:34 DEBUG  TaskList: ## Running Backup ISO...
07-30 16:34 DEBUG  TaskList: ## Finished Backup ISO
07-30 16:34 DEBUG  TaskList: ## Running Remove bootloader entry...
07-30 16:34 DEBUG  WindowsBackend: Could not find bcd id
07-30 16:34 DEBUG  WindowsBackend: undo_bootini C:
07-30 16:34 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 134785.035156 mb free ntfs)
07-30 16:34 DEBUG  WindowsBackend: undo_bootini D:
07-30 16:34 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 136774.441406 mb free ntfs)
07-30 16:34 DEBUG  WindowsBackend: undo_bootini H:
07-30 16:34 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 12.09375 mb free fat)
07-30 16:34 DEBUG  TaskList: ## Finished Remove bootloader entry
07-30 16:34 DEBUG  TaskList: ## Running Remove target dir...
07-30 16:34 DEBUG  CommonBackend: Deleting C:\ubuntu
07-30 16:34 DEBUG  TaskList: ## Finished Remove target dir
07-30 16:34 DEBUG  TaskList: ## Running Remove registry key...
07-30 16:34 DEBUG  TaskList: ## Finished Remove registry key
07-30 16:34 DEBUG  TaskList: # Finished tasklist
07-30 16:34 INFO   root: Almost finished uninstalling
07-30 16:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pyl4C9B.tmp\translations, languages=['en_US', 'en']
07-30 16:34 INFO   root: Finished uninstallation
07-30 16:34 DEBUG  root: application.quit
07-30 16:34 DEBUG  WindowsFrontend: frontend.quit
07-30 16:34 DEBUG  WindowsFrontend: frontend.on_quit
07-30 16:34 DEBUG  root: application.on_quit
07-30 16:34 INFO   root: sys.exit
07-30 16:34 INFO   root: === wubi 11.04 rev211 ===
07-30 16:34 DEBUG  root: Logfile is c:\users\kay\appdata\local\temp\wubi-11.04-rev211.log
07-30 16:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\school\\year 3\\FYP\\Ubuntu\\wubi.exe"']
07-30 16:34 DEBUG  CommonBackend: data_dir=C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp\data
07-30 16:34 DEBUG  WindowsBackend: 7z=C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp\bin\7z.exe
07-30 16:34 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-30 16:34 DEBUG  CommonBackend: Fetching basic info...
07-30 16:34 DEBUG  CommonBackend: original_exe=C:\school\year 3\FYP\Ubuntu\wubi.exe
07-30 16:34 DEBUG  CommonBackend: platform=win32
07-30 16:34 DEBUG  CommonBackend: osname=nt
07-30 16:34 DEBUG  CommonBackend: language=en_US
07-30 16:34 DEBUG  CommonBackend: encoding=cp936
07-30 16:34 DEBUG  WindowsBackend: arch=amd64
07-30 16:34 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp\data\isolist.ini
07-30 16:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-30 16:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-30 16:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-30 16:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-30 16:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-30 16:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-30 16:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-30 16:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-30 16:34 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-30 16:34 DEBUG  WindowsBackend: Fetching host info...
07-30 16:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-30 16:34 DEBUG  WindowsBackend: windows version=vista
07-30 16:34 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
07-30 16:34 DEBUG  WindowsBackend: windows_sp=Service Pack 1
07-30 16:34 DEBUG  WindowsBackend: windows_build=7601
07-30 16:34 DEBUG  WindowsBackend: gmt=8
07-30 16:34 DEBUG  WindowsBackend: country=US
07-30 16:34 DEBUG  WindowsBackend: timezone=America/New_York
07-30 16:34 DEBUG  WindowsBackend: windows_username=Kay
07-30 16:34 DEBUG  WindowsBackend: user_full_name=Kay
07-30 16:34 DEBUG  WindowsBackend: user_directory=C:\Users\Kay
07-30 16:34 DEBUG  WindowsBackend: windows_language_code=1033
07-30 16:34 DEBUG  WindowsBackend: windows_language=English
07-30 16:34 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz
07-30 16:34 DEBUG  WindowsBackend: bootloader=vista
07-30 16:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 135102.117188 mb free ntfs)
07-30 16:34 DEBUG  WindowsBackend: drive=Drive(C: hd 135102.117188 mb free ntfs)
07-30 16:34 DEBUG  WindowsBackend: drive=Drive(D: hd 136774.441406 mb free ntfs)
07-30 16:34 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-30 16:34 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-30 16:34 DEBUG  WindowsBackend: drive=Drive(H: removable 12.09375 mb free fat)
07-30 16:34 DEBUG  WindowsBackend: uninstaller_path=None
07-30 16:34 DEBUG  WindowsBackend: previous_target_dir=None
07-30 16:34 DEBUG  WindowsBackend: previous_distro_name=None
07-30 16:34 DEBUG  WindowsBackend: keyboard_id=67699721
07-30 16:34 DEBUG  WindowsBackend: keyboard_layout=us
07-30 16:34 DEBUG  WindowsBackend: keyboard_variant=
07-30 16:34 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
07-30 16:34 DEBUG  CommonBackend: locale=en_US.UTF-8
07-30 16:34 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-30 16:34 DEBUG  CommonBackend: Searching ISOs on USB devices
07-30 16:34 DEBUG  CommonBackend: Searching for local CDs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp is a valid Ubuntu Netbook CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 16:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:34 INFO   root: Running the installer...
07-30 16:34 DEBUG  WindowsFrontend: __init__...
07-30 16:34 DEBUG  WindowsFrontend: on_init...
07-30 16:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp\translations, languages=['en_US', 'en']
07-30 16:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pylAC85.tmp\translations, languages=['en_US', 'en']
07-30 16:35 INFO   root: === wubi 11.04 rev211 ===
07-30 16:35 DEBUG  root: Logfile is c:\users\kay\appdata\local\temp\wubi-11.04-rev211.log
07-30 16:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\school\\year 3\\FYP\\Ubuntu\\wubi.exe"']
07-30 16:35 DEBUG  CommonBackend: data_dir=C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\data
07-30 16:35 DEBUG  WindowsBackend: 7z=C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\bin\7z.exe
07-30 16:35 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-30 16:35 DEBUG  CommonBackend: Fetching basic info...
07-30 16:35 DEBUG  CommonBackend: original_exe=C:\school\year 3\FYP\Ubuntu\wubi.exe
07-30 16:35 DEBUG  CommonBackend: platform=win32
07-30 16:35 DEBUG  CommonBackend: osname=nt
07-30 16:35 DEBUG  CommonBackend: language=en_US
07-30 16:35 DEBUG  CommonBackend: encoding=cp936
07-30 16:35 DEBUG  WindowsBackend: arch=amd64
07-30 16:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\data\isolist.ini
07-30 16:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-30 16:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-30 16:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-30 16:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-30 16:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-30 16:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-30 16:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-30 16:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-30 16:35 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-30 16:35 DEBUG  WindowsBackend: Fetching host info...
07-30 16:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-30 16:35 DEBUG  WindowsBackend: windows version=vista
07-30 16:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
07-30 16:35 DEBUG  WindowsBackend: windows_sp=Service Pack 1
07-30 16:35 DEBUG  WindowsBackend: windows_build=7601
07-30 16:35 DEBUG  WindowsBackend: gmt=8
07-30 16:35 DEBUG  WindowsBackend: country=US
07-30 16:35 DEBUG  WindowsBackend: timezone=America/New_York
07-30 16:35 DEBUG  WindowsBackend: windows_username=Kay
07-30 16:35 DEBUG  WindowsBackend: user_full_name=Kay
07-30 16:35 DEBUG  WindowsBackend: user_directory=C:\Users\Kay
07-30 16:35 DEBUG  WindowsBackend: windows_language_code=1033
07-30 16:35 DEBUG  WindowsBackend: windows_language=English
07-30 16:35 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz
07-30 16:35 DEBUG  WindowsBackend: bootloader=vista
07-30 16:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 135096.308594 mb free ntfs)
07-30 16:35 DEBUG  WindowsBackend: drive=Drive(C: hd 135096.308594 mb free ntfs)
07-30 16:35 DEBUG  WindowsBackend: drive=Drive(D: hd 136774.441406 mb free ntfs)
07-30 16:35 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-30 16:35 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-30 16:35 DEBUG  WindowsBackend: drive=Drive(H: removable 12.09375 mb free fat)
07-30 16:35 DEBUG  WindowsBackend: uninstaller_path=None
07-30 16:35 DEBUG  WindowsBackend: previous_target_dir=None
07-30 16:35 DEBUG  WindowsBackend: previous_distro_name=None
07-30 16:35 DEBUG  WindowsBackend: keyboard_id=67699721
07-30 16:35 DEBUG  WindowsBackend: keyboard_layout=us
07-30 16:35 DEBUG  WindowsBackend: keyboard_variant=
07-30 16:35 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
07-30 16:35 DEBUG  CommonBackend: locale=en_US.UTF-8
07-30 16:35 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-30 16:35 DEBUG  CommonBackend: Searching ISOs on USB devices
07-30 16:35 DEBUG  CommonBackend: Searching for local CDs
07-30 16:35 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp is a valid Ubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp is a valid Ubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp is a valid Ubuntu Netbook CD
07-30 16:35 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp is a valid Kubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp is a valid Kubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp is a valid Xubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp is a valid Xubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp is a valid Mythbuntu CD
07-30 16:35 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp is a valid Mythbuntu CD
07-30 16:35 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-30 16:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 16:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-30 16:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-30 16:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 16:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-30 16:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-30 16:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 16:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-30 16:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
07-30 16:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 16:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-30 16:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:35 INFO   root: Running the installer...
07-30 16:35 DEBUG  WindowsFrontend: __init__...
07-30 16:35 DEBUG  WindowsFrontend: on_init...
07-30 16:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\translations, languages=['en_US', 'en']
07-30 16:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\translations, languages=['en_US', 'en']
07-30 16:35 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=kay
07-30 16:35 INFO   root: Received settings
07-30 16:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\translations, languages=['en_US', 'en']
07-30 16:35 DEBUG  TaskList: # Running tasklist...
07-30 16:35 DEBUG  TaskList: ## Running select_target_dir...
07-30 16:35 INFO   WindowsBackend: Installing into C:\ubuntu
07-30 16:35 DEBUG  TaskList: ## Finished select_target_dir
07-30 16:35 DEBUG  TaskList: ## Running create_dir_structure...
07-30 16:35 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-30 16:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-30 16:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-30 16:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-30 16:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-30 16:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-30 16:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-30 16:35 DEBUG  TaskList: ## Finished create_dir_structure
07-30 16:35 DEBUG  TaskList: ## Running uncompress_target_dir...
07-30 16:35 DEBUG  TaskList: ## Finished uncompress_target_dir
07-30 16:35 DEBUG  TaskList: ## Running create_uninstaller...
07-30 16:35 DEBUG  WindowsBackend: Copying uninstaller C:\school\year 3\FYP\Ubuntu\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-30 16:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-30 16:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-30 16:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-30 16:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-30 16:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
07-30 16:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-30 16:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-30 16:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-30 16:35 DEBUG  TaskList: ## Finished create_uninstaller
07-30 16:35 DEBUG  TaskList: ## Running copy_installation_files...
07-30 16:35 DEBUG  WindowsBackend: Copying C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-30 16:35 DEBUG  WindowsBackend: Copying C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\winboot -> C:\ubuntu\winboot
07-30 16:35 DEBUG  WindowsBackend: Copying C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-30 16:35 DEBUG  TaskList: ## Finished copy_installation_files
07-30 16:35 DEBUG  TaskList: ## Running get_iso...
07-30 16:35 DEBUG  CommonBackend: Searching for local CD
07-30 16:35 DEBUG  Distro:   checking whether C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp is a valid Ubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain C:\Users\Kay\AppData\Local\Temp\pyl8AB3.tmp\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-30 16:35 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-30 16:35 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-30 16:35 DEBUG  CommonBackend: Searching for local ISO
07-30 16:35 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-30 16:35 DEBUG  TaskList: New task get_metalink
07-30 16:35 DEBUG  TaskList: ### Running get_metalink...
07-30 16:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
07-30 16:35 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
07-30 16:35 DEBUG  downloader: download finished (read 28363 bytes)
07-30 16:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
07-30 16:35 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
07-30 16:35 DEBUG  downloader: download finished (read 874 bytes)
07-30 16:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
07-30 16:35 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
07-30 16:35 DEBUG  downloader: download finished (read 198 bytes)
07-30 16:35 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-30 16:35 INFO   saplog: Checking block bindings..
07-30 16:35 INFO   saplog: Key verified successfully.
07-30 16:35 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

07-30 16:35 DEBUG  TaskList: ### Finished get_metalink
07-30 16:35 DEBUG  TaskList: New task download
07-30 16:35 DEBUG  TaskList: ### Running download...
07-30 16:35 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-30 16:36 INFO   WindowsFrontend: Operation cancelled
07-30 16:36 DEBUG  WindowsFrontend: frontend.quit
07-30 16:36 DEBUG  WindowsFrontend: frontend.on_quit
07-30 16:36 DEBUG  root: application.on_quit
07-30 16:36 INFO   root: sys.exit
07-30 17:40 ERROR  TaskList: Traceback (most recent call last):
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


07-30 17:40 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
07-30 17:40 DEBUG  TaskList: ### Finished download
07-30 17:40 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
07-30 17:40 DEBUG  TaskList: # Cancelling tasklist
07-30 17:40 DEBUG  TaskList: # Finished tasklist
07-30 17:40 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'

Sorry, if this message is too long.
Please help me with this. I am completely new to Ubuntu.
How shall I solve the problem?

Thank you in advance. 
kay

---

### Post by Odipides on 2011-07-30
Have you tried cutting the ISO (ubuntu-11.04-desktop-amd64.iso) to a CD and booting from the CD ROM?

If you already have Windows installed, the Ubuntu installation system will let you install a dual boot system pretty easily. I never use Wubi; gives me grief whenever I've tried it. The native installation system is generally easier and more reliable.

Not having any $#&#$& Windows systems any more also helps :).

---

### Post by bcbc on 2011-07-30
> File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
File "\lib\bittorrent\Rerequester.py", line 96, in fail
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

The problem is downloading the ISO using Wubi's bittorrent client. Maybe your firewall is blocking it. Did you allow firewall access to pyrun.exe (the python runtime).

You can also [download]("http://www.ubuntu.com/download/ubuntu/download") the desktop CD ISO yourself and then save it in the same folder as wubi.exe and wubi will find and use it.

For more details see: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

