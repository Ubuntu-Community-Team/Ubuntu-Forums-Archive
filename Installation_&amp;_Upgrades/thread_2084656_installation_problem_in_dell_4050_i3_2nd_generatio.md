---
title: "installation problem in dell 4050 i3 2nd generation"
date: 2012-11-16
forum: Installation &amp; Upgrades
---

### Post by coolguysraju on 2012-11-16
at last point of installation it shows error
and ask to view log file and as if it is not installed.I use wubi.exe.
log file data :
whose data are as



10-28 07:32 INFO   root: === wubi 12.10 rev273 ===
10-28 07:32 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 07:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\installed file\\linux\\wubi.exe"']
10-28 07:32 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp\data
10-28 07:32 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp\bin\7z.exe
10-28 07:32 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 07:32 DEBUG  CommonBackend: Fetching basic info...
10-28 07:32 DEBUG  CommonBackend: original_exe=D:\installed file\linux\wubi.exe
10-28 07:32 DEBUG  CommonBackend: platform=win32
10-28 07:32 DEBUG  CommonBackend: osname=nt
10-28 07:32 DEBUG  CommonBackend: language=en_US
10-28 07:32 DEBUG  CommonBackend: encoding=cp1252
10-28 07:32 DEBUG  WindowsBackend: arch=amd64
10-28 07:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp\data\isolist.ini
10-28 07:32 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 07:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 07:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 07:32 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 07:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 07:32 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 07:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 07:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 07:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 07:32 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 07:32 DEBUG  WindowsBackend: Fetching host info...
10-28 07:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 07:32 DEBUG  WindowsBackend: windows version=vista
10-28 07:32 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 07:32 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 07:32 DEBUG  WindowsBackend: windows_build=7601
10-28 07:32 DEBUG  WindowsBackend: gmt=5
10-28 07:32 DEBUG  WindowsBackend: country=US
10-28 07:32 DEBUG  WindowsBackend: timezone=America/New_York
10-28 07:32 DEBUG  WindowsBackend: windows_username=sandesh
10-28 07:32 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 07:32 DEBUG  WindowsBackend: user_directory=
10-28 07:32 DEBUG  WindowsBackend: windows_language_code=1033
10-28 07:32 DEBUG  WindowsBackend: windows_language=English
10-28 07:32 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 07:32 DEBUG  WindowsBackend: bootloader=vista
10-28 07:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29239.8476563 mb free ntfs)
10-28 07:32 DEBUG  WindowsBackend: drive=Drive(C: hd 29239.8476563 mb free ntfs)
10-28 07:32 DEBUG  WindowsBackend: drive=Drive(D: hd 90774.8984375 mb free ntfs)
10-28 07:32 DEBUG  WindowsBackend: drive=Drive(E: hd 61292.8242188 mb free ntfs)
10-28 07:32 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 07:32 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 07:32 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 07:32 DEBUG  WindowsBackend: uninstaller_path=None
10-28 07:32 DEBUG  WindowsBackend: previous_target_dir=None
10-28 07:32 DEBUG  WindowsBackend: previous_distro_name=None
10-28 07:32 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 07:32 DEBUG  WindowsBackend: keyboard_layout=us
10-28 07:32 DEBUG  WindowsBackend: keyboard_variant=
10-28 07:32 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 07:32 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 07:32 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 07:32 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 07:32 DEBUG  CommonBackend: Searching for local CDs
10-28 07:32 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp is a valid Ubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp is a valid Ubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp is a valid Kubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp is a valid Kubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp is a valid Mythbuntu CD
10-28 07:32 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp is a valid Mythbuntu CD
10-28 07:32 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp is a valid Edubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp is a valid Edubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp is a valid Lubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp is a valid Lubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:32 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:32 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:32 INFO   root: Running the installer...
10-28 07:32 DEBUG  WindowsFrontend: __init__...
10-28 07:32 DEBUG  WindowsFrontend: on_init...
10-28 07:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp\translations, languages=['en_US', 'en']
10-28 07:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl6BAD.tmp\translations, languages=['en_US', 'en']
10-28 07:34 INFO   WindowsFrontend: Operation cancelled
10-28 07:34 DEBUG  WindowsFrontend: frontend.quit
10-28 07:34 DEBUG  WindowsFrontend: frontend.on_quit
10-28 07:34 DEBUG  root: application.on_quit
10-28 07:34 INFO   root: sys.exit
10-28 07:34 INFO   root: === wubi 12.10 rev273 ===
10-28 07:34 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 07:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\installed file\\linux\\wubi.exe"']
10-28 07:34 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp\data
10-28 07:34 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp\bin\7z.exe
10-28 07:34 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 07:34 DEBUG  CommonBackend: Fetching basic info...
10-28 07:34 DEBUG  CommonBackend: original_exe=D:\installed file\linux\wubi.exe
10-28 07:34 DEBUG  CommonBackend: platform=win32
10-28 07:34 DEBUG  CommonBackend: osname=nt
10-28 07:34 DEBUG  CommonBackend: language=en_US
10-28 07:34 DEBUG  CommonBackend: encoding=cp1252
10-28 07:34 DEBUG  WindowsBackend: arch=amd64
10-28 07:34 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp\data\isolist.ini
10-28 07:34 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 07:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 07:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 07:34 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 07:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 07:34 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 07:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 07:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 07:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 07:34 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 07:34 DEBUG  WindowsBackend: Fetching host info...
10-28 07:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 07:34 DEBUG  WindowsBackend: windows version=vista
10-28 07:34 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 07:34 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 07:34 DEBUG  WindowsBackend: windows_build=7601
10-28 07:34 DEBUG  WindowsBackend: gmt=5
10-28 07:34 DEBUG  WindowsBackend: country=US
10-28 07:34 DEBUG  WindowsBackend: timezone=America/New_York
10-28 07:34 DEBUG  WindowsBackend: windows_username=sandesh
10-28 07:34 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 07:34 DEBUG  WindowsBackend: user_directory=
10-28 07:34 DEBUG  WindowsBackend: windows_language_code=1033
10-28 07:34 DEBUG  WindowsBackend: windows_language=English
10-28 07:34 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 07:34 DEBUG  WindowsBackend: bootloader=vista
10-28 07:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29238.8671875 mb free ntfs)
10-28 07:34 DEBUG  WindowsBackend: drive=Drive(C: hd 29238.8671875 mb free ntfs)
10-28 07:34 DEBUG  WindowsBackend: drive=Drive(D: hd 90774.8984375 mb free ntfs)
10-28 07:34 DEBUG  WindowsBackend: drive=Drive(E: hd 61292.8242188 mb free ntfs)
10-28 07:34 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 07:34 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 07:34 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 07:34 DEBUG  WindowsBackend: uninstaller_path=None
10-28 07:34 DEBUG  WindowsBackend: previous_target_dir=None
10-28 07:34 DEBUG  WindowsBackend: previous_distro_name=None
10-28 07:34 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 07:34 DEBUG  WindowsBackend: keyboard_layout=us
10-28 07:34 DEBUG  WindowsBackend: keyboard_variant=
10-28 07:34 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 07:34 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 07:34 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 07:34 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 07:34 DEBUG  CommonBackend: Searching for local CDs
10-28 07:34 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp is a valid Ubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp is a valid Ubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp is a valid Kubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp is a valid Kubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp is a valid Mythbuntu CD
10-28 07:34 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp is a valid Mythbuntu CD
10-28 07:34 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp is a valid Edubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp is a valid Edubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp is a valid Lubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp is a valid Lubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:34 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:34 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:34 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:34 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:34 INFO   root: Running the installer...
10-28 07:34 DEBUG  WindowsFrontend: __init__...
10-28 07:34 DEBUG  WindowsFrontend: on_init...
10-28 07:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp\translations, languages=['en_US', 'en']
10-28 07:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylADEA.tmp\translations, languages=['en_US', 'en']
10-28 07:36 INFO   WindowsFrontend: Operation cancelled
10-28 07:36 DEBUG  WindowsFrontend: frontend.quit
10-28 07:36 DEBUG  WindowsFrontend: frontend.on_quit
10-28 07:36 DEBUG  root: application.on_quit
10-28 07:36 INFO   root: sys.exit
10-28 07:36 INFO   root: === wubi 12.10 rev273 ===
10-28 07:36 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 07:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\installed file\\linux\\wubi.exe"']
10-28 07:36 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp\data
10-28 07:36 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp\bin\7z.exe
10-28 07:36 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 07:36 DEBUG  CommonBackend: Fetching basic info...
10-28 07:36 DEBUG  CommonBackend: original_exe=D:\installed file\linux\wubi.exe
10-28 07:36 DEBUG  CommonBackend: platform=win32
10-28 07:36 DEBUG  CommonBackend: osname=nt
10-28 07:36 DEBUG  CommonBackend: language=en_US
10-28 07:36 DEBUG  CommonBackend: encoding=cp1252
10-28 07:36 DEBUG  WindowsBackend: arch=amd64
10-28 07:36 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp\data\isolist.ini
10-28 07:36 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 07:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 07:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 07:36 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 07:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 07:36 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 07:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 07:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 07:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 07:36 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 07:36 DEBUG  WindowsBackend: Fetching host info...
10-28 07:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 07:36 DEBUG  WindowsBackend: windows version=vista
10-28 07:36 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 07:36 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 07:36 DEBUG  WindowsBackend: windows_build=7601
10-28 07:36 DEBUG  WindowsBackend: gmt=5
10-28 07:36 DEBUG  WindowsBackend: country=US
10-28 07:36 DEBUG  WindowsBackend: timezone=America/New_York
10-28 07:36 DEBUG  WindowsBackend: windows_username=sandesh
10-28 07:36 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 07:36 DEBUG  WindowsBackend: user_directory=
10-28 07:36 DEBUG  WindowsBackend: windows_language_code=1033
10-28 07:36 DEBUG  WindowsBackend: windows_language=English
10-28 07:36 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 07:36 DEBUG  WindowsBackend: bootloader=vista
10-28 07:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29238.6914063 mb free ntfs)
10-28 07:36 DEBUG  WindowsBackend: drive=Drive(C: hd 29238.6914063 mb free ntfs)
10-28 07:36 DEBUG  WindowsBackend: drive=Drive(D: hd 90774.8984375 mb free ntfs)
10-28 07:36 DEBUG  WindowsBackend: drive=Drive(E: hd 61292.8242188 mb free ntfs)
10-28 07:36 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 07:36 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 07:36 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 07:36 DEBUG  WindowsBackend: uninstaller_path=None
10-28 07:36 DEBUG  WindowsBackend: previous_target_dir=None
10-28 07:36 DEBUG  WindowsBackend: previous_distro_name=None
10-28 07:36 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 07:36 DEBUG  WindowsBackend: keyboard_layout=us
10-28 07:36 DEBUG  WindowsBackend: keyboard_variant=
10-28 07:36 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 07:36 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 07:36 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 07:36 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 07:36 DEBUG  CommonBackend: Searching for local CDs
10-28 07:36 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp is a valid Ubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp is a valid Ubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp is a valid Kubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp is a valid Kubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp is a valid Mythbuntu CD
10-28 07:36 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp is a valid Mythbuntu CD
10-28 07:36 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp is a valid Edubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp is a valid Edubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp is a valid Lubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp is a valid Lubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:36 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:36 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:36 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:36 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:36 INFO   root: Running the installer...
10-28 07:36 DEBUG  WindowsFrontend: __init__...
10-28 07:36 DEBUG  WindowsFrontend: on_init...
10-28 07:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp\translations, languages=['en_US', 'en']
10-28 07:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl8516.tmp\translations, languages=['en_US', 'en']
10-28 07:42 INFO   WindowsFrontend: Operation cancelled
10-28 07:42 DEBUG  WindowsFrontend: frontend.quit
10-28 07:42 DEBUG  WindowsFrontend: frontend.on_quit
10-28 07:42 DEBUG  root: application.on_quit
10-28 07:42 INFO   root: sys.exit
10-28 07:42 INFO   root: === wubi 12.10 rev273 ===
10-28 07:42 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 07:42 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\installed file\\linux\\wubi.exe"']
10-28 07:42 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp\data
10-28 07:42 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp\bin\7z.exe
10-28 07:42 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 07:42 DEBUG  CommonBackend: Fetching basic info...
10-28 07:42 DEBUG  CommonBackend: original_exe=D:\installed file\linux\wubi.exe
10-28 07:42 DEBUG  CommonBackend: platform=win32
10-28 07:42 DEBUG  CommonBackend: osname=nt
10-28 07:42 DEBUG  CommonBackend: language=en_US
10-28 07:42 DEBUG  CommonBackend: encoding=cp1252
10-28 07:42 DEBUG  WindowsBackend: arch=amd64
10-28 07:42 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp\data\isolist.ini
10-28 07:42 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 07:42 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 07:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 07:42 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 07:42 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 07:42 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 07:42 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 07:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 07:42 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 07:42 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 07:42 DEBUG  WindowsBackend: Fetching host info...
10-28 07:42 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 07:42 DEBUG  WindowsBackend: windows version=vista
10-28 07:42 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 07:42 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 07:42 DEBUG  WindowsBackend: windows_build=7601
10-28 07:42 DEBUG  WindowsBackend: gmt=5
10-28 07:42 DEBUG  WindowsBackend: country=US
10-28 07:42 DEBUG  WindowsBackend: timezone=America/New_York
10-28 07:42 DEBUG  WindowsBackend: windows_username=sandesh
10-28 07:42 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 07:42 DEBUG  WindowsBackend: user_directory=
10-28 07:42 DEBUG  WindowsBackend: windows_language_code=1033
10-28 07:42 DEBUG  WindowsBackend: windows_language=English
10-28 07:42 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 07:42 DEBUG  WindowsBackend: bootloader=vista
10-28 07:42 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29238.1171875 mb free ntfs)
10-28 07:42 DEBUG  WindowsBackend: drive=Drive(C: hd 29238.1171875 mb free ntfs)
10-28 07:42 DEBUG  WindowsBackend: drive=Drive(D: hd 90774.8984375 mb free ntfs)
10-28 07:42 DEBUG  WindowsBackend: drive=Drive(E: hd 61292.8242188 mb free ntfs)
10-28 07:42 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 07:42 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 07:42 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 07:42 DEBUG  WindowsBackend: uninstaller_path=None
10-28 07:42 DEBUG  WindowsBackend: previous_target_dir=None
10-28 07:42 DEBUG  WindowsBackend: previous_distro_name=None
10-28 07:42 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 07:42 DEBUG  WindowsBackend: keyboard_layout=us
10-28 07:42 DEBUG  WindowsBackend: keyboard_variant=
10-28 07:42 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 07:42 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 07:42 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 07:42 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 07:42 DEBUG  CommonBackend: Searching for local CDs
10-28 07:42 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp is a valid Ubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp is a valid Ubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp is a valid Kubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp is a valid Kubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp is a valid Mythbuntu CD
10-28 07:42 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp is a valid Mythbuntu CD
10-28 07:42 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp is a valid Edubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp is a valid Edubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp is a valid Lubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp is a valid Lubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:42 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:42 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:42 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:42 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:42 INFO   root: Running the installer...
10-28 07:42 DEBUG  WindowsFrontend: __init__...
10-28 07:42 DEBUG  WindowsFrontend: on_init...
10-28 07:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp\translations, languages=['en_US', 'en']
10-28 07:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl5B68.tmp\translations, languages=['en_US', 'en']
10-28 07:43 INFO   WindowsFrontend: Operation cancelled
10-28 07:43 DEBUG  WindowsFrontend: frontend.quit
10-28 07:43 DEBUG  WindowsFrontend: frontend.on_quit
10-28 07:43 DEBUG  root: application.on_quit
10-28 07:43 INFO   root: sys.exit
10-28 07:43 INFO   root: === wubi 12.10 rev273 ===
10-28 07:43 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 07:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\installed file\\linux\\wubi.exe"']
10-28 07:43 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\data
10-28 07:43 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\bin\7z.exe
10-28 07:43 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 07:43 DEBUG  CommonBackend: Fetching basic info...
10-28 07:43 DEBUG  CommonBackend: original_exe=D:\installed file\linux\wubi.exe
10-28 07:43 DEBUG  CommonBackend: platform=win32
10-28 07:43 DEBUG  CommonBackend: osname=nt
10-28 07:43 DEBUG  CommonBackend: language=en_US
10-28 07:43 DEBUG  CommonBackend: encoding=cp1252
10-28 07:43 DEBUG  WindowsBackend: arch=amd64
10-28 07:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\data\isolist.ini
10-28 07:43 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 07:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 07:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 07:43 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 07:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 07:43 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 07:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 07:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 07:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 07:43 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 07:43 DEBUG  WindowsBackend: Fetching host info...
10-28 07:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 07:43 DEBUG  WindowsBackend: windows version=vista
10-28 07:43 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 07:43 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 07:43 DEBUG  WindowsBackend: windows_build=7601
10-28 07:43 DEBUG  WindowsBackend: gmt=5
10-28 07:43 DEBUG  WindowsBackend: country=US
10-28 07:43 DEBUG  WindowsBackend: timezone=America/New_York
10-28 07:43 DEBUG  WindowsBackend: windows_username=sandesh
10-28 07:43 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 07:43 DEBUG  WindowsBackend: user_directory=
10-28 07:43 DEBUG  WindowsBackend: windows_language_code=1033
10-28 07:43 DEBUG  WindowsBackend: windows_language=English
10-28 07:43 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 07:43 DEBUG  WindowsBackend: bootloader=vista
10-28 07:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29237.4492188 mb free ntfs)
10-28 07:43 DEBUG  WindowsBackend: drive=Drive(C: hd 29237.4492188 mb free ntfs)
10-28 07:43 DEBUG  WindowsBackend: drive=Drive(D: hd 90774.8984375 mb free ntfs)
10-28 07:43 DEBUG  WindowsBackend: drive=Drive(E: hd 61292.8242188 mb free ntfs)
10-28 07:43 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 07:43 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 07:43 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 07:43 DEBUG  WindowsBackend: uninstaller_path=None
10-28 07:43 DEBUG  WindowsBackend: previous_target_dir=None
10-28 07:43 DEBUG  WindowsBackend: previous_distro_name=None
10-28 07:43 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 07:43 DEBUG  WindowsBackend: keyboard_layout=us
10-28 07:43 DEBUG  WindowsBackend: keyboard_variant=
10-28 07:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 07:43 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 07:43 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 07:43 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 07:43 DEBUG  CommonBackend: Searching for local CDs
10-28 07:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp is a valid Ubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp is a valid Ubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp is a valid Kubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp is a valid Kubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp is a valid Mythbuntu CD
10-28 07:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp is a valid Mythbuntu CD
10-28 07:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp is a valid Edubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp is a valid Edubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp is a valid Lubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp is a valid Lubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:43 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:44 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:44 INFO   root: Running the installer...
10-28 07:44 DEBUG  WindowsFrontend: __init__...
10-28 07:44 DEBUG  WindowsFrontend: on_init...
10-28 07:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\translations, languages=['en_US', 'en']
10-28 07:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\translations, languages=['en_US', 'en']
10-28 07:47 INFO   root: === wubi 12.10 rev273 ===
10-28 07:47 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 07:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\installed file\\linux\\wubi.exe"']
10-28 07:47 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\data
10-28 07:47 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\bin\7z.exe
10-28 07:47 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 07:47 DEBUG  CommonBackend: Fetching basic info...
10-28 07:47 DEBUG  CommonBackend: original_exe=D:\installed file\linux\wubi.exe
10-28 07:47 DEBUG  CommonBackend: platform=win32
10-28 07:47 DEBUG  CommonBackend: osname=nt
10-28 07:47 DEBUG  CommonBackend: language=en_US
10-28 07:47 DEBUG  CommonBackend: encoding=cp1252
10-28 07:47 DEBUG  WindowsBackend: arch=amd64
10-28 07:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\data\isolist.ini
10-28 07:47 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 07:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 07:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 07:47 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 07:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 07:47 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 07:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 07:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 07:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 07:47 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 07:47 DEBUG  WindowsBackend: Fetching host info...
10-28 07:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 07:47 DEBUG  WindowsBackend: windows version=vista
10-28 07:47 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 07:47 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 07:47 DEBUG  WindowsBackend: windows_build=7601
10-28 07:47 DEBUG  WindowsBackend: gmt=5
10-28 07:47 DEBUG  WindowsBackend: country=US
10-28 07:47 DEBUG  WindowsBackend: timezone=America/New_York
10-28 07:47 DEBUG  WindowsBackend: windows_username=sandesh
10-28 07:47 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 07:47 DEBUG  WindowsBackend: user_directory=
10-28 07:47 DEBUG  WindowsBackend: windows_language_code=1033
10-28 07:47 DEBUG  WindowsBackend: windows_language=English
10-28 07:47 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 07:47 DEBUG  WindowsBackend: bootloader=vista
10-28 07:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29224.7578125 mb free ntfs)
10-28 07:47 DEBUG  WindowsBackend: drive=Drive(C: hd 29224.7578125 mb free ntfs)
10-28 07:47 DEBUG  WindowsBackend: drive=Drive(D: hd 90774.8984375 mb free ntfs)
10-28 07:47 DEBUG  WindowsBackend: drive=Drive(E: hd 61292.8242188 mb free ntfs)
10-28 07:47 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 07:47 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 07:47 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 07:47 DEBUG  WindowsBackend: uninstaller_path=None
10-28 07:47 DEBUG  WindowsBackend: previous_target_dir=None
10-28 07:47 DEBUG  WindowsBackend: previous_distro_name=None
10-28 07:47 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 07:47 DEBUG  WindowsBackend: keyboard_layout=us
10-28 07:47 DEBUG  WindowsBackend: keyboard_variant=
10-28 07:47 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 07:47 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 07:47 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 07:47 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 07:47 DEBUG  CommonBackend: Searching for local CDs
10-28 07:47 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp is a valid Ubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp is a valid Ubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp is a valid Kubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp is a valid Kubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp is a valid Mythbuntu CD
10-28 07:47 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp is a valid Mythbuntu CD
10-28 07:47 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp is a valid Edubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp is a valid Edubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp is a valid Lubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp is a valid Lubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:47 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:47 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:47 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:47 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:47 INFO   root: Running the installer...
10-28 07:47 DEBUG  WindowsFrontend: __init__...
10-28 07:47 DEBUG  WindowsFrontend: on_init...
10-28 07:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\translations, languages=['en_US', 'en']
10-28 07:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\translations, languages=['en_US', 'en']
10-28 07:51 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sandesh
10-28 07:51 INFO   root: Received settings
10-28 07:51 DEBUG  CommonBackend: Searching for local CD
10-28 07:51 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp is a valid Ubuntu CD
10-28 07:51 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\casper\filesystem.squashfs
10-28 07:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:51 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:51 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:51 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:51 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:51 DEBUG  CommonBackend: Searching for local ISO
10-28 07:51 DEBUG  Distro:   checking Ubuntu ISO D:\installed file\linux\ubuntu-12.10-desktop-i386.iso
10-28 07:51 DEBUG  WindowsBackend:   extracting .disk\info from D:\installed file\linux\ubuntu-12.10-desktop-i386.iso
10-28 07:51 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
10-28 07:51 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
10-28 07:51 INFO   Distro: Found a valid iso for Ubuntu: D:\installed file\linux\ubuntu-12.10-desktop-i386.iso
10-28 07:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\translations, languages=['en_US', 'en']
10-28 07:51 DEBUG  TaskList: # Running tasklist...
10-28 07:51 DEBUG  TaskList: ## Running select_target_dir...
10-28 07:51 INFO   WindowsBackend: Installing into C:\ubuntu
10-28 07:51 DEBUG  TaskList: ## Finished select_target_dir
10-28 07:51 DEBUG  TaskList: ## Running create_dir_structure...
10-28 07:51 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-28 07:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-28 07:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-28 07:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-28 07:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-28 07:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-28 07:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-28 07:51 DEBUG  TaskList: ## Finished create_dir_structure
10-28 07:51 DEBUG  TaskList: ## Running uncompress_target_dir...
10-28 07:51 DEBUG  TaskList: ## Finished uncompress_target_dir
10-28 07:51 DEBUG  TaskList: ## Running create_uninstaller...
10-28 07:51 DEBUG  WindowsBackend: Copying uninstaller D:\installed file\linux\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-28 07:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-28 07:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-28 07:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-28 07:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-28 07:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
10-28 07:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-28 07:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-28 07:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-28 07:51 DEBUG  TaskList: ## Finished create_uninstaller
10-28 07:51 DEBUG  TaskList: ## Running copy_installation_files...
10-28 07:51 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-28 07:51 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\winboot -> C:\ubuntu\winboot
10-28 07:51 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl9C5E.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-28 07:51 DEBUG  TaskList: ## Finished copy_installation_files
10-28 07:51 DEBUG  TaskList: ## Running get_iso...
10-28 07:51 DEBUG  CommonBackend: Trying to use ISO D:\installed file\linux\ubuntu-12.10-desktop-i386.iso
10-28 07:51 DEBUG  TaskList: New task check_iso
10-28 07:51 DEBUG  TaskList: ### Running check_iso...
10-28 07:51 DEBUG  CommonBackend: Checking D:\installed file\linux\ubuntu-12.10-desktop-i386.iso
10-28 07:51 DEBUG  Distro:   checking Ubuntu ISO D:\installed file\linux\ubuntu-12.10-desktop-i386.iso
10-28 07:51 INFO   Distro: Found a valid iso for Ubuntu: D:\installed file\linux\ubuntu-12.10-desktop-i386.iso
10-28 07:51 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
10-28 07:51 DEBUG  TaskList: New task get_metalink
10-28 07:51 DEBUG  TaskList: #### Running get_metalink...
10-28 07:51 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) > C:\ubuntu\install
10-28 07:51 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 07:51 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) > C:\ubuntu\install
10-28 07:51 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 07:51 DEBUG  TaskList: #### Finished get_metalink
10-28 07:51 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for D:\installed file\linux\ubuntu-12.10-desktop-i386.iso, ignoring
10-28 07:51 DEBUG  TaskList: ### Finished check_iso
10-28 07:51 DEBUG  TaskList: New task copy_file
10-28 07:51 DEBUG  CommonBackend: Copying D:\installed file\linux\ubuntu-12.10-desktop-i386.iso > C:\ubuntu\install\installation.iso
10-28 07:51 DEBUG  TaskList: ### Running copy_file...
10-28 07:51 INFO   WindowsFrontend: Operation cancelled
10-28 07:51 DEBUG  WindowsFrontend: frontend.quit
10-28 07:51 DEBUG  WindowsFrontend: frontend.on_quit
10-28 07:51 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
10-28 07:51 DEBUG  TaskList: # Cancelling tasklist
10-28 07:51 DEBUG  TaskList: ### Finished copy_file
10-28 07:51 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
10-28 07:51 DEBUG  root: application.on_quit
10-28 07:51 DEBUG  root: Forceful exit
10-28 07:51 INFO   root: sys.exit
10-28 07:52 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ishaan
10-28 07:52 INFO   root: Received settings
10-28 07:52 DEBUG  CommonBackend: Searching for local CD
10-28 07:52 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp is a valid Ubuntu CD
10-28 07:52 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\casper\filesystem.squashfs
10-28 07:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:52 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:52 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:52 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:52 DEBUG  CommonBackend: Searching for local ISO
10-28 07:52 DEBUG  Distro:   checking Ubuntu ISO D:\installed file\linux\ubuntu-12.10-desktop-i386.iso
10-28 07:52 DEBUG  WindowsBackend:   extracting .disk\info from D:\installed file\linux\ubuntu-12.10-desktop-i386.iso
10-28 07:52 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
10-28 07:52 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
10-28 07:52 INFO   Distro: Found a valid iso for Ubuntu: D:\installed file\linux\ubuntu-12.10-desktop-i386.iso
10-28 07:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\translations, languages=['en_US', 'en']
10-28 07:52 DEBUG  TaskList: # Running tasklist...
10-28 07:52 DEBUG  TaskList: ## Running select_target_dir...
10-28 07:52 INFO   WindowsBackend: Installing into D:\ubuntu
10-28 07:52 DEBUG  TaskList: ## Finished select_target_dir
10-28 07:52 DEBUG  TaskList: ## Running create_dir_structure...
10-28 07:52 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-28 07:52 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-28 07:52 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-28 07:52 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-28 07:52 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-28 07:52 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-28 07:52 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-28 07:52 DEBUG  TaskList: ## Finished create_dir_structure
10-28 07:52 DEBUG  TaskList: ## Running uncompress_target_dir...
10-28 07:52 DEBUG  TaskList: ## Finished uncompress_target_dir
10-28 07:52 DEBUG  TaskList: ## Running create_uninstaller...
10-28 07:52 DEBUG  WindowsBackend: Copying uninstaller D:\installed file\linux\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-28 07:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-28 07:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-28 07:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-28 07:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-28 07:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
10-28 07:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-28 07:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-28 07:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-28 07:52 DEBUG  TaskList: ## Finished create_uninstaller
10-28 07:52 DEBUG  TaskList: ## Running copy_installation_files...
10-28 07:52 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-28 07:52 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\winboot -> D:\ubuntu\winboot
10-28 07:52 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl5BB6.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
10-28 07:52 DEBUG  TaskList: ## Finished copy_installation_files
10-28 07:52 DEBUG  TaskList: ## Running get_iso...
10-28 07:52 DEBUG  CommonBackend: Trying to use ISO D:\installed file\linux\ubuntu-12.10-desktop-i386.iso
10-28 07:52 DEBUG  TaskList: New task check_iso
10-28 07:52 DEBUG  TaskList: ### Running check_iso...
10-28 07:52 DEBUG  CommonBackend: Checking D:\installed file\linux\ubuntu-12.10-desktop-i386.iso
10-28 07:52 DEBUG  Distro:   checking Ubuntu ISO D:\installed file\linux\ubuntu-12.10-desktop-i386.iso
10-28 07:52 INFO   Distro: Found a valid iso for Ubuntu: D:\installed file\linux\ubuntu-12.10-desktop-i386.iso
10-28 07:52 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
10-28 07:52 DEBUG  TaskList: New task get_metalink
10-28 07:52 DEBUG  TaskList: #### Running get_metalink...
10-28 07:52 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) > D:\ubuntu\install
10-28 07:52 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 07:52 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) > D:\ubuntu\install
10-28 07:52 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 07:52 DEBUG  TaskList: #### Finished get_metalink
10-28 07:52 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for D:\installed file\linux\ubuntu-12.10-desktop-i386.iso, ignoring
10-28 07:52 DEBUG  TaskList: ### Finished check_iso
10-28 07:52 DEBUG  TaskList: New task copy_file
10-28 07:52 DEBUG  CommonBackend: Copying D:\installed file\linux\ubuntu-12.10-desktop-i386.iso > D:\ubuntu\install\installation.iso
10-28 07:52 DEBUG  TaskList: ### Running copy_file...
10-28 07:52 DEBUG  TaskList: ### Finished copy_file
10-28 07:52 DEBUG  TaskList: ## Finished get_iso
10-28 07:52 DEBUG  TaskList: ## Running extract_kernel...
10-28 07:52 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\installation.iso
10-28 07:52 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\installation.iso
10-28 07:52 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\installation.iso
10-28 07:52 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\installation.iso
10-28 07:52 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-28 07:52 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
10-28 07:52 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = dedeef44f082210eb0d605d21837feb5 == dedeef44f082210eb0d605d21837feb5
10-28 07:52 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
10-28 07:52 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = bf4099046c27293af1f7ec8c76baf1c7 == bf4099046c27293af1f7ec8c76baf1c7
10-28 07:52 DEBUG  TaskList: ## Finished extract_kernel
10-28 07:52 DEBUG  TaskList: ## Running choose_disk_sizes...
10-28 07:52 DEBUG  WindowsBackend: total size=20000
  root=19744
  swap=256
  home=0
  usr=0
10-28 07:52 DEBUG  TaskList: ## Finished choose_disk_sizes
10-28 07:52 DEBUG  TaskList: ## Running create_preseed...
10-28 07:52 DEBUG  TaskList: ## Finished create_preseed
10-28 07:52 DEBUG  TaskList: ## Running modify_bootloader...
10-28 07:52 DEBUG  TaskList: New task modify_bcd
10-28 07:52 DEBUG  TaskList: ### Running modify_bcd...
10-28 07:52 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 29237.4492188 mb free ntfs)
10-28 07:52 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa4d-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa4d-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 07:52 DEBUG  TaskList: # Cancelling tasklist
10-28 07:52 DEBUG  TaskList: New task modify_bcd
10-28 07:52 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa4d-4ca4-11e1-853b-984507711b55} device partition=D:
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
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa4d-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 07:53 DEBUG  TaskList: New task modify_bcd
10-28 07:53 DEBUG  TaskList: New task modify_bcd
10-28 07:53 DEBUG  TaskList: New task modify_bcd
10-28 07:53 DEBUG  TaskList: ## Finished modify_bootloader
10-28 07:53 DEBUG  TaskList: # Finished tasklist
10-28 07:53 INFO   root: === wubi 12.10 rev273 ===
10-28 07:53 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 07:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
10-28 07:53 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\data
10-28 07:53 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\bin\7z.exe
10-28 07:53 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 07:53 DEBUG  CommonBackend: Fetching basic info...
10-28 07:53 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-28 07:53 DEBUG  CommonBackend: platform=win32
10-28 07:53 DEBUG  CommonBackend: osname=nt
10-28 07:53 DEBUG  CommonBackend: language=en_US
10-28 07:53 DEBUG  CommonBackend: encoding=cp1252
10-28 07:53 DEBUG  WindowsBackend: arch=amd64
10-28 07:53 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\data\isolist.ini
10-28 07:53 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 07:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 07:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 07:53 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 07:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 07:53 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 07:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 07:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 07:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 07:53 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 07:53 DEBUG  WindowsBackend: Fetching host info...
10-28 07:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 07:53 DEBUG  WindowsBackend: windows version=vista
10-28 07:53 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 07:53 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 07:53 DEBUG  WindowsBackend: windows_build=7601
10-28 07:53 DEBUG  WindowsBackend: gmt=5
10-28 07:53 DEBUG  WindowsBackend: country=US
10-28 07:53 DEBUG  WindowsBackend: timezone=America/New_York
10-28 07:53 DEBUG  WindowsBackend: windows_username=sandesh
10-28 07:53 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 07:53 DEBUG  WindowsBackend: user_directory=
10-28 07:53 DEBUG  WindowsBackend: windows_language_code=1033
10-28 07:53 DEBUG  WindowsBackend: windows_language=English
10-28 07:53 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 07:53 DEBUG  WindowsBackend: bootloader=vista
10-28 07:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28857.8164063 mb free ntfs)
10-28 07:53 DEBUG  WindowsBackend: drive=Drive(C: hd 28857.8164063 mb free ntfs)
10-28 07:53 DEBUG  WindowsBackend: drive=Drive(D: hd 89997.9570313 mb free ntfs)
10-28 07:53 DEBUG  WindowsBackend: drive=Drive(E: hd 61292.8242188 mb free ntfs)
10-28 07:53 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 07:53 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 07:53 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 07:53 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-28 07:53 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-28 07:53 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-28 07:53 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 07:53 DEBUG  WindowsBackend: keyboard_layout=us
10-28 07:53 DEBUG  WindowsBackend: keyboard_variant=
10-28 07:53 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 07:53 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 07:53 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 07:53 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 07:53 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 07:53 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
10-28 07:53 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
10-28 07:53 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
10-28 07:53 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 07:53 DEBUG  CommonBackend: Searching for local CDs
10-28 07:53 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Ubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Ubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Kubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Kubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Mythbuntu CD
10-28 07:53 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Mythbuntu CD
10-28 07:53 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Edubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Edubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Lubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Lubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:53 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:53 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:53 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:53 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:53 INFO   root: Already installed, running the uninstaller...
10-28 07:53 INFO   root: Running the uninstaller...
10-28 07:53 INFO   CommonBackend: This is the uninstaller running
10-28 07:53 DEBUG  WindowsFrontend: __init__...
10-28 07:53 DEBUG  WindowsFrontend: on_init...
10-28 07:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\translations, languages=['en_US', 'en']
10-28 07:54 INFO   root: Received settings
10-28 07:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\translations, languages=['en_US', 'en']
10-28 07:54 DEBUG  TaskList: # Running tasklist...
10-28 07:54 DEBUG  TaskList: ## Running Remove bootloader entry...
10-28 07:54 DEBUG  WindowsBackend: Could not find bcd id
10-28 07:54 DEBUG  WindowsBackend: undo_bootini C:
10-28 07:54 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 28857.8164063 mb free ntfs)
10-28 07:54 DEBUG  WindowsBackend: undo_bootini D:
10-28 07:54 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 89997.9570313 mb free ntfs)
10-28 07:54 DEBUG  WindowsBackend: undo_bootini E:
10-28 07:54 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 61292.8242188 mb free ntfs)
10-28 07:54 DEBUG  WindowsBackend: undo_bootini H:
10-28 07:54 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 844.5234375 mb free ntfs)
10-28 07:54 DEBUG  WindowsBackend: undo_bootini M:
10-28 07:54 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
10-28 07:54 DEBUG  TaskList: ## Finished Remove bootloader entry
10-28 07:54 DEBUG  TaskList: ## Running Remove target dir...
10-28 07:54 DEBUG  CommonBackend: Deleting D:\ubuntu
10-28 07:54 DEBUG  TaskList: ## Finished Remove target dir
10-28 07:54 DEBUG  TaskList: ## Running Remove registry key...
10-28 07:54 DEBUG  TaskList: ## Finished Remove registry key
10-28 07:54 DEBUG  TaskList: # Finished tasklist
10-28 07:54 INFO   root: Almost finished uninstalling
10-28 07:54 INFO   root: Finished uninstallation
10-28 07:54 DEBUG  CommonBackend: Fetching basic info...
10-28 07:54 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-28 07:54 DEBUG  CommonBackend: platform=win32
10-28 07:54 DEBUG  CommonBackend: osname=nt
10-28 07:54 DEBUG  WindowsBackend: arch=amd64
10-28 07:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\data\isolist.ini
10-28 07:54 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 07:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 07:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 07:54 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 07:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 07:54 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 07:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 07:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 07:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 07:54 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 07:54 DEBUG  WindowsBackend: Fetching host info...
10-28 07:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 07:54 DEBUG  WindowsBackend: windows version=vista
10-28 07:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 07:54 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 07:54 DEBUG  WindowsBackend: windows_build=7601
10-28 07:54 DEBUG  WindowsBackend: gmt=5
10-28 07:54 DEBUG  WindowsBackend: country=US
10-28 07:54 DEBUG  WindowsBackend: timezone=America/New_York
10-28 07:54 DEBUG  WindowsBackend: windows_username=sandesh
10-28 07:54 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 07:54 DEBUG  WindowsBackend: user_directory=
10-28 07:54 DEBUG  WindowsBackend: windows_language_code=1033
10-28 07:54 DEBUG  WindowsBackend: windows_language=English
10-28 07:54 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 07:54 DEBUG  WindowsBackend: bootloader=vista
10-28 07:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28857.8007813 mb free ntfs)
10-28 07:54 DEBUG  WindowsBackend: drive=Drive(C: hd 28857.8007813 mb free ntfs)
10-28 07:54 DEBUG  WindowsBackend: drive=Drive(D: hd 90774.8984375 mb free ntfs)
10-28 07:54 DEBUG  WindowsBackend: drive=Drive(E: hd 61292.8242188 mb free ntfs)
10-28 07:54 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 07:54 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 07:54 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 07:54 DEBUG  WindowsBackend: uninstaller_path=None
10-28 07:54 DEBUG  WindowsBackend: previous_target_dir=None
10-28 07:54 DEBUG  WindowsBackend: previous_distro_name=None
10-28 07:54 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 07:54 DEBUG  WindowsBackend: keyboard_layout=us
10-28 07:54 DEBUG  WindowsBackend: keyboard_variant=
10-28 07:54 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 07:54 DEBUG  CommonBackend: Checking pre-specified ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 07:54 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 07:54 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 07:54 DEBUG  CommonBackend: Searching for local CDs
10-28 07:54 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Kubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Kubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Mythbuntu CD
10-28 07:54 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Mythbuntu CD
10-28 07:54 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Edubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Edubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Lubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Lubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:54 INFO   root: Running the installer...
10-28 07:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\translations, languages=['en_US', 'en']
10-28 07:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\translations, languages=['en_US', 'en']
10-28 07:54 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sandesh
10-28 07:54 INFO   root: Received settings
10-28 07:54 DEBUG  CommonBackend: Searching for local CD
10-28 07:54 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:54 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:54 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\translations, languages=['en_US', 'en']
10-28 07:54 DEBUG  TaskList: # Running tasklist...
10-28 07:54 DEBUG  TaskList: ## Running select_target_dir...
10-28 07:54 INFO   WindowsBackend: Installing into D:\ubuntu
10-28 07:54 DEBUG  TaskList: ## Finished select_target_dir
10-28 07:54 DEBUG  TaskList: ## Running create_dir_structure...
10-28 07:54 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-28 07:54 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-28 07:54 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-28 07:54 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-28 07:54 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-28 07:54 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-28 07:54 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-28 07:54 DEBUG  TaskList: ## Finished create_dir_structure
10-28 07:54 DEBUG  TaskList: ## Running uncompress_target_dir...
10-28 07:54 DEBUG  TaskList: ## Finished uncompress_target_dir
10-28 07:54 DEBUG  TaskList: ## Running create_uninstaller...
10-28 07:54 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-28 07:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-28 07:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-28 07:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-28 07:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-28 07:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
10-28 07:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-28 07:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-28 07:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-28 07:54 DEBUG  TaskList: ## Finished create_uninstaller
10-28 07:54 DEBUG  TaskList: ## Running copy_installation_files...
10-28 07:54 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-28 07:54 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\winboot -> D:\ubuntu\winboot
10-28 07:54 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl7252.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
10-28 07:54 DEBUG  TaskList: ## Finished copy_installation_files
10-28 07:54 DEBUG  TaskList: ## Running get_iso...
10-28 07:54 DEBUG  CommonBackend: Trying to use pre-specified ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 07:54 DEBUG  TaskList: New task is_valid_iso
10-28 07:54 DEBUG  TaskList: ### Running is_valid_iso...
10-28 07:54 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 07:54 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 07:54 DEBUG  TaskList: ### Finished is_valid_iso
10-28 07:54 DEBUG  TaskList: New task check_iso
10-28 07:54 DEBUG  TaskList: ### Running check_iso...
10-28 07:54 DEBUG  CommonBackend: Checking D:\ubuntu-12.10-desktop-i386.iso
10-28 07:54 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 07:54 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 07:54 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
10-28 07:54 DEBUG  TaskList: New task get_metalink
10-28 07:54 DEBUG  TaskList: #### Running get_metalink...
10-28 07:54 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) > D:\ubuntu\install
10-28 07:54 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 07:54 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) > D:\ubuntu\install
10-28 07:54 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 07:54 DEBUG  TaskList: #### Finished get_metalink
10-28 07:54 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for D:\ubuntu-12.10-desktop-i386.iso, ignoring
10-28 07:54 DEBUG  TaskList: ### Finished check_iso
10-28 07:54 DEBUG  TaskList: New task copy_file
10-28 07:54 DEBUG  CommonBackend: Copying D:\ubuntu-12.10-desktop-i386.iso > D:\ubuntu\install\installation.iso
10-28 07:54 DEBUG  TaskList: ### Running copy_file...
10-28 07:55 DEBUG  TaskList: ### Finished copy_file
10-28 07:55 DEBUG  TaskList: ## Finished get_iso
10-28 07:55 DEBUG  TaskList: ## Running extract_kernel...
10-28 07:55 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\installation.iso
10-28 07:55 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\installation.iso
10-28 07:55 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\installation.iso
10-28 07:55 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\installation.iso
10-28 07:55 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-28 07:55 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
10-28 07:55 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = dedeef44f082210eb0d605d21837feb5 == dedeef44f082210eb0d605d21837feb5
10-28 07:55 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
10-28 07:55 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = bf4099046c27293af1f7ec8c76baf1c7 == bf4099046c27293af1f7ec8c76baf1c7
10-28 07:55 DEBUG  TaskList: ## Finished extract_kernel
10-28 07:55 DEBUG  TaskList: ## Running choose_disk_sizes...
10-28 07:55 DEBUG  WindowsBackend: total size=20000
  root=19744
  swap=256
  home=0
  usr=0
10-28 07:55 DEBUG  TaskList: ## Finished choose_disk_sizes
10-28 07:55 DEBUG  TaskList: ## Running create_preseed...
10-28 07:55 DEBUG  TaskList: ## Finished create_preseed
10-28 07:55 DEBUG  TaskList: ## Running modify_bootloader...
10-28 07:55 DEBUG  TaskList: New task modify_bcd
10-28 07:55 DEBUG  TaskList: ### Running modify_bcd...
10-28 07:55 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 28857.8007813 mb free ntfs)
10-28 07:55 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa4e-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa4e-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 07:55 DEBUG  TaskList: # Cancelling tasklist
10-28 07:55 DEBUG  TaskList: New task modify_bcd
10-28 07:55 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa4e-4ca4-11e1-853b-984507711b55} device partition=D:
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
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa4e-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 07:55 DEBUG  TaskList: New task modify_bcd
10-28 07:55 DEBUG  TaskList: New task modify_bcd
10-28 07:55 DEBUG  TaskList: New task modify_bcd
10-28 07:55 DEBUG  TaskList: ## Finished modify_bootloader
10-28 07:55 DEBUG  TaskList: # Finished tasklist
10-28 07:57 INFO   root: === wubi 12.10 rev273 ===
10-28 07:57 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 07:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
10-28 07:57 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\data
10-28 07:57 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\bin\7z.exe
10-28 07:57 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 07:57 DEBUG  CommonBackend: Fetching basic info...
10-28 07:57 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
10-28 07:57 DEBUG  CommonBackend: platform=win32
10-28 07:57 DEBUG  CommonBackend: osname=nt
10-28 07:57 DEBUG  CommonBackend: language=en_US
10-28 07:57 DEBUG  CommonBackend: encoding=cp1252
10-28 07:57 DEBUG  WindowsBackend: arch=amd64
10-28 07:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\data\isolist.ini
10-28 07:57 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 07:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 07:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 07:57 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 07:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 07:57 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 07:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 07:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 07:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 07:57 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 07:57 DEBUG  WindowsBackend: Fetching host info...
10-28 07:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 07:57 DEBUG  WindowsBackend: windows version=vista
10-28 07:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 07:57 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 07:57 DEBUG  WindowsBackend: windows_build=7601
10-28 07:57 DEBUG  WindowsBackend: gmt=5
10-28 07:57 DEBUG  WindowsBackend: country=US
10-28 07:57 DEBUG  WindowsBackend: timezone=America/New_York
10-28 07:57 DEBUG  WindowsBackend: windows_username=sandesh
10-28 07:57 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 07:57 DEBUG  WindowsBackend: user_directory=
10-28 07:57 DEBUG  WindowsBackend: windows_language_code=1033
10-28 07:57 DEBUG  WindowsBackend: windows_language=English
10-28 07:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 07:57 DEBUG  WindowsBackend: bootloader=vista
10-28 07:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28855.8632813 mb free ntfs)
10-28 07:57 DEBUG  WindowsBackend: drive=Drive(C: hd 28855.8632813 mb free ntfs)
10-28 07:57 DEBUG  WindowsBackend: drive=Drive(D: hd 89997.9570313 mb free ntfs)
10-28 07:57 DEBUG  WindowsBackend: drive=Drive(E: hd 61292.8242188 mb free ntfs)
10-28 07:57 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 07:57 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 07:57 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 07:57 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-28 07:57 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-28 07:57 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-28 07:57 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 07:57 DEBUG  WindowsBackend: keyboard_layout=us
10-28 07:57 DEBUG  WindowsBackend: keyboard_variant=
10-28 07:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 07:57 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 07:57 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 07:57 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 07:57 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 07:57 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
10-28 07:57 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
10-28 07:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
10-28 07:57 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 07:57 DEBUG  CommonBackend: Searching for local CDs
10-28 07:57 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp is a valid Ubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp is a valid Ubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp is a valid Kubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp is a valid Kubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp is a valid Mythbuntu CD
10-28 07:57 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp is a valid Mythbuntu CD
10-28 07:57 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp is a valid Edubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp is a valid Edubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp is a valid Lubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp is a valid Lubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:57 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:57 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:57 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:57 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:57 INFO   root: Running the uninstaller...
10-28 07:57 INFO   CommonBackend: This is the uninstaller running
10-28 07:57 DEBUG  WindowsFrontend: __init__...
10-28 07:57 DEBUG  WindowsFrontend: on_init...
10-28 07:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\translations, languages=['en_US', 'en']
10-28 07:57 INFO   root: Received settings
10-28 07:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\translations, languages=['en_US', 'en']
10-28 07:57 DEBUG  TaskList: # Running tasklist...
10-28 07:57 DEBUG  TaskList: ## Running Remove bootloader entry...
10-28 07:57 DEBUG  WindowsBackend: Could not find bcd id
10-28 07:57 DEBUG  WindowsBackend: undo_bootini C:
10-28 07:57 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 28855.8632813 mb free ntfs)
10-28 07:57 DEBUG  WindowsBackend: undo_bootini D:
10-28 07:57 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 89997.9570313 mb free ntfs)
10-28 07:57 DEBUG  WindowsBackend: undo_bootini E:
10-28 07:57 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 61292.8242188 mb free ntfs)
10-28 07:57 DEBUG  WindowsBackend: undo_bootini H:
10-28 07:57 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 844.5234375 mb free ntfs)
10-28 07:57 DEBUG  WindowsBackend: undo_bootini M:
10-28 07:57 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
10-28 07:57 DEBUG  TaskList: ## Finished Remove bootloader entry
10-28 07:57 DEBUG  TaskList: ## Running Remove target dir...
10-28 07:57 DEBUG  CommonBackend: Deleting D:\ubuntu
10-28 07:57 DEBUG  TaskList: ## Finished Remove target dir
10-28 07:57 DEBUG  TaskList: ## Running Remove registry key...
10-28 07:57 DEBUG  TaskList: ## Finished Remove registry key
10-28 07:57 DEBUG  TaskList: # Finished tasklist
10-28 07:57 INFO   root: Almost finished uninstalling
10-28 07:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl9868.tmp\translations, languages=['en_US', 'en']
10-28 07:57 INFO   root: Finished uninstallation
10-28 07:57 DEBUG  root: application.quit
10-28 07:57 DEBUG  WindowsFrontend: frontend.quit
10-28 07:57 DEBUG  WindowsFrontend: frontend.on_quit
10-28 07:57 DEBUG  root: application.on_quit
10-28 07:57 INFO   root: sys.exit
10-28 07:58 INFO   root: === wubi 12.10 rev273 ===
10-28 07:58 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 07:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
10-28 07:58 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\data
10-28 07:58 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\bin\7z.exe
10-28 07:58 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 07:58 DEBUG  CommonBackend: Fetching basic info...
10-28 07:58 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-28 07:58 DEBUG  CommonBackend: platform=win32
10-28 07:58 DEBUG  CommonBackend: osname=nt
10-28 07:58 DEBUG  CommonBackend: language=en_US
10-28 07:58 DEBUG  CommonBackend: encoding=cp1252
10-28 07:58 DEBUG  WindowsBackend: arch=amd64
10-28 07:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\data\isolist.ini
10-28 07:58 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 07:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 07:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 07:58 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 07:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 07:58 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 07:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 07:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 07:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 07:58 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 07:58 DEBUG  WindowsBackend: Fetching host info...
10-28 07:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 07:58 DEBUG  WindowsBackend: windows version=vista
10-28 07:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 07:58 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 07:58 DEBUG  WindowsBackend: windows_build=7601
10-28 07:58 DEBUG  WindowsBackend: gmt=5
10-28 07:58 DEBUG  WindowsBackend: country=US
10-28 07:58 DEBUG  WindowsBackend: timezone=America/New_York
10-28 07:58 DEBUG  WindowsBackend: windows_username=sandesh
10-28 07:58 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 07:58 DEBUG  WindowsBackend: user_directory=
10-28 07:58 DEBUG  WindowsBackend: windows_language_code=1033
10-28 07:58 DEBUG  WindowsBackend: windows_language=English
10-28 07:58 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 07:58 DEBUG  WindowsBackend: bootloader=vista
10-28 07:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28856.3164063 mb free ntfs)
10-28 07:58 DEBUG  WindowsBackend: drive=Drive(C: hd 28856.3164063 mb free ntfs)
10-28 07:58 DEBUG  WindowsBackend: drive=Drive(D: hd 90649.3242188 mb free ntfs)
10-28 07:58 DEBUG  WindowsBackend: drive=Drive(E: hd 61292.8242188 mb free ntfs)
10-28 07:58 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 07:58 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 07:58 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 07:58 DEBUG  WindowsBackend: uninstaller_path=None
10-28 07:58 DEBUG  WindowsBackend: previous_target_dir=None
10-28 07:58 DEBUG  WindowsBackend: previous_distro_name=None
10-28 07:58 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 07:58 DEBUG  WindowsBackend: keyboard_layout=us
10-28 07:58 DEBUG  WindowsBackend: keyboard_variant=
10-28 07:58 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 07:58 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 07:58 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 07:58 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 07:58 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 07:58 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
10-28 07:58 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
10-28 07:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
10-28 07:58 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 07:58 DEBUG  CommonBackend: Searching for local CDs
10-28 07:58 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp is a valid Kubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp is a valid Kubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp is a valid Mythbuntu CD
10-28 07:58 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp is a valid Mythbuntu CD
10-28 07:58 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp is a valid Edubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp is a valid Edubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp is a valid Lubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp is a valid Lubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 07:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 07:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 07:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 07:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:58 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 07:58 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:58 INFO   root: Running the installer...
10-28 07:58 DEBUG  WindowsFrontend: __init__...
10-28 07:58 DEBUG  WindowsFrontend: on_init...
10-28 07:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\translations, languages=['en_US', 'en']
10-28 07:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\translations, languages=['en_US', 'en']
10-28 07:58 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sandesh
10-28 07:58 INFO   root: Received settings
10-28 07:58 DEBUG  CommonBackend: Searching for local CD
10-28 07:58 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 07:58 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 07:58 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 07:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\translations, languages=['en_US', 'en']
10-28 07:58 DEBUG  TaskList: # Running tasklist...
10-28 07:58 DEBUG  TaskList: ## Running select_target_dir...
10-28 07:58 INFO   WindowsBackend: Installing into D:\ubuntu
10-28 07:58 DEBUG  TaskList: ## Finished select_target_dir
10-28 07:58 DEBUG  TaskList: ## Running create_dir_structure...
10-28 07:58 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-28 07:58 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-28 07:58 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-28 07:58 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-28 07:58 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-28 07:58 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-28 07:58 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-28 07:58 DEBUG  TaskList: ## Finished create_dir_structure
10-28 07:58 DEBUG  TaskList: ## Running uncompress_target_dir...
10-28 07:58 DEBUG  TaskList: ## Finished uncompress_target_dir
10-28 07:58 DEBUG  TaskList: ## Running create_uninstaller...
10-28 07:58 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-28 07:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-28 07:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-28 07:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-28 07:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-28 07:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
10-28 07:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-28 07:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-28 07:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-28 07:58 DEBUG  TaskList: ## Finished create_uninstaller
10-28 07:58 DEBUG  TaskList: ## Running copy_installation_files...
10-28 07:58 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-28 07:58 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\winboot -> D:\ubuntu\winboot
10-28 07:58 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl5C52.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
10-28 07:58 DEBUG  TaskList: ## Finished copy_installation_files
10-28 07:58 DEBUG  TaskList: ## Running get_iso...
10-28 07:58 DEBUG  CommonBackend: Trying to use pre-specified ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 07:58 DEBUG  TaskList: New task is_valid_iso
10-28 07:58 DEBUG  TaskList: ### Running is_valid_iso...
10-28 07:58 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 07:58 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 07:58 DEBUG  TaskList: ### Finished is_valid_iso
10-28 07:58 DEBUG  TaskList: New task check_iso
10-28 07:58 DEBUG  TaskList: ### Running check_iso...
10-28 07:58 DEBUG  CommonBackend: Checking D:\ubuntu-12.10-desktop-i386.iso
10-28 07:58 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 07:58 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 07:58 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
10-28 07:58 DEBUG  TaskList: New task get_metalink
10-28 07:58 DEBUG  TaskList: #### Running get_metalink...
10-28 07:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) > D:\ubuntu\install
10-28 07:58 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 07:58 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) > D:\ubuntu\install
10-28 07:58 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 07:58 DEBUG  TaskList: #### Finished get_metalink
10-28 07:58 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for D:\ubuntu-12.10-desktop-i386.iso, ignoring
10-28 07:58 DEBUG  TaskList: ### Finished check_iso
10-28 07:58 DEBUG  TaskList: New task copy_file
10-28 07:58 DEBUG  CommonBackend: Copying D:\ubuntu-12.10-desktop-i386.iso > D:\ubuntu\install\installation.iso
10-28 07:58 DEBUG  TaskList: ### Running copy_file...
10-28 07:59 DEBUG  TaskList: ### Finished copy_file
10-28 07:59 DEBUG  TaskList: ## Finished get_iso
10-28 07:59 DEBUG  TaskList: ## Running extract_kernel...
10-28 07:59 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\installation.iso
10-28 07:59 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\installation.iso
10-28 07:59 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\installation.iso
10-28 07:59 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\installation.iso
10-28 07:59 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-28 07:59 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
10-28 07:59 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = dedeef44f082210eb0d605d21837feb5 == dedeef44f082210eb0d605d21837feb5
10-28 07:59 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
10-28 07:59 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = bf4099046c27293af1f7ec8c76baf1c7 == bf4099046c27293af1f7ec8c76baf1c7
10-28 07:59 DEBUG  TaskList: ## Finished extract_kernel
10-28 07:59 DEBUG  TaskList: ## Running choose_disk_sizes...
10-28 07:59 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
10-28 07:59 DEBUG  TaskList: ## Finished choose_disk_sizes
10-28 07:59 DEBUG  TaskList: ## Running create_preseed...
10-28 07:59 DEBUG  TaskList: ## Finished create_preseed
10-28 07:59 DEBUG  TaskList: ## Running modify_bootloader...
10-28 07:59 DEBUG  TaskList: New task modify_bcd
10-28 07:59 DEBUG  TaskList: ### Running modify_bcd...
10-28 07:59 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 28856.3164063 mb free ntfs)
10-28 07:59 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa4f-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa4f-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 07:59 DEBUG  TaskList: # Cancelling tasklist
10-28 07:59 DEBUG  TaskList: New task modify_bcd
10-28 07:59 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa4f-4ca4-11e1-853b-984507711b55} device partition=D:
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
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa4f-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 07:59 DEBUG  TaskList: New task modify_bcd
10-28 07:59 DEBUG  TaskList: New task modify_bcd
10-28 07:59 DEBUG  TaskList: New task modify_bcd
10-28 07:59 DEBUG  TaskList: ## Finished modify_bootloader
10-28 07:59 DEBUG  TaskList: # Finished tasklist
10-28 08:01 INFO   root: === wubi 12.10 rev273 ===
10-28 08:01 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 08:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
10-28 08:01 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\data
10-28 08:01 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\bin\7z.exe
10-28 08:01 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 08:01 DEBUG  CommonBackend: Fetching basic info...
10-28 08:01 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-28 08:01 DEBUG  CommonBackend: platform=win32
10-28 08:01 DEBUG  CommonBackend: osname=nt
10-28 08:01 DEBUG  CommonBackend: language=en_US
10-28 08:01 DEBUG  CommonBackend: encoding=cp1252
10-28 08:01 DEBUG  WindowsBackend: arch=amd64
10-28 08:01 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\data\isolist.ini
10-28 08:01 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 08:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 08:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 08:01 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 08:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 08:01 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 08:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 08:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 08:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 08:01 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 08:01 DEBUG  WindowsBackend: Fetching host info...
10-28 08:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 08:01 DEBUG  WindowsBackend: windows version=vista
10-28 08:01 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 08:01 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 08:01 DEBUG  WindowsBackend: windows_build=7601
10-28 08:01 DEBUG  WindowsBackend: gmt=5
10-28 08:01 DEBUG  WindowsBackend: country=US
10-28 08:01 DEBUG  WindowsBackend: timezone=America/New_York
10-28 08:01 DEBUG  WindowsBackend: windows_username=sandesh
10-28 08:01 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 08:01 DEBUG  WindowsBackend: user_directory=C:\Users\sandesh
10-28 08:01 DEBUG  WindowsBackend: windows_language_code=1033
10-28 08:01 DEBUG  WindowsBackend: windows_language=English
10-28 08:01 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 08:01 DEBUG  WindowsBackend: bootloader=vista
10-28 08:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28853.5507813 mb free ntfs)
10-28 08:01 DEBUG  WindowsBackend: drive=Drive(C: hd 28853.5507813 mb free ntfs)
10-28 08:01 DEBUG  WindowsBackend: drive=Drive(D: hd 89872.3828125 mb free ntfs)
10-28 08:01 DEBUG  WindowsBackend: drive=Drive(E: hd 61292.8242188 mb free ntfs)
10-28 08:01 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 08:01 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:01 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 08:01 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-28 08:01 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-28 08:01 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-28 08:01 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 08:01 DEBUG  WindowsBackend: keyboard_layout=us
10-28 08:01 DEBUG  WindowsBackend: keyboard_variant=
10-28 08:01 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 08:01 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 08:01 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 08:01 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 08:01 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:01 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
10-28 08:01 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
10-28 08:01 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
10-28 08:01 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:01 DEBUG  CommonBackend: Searching for local CDs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 INFO   root: Already installed, running the uninstaller...
10-28 08:01 INFO   root: Running the uninstaller...
10-28 08:01 INFO   CommonBackend: This is the uninstaller running
10-28 08:01 DEBUG  WindowsFrontend: __init__...
10-28 08:01 DEBUG  WindowsFrontend: on_init...
10-28 08:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\translations, languages=['en_US', 'en']
10-28 08:01 INFO   root: Received settings
10-28 08:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\translations, languages=['en_US', 'en']
10-28 08:01 DEBUG  TaskList: # Running tasklist...
10-28 08:01 DEBUG  TaskList: ## Running Remove bootloader entry...
10-28 08:01 DEBUG  WindowsBackend: Could not find bcd id
10-28 08:01 DEBUG  WindowsBackend: undo_bootini C:
10-28 08:01 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 28853.5507813 mb free ntfs)
10-28 08:01 DEBUG  WindowsBackend: undo_bootini D:
10-28 08:01 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 89872.3828125 mb free ntfs)
10-28 08:01 DEBUG  WindowsBackend: undo_bootini E:
10-28 08:01 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 61292.8242188 mb free ntfs)
10-28 08:01 DEBUG  WindowsBackend: undo_bootini H:
10-28 08:01 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:01 DEBUG  WindowsBackend: undo_bootini M:
10-28 08:01 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
10-28 08:01 DEBUG  TaskList: ## Finished Remove bootloader entry
10-28 08:01 DEBUG  TaskList: ## Running Remove target dir...
10-28 08:01 DEBUG  CommonBackend: Deleting D:\ubuntu
10-28 08:01 DEBUG  TaskList: ## Finished Remove target dir
10-28 08:01 DEBUG  TaskList: ## Running Remove registry key...
10-28 08:01 DEBUG  TaskList: ## Finished Remove registry key
10-28 08:01 DEBUG  TaskList: # Finished tasklist
10-28 08:01 INFO   root: Almost finished uninstalling
10-28 08:01 INFO   root: Finished uninstallation
10-28 08:01 DEBUG  CommonBackend: Fetching basic info...
10-28 08:01 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-28 08:01 DEBUG  CommonBackend: platform=win32
10-28 08:01 DEBUG  CommonBackend: osname=nt
10-28 08:01 DEBUG  WindowsBackend: arch=amd64
10-28 08:01 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\data\isolist.ini
10-28 08:01 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 08:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 08:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 08:01 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 08:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 08:01 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 08:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 08:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 08:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 08:01 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 08:01 DEBUG  WindowsBackend: Fetching host info...
10-28 08:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 08:01 DEBUG  WindowsBackend: windows version=vista
10-28 08:01 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 08:01 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 08:01 DEBUG  WindowsBackend: windows_build=7601
10-28 08:01 DEBUG  WindowsBackend: gmt=5
10-28 08:01 DEBUG  WindowsBackend: country=US
10-28 08:01 DEBUG  WindowsBackend: timezone=America/New_York
10-28 08:01 DEBUG  WindowsBackend: windows_username=sandesh
10-28 08:01 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 08:01 DEBUG  WindowsBackend: user_directory=C:\Users\sandesh
10-28 08:01 DEBUG  WindowsBackend: windows_language_code=1033
10-28 08:01 DEBUG  WindowsBackend: windows_language=English
10-28 08:01 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 08:01 DEBUG  WindowsBackend: bootloader=vista
10-28 08:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28853.0625 mb free ntfs)
10-28 08:01 DEBUG  WindowsBackend: drive=Drive(C: hd 28853.0625 mb free ntfs)
10-28 08:01 DEBUG  WindowsBackend: drive=Drive(D: hd 90649.3242188 mb free ntfs)
10-28 08:01 DEBUG  WindowsBackend: drive=Drive(E: hd 61292.8242188 mb free ntfs)
10-28 08:01 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 08:01 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:01 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 08:01 DEBUG  WindowsBackend: uninstaller_path=None
10-28 08:01 DEBUG  WindowsBackend: previous_target_dir=None
10-28 08:01 DEBUG  WindowsBackend: previous_distro_name=None
10-28 08:01 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 08:01 DEBUG  WindowsBackend: keyboard_layout=us
10-28 08:01 DEBUG  WindowsBackend: keyboard_variant=
10-28 08:01 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 08:01 DEBUG  CommonBackend: Checking pre-specified ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:01 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:01 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:01 DEBUG  CommonBackend: Searching for local CDs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:01 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:01 INFO   root: Running the installer...
10-28 08:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\translations, languages=['en_US', 'en']
10-28 08:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\translations, languages=['en_US', 'en']
10-28 08:02 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sandesh
10-28 08:02 INFO   root: Received settings
10-28 08:02 DEBUG  CommonBackend: Searching for local CD
10-28 08:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp is a valid Ubuntu CD
10-28 08:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\casper\filesystem.squashfs
10-28 08:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:02 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\translations, languages=['en_US', 'en']
10-28 08:02 DEBUG  TaskList: # Running tasklist...
10-28 08:02 DEBUG  TaskList: ## Running select_target_dir...
10-28 08:02 INFO   WindowsBackend: Installing into D:\ubuntu
10-28 08:02 DEBUG  TaskList: ## Finished select_target_dir
10-28 08:02 DEBUG  TaskList: ## Running create_dir_structure...
10-28 08:02 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-28 08:02 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-28 08:02 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-28 08:02 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-28 08:02 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-28 08:02 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-28 08:02 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-28 08:02 DEBUG  TaskList: ## Finished create_dir_structure
10-28 08:02 DEBUG  TaskList: ## Running uncompress_target_dir...
10-28 08:02 DEBUG  TaskList: ## Finished uncompress_target_dir
10-28 08:02 DEBUG  TaskList: ## Running create_uninstaller...
10-28 08:02 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-28 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-28 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-28 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-28 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-28 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
10-28 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-28 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-28 08:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-28 08:02 DEBUG  TaskList: ## Finished create_uninstaller
10-28 08:02 DEBUG  TaskList: ## Running copy_installation_files...
10-28 08:02 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-28 08:02 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\winboot -> D:\ubuntu\winboot
10-28 08:02 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl59F2.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
10-28 08:02 DEBUG  TaskList: ## Finished copy_installation_files
10-28 08:02 DEBUG  TaskList: ## Running get_iso...
10-28 08:02 DEBUG  CommonBackend: Trying to use pre-specified ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:02 DEBUG  TaskList: New task is_valid_iso
10-28 08:02 DEBUG  TaskList: ### Running is_valid_iso...
10-28 08:02 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:02 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:02 DEBUG  TaskList: ### Finished is_valid_iso
10-28 08:02 DEBUG  TaskList: New task check_iso
10-28 08:02 DEBUG  TaskList: ### Running check_iso...
10-28 08:02 DEBUG  CommonBackend: Checking D:\ubuntu-12.10-desktop-i386.iso
10-28 08:02 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:02 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:02 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
10-28 08:02 DEBUG  TaskList: New task get_metalink
10-28 08:02 DEBUG  TaskList: #### Running get_metalink...
10-28 08:02 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) > D:\ubuntu\install
10-28 08:02 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 08:02 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) > D:\ubuntu\install
10-28 08:02 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 08:02 DEBUG  TaskList: #### Finished get_metalink
10-28 08:02 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for D:\ubuntu-12.10-desktop-i386.iso, ignoring
10-28 08:02 DEBUG  TaskList: ### Finished check_iso
10-28 08:02 DEBUG  TaskList: New task copy_file
10-28 08:02 DEBUG  CommonBackend: Copying D:\ubuntu-12.10-desktop-i386.iso > D:\ubuntu\install\installation.iso
10-28 08:02 DEBUG  TaskList: ### Running copy_file...
10-28 08:03 DEBUG  TaskList: ### Finished copy_file
10-28 08:03 DEBUG  TaskList: ## Finished get_iso
10-28 08:03 DEBUG  TaskList: ## Running extract_kernel...
10-28 08:03 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\installation.iso
10-28 08:03 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\installation.iso
10-28 08:03 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\installation.iso
10-28 08:03 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\installation.iso
10-28 08:03 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-28 08:03 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
10-28 08:03 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = dedeef44f082210eb0d605d21837feb5 == dedeef44f082210eb0d605d21837feb5
10-28 08:03 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
10-28 08:03 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = bf4099046c27293af1f7ec8c76baf1c7 == bf4099046c27293af1f7ec8c76baf1c7
10-28 08:03 DEBUG  TaskList: ## Finished extract_kernel
10-28 08:03 DEBUG  TaskList: ## Running choose_disk_sizes...
10-28 08:03 DEBUG  WindowsBackend: total size=20000
  root=19744
  swap=256
  home=0
  usr=0
10-28 08:03 DEBUG  TaskList: ## Finished choose_disk_sizes
10-28 08:03 DEBUG  TaskList: ## Running create_preseed...
10-28 08:03 DEBUG  TaskList: ## Finished create_preseed
10-28 08:03 DEBUG  TaskList: ## Running modify_bootloader...
10-28 08:03 DEBUG  TaskList: New task modify_bcd
10-28 08:03 DEBUG  TaskList: ### Running modify_bcd...
10-28 08:03 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 28853.0625 mb free ntfs)
10-28 08:03 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa50-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa50-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 08:03 DEBUG  TaskList: # Cancelling tasklist
10-28 08:03 DEBUG  TaskList: New task modify_bcd
10-28 08:03 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa50-4ca4-11e1-853b-984507711b55} device partition=D:
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
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa50-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 08:03 DEBUG  TaskList: New task modify_bcd
10-28 08:03 DEBUG  TaskList: New task modify_bcd
10-28 08:03 DEBUG  TaskList: New task modify_bcd
10-28 08:03 DEBUG  TaskList: ## Finished modify_bootloader
10-28 08:03 DEBUG  TaskList: # Finished tasklist
10-28 08:05 INFO   root: === wubi 12.10 rev273 ===
10-28 08:05 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 08:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
10-28 08:05 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\data
10-28 08:05 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\bin\7z.exe
10-28 08:05 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 08:05 DEBUG  CommonBackend: Fetching basic info...
10-28 08:05 DEBUG  CommonBackend: original_exe=E:\wubi.exe
10-28 08:05 DEBUG  CommonBackend: platform=win32
10-28 08:05 DEBUG  CommonBackend: osname=nt
10-28 08:05 DEBUG  CommonBackend: language=en_US
10-28 08:05 DEBUG  CommonBackend: encoding=cp1252
10-28 08:05 DEBUG  WindowsBackend: arch=amd64
10-28 08:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\data\isolist.ini
10-28 08:05 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 08:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 08:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 08:05 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 08:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 08:05 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 08:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 08:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 08:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 08:05 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 08:05 DEBUG  WindowsBackend: Fetching host info...
10-28 08:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 08:05 DEBUG  WindowsBackend: windows version=vista
10-28 08:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 08:05 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 08:05 DEBUG  WindowsBackend: windows_build=7601
10-28 08:05 DEBUG  WindowsBackend: gmt=5
10-28 08:05 DEBUG  WindowsBackend: country=US
10-28 08:05 DEBUG  WindowsBackend: timezone=America/New_York
10-28 08:05 DEBUG  WindowsBackend: windows_username=sandesh
10-28 08:05 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 08:05 DEBUG  WindowsBackend: user_directory=C:\Users\sandesh
10-28 08:05 DEBUG  WindowsBackend: windows_language_code=1033
10-28 08:05 DEBUG  WindowsBackend: windows_language=English
10-28 08:05 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 08:05 DEBUG  WindowsBackend: bootloader=vista
10-28 08:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28849.6210938 mb free ntfs)
10-28 08:05 DEBUG  WindowsBackend: drive=Drive(C: hd 28849.6210938 mb free ntfs)
10-28 08:05 DEBUG  WindowsBackend: drive=Drive(D: hd 89872.3828125 mb free ntfs)
10-28 08:05 DEBUG  WindowsBackend: drive=Drive(E: hd 61290.4375 mb free ntfs)
10-28 08:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 08:05 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:05 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 08:05 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-28 08:05 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-28 08:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-28 08:05 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 08:05 DEBUG  WindowsBackend: keyboard_layout=us
10-28 08:05 DEBUG  WindowsBackend: keyboard_variant=
10-28 08:05 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 08:05 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 08:05 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 08:05 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 08:05 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:05 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
10-28 08:05 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
10-28 08:05 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
10-28 08:05 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:05 DEBUG  CommonBackend: Searching for local CDs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:05 INFO   root: Already installed, running the uninstaller...
10-28 08:05 INFO   root: Running the uninstaller...
10-28 08:05 INFO   CommonBackend: This is the uninstaller running
10-28 08:05 DEBUG  WindowsFrontend: __init__...
10-28 08:05 DEBUG  WindowsFrontend: on_init...
10-28 08:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\translations, languages=['en_US', 'en']
10-28 08:05 INFO   root: Received settings
10-28 08:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\translations, languages=['en_US', 'en']
10-28 08:05 DEBUG  TaskList: # Running tasklist...
10-28 08:05 DEBUG  TaskList: ## Running Remove bootloader entry...
10-28 08:05 DEBUG  WindowsBackend: Could not find bcd id
10-28 08:05 DEBUG  WindowsBackend: undo_bootini C:
10-28 08:05 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 28849.6210938 mb free ntfs)
10-28 08:05 DEBUG  WindowsBackend: undo_bootini D:
10-28 08:05 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 89872.3828125 mb free ntfs)
10-28 08:05 DEBUG  WindowsBackend: undo_bootini E:
10-28 08:05 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 61290.4375 mb free ntfs)
10-28 08:05 DEBUG  WindowsBackend: undo_bootini H:
10-28 08:05 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:05 DEBUG  WindowsBackend: undo_bootini M:
10-28 08:05 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
10-28 08:05 DEBUG  TaskList: ## Finished Remove bootloader entry
10-28 08:05 DEBUG  TaskList: ## Running Remove target dir...
10-28 08:05 DEBUG  CommonBackend: Deleting D:\ubuntu
10-28 08:05 DEBUG  TaskList: ## Finished Remove target dir
10-28 08:05 DEBUG  TaskList: ## Running Remove registry key...
10-28 08:05 DEBUG  TaskList: ## Finished Remove registry key
10-28 08:05 DEBUG  TaskList: # Finished tasklist
10-28 08:05 INFO   root: Almost finished uninstalling
10-28 08:05 INFO   root: Finished uninstallation
10-28 08:05 DEBUG  CommonBackend: Fetching basic info...
10-28 08:05 DEBUG  CommonBackend: original_exe=E:\wubi.exe
10-28 08:05 DEBUG  CommonBackend: platform=win32
10-28 08:05 DEBUG  CommonBackend: osname=nt
10-28 08:05 DEBUG  WindowsBackend: arch=amd64
10-28 08:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\data\isolist.ini
10-28 08:05 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 08:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 08:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 08:05 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 08:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 08:05 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 08:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 08:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 08:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 08:05 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 08:05 DEBUG  WindowsBackend: Fetching host info...
10-28 08:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 08:05 DEBUG  WindowsBackend: windows version=vista
10-28 08:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 08:05 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 08:05 DEBUG  WindowsBackend: windows_build=7601
10-28 08:05 DEBUG  WindowsBackend: gmt=5
10-28 08:05 DEBUG  WindowsBackend: country=US
10-28 08:05 DEBUG  WindowsBackend: timezone=America/New_York
10-28 08:05 DEBUG  WindowsBackend: windows_username=sandesh
10-28 08:05 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 08:05 DEBUG  WindowsBackend: user_directory=C:\Users\sandesh
10-28 08:05 DEBUG  WindowsBackend: windows_language_code=1033
10-28 08:05 DEBUG  WindowsBackend: windows_language=English
10-28 08:05 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 08:05 DEBUG  WindowsBackend: bootloader=vista
10-28 08:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28849.7226563 mb free ntfs)
10-28 08:05 DEBUG  WindowsBackend: drive=Drive(C: hd 28849.7226563 mb free ntfs)
10-28 08:05 DEBUG  WindowsBackend: drive=Drive(D: hd 90649.3242188 mb free ntfs)
10-28 08:05 DEBUG  WindowsBackend: drive=Drive(E: hd 61290.4375 mb free ntfs)
10-28 08:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 08:05 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:05 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 08:05 DEBUG  WindowsBackend: uninstaller_path=None
10-28 08:05 DEBUG  WindowsBackend: previous_target_dir=None
10-28 08:05 DEBUG  WindowsBackend: previous_distro_name=None
10-28 08:05 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 08:05 DEBUG  WindowsBackend: keyboard_layout=us
10-28 08:05 DEBUG  WindowsBackend: keyboard_variant=
10-28 08:05 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 08:05 DEBUG  CommonBackend: Checking pre-specified ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:05 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:05 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:05 DEBUG  CommonBackend: Searching for local CDs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:05 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:06 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:06 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:06 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:06 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:06 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:06 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:06 INFO   root: Running the installer...
10-28 08:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\translations, languages=['en_US', 'en']
10-28 08:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\translations, languages=['en_US', 'en']
10-28 08:06 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=16000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sandesh
10-28 08:06 INFO   root: Received settings
10-28 08:06 DEBUG  CommonBackend: Searching for local CD
10-28 08:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp is a valid Ubuntu CD
10-28 08:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\casper\filesystem.squashfs
10-28 08:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:06 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:06 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:06 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\translations, languages=['en_US', 'en']
10-28 08:06 DEBUG  TaskList: # Running tasklist...
10-28 08:06 DEBUG  TaskList: ## Running select_target_dir...
10-28 08:06 INFO   WindowsBackend: Installing into E:\ubuntu
10-28 08:06 DEBUG  TaskList: ## Finished select_target_dir
10-28 08:06 DEBUG  TaskList: ## Running create_dir_structure...
10-28 08:06 DEBUG  CommonBackend: Creating dir E:\ubuntu
10-28 08:06 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
10-28 08:06 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
10-28 08:06 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
10-28 08:06 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
10-28 08:06 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
10-28 08:06 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
10-28 08:06 DEBUG  TaskList: ## Finished create_dir_structure
10-28 08:06 DEBUG  TaskList: ## Running uncompress_target_dir...
10-28 08:06 DEBUG  TaskList: ## Finished uncompress_target_dir
10-28 08:06 DEBUG  TaskList: ## Running create_uninstaller...
10-28 08:06 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
10-28 08:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
10-28 08:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
10-28 08:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-28 08:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
10-28 08:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
10-28 08:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-28 08:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-28 08:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-28 08:06 DEBUG  TaskList: ## Finished create_uninstaller
10-28 08:06 DEBUG  TaskList: ## Running copy_installation_files...
10-28 08:06 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
10-28 08:06 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\winboot -> E:\ubuntu\winboot
10-28 08:06 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl5BA7.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
10-28 08:06 DEBUG  TaskList: ## Finished copy_installation_files
10-28 08:06 DEBUG  TaskList: ## Running get_iso...
10-28 08:06 DEBUG  CommonBackend: Trying to use pre-specified ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:06 DEBUG  TaskList: New task is_valid_iso
10-28 08:06 DEBUG  TaskList: ### Running is_valid_iso...
10-28 08:06 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:06 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:06 DEBUG  TaskList: ### Finished is_valid_iso
10-28 08:06 DEBUG  TaskList: New task check_iso
10-28 08:06 DEBUG  TaskList: ### Running check_iso...
10-28 08:06 DEBUG  CommonBackend: Checking D:\ubuntu-12.10-desktop-i386.iso
10-28 08:06 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:06 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:06 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
10-28 08:06 DEBUG  TaskList: New task get_metalink
10-28 08:06 DEBUG  TaskList: #### Running get_metalink...
10-28 08:06 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) > E:\ubuntu\install
10-28 08:06 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 08:06 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) > E:\ubuntu\install
10-28 08:06 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 08:06 DEBUG  TaskList: #### Finished get_metalink
10-28 08:06 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for D:\ubuntu-12.10-desktop-i386.iso, ignoring
10-28 08:06 DEBUG  TaskList: ### Finished check_iso
10-28 08:06 DEBUG  TaskList: New task copy_file
10-28 08:06 DEBUG  CommonBackend: Copying D:\ubuntu-12.10-desktop-i386.iso > E:\ubuntu\install\installation.iso
10-28 08:06 DEBUG  TaskList: ### Running copy_file...
10-28 08:07 DEBUG  TaskList: ### Finished copy_file
10-28 08:07 DEBUG  TaskList: ## Finished get_iso
10-28 08:07 DEBUG  TaskList: ## Running extract_kernel...
10-28 08:07 DEBUG  CommonBackend: Extracting files from ISO E:\ubuntu\install\installation.iso
10-28 08:07 DEBUG  WindowsBackend:   extracting md5sum.txt from E:\ubuntu\install\installation.iso
10-28 08:07 DEBUG  WindowsBackend:   extracting casper\vmlinuz from E:\ubuntu\install\installation.iso
10-28 08:07 DEBUG  WindowsBackend:   extracting casper\initrd.lz from E:\ubuntu\install\installation.iso
10-28 08:07 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-28 08:07 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\vmlinuz
10-28 08:07 DEBUG  CommonBackend:   E:\ubuntu\install\boot\vmlinuz md5 = dedeef44f082210eb0d605d21837feb5 == dedeef44f082210eb0d605d21837feb5
10-28 08:07 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\initrd.lz
10-28 08:07 DEBUG  CommonBackend:   E:\ubuntu\install\boot\initrd.lz md5 = bf4099046c27293af1f7ec8c76baf1c7 == bf4099046c27293af1f7ec8c76baf1c7
10-28 08:07 DEBUG  TaskList: ## Finished extract_kernel
10-28 08:07 DEBUG  TaskList: ## Running choose_disk_sizes...
10-28 08:07 DEBUG  WindowsBackend: total size=16000
  root=15744
  swap=256
  home=0
  usr=0
10-28 08:07 DEBUG  TaskList: ## Finished choose_disk_sizes
10-28 08:07 DEBUG  TaskList: ## Running create_preseed...
10-28 08:07 DEBUG  TaskList: ## Finished create_preseed
10-28 08:07 DEBUG  TaskList: ## Running modify_bootloader...
10-28 08:07 DEBUG  TaskList: New task modify_bcd
10-28 08:07 DEBUG  TaskList: ### Running modify_bcd...
10-28 08:07 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 28849.7226563 mb free ntfs)
10-28 08:07 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa51-4ca4-11e1-853b-984507711b55} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa51-4ca4-11e1-853b-984507711b55} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 08:07 DEBUG  TaskList: # Cancelling tasklist
10-28 08:07 DEBUG  TaskList: New task modify_bcd
10-28 08:07 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa51-4ca4-11e1-853b-984507711b55} device partition=E:
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
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa51-4ca4-11e1-853b-984507711b55} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 08:07 DEBUG  TaskList: New task modify_bcd
10-28 08:07 DEBUG  TaskList: New task modify_bcd
10-28 08:07 DEBUG  TaskList: New task modify_bcd
10-28 08:07 DEBUG  TaskList: ## Finished modify_bootloader
10-28 08:07 DEBUG  TaskList: # Finished tasklist
10-28 08:07 INFO   root: === wubi 12.10 rev273 ===
10-28 08:07 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 08:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubuntu\\uninstall-wubi.exe"']
10-28 08:07 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\data
10-28 08:07 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\bin\7z.exe
10-28 08:07 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 08:07 DEBUG  CommonBackend: Fetching basic info...
10-28 08:07 DEBUG  CommonBackend: original_exe=E:\ubuntu\uninstall-wubi.exe
10-28 08:07 DEBUG  CommonBackend: platform=win32
10-28 08:07 DEBUG  CommonBackend: osname=nt
10-28 08:07 DEBUG  CommonBackend: language=en_US
10-28 08:07 DEBUG  CommonBackend: encoding=cp1252
10-28 08:07 DEBUG  WindowsBackend: arch=amd64
10-28 08:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\data\isolist.ini
10-28 08:07 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 08:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 08:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 08:07 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 08:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 08:07 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 08:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 08:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 08:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 08:07 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 08:07 DEBUG  WindowsBackend: Fetching host info...
10-28 08:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 08:07 DEBUG  WindowsBackend: windows version=vista
10-28 08:07 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 08:07 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 08:07 DEBUG  WindowsBackend: windows_build=7601
10-28 08:07 DEBUG  WindowsBackend: gmt=5
10-28 08:07 DEBUG  WindowsBackend: country=US
10-28 08:07 DEBUG  WindowsBackend: timezone=America/New_York
10-28 08:07 DEBUG  WindowsBackend: windows_username=sandesh
10-28 08:07 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 08:07 DEBUG  WindowsBackend: user_directory=C:\Users\sandesh
10-28 08:07 DEBUG  WindowsBackend: windows_language_code=1033
10-28 08:07 DEBUG  WindowsBackend: windows_language=English
10-28 08:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 08:07 DEBUG  WindowsBackend: bootloader=vista
10-28 08:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28849.609375 mb free ntfs)
10-28 08:07 DEBUG  WindowsBackend: drive=Drive(C: hd 28849.609375 mb free ntfs)
10-28 08:07 DEBUG  WindowsBackend: drive=Drive(D: hd 90210.8671875 mb free ntfs)
10-28 08:07 DEBUG  WindowsBackend: drive=Drive(E: hd 60513.4960938 mb free ntfs)
10-28 08:07 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 08:07 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:07 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 08:07 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
10-28 08:07 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
10-28 08:07 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-28 08:07 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 08:07 DEBUG  WindowsBackend: keyboard_layout=us
10-28 08:07 DEBUG  WindowsBackend: keyboard_variant=
10-28 08:07 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 08:07 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 08:07 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 08:07 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 08:07 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:07 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
10-28 08:07 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
10-28 08:07 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
10-28 08:07 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:07 DEBUG  CommonBackend: Searching for local CDs
10-28 08:07 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp is a valid Ubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp is a valid Ubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp is a valid Kubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp is a valid Kubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp is a valid Mythbuntu CD
10-28 08:07 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp is a valid Mythbuntu CD
10-28 08:07 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp is a valid Edubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp is a valid Edubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp is a valid Lubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp is a valid Lubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:07 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:07 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:07 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:07 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:07 INFO   root: Running the uninstaller...
10-28 08:07 INFO   CommonBackend: This is the uninstaller running
10-28 08:07 DEBUG  WindowsFrontend: __init__...
10-28 08:07 DEBUG  WindowsFrontend: on_init...
10-28 08:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\translations, languages=['en_US', 'en']
10-28 08:08 INFO   root: Received settings
10-28 08:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\translations, languages=['en_US', 'en']
10-28 08:08 DEBUG  TaskList: # Running tasklist...
10-28 08:08 DEBUG  TaskList: ## Running Remove bootloader entry...
10-28 08:08 DEBUG  WindowsBackend: Could not find bcd id
10-28 08:08 DEBUG  WindowsBackend: undo_bootini C:
10-28 08:08 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 28849.609375 mb free ntfs)
10-28 08:08 DEBUG  WindowsBackend: undo_bootini D:
10-28 08:08 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 90210.8671875 mb free ntfs)
10-28 08:08 DEBUG  WindowsBackend: undo_bootini E:
10-28 08:08 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 60513.4960938 mb free ntfs)
10-28 08:08 DEBUG  WindowsBackend: undo_bootini H:
10-28 08:08 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:08 DEBUG  WindowsBackend: undo_bootini M:
10-28 08:08 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
10-28 08:08 DEBUG  TaskList: ## Finished Remove bootloader entry
10-28 08:08 DEBUG  TaskList: ## Running Remove target dir...
10-28 08:08 DEBUG  CommonBackend: Deleting E:\ubuntu
10-28 08:08 DEBUG  TaskList: ## Finished Remove target dir
10-28 08:08 DEBUG  TaskList: ## Running Remove registry key...
10-28 08:08 DEBUG  TaskList: ## Finished Remove registry key
10-28 08:08 DEBUG  TaskList: # Finished tasklist
10-28 08:08 INFO   root: Almost finished uninstalling
10-28 08:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl1F72.tmp\translations, languages=['en_US', 'en']
10-28 08:08 INFO   root: Finished uninstallation
10-28 08:08 DEBUG  root: application.quit
10-28 08:08 DEBUG  WindowsFrontend: frontend.quit
10-28 08:08 DEBUG  WindowsFrontend: frontend.on_quit
10-28 08:08 DEBUG  root: application.on_quit
10-28 08:08 INFO   root: sys.exit
10-28 08:08 INFO   root: === wubi 12.10 rev273 ===
10-28 08:08 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 08:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
10-28 08:08 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\data
10-28 08:08 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\bin\7z.exe
10-28 08:08 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 08:08 DEBUG  CommonBackend: Fetching basic info...
10-28 08:08 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-28 08:08 DEBUG  CommonBackend: platform=win32
10-28 08:08 DEBUG  CommonBackend: osname=nt
10-28 08:08 DEBUG  CommonBackend: language=en_US
10-28 08:08 DEBUG  CommonBackend: encoding=cp1252
10-28 08:08 DEBUG  WindowsBackend: arch=amd64
10-28 08:08 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\data\isolist.ini
10-28 08:08 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 08:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 08:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 08:08 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 08:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 08:08 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 08:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 08:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 08:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 08:08 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 08:08 DEBUG  WindowsBackend: Fetching host info...
10-28 08:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 08:08 DEBUG  WindowsBackend: windows version=vista
10-28 08:08 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 08:08 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 08:08 DEBUG  WindowsBackend: windows_build=7601
10-28 08:08 DEBUG  WindowsBackend: gmt=5
10-28 08:08 DEBUG  WindowsBackend: country=US
10-28 08:08 DEBUG  WindowsBackend: timezone=America/New_York
10-28 08:08 DEBUG  WindowsBackend: windows_username=sandesh
10-28 08:08 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 08:08 DEBUG  WindowsBackend: user_directory=C:\Users\sandesh
10-28 08:08 DEBUG  WindowsBackend: windows_language_code=1033
10-28 08:08 DEBUG  WindowsBackend: windows_language=English
10-28 08:08 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 08:08 DEBUG  WindowsBackend: bootloader=vista
10-28 08:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28849.1289063 mb free ntfs)
10-28 08:08 DEBUG  WindowsBackend: drive=Drive(C: hd 28849.1289063 mb free ntfs)
10-28 08:08 DEBUG  WindowsBackend: drive=Drive(D: hd 89896.9296875 mb free ntfs)
10-28 08:08 DEBUG  WindowsBackend: drive=Drive(E: hd 61290.4375 mb free ntfs)
10-28 08:08 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 08:08 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:08 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 08:08 DEBUG  WindowsBackend: uninstaller_path=None
10-28 08:08 DEBUG  WindowsBackend: previous_target_dir=None
10-28 08:08 DEBUG  WindowsBackend: previous_distro_name=None
10-28 08:08 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 08:08 DEBUG  WindowsBackend: keyboard_layout=us
10-28 08:08 DEBUG  WindowsBackend: keyboard_variant=
10-28 08:08 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 08:08 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 08:08 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 08:08 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 08:08 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:08 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
10-28 08:08 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
10-28 08:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
10-28 08:08 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:08 DEBUG  CommonBackend: Searching for local CDs
10-28 08:08 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp is a valid Ubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp is a valid Ubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp is a valid Kubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp is a valid Kubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp is a valid Mythbuntu CD
10-28 08:08 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp is a valid Mythbuntu CD
10-28 08:08 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp is a valid Edubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp is a valid Edubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp is a valid Lubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp is a valid Lubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:08 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:08 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:08 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:08 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:08 INFO   root: Running the installer...
10-28 08:08 DEBUG  WindowsFrontend: __init__...
10-28 08:08 DEBUG  WindowsFrontend: on_init...
10-28 08:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\translations, languages=['en_US', 'en']
10-28 08:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\translations, languages=['en_US', 'en']
10-28 08:09 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=16000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sandesh
10-28 08:09 INFO   root: Received settings
10-28 08:09 DEBUG  CommonBackend: Searching for local CD
10-28 08:09 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp is a valid Ubuntu CD
10-28 08:09 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\casper\filesystem.squashfs
10-28 08:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:09 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:09 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:09 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\translations, languages=['en_US', 'en']
10-28 08:09 DEBUG  TaskList: # Running tasklist...
10-28 08:09 DEBUG  TaskList: ## Running select_target_dir...
10-28 08:09 INFO   WindowsBackend: Installing into D:\ubuntu
10-28 08:09 DEBUG  TaskList: ## Finished select_target_dir
10-28 08:09 DEBUG  TaskList: ## Running create_dir_structure...
10-28 08:09 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-28 08:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-28 08:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-28 08:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-28 08:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-28 08:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-28 08:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-28 08:09 DEBUG  TaskList: ## Finished create_dir_structure
10-28 08:09 DEBUG  TaskList: ## Running uncompress_target_dir...
10-28 08:09 DEBUG  TaskList: ## Finished uncompress_target_dir
10-28 08:09 DEBUG  TaskList: ## Running create_uninstaller...
10-28 08:09 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-28 08:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-28 08:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-28 08:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-28 08:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-28 08:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
10-28 08:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-28 08:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-28 08:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-28 08:09 DEBUG  TaskList: ## Finished create_uninstaller
10-28 08:09 DEBUG  TaskList: ## Running copy_installation_files...
10-28 08:09 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-28 08:09 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\winboot -> D:\ubuntu\winboot
10-28 08:09 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl193B.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
10-28 08:09 DEBUG  TaskList: ## Finished copy_installation_files
10-28 08:09 DEBUG  TaskList: ## Running get_iso...
10-28 08:09 DEBUG  CommonBackend: Trying to use pre-specified ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:09 DEBUG  TaskList: New task is_valid_iso
10-28 08:09 DEBUG  TaskList: ### Running is_valid_iso...
10-28 08:09 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:09 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:09 DEBUG  TaskList: ### Finished is_valid_iso
10-28 08:09 DEBUG  TaskList: New task check_iso
10-28 08:09 DEBUG  TaskList: ### Running check_iso...
10-28 08:09 DEBUG  CommonBackend: Checking D:\ubuntu-12.10-desktop-i386.iso
10-28 08:09 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:09 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:09 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
10-28 08:09 DEBUG  TaskList: New task get_metalink
10-28 08:09 DEBUG  TaskList: #### Running get_metalink...
10-28 08:09 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) > D:\ubuntu\install
10-28 08:09 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 08:09 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) > D:\ubuntu\install
10-28 08:09 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 08:09 DEBUG  TaskList: #### Finished get_metalink
10-28 08:09 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for D:\ubuntu-12.10-desktop-i386.iso, ignoring
10-28 08:09 DEBUG  TaskList: ### Finished check_iso
10-28 08:09 DEBUG  TaskList: New task copy_file
10-28 08:09 DEBUG  CommonBackend: Copying D:\ubuntu-12.10-desktop-i386.iso > D:\ubuntu\install\installation.iso
10-28 08:09 DEBUG  TaskList: ### Running copy_file...
10-28 08:09 DEBUG  TaskList: ### Finished copy_file
10-28 08:09 DEBUG  TaskList: ## Finished get_iso
10-28 08:09 DEBUG  TaskList: ## Running extract_kernel...
10-28 08:09 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\installation.iso
10-28 08:09 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\installation.iso
10-28 08:09 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\installation.iso
10-28 08:09 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\installation.iso
10-28 08:09 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-28 08:09 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
10-28 08:09 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = dedeef44f082210eb0d605d21837feb5 == dedeef44f082210eb0d605d21837feb5
10-28 08:09 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
10-28 08:09 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = bf4099046c27293af1f7ec8c76baf1c7 == bf4099046c27293af1f7ec8c76baf1c7
10-28 08:09 DEBUG  TaskList: ## Finished extract_kernel
10-28 08:09 DEBUG  TaskList: ## Running choose_disk_sizes...
10-28 08:09 DEBUG  WindowsBackend: total size=16000
  root=15744
  swap=256
  home=0
  usr=0
10-28 08:09 DEBUG  TaskList: ## Finished choose_disk_sizes
10-28 08:09 DEBUG  TaskList: ## Running create_preseed...
10-28 08:09 DEBUG  TaskList: ## Finished create_preseed
10-28 08:09 DEBUG  TaskList: ## Running modify_bootloader...
10-28 08:09 DEBUG  TaskList: New task modify_bcd
10-28 08:09 DEBUG  TaskList: ### Running modify_bcd...
10-28 08:09 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 28849.1289063 mb free ntfs)
10-28 08:09 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa52-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa52-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 08:09 DEBUG  TaskList: # Cancelling tasklist
10-28 08:09 DEBUG  TaskList: New task modify_bcd
10-28 08:09 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa52-4ca4-11e1-853b-984507711b55} device partition=D:
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
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa52-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 08:09 DEBUG  TaskList: New task modify_bcd
10-28 08:09 DEBUG  TaskList: New task modify_bcd
10-28 08:09 DEBUG  TaskList: New task modify_bcd
10-28 08:09 DEBUG  TaskList: ## Finished modify_bootloader
10-28 08:09 DEBUG  TaskList: # Finished tasklist
10-28 08:10 INFO   root: === wubi 12.10 rev273 ===
10-28 08:10 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 08:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu-12.10-desktop-i386\\wubi.exe"']
10-28 08:10 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp\data
10-28 08:10 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp\bin\7z.exe
10-28 08:10 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 08:10 DEBUG  CommonBackend: Fetching basic info...
10-28 08:10 DEBUG  CommonBackend: original_exe=D:\ubuntu-12.10-desktop-i386\wubi.exe
10-28 08:10 DEBUG  CommonBackend: platform=win32
10-28 08:10 DEBUG  CommonBackend: osname=nt
10-28 08:10 DEBUG  CommonBackend: language=en_US
10-28 08:10 DEBUG  CommonBackend: encoding=cp1252
10-28 08:10 DEBUG  WindowsBackend: arch=amd64
10-28 08:10 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp\data\isolist.ini
10-28 08:10 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 08:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 08:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 08:10 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 08:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 08:10 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 08:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 08:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 08:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 08:10 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 08:10 DEBUG  WindowsBackend: Fetching host info...
10-28 08:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 08:10 DEBUG  WindowsBackend: windows version=vista
10-28 08:10 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 08:10 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 08:10 DEBUG  WindowsBackend: windows_build=7601
10-28 08:10 DEBUG  WindowsBackend: gmt=5
10-28 08:10 DEBUG  WindowsBackend: country=US
10-28 08:10 DEBUG  WindowsBackend: timezone=America/New_York
10-28 08:10 DEBUG  WindowsBackend: windows_username=sandesh
10-28 08:10 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 08:10 DEBUG  WindowsBackend: user_directory=C:\Users\sandesh
10-28 08:10 DEBUG  WindowsBackend: windows_language_code=1033
10-28 08:10 DEBUG  WindowsBackend: windows_language=English
10-28 08:10 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 08:10 DEBUG  WindowsBackend: bootloader=vista
10-28 08:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28852.359375 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(C: hd 28852.359375 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(D: hd 89119.9882813 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(E: hd 61290.4375 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 08:10 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-28 08:10 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-28 08:10 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-28 08:10 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 08:10 DEBUG  WindowsBackend: keyboard_layout=us
10-28 08:10 DEBUG  WindowsBackend: keyboard_variant=
10-28 08:10 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 08:10 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 08:10 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 08:10 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 08:10 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:10 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
10-28 08:10 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
10-28 08:10 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
10-28 08:10 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:10 DEBUG  CommonBackend: Searching for local CDs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 INFO   root: Already installed, running the uninstaller...
10-28 08:10 INFO   root: Running the uninstaller...
10-28 08:10 INFO   CommonBackend: Launching previous uninestaller D:\ubuntu\uninstall-wubi.exe
10-28 08:10 INFO   root: === wubi 12.10 rev273 ===
10-28 08:10 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 08:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
10-28 08:10 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\data
10-28 08:10 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\bin\7z.exe
10-28 08:10 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 08:10 DEBUG  CommonBackend: Fetching basic info...
10-28 08:10 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
10-28 08:10 DEBUG  CommonBackend: platform=win32
10-28 08:10 DEBUG  CommonBackend: osname=nt
10-28 08:10 DEBUG  CommonBackend: language=en_US
10-28 08:10 DEBUG  CommonBackend: encoding=cp1252
10-28 08:10 DEBUG  WindowsBackend: arch=amd64
10-28 08:10 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\data\isolist.ini
10-28 08:10 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 08:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 08:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 08:10 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 08:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 08:10 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 08:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 08:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 08:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 08:10 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 08:10 DEBUG  WindowsBackend: Fetching host info...
10-28 08:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 08:10 DEBUG  WindowsBackend: windows version=vista
10-28 08:10 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 08:10 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 08:10 DEBUG  WindowsBackend: windows_build=7601
10-28 08:10 DEBUG  WindowsBackend: gmt=5
10-28 08:10 DEBUG  WindowsBackend: country=US
10-28 08:10 DEBUG  WindowsBackend: timezone=America/New_York
10-28 08:10 DEBUG  WindowsBackend: windows_username=sandesh
10-28 08:10 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 08:10 DEBUG  WindowsBackend: user_directory=C:\Users\sandesh
10-28 08:10 DEBUG  WindowsBackend: windows_language_code=1033
10-28 08:10 DEBUG  WindowsBackend: windows_language=English
10-28 08:10 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 08:10 DEBUG  WindowsBackend: bootloader=vista
10-28 08:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28842.828125 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(C: hd 28842.828125 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(D: hd 89119.9882813 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(E: hd 61290.4375 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 08:10 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-28 08:10 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-28 08:10 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-28 08:10 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 08:10 DEBUG  WindowsBackend: keyboard_layout=us
10-28 08:10 DEBUG  WindowsBackend: keyboard_variant=
10-28 08:10 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 08:10 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 08:10 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 08:10 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 08:10 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:10 DEBUG  root: application.quit
10-28 08:10 DEBUG  root: application.on_quit
10-28 08:10 INFO   root: sys.exit
10-28 08:10 INFO   root: Quitting application
10-28 08:10 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
10-28 08:10 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
10-28 08:10 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
10-28 08:10 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:10 DEBUG  CommonBackend: Searching for local CDs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 INFO   root: Running the uninstaller...
10-28 08:10 INFO   CommonBackend: This is the uninstaller running
10-28 08:10 DEBUG  WindowsFrontend: __init__...
10-28 08:10 DEBUG  WindowsFrontend: on_init...
10-28 08:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\translations, languages=['en_US', 'en']
10-28 08:10 INFO   root: Received settings
10-28 08:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\translations, languages=['en_US', 'en']
10-28 08:10 DEBUG  TaskList: # Running tasklist...
10-28 08:10 DEBUG  TaskList: ## Running Remove bootloader entry...
10-28 08:10 DEBUG  WindowsBackend: Could not find bcd id
10-28 08:10 DEBUG  WindowsBackend: undo_bootini C:
10-28 08:10 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 28842.828125 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: undo_bootini D:
10-28 08:10 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 89119.9882813 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: undo_bootini E:
10-28 08:10 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 61290.4375 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: undo_bootini H:
10-28 08:10 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: undo_bootini M:
10-28 08:10 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
10-28 08:10 DEBUG  TaskList: ## Finished Remove bootloader entry
10-28 08:10 DEBUG  TaskList: ## Running Remove target dir...
10-28 08:10 DEBUG  CommonBackend: Deleting D:\ubuntu
10-28 08:10 DEBUG  TaskList: ## Finished Remove target dir
10-28 08:10 DEBUG  TaskList: ## Running Remove registry key...
10-28 08:10 DEBUG  TaskList: ## Finished Remove registry key
10-28 08:10 DEBUG  TaskList: # Finished tasklist
10-28 08:10 INFO   root: Almost finished uninstalling
10-28 08:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl95F8.tmp\translations, languages=['en_US', 'en']
10-28 08:10 INFO   root: Finished uninstallation
10-28 08:10 DEBUG  root: application.quit
10-28 08:10 DEBUG  WindowsFrontend: frontend.quit
10-28 08:10 DEBUG  WindowsFrontend: frontend.on_quit
10-28 08:10 DEBUG  root: application.on_quit
10-28 08:10 INFO   root: sys.exit
10-28 08:10 INFO   root: === wubi 12.10 rev273 ===
10-28 08:10 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 08:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu-12.10-desktop-i386\\wubi.exe"']
10-28 08:10 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\data
10-28 08:10 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\bin\7z.exe
10-28 08:10 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 08:10 DEBUG  CommonBackend: Fetching basic info...
10-28 08:10 DEBUG  CommonBackend: original_exe=D:\ubuntu-12.10-desktop-i386\wubi.exe
10-28 08:10 DEBUG  CommonBackend: platform=win32
10-28 08:10 DEBUG  CommonBackend: osname=nt
10-28 08:10 DEBUG  CommonBackend: language=en_US
10-28 08:10 DEBUG  CommonBackend: encoding=cp1252
10-28 08:10 DEBUG  WindowsBackend: arch=amd64
10-28 08:10 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\data\isolist.ini
10-28 08:10 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 08:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 08:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 08:10 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 08:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 08:10 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 08:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 08:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 08:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 08:10 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 08:10 DEBUG  WindowsBackend: Fetching host info...
10-28 08:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 08:10 DEBUG  WindowsBackend: windows version=vista
10-28 08:10 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 08:10 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 08:10 DEBUG  WindowsBackend: windows_build=7601
10-28 08:10 DEBUG  WindowsBackend: gmt=5
10-28 08:10 DEBUG  WindowsBackend: country=US
10-28 08:10 DEBUG  WindowsBackend: timezone=America/New_York
10-28 08:10 DEBUG  WindowsBackend: windows_username=sandesh
10-28 08:10 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 08:10 DEBUG  WindowsBackend: user_directory=C:\Users\sandesh
10-28 08:10 DEBUG  WindowsBackend: windows_language_code=1033
10-28 08:10 DEBUG  WindowsBackend: windows_language=English
10-28 08:10 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 08:10 DEBUG  WindowsBackend: bootloader=vista
10-28 08:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28852.3789063 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(C: hd 28852.3789063 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(D: hd 89896.9296875 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(E: hd 61290.4375 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:10 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 08:10 DEBUG  WindowsBackend: uninstaller_path=None
10-28 08:10 DEBUG  WindowsBackend: previous_target_dir=None
10-28 08:10 DEBUG  WindowsBackend: previous_distro_name=None
10-28 08:10 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 08:10 DEBUG  WindowsBackend: keyboard_layout=us
10-28 08:10 DEBUG  WindowsBackend: keyboard_variant=
10-28 08:10 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 08:10 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 08:10 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 08:10 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 08:10 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:10 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
10-28 08:10 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
10-28 08:10 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
10-28 08:10 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:10 DEBUG  CommonBackend: Searching for local CDs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 INFO   root: Running the installer...
10-28 08:10 DEBUG  WindowsFrontend: __init__...
10-28 08:10 DEBUG  WindowsFrontend: on_init...
10-28 08:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\translations, languages=['en_US', 'en']
10-28 08:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\translations, languages=['en_US', 'en']
10-28 08:10 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=16000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sandesh
10-28 08:10 INFO   root: Received settings
10-28 08:10 DEBUG  CommonBackend: Searching for local CD
10-28 08:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:10 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\translations, languages=['en_US', 'en']
10-28 08:10 DEBUG  TaskList: # Running tasklist...
10-28 08:10 DEBUG  TaskList: ## Running select_target_dir...
10-28 08:10 INFO   WindowsBackend: Installing into D:\ubuntu
10-28 08:10 DEBUG  TaskList: ## Finished select_target_dir
10-28 08:10 DEBUG  TaskList: ## Running create_dir_structure...
10-28 08:10 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-28 08:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-28 08:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-28 08:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-28 08:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-28 08:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-28 08:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-28 08:10 DEBUG  TaskList: ## Finished create_dir_structure
10-28 08:10 DEBUG  TaskList: ## Running uncompress_target_dir...
10-28 08:10 DEBUG  TaskList: ## Finished uncompress_target_dir
10-28 08:10 DEBUG  TaskList: ## Running create_uninstaller...
10-28 08:10 DEBUG  WindowsBackend: Copying uninstaller D:\ubuntu-12.10-desktop-i386\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-28 08:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-28 08:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-28 08:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-28 08:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-28 08:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
10-28 08:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-28 08:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-28 08:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-28 08:10 DEBUG  TaskList: ## Finished create_uninstaller
10-28 08:10 DEBUG  TaskList: ## Running copy_installation_files...
10-28 08:10 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-28 08:10 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\winboot -> D:\ubuntu\winboot
10-28 08:10 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pylD70D.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
10-28 08:10 DEBUG  TaskList: ## Finished copy_installation_files
10-28 08:10 DEBUG  TaskList: ## Running get_iso...
10-28 08:10 DEBUG  CommonBackend: Trying to use pre-specified ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:10 DEBUG  TaskList: New task is_valid_iso
10-28 08:10 DEBUG  TaskList: ### Running is_valid_iso...
10-28 08:10 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:10 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:10 DEBUG  TaskList: ### Finished is_valid_iso
10-28 08:10 DEBUG  TaskList: New task check_iso
10-28 08:10 DEBUG  TaskList: ### Running check_iso...
10-28 08:10 DEBUG  CommonBackend: Checking D:\ubuntu-12.10-desktop-i386.iso
10-28 08:10 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:10 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:10 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
10-28 08:10 DEBUG  TaskList: New task get_metalink
10-28 08:10 DEBUG  TaskList: #### Running get_metalink...
10-28 08:10 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) > D:\ubuntu\install
10-28 08:10 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 08:10 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) > D:\ubuntu\install
10-28 08:10 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 08:10 DEBUG  TaskList: #### Finished get_metalink
10-28 08:10 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for D:\ubuntu-12.10-desktop-i386.iso, ignoring
10-28 08:10 DEBUG  TaskList: ### Finished check_iso
10-28 08:10 DEBUG  TaskList: New task copy_file
10-28 08:10 DEBUG  CommonBackend: Copying D:\ubuntu-12.10-desktop-i386.iso > D:\ubuntu\install\installation.iso
10-28 08:10 DEBUG  TaskList: ### Running copy_file...
10-28 08:11 DEBUG  TaskList: ### Finished copy_file
10-28 08:11 DEBUG  TaskList: ## Finished get_iso
10-28 08:11 DEBUG  TaskList: ## Running extract_kernel...
10-28 08:11 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\installation.iso
10-28 08:11 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\installation.iso
10-28 08:11 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\installation.iso
10-28 08:11 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\installation.iso
10-28 08:11 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-28 08:11 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
10-28 08:11 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = dedeef44f082210eb0d605d21837feb5 == dedeef44f082210eb0d605d21837feb5
10-28 08:11 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
10-28 08:11 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = bf4099046c27293af1f7ec8c76baf1c7 == bf4099046c27293af1f7ec8c76baf1c7
10-28 08:11 DEBUG  TaskList: ## Finished extract_kernel
10-28 08:11 DEBUG  TaskList: ## Running choose_disk_sizes...
10-28 08:11 DEBUG  WindowsBackend: total size=16000
  root=15744
  swap=256
  home=0
  usr=0
10-28 08:11 DEBUG  TaskList: ## Finished choose_disk_sizes
10-28 08:11 DEBUG  TaskList: ## Running create_preseed...
10-28 08:11 DEBUG  TaskList: ## Finished create_preseed
10-28 08:11 DEBUG  TaskList: ## Running modify_bootloader...
10-28 08:11 DEBUG  TaskList: New task modify_bcd
10-28 08:11 DEBUG  TaskList: ### Running modify_bcd...
10-28 08:11 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 28852.3789063 mb free ntfs)
10-28 08:11 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa53-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa53-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 08:11 DEBUG  TaskList: # Cancelling tasklist
10-28 08:11 DEBUG  TaskList: New task modify_bcd
10-28 08:11 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa53-4ca4-11e1-853b-984507711b55} device partition=D:
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
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa53-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 08:11 DEBUG  TaskList: New task modify_bcd
10-28 08:11 DEBUG  TaskList: New task modify_bcd
10-28 08:11 DEBUG  TaskList: New task modify_bcd
10-28 08:11 DEBUG  TaskList: ## Finished modify_bootloader
10-28 08:11 DEBUG  TaskList: # Finished tasklist
10-28 08:12 INFO   root: === wubi 12.10 rev273 ===
10-28 08:12 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 08:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
10-28 08:12 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\data
10-28 08:12 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\bin\7z.exe
10-28 08:12 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 08:12 DEBUG  CommonBackend: Fetching basic info...
10-28 08:12 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
10-28 08:12 DEBUG  CommonBackend: platform=win32
10-28 08:12 DEBUG  CommonBackend: osname=nt
10-28 08:12 DEBUG  CommonBackend: language=en_US
10-28 08:12 DEBUG  CommonBackend: encoding=cp1252
10-28 08:12 DEBUG  WindowsBackend: arch=amd64
10-28 08:12 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\data\isolist.ini
10-28 08:12 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 08:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 08:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 08:12 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 08:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 08:12 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 08:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 08:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 08:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 08:12 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 08:12 DEBUG  WindowsBackend: Fetching host info...
10-28 08:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 08:12 DEBUG  WindowsBackend: windows version=vista
10-28 08:12 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 08:12 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 08:12 DEBUG  WindowsBackend: windows_build=7601
10-28 08:12 DEBUG  WindowsBackend: gmt=5
10-28 08:12 DEBUG  WindowsBackend: country=US
10-28 08:12 DEBUG  WindowsBackend: timezone=America/New_York
10-28 08:12 DEBUG  WindowsBackend: windows_username=sandesh
10-28 08:12 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 08:12 DEBUG  WindowsBackend: user_directory=C:\Users\sandesh
10-28 08:12 DEBUG  WindowsBackend: windows_language_code=1033
10-28 08:12 DEBUG  WindowsBackend: windows_language=English
10-28 08:12 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 08:12 DEBUG  WindowsBackend: bootloader=vista
10-28 08:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28851.625 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: drive=Drive(C: hd 28851.625 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: drive=Drive(D: hd 89119.9882813 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: drive=Drive(E: hd 61290.4375 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 08:12 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 08:12 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-28 08:12 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-28 08:12 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-28 08:12 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 08:12 DEBUG  WindowsBackend: keyboard_layout=us
10-28 08:12 DEBUG  WindowsBackend: keyboard_variant=
10-28 08:12 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 08:12 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 08:12 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 08:12 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 08:12 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:12 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
10-28 08:12 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
10-28 08:12 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
10-28 08:12 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:12 DEBUG  CommonBackend: Searching for local CDs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 INFO   root: Running the uninstaller...
10-28 08:12 INFO   CommonBackend: This is the uninstaller running
10-28 08:12 DEBUG  WindowsFrontend: __init__...
10-28 08:12 DEBUG  WindowsFrontend: on_init...
10-28 08:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\translations, languages=['en_US', 'en']
10-28 08:12 INFO   root: === wubi 12.10 rev273 ===
10-28 08:12 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 08:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
10-28 08:12 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\data
10-28 08:12 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\bin\7z.exe
10-28 08:12 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 08:12 DEBUG  CommonBackend: Fetching basic info...
10-28 08:12 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
10-28 08:12 DEBUG  CommonBackend: platform=win32
10-28 08:12 DEBUG  CommonBackend: osname=nt
10-28 08:12 DEBUG  CommonBackend: language=en_US
10-28 08:12 DEBUG  CommonBackend: encoding=cp1252
10-28 08:12 DEBUG  WindowsBackend: arch=amd64
10-28 08:12 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\data\isolist.ini
10-28 08:12 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 08:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 08:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 08:12 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 08:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 08:12 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 08:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 08:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 08:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 08:12 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 08:12 DEBUG  WindowsBackend: Fetching host info...
10-28 08:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 08:12 DEBUG  WindowsBackend: windows version=vista
10-28 08:12 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 08:12 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 08:12 DEBUG  WindowsBackend: windows_build=7601
10-28 08:12 DEBUG  WindowsBackend: gmt=5
10-28 08:12 DEBUG  WindowsBackend: country=US
10-28 08:12 DEBUG  WindowsBackend: timezone=America/New_York
10-28 08:12 DEBUG  WindowsBackend: windows_username=sandesh
10-28 08:12 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 08:12 DEBUG  WindowsBackend: user_directory=C:\Users\sandesh
10-28 08:12 DEBUG  WindowsBackend: windows_language_code=1033
10-28 08:12 DEBUG  WindowsBackend: windows_language=English
10-28 08:12 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 08:12 DEBUG  WindowsBackend: bootloader=vista
10-28 08:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28841.5976563 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: drive=Drive(C: hd 28841.5976563 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: drive=Drive(D: hd 89119.9882813 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: drive=Drive(E: hd 61290.4375 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 08:12 DEBUG  WindowsBackend: drive=Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 08:12 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-28 08:12 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-28 08:12 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-28 08:12 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 08:12 DEBUG  WindowsBackend: keyboard_layout=us
10-28 08:12 DEBUG  WindowsBackend: keyboard_variant=
10-28 08:12 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 08:12 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 08:12 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 08:12 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 08:12 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
10-28 08:12 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
10-28 08:12 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
10-28 08:12 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
10-28 08:12 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
10-28 08:12 DEBUG  CommonBackend: Searching for local CDs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 08:12 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 08:12 INFO   root: Running the uninstaller...
10-28 08:12 INFO   CommonBackend: This is the uninstaller running
10-28 08:12 DEBUG  WindowsFrontend: __init__...
10-28 08:12 DEBUG  WindowsFrontend: on_init...
10-28 08:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\translations, languages=['en_US', 'en']
10-28 08:12 INFO   root: Received settings
10-28 08:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\translations, languages=['en_US', 'en']
10-28 08:12 DEBUG  TaskList: # Running tasklist...
10-28 08:12 DEBUG  TaskList: ## Running Remove bootloader entry...
10-28 08:12 DEBUG  WindowsBackend: Could not find bcd id
10-28 08:12 DEBUG  WindowsBackend: undo_bootini C:
10-28 08:12 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 28851.625 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: undo_bootini D:
10-28 08:12 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 89119.9882813 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: undo_bootini E:
10-28 08:12 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 61290.4375 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: undo_bootini H:
10-28 08:12 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: undo_bootini M:
10-28 08:12 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
10-28 08:12 DEBUG  TaskList: ## Finished Remove bootloader entry
10-28 08:12 DEBUG  TaskList: ## Running Remove target dir...
10-28 08:12 DEBUG  CommonBackend: Deleting D:\ubuntu
10-28 08:12 DEBUG  TaskList: ## Finished Remove target dir
10-28 08:12 DEBUG  TaskList: ## Running Remove registry key...
10-28 08:12 DEBUG  TaskList: ## Finished Remove registry key
10-28 08:12 DEBUG  TaskList: # Finished tasklist
10-28 08:12 INFO   root: Almost finished uninstalling
10-28 08:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl2A99.tmp\translations, languages=['en_US', 'en']
10-28 08:12 INFO   root: Finished uninstallation
10-28 08:12 DEBUG  root: application.quit
10-28 08:12 DEBUG  WindowsFrontend: frontend.quit
10-28 08:12 DEBUG  WindowsFrontend: frontend.on_quit
10-28 08:12 DEBUG  root: application.on_quit
10-28 08:12 INFO   root: sys.exit
10-28 08:12 INFO   root: Received settings
10-28 08:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\translations, languages=['en_US', 'en']
10-28 08:12 DEBUG  TaskList: # Running tasklist...
10-28 08:12 DEBUG  TaskList: ## Running Remove bootloader entry...
10-28 08:12 DEBUG  WindowsBackend: Could not find bcd id
10-28 08:12 DEBUG  WindowsBackend: undo_bootini C:
10-28 08:12 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 28841.5976563 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: undo_bootini D:
10-28 08:12 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 89119.9882813 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: undo_bootini E:
10-28 08:12 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 61290.4375 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: undo_bootini H:
10-28 08:12 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 844.5234375 mb free ntfs)
10-28 08:12 DEBUG  WindowsBackend: undo_bootini M:
10-28 08:12 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
10-28 08:12 DEBUG  TaskList: ## Finished Remove bootloader entry
10-28 08:12 DEBUG  TaskList: ## Running Remove target dir...
10-28 08:12 DEBUG  CommonBackend: Cannot find D:\ubuntu
10-28 08:12 DEBUG  TaskList: ## Finished Remove target dir
10-28 08:12 DEBUG  TaskList: ## Running Remove registry key...
10-28 08:12 ERROR  registry: Cannot delete registry key Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
[Errno 2] The system cannot find the file specified
Traceback (most recent call last):
  File "\lib\wubi\backends\win32\registry.py", line 56, in delete_key
WindowsError: [Errno 2] The system cannot find the file specified
10-28 08:12 DEBUG  TaskList: ## Finished Remove registry key
10-28 08:12 DEBUG  TaskList: # Finished tasklist
10-28 08:12 INFO   root: Almost finished uninstalling
10-28 08:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl3BF7.tmp\translations, languages=['en_US', 'en']
10-28 08:12 INFO   root: Finished uninstallation
10-28 08:12 DEBUG  root: application.quit
10-28 08:12 DEBUG  WindowsFrontend: frontend.quit
10-28 08:12 DEBUG  WindowsFrontend: frontend.on_quit
10-28 08:12 DEBUG  root: application.on_quit
10-28 08:12 INFO   root: sys.exit
10-28 15:09 INFO   root: === wubi 12.10 rev273 ===
10-28 15:09 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 15:09 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
10-28 15:09 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\data
10-28 15:09 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\bin\7z.exe
10-28 15:09 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 15:09 DEBUG  CommonBackend: Fetching basic info...
10-28 15:09 DEBUG  CommonBackend: original_exe=E:\wubi.exe
10-28 15:09 DEBUG  CommonBackend: platform=win32
10-28 15:09 DEBUG  CommonBackend: osname=nt
10-28 15:09 DEBUG  CommonBackend: language=en_US
10-28 15:09 DEBUG  CommonBackend: encoding=cp1252
10-28 15:09 DEBUG  WindowsBackend: arch=amd64
10-28 15:09 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\data\isolist.ini
10-28 15:09 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 15:09 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 15:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 15:09 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 15:09 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 15:09 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 15:09 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 15:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 15:09 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 15:09 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 15:09 DEBUG  WindowsBackend: Fetching host info...
10-28 15:09 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 15:09 DEBUG  WindowsBackend: windows version=vista
10-28 15:09 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 15:09 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 15:09 DEBUG  WindowsBackend: windows_build=7601
10-28 15:09 DEBUG  WindowsBackend: gmt=5
10-28 15:09 DEBUG  WindowsBackend: country=US
10-28 15:09 DEBUG  WindowsBackend: timezone=America/New_York
10-28 15:09 DEBUG  WindowsBackend: windows_username=sandesh
10-28 15:09 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 15:09 DEBUG  WindowsBackend: user_directory=
10-28 15:09 DEBUG  WindowsBackend: windows_language_code=1033
10-28 15:09 DEBUG  WindowsBackend: windows_language=English
10-28 15:09 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 15:09 DEBUG  WindowsBackend: bootloader=vista
10-28 15:09 DEBUG  WindowsBackend: system_drive=Drive(C: hd 32703.3515625 mb free ntfs)
10-28 15:09 DEBUG  WindowsBackend: drive=Drive(C: hd 32703.3515625 mb free ntfs)
10-28 15:09 DEBUG  WindowsBackend: drive=Drive(D: hd 99705.7695313 mb free ntfs)
10-28 15:09 DEBUG  WindowsBackend: drive=Drive(E: hd 61252.2226563 mb free ntfs)
10-28 15:09 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 15:09 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 15:09 DEBUG  WindowsBackend: uninstaller_path=None
10-28 15:09 DEBUG  WindowsBackend: previous_target_dir=None
10-28 15:09 DEBUG  WindowsBackend: previous_distro_name=None
10-28 15:09 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 15:09 DEBUG  WindowsBackend: keyboard_layout=us
10-28 15:09 DEBUG  WindowsBackend: keyboard_variant=
10-28 15:09 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 15:09 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 15:09 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 15:09 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 15:09 DEBUG  CommonBackend: Searching for local CDs
10-28 15:09 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp is a valid Ubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp is a valid Ubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp is a valid Kubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp is a valid Kubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp is a valid Mythbuntu CD
10-28 15:09 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp is a valid Mythbuntu CD
10-28 15:09 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp is a valid Edubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp is a valid Edubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp is a valid Lubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp is a valid Lubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 15:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 15:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 15:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 15:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 15:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 15:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 15:09 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 15:09 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:09 INFO   root: Running the installer...
10-28 15:09 DEBUG  WindowsFrontend: __init__...
10-28 15:09 DEBUG  WindowsFrontend: on_init...
10-28 15:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\translations, languages=['en_US', 'en']
10-28 15:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\translations, languages=['en_US', 'en']
10-28 15:09 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sandesh
10-28 15:09 INFO   root: Received settings
10-28 15:09 DEBUG  CommonBackend: Searching for local CD
10-28 15:09 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp is a valid Ubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:09 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 15:09 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:09 DEBUG  CommonBackend: Searching for local ISO
10-28 15:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl608A.tmp\translations, languages=['en_US', 'en']
10-28 15:09 DEBUG  TaskList: # Running tasklist...
10-28 15:09 DEBUG  TaskList: ## Running select_target_dir...
10-28 15:09 INFO   WindowsBackend: Installing into D:\ubuntu
10-28 15:09 DEBUG  TaskList: ## Finished select_target_dir
10-28 15:09 DEBUG  TaskList: ## Running create_dir_structure...
10-28 15:09 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-28 15:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-28 15:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-28 15:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-28 15:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-28 15:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-28 15:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-28 15:09 DEBUG  TaskList: ## Finished create_dir_structure
10-28 15:09 DEBUG  TaskList: ## Running create_uninstaller...
10-28 15:09 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-28 15:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-28 15:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-28 15:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-28 15:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-28 15:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
10-28 15:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-28 15:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-28 15:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-28 15:09 DEBUG  TaskList: ## Finished create_uninstaller
10-28 15:09 DEBUG  TaskList: ## Running create_preseed_diskimage...
10-28 15:09 DEBUG  TaskList: ## Finished create_preseed_diskimage
10-28 15:09 DEBUG  TaskList: ## Running get_diskimage...
10-28 15:09 DEBUG  TaskList: New task download
10-28 15:09 DEBUG  TaskList: ### Running download...
10-28 15:09 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz) > D:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz
10-28 15:09 ERROR  TaskList: [Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 77, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 15:09 ERROR  TaskList: Non fatal error [Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')> in task download
10-28 15:09 DEBUG  TaskList: ### Finished download
10-28 15:09 DEBUG  TaskList: New task download
10-28 15:09 DEBUG  TaskList: ### Running download...
10-28 15:09 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/wubi/current/amd64.tar.xz](http://cdimage.ubuntu.com/wubi/current/amd64.tar.xz) > D:\ubuntu\disks\amd64.tar.xz
10-28 15:09 ERROR  TaskList: [Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 77, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 15:09 ERROR  TaskList: Non fatal error [Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')> in task download
10-28 15:09 DEBUG  TaskList: ### Finished download
10-28 15:09 ERROR  TaskList: Could not retrieve the required disk image files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 592, in get_diskimage
Exception: Could not retrieve the required disk image files
10-28 15:09 DEBUG  TaskList: # Cancelling tasklist
10-28 15:09 DEBUG  TaskList: # Finished tasklist
10-28 15:09 ERROR  root: Could not retrieve the required disk image files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 592, in get_diskimage
Exception: Could not retrieve the required disk image files
10-28 15:10 INFO   root: === wubi 12.10 rev273 ===
10-28 15:10 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
10-28 15:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\software\\program files\\Linux\\ubuntu\\wubi.exe"']
10-28 15:10 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\data
10-28 15:10 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\bin\7z.exe
10-28 15:10 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-28 15:10 DEBUG  CommonBackend: Fetching basic info...
10-28 15:10 DEBUG  CommonBackend: original_exe=D:\software\program files\Linux\ubuntu\wubi.exe
10-28 15:10 DEBUG  CommonBackend: platform=win32
10-28 15:10 DEBUG  CommonBackend: osname=nt
10-28 15:10 DEBUG  CommonBackend: language=en_US
10-28 15:10 DEBUG  CommonBackend: encoding=cp1252
10-28 15:10 DEBUG  WindowsBackend: arch=amd64
10-28 15:10 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\data\isolist.ini
10-28 15:10 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 15:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 15:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 15:10 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 15:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 15:10 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 15:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 15:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 15:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 15:10 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 15:10 DEBUG  WindowsBackend: Fetching host info...
10-28 15:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 15:10 DEBUG  WindowsBackend: windows version=vista
10-28 15:10 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 15:10 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 15:10 DEBUG  WindowsBackend: windows_build=7601
10-28 15:10 DEBUG  WindowsBackend: gmt=5
10-28 15:10 DEBUG  WindowsBackend: country=US
10-28 15:10 DEBUG  WindowsBackend: timezone=America/New_York
10-28 15:10 DEBUG  WindowsBackend: windows_username=sandesh
10-28 15:10 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 15:10 DEBUG  WindowsBackend: user_directory=
10-28 15:10 DEBUG  WindowsBackend: windows_language_code=1033
10-28 15:10 DEBUG  WindowsBackend: windows_language=English
10-28 15:10 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 15:10 DEBUG  WindowsBackend: bootloader=vista
10-28 15:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 32703.0039063 mb free ntfs)
10-28 15:10 DEBUG  WindowsBackend: drive=Drive(C: hd 32703.0039063 mb free ntfs)
10-28 15:10 DEBUG  WindowsBackend: drive=Drive(D: hd 99703.3828125 mb free ntfs)
10-28 15:10 DEBUG  WindowsBackend: drive=Drive(E: hd 61252.2226563 mb free ntfs)
10-28 15:10 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 15:10 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 15:10 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-28 15:10 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-28 15:10 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-28 15:10 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 15:10 DEBUG  WindowsBackend: keyboard_layout=us
10-28 15:10 DEBUG  WindowsBackend: keyboard_variant=
10-28 15:10 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-28 15:10 DEBUG  CommonBackend: locale=en_US.UTF-8
10-28 15:10 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 15:10 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 15:10 DEBUG  CommonBackend: Searching for local CDs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 INFO   root: Already installed, running the uninstaller...
10-28 15:10 INFO   root: Running the uninstaller...
10-28 15:10 INFO   CommonBackend: This is the uninstaller running
10-28 15:10 DEBUG  WindowsFrontend: __init__...
10-28 15:10 DEBUG  WindowsFrontend: on_init...
10-28 15:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\translations, languages=['en_US', 'en']
10-28 15:10 INFO   root: Received settings
10-28 15:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\translations, languages=['en_US', 'en']
10-28 15:10 DEBUG  TaskList: # Running tasklist...
10-28 15:10 DEBUG  TaskList: ## Running Remove bootloader entry...
10-28 15:10 DEBUG  WindowsBackend: Could not find bcd id
10-28 15:10 DEBUG  WindowsBackend: undo_bootini C:
10-28 15:10 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 32703.0039063 mb free ntfs)
10-28 15:10 DEBUG  WindowsBackend: undo_bootini D:
10-28 15:10 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 99703.3828125 mb free ntfs)
10-28 15:10 DEBUG  WindowsBackend: undo_bootini E:
10-28 15:10 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 61252.2226563 mb free ntfs)
10-28 15:10 DEBUG  WindowsBackend: undo_bootini M:
10-28 15:10 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
10-28 15:10 DEBUG  TaskList: ## Finished Remove bootloader entry
10-28 15:10 DEBUG  TaskList: ## Running Remove target dir...
10-28 15:10 DEBUG  CommonBackend: Deleting D:\ubuntu
10-28 15:10 DEBUG  TaskList: ## Finished Remove target dir
10-28 15:10 DEBUG  TaskList: ## Running Remove registry key...
10-28 15:10 DEBUG  TaskList: ## Finished Remove registry key
10-28 15:10 DEBUG  TaskList: # Finished tasklist
10-28 15:10 INFO   root: Almost finished uninstalling
10-28 15:10 INFO   root: Finished uninstallation
10-28 15:10 DEBUG  CommonBackend: Fetching basic info...
10-28 15:10 DEBUG  CommonBackend: original_exe=D:\software\program files\Linux\ubuntu\wubi.exe
10-28 15:10 DEBUG  CommonBackend: platform=win32
10-28 15:10 DEBUG  CommonBackend: osname=nt
10-28 15:10 DEBUG  WindowsBackend: arch=amd64
10-28 15:10 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\data\isolist.ini
10-28 15:10 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-28 15:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-28 15:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-28 15:10 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-28 15:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-28 15:10 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-28 15:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-28 15:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-28 15:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-28 15:10 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-28 15:10 DEBUG  WindowsBackend: Fetching host info...
10-28 15:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-28 15:10 DEBUG  WindowsBackend: windows version=vista
10-28 15:10 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-28 15:10 DEBUG  WindowsBackend: windows_sp=Service Pack 1
10-28 15:10 DEBUG  WindowsBackend: windows_build=7601
10-28 15:10 DEBUG  WindowsBackend: gmt=5
10-28 15:10 DEBUG  WindowsBackend: country=US
10-28 15:10 DEBUG  WindowsBackend: timezone=America/New_York
10-28 15:10 DEBUG  WindowsBackend: windows_username=sandesh
10-28 15:10 DEBUG  WindowsBackend: user_full_name=sandesh
10-28 15:10 DEBUG  WindowsBackend: user_directory=
10-28 15:10 DEBUG  WindowsBackend: windows_language_code=1033
10-28 15:10 DEBUG  WindowsBackend: windows_language=English
10-28 15:10 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
10-28 15:10 DEBUG  WindowsBackend: bootloader=vista
10-28 15:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 32702.9726563 mb free ntfs)
10-28 15:10 DEBUG  WindowsBackend: drive=Drive(C: hd 32702.9726563 mb free ntfs)
10-28 15:10 DEBUG  WindowsBackend: drive=Drive(D: hd 99705.7695313 mb free ntfs)
10-28 15:10 DEBUG  WindowsBackend: drive=Drive(E: hd 61252.2226563 mb free ntfs)
10-28 15:10 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-28 15:10 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
10-28 15:10 DEBUG  WindowsBackend: uninstaller_path=None
10-28 15:10 DEBUG  WindowsBackend: previous_target_dir=None
10-28 15:10 DEBUG  WindowsBackend: previous_distro_name=None
10-28 15:10 DEBUG  WindowsBackend: keyboard_id=67699721
10-28 15:10 DEBUG  WindowsBackend: keyboard_layout=us
10-28 15:10 DEBUG  WindowsBackend: keyboard_variant=
10-28 15:10 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
10-28 15:10 DEBUG  CommonBackend: Searching ISOs on USB devices
10-28 15:10 DEBUG  CommonBackend: Searching for local CDs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 INFO   root: Running the installer...
10-28 15:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\translations, languages=['en_US', 'en']
10-28 15:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\translations, languages=['en_US', 'en']
10-28 15:10 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sandesh
10-28 15:10 INFO   root: Received settings
10-28 15:10 DEBUG  CommonBackend: Searching for local CD
10-28 15:10 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-28 15:10 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
10-28 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
10-28 15:10 DEBUG  CommonBackend: Searching for local ISO
10-28 15:10 DEBUG  Distro:   checking Ubuntu ISO D:\software\program files\Linux\ubuntu\ubuntu-12.10-desktop-i386.iso
10-28 15:10 DEBUG  WindowsBackend:   extracting .disk\info from D:\software\program files\Linux\ubuntu\ubuntu-12.10-desktop-i386.iso
10-28 15:10 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
10-28 15:10 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
10-28 15:10 INFO   Distro: Found a valid iso for Ubuntu: D:\software\program files\Linux\ubuntu\ubuntu-12.10-desktop-i386.iso
10-28 15:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\translations, languages=['en_US', 'en']
10-28 15:10 DEBUG  TaskList: # Running tasklist...
10-28 15:10 DEBUG  TaskList: ## Running select_target_dir...
10-28 15:10 INFO   WindowsBackend: Installing into D:\ubuntu
10-28 15:10 DEBUG  TaskList: ## Finished select_target_dir
10-28 15:10 DEBUG  TaskList: ## Running create_dir_structure...
10-28 15:10 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-28 15:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-28 15:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-28 15:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-28 15:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-28 15:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-28 15:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-28 15:10 DEBUG  TaskList: ## Finished create_dir_structure
10-28 15:10 DEBUG  TaskList: ## Running uncompress_target_dir...
10-28 15:10 DEBUG  TaskList: ## Finished uncompress_target_dir
10-28 15:10 DEBUG  TaskList: ## Running create_uninstaller...
10-28 15:10 DEBUG  WindowsBackend: Copying uninstaller D:\software\program files\Linux\ubuntu\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-28 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-28 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-28 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-28 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-28 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
10-28 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-28 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-28 15:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-28 15:10 DEBUG  TaskList: ## Finished create_uninstaller
10-28 15:10 DEBUG  TaskList: ## Running copy_installation_files...
10-28 15:10 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-28 15:10 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\winboot -> D:\ubuntu\winboot
10-28 15:10 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pylB425.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
10-28 15:10 DEBUG  TaskList: ## Finished copy_installation_files
10-28 15:10 DEBUG  TaskList: ## Running get_iso...
10-28 15:10 DEBUG  CommonBackend: Trying to use ISO D:\software\program files\Linux\ubuntu\ubuntu-12.10-desktop-i386.iso
10-28 15:10 DEBUG  TaskList: New task check_iso
10-28 15:10 DEBUG  TaskList: ### Running check_iso...
10-28 15:10 DEBUG  CommonBackend: Checking D:\software\program files\Linux\ubuntu\ubuntu-12.10-desktop-i386.iso
10-28 15:10 DEBUG  Distro:   checking Ubuntu ISO D:\software\program files\Linux\ubuntu\ubuntu-12.10-desktop-i386.iso
10-28 15:10 INFO   Distro: Found a valid iso for Ubuntu: D:\software\program files\Linux\ubuntu\ubuntu-12.10-desktop-i386.iso
10-28 15:10 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
10-28 15:10 DEBUG  TaskList: New task get_metalink
10-28 15:10 DEBUG  TaskList: #### Running get_metalink...
10-28 15:10 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) > D:\ubuntu\install
10-28 15:10 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 15:10 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) > D:\ubuntu\install
10-28 15:10 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
10-28 15:10 DEBUG  TaskList: #### Finished get_metalink
10-28 15:10 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for D:\software\program files\Linux\ubuntu\ubuntu-12.10-desktop-i386.iso, ignoring
10-28 15:10 DEBUG  TaskList: ### Finished check_iso
10-28 15:10 DEBUG  TaskList: New task copy_file
10-28 15:10 DEBUG  CommonBackend: Copying D:\software\program files\Linux\ubuntu\ubuntu-12.10-desktop-i386.iso > D:\ubuntu\install\installation.iso
10-28 15:10 DEBUG  TaskList: ### Running copy_file...
10-28 15:11 DEBUG  TaskList: ### Finished copy_file
10-28 15:11 DEBUG  TaskList: ## Finished get_iso
10-28 15:11 DEBUG  TaskList: ## Running extract_kernel...
10-28 15:11 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\installation.iso
10-28 15:11 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\installation.iso
10-28 15:11 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\installation.iso
10-28 15:11 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\installation.iso
10-28 15:11 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-28 15:11 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
10-28 15:11 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = dedeef44f082210eb0d605d21837feb5 == dedeef44f082210eb0d605d21837feb5
10-28 15:11 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
10-28 15:11 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = bf4099046c27293af1f7ec8c76baf1c7 == bf4099046c27293af1f7ec8c76baf1c7
10-28 15:11 DEBUG  TaskList: ## Finished extract_kernel
10-28 15:11 DEBUG  TaskList: ## Running choose_disk_sizes...
10-28 15:11 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
10-28 15:11 DEBUG  TaskList: ## Finished choose_disk_sizes
10-28 15:11 DEBUG  TaskList: ## Running create_preseed...
10-28 15:11 DEBUG  TaskList: ## Finished create_preseed
10-28 15:11 DEBUG  TaskList: ## Running modify_bootloader...
10-28 15:11 DEBUG  TaskList: New task modify_bcd
10-28 15:11 DEBUG  TaskList: ### Running modify_bcd...
10-28 15:11 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 32702.9726563 mb free ntfs)
10-28 15:11 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa54-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa54-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 15:11 DEBUG  TaskList: # Cancelling tasklist
10-28 15:11 DEBUG  TaskList: New task modify_bcd
10-28 15:11 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa54-4ca4-11e1-853b-984507711b55} device partition=D:
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
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa54-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
10-28 15:11 DEBUG  TaskList: New task modify_bcd
10-28 15:11 DEBUG  TaskList: New task modify_bcd
10-28 15:11 DEBUG  TaskList: ## Finished modify_bootloader
10-28 15:11 DEBUG  TaskList: # Finished tasklist
11-02 14:20 INFO   root: === wubi 12.10 rev273 ===
11-02 14:20 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
11-02 14:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
11-02 14:20 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\data
11-02 14:20 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\bin\7z.exe
11-02 14:20 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-02 14:20 DEBUG  CommonBackend: Fetching basic info...
11-02 14:20 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
11-02 14:20 DEBUG  CommonBackend: platform=win32
11-02 14:20 DEBUG  CommonBackend: osname=nt
11-02 14:20 DEBUG  CommonBackend: language=en_US
11-02 14:20 DEBUG  CommonBackend: encoding=cp1252
11-02 14:20 DEBUG  WindowsBackend: arch=amd64
11-02 14:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\data\isolist.ini
11-02 14:20 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-02 14:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-02 14:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-02 14:20 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-02 14:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-02 14:20 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-02 14:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-02 14:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-02 14:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-02 14:20 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-02 14:20 DEBUG  WindowsBackend: Fetching host info...
11-02 14:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-02 14:20 DEBUG  WindowsBackend: windows version=vista
11-02 14:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-02 14:20 DEBUG  WindowsBackend: windows_sp=Service Pack 1
11-02 14:20 DEBUG  WindowsBackend: windows_build=7601
11-02 14:20 DEBUG  WindowsBackend: gmt=5
11-02 14:20 DEBUG  WindowsBackend: country=US
11-02 14:20 DEBUG  WindowsBackend: timezone=America/New_York
11-02 14:20 DEBUG  WindowsBackend: windows_username=sandesh
11-02 14:20 DEBUG  WindowsBackend: user_full_name=sandesh
11-02 14:20 DEBUG  WindowsBackend: user_directory=
11-02 14:20 DEBUG  WindowsBackend: windows_language_code=1033
11-02 14:20 DEBUG  WindowsBackend: windows_language=English
11-02 14:20 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
11-02 14:20 DEBUG  WindowsBackend: bootloader=vista
11-02 14:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 33085.7109375 mb free ntfs)
11-02 14:20 DEBUG  WindowsBackend: drive=Drive(C: hd 33085.7109375 mb free ntfs)
11-02 14:20 DEBUG  WindowsBackend: drive=Drive(D: hd 89630.6640625 mb free ntfs)
11-02 14:20 DEBUG  WindowsBackend: drive=Drive(E: hd 59381.9804688 mb free ntfs)
11-02 14:20 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-02 14:20 DEBUG  WindowsBackend: drive=Drive(H: removable 422.1953125 mb free ntfs)
11-02 14:20 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
11-02 14:20 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
11-02 14:20 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
11-02 14:20 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-02 14:20 DEBUG  WindowsBackend: keyboard_id=67699721
11-02 14:20 DEBUG  WindowsBackend: keyboard_layout=us
11-02 14:20 DEBUG  WindowsBackend: keyboard_variant=
11-02 14:20 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-02 14:20 DEBUG  CommonBackend: locale=en_US.UTF-8
11-02 14:20 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
11-02 14:20 DEBUG  CommonBackend: Searching ISOs on USB devices
11-02 14:20 DEBUG  Distro:   checking Ubuntu ISO H:\ubuntu-12.10-desktop-i386.iso
11-02 14:20 DEBUG  WindowsBackend:   extracting .disk\info from H:\ubuntu-12.10-desktop-i386.iso
11-02 14:20 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
11-02 14:20 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
11-02 14:20 INFO   Distro: Found a valid iso for Ubuntu: H:\ubuntu-12.10-desktop-i386.iso
11-02 14:20 DEBUG  CommonBackend: Searching for local CDs
11-02 14:20 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp is a valid Ubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp is a valid Ubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp is a valid Kubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp is a valid Kubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp is a valid Mythbuntu CD
11-02 14:20 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp is a valid Mythbuntu CD
11-02 14:20 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp is a valid Edubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp is a valid Edubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp is a valid Lubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp is a valid Lubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-02 14:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-02 14:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-02 14:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-02 14:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-02 14:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-02 14:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-02 14:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-02 14:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-02 14:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-02 14:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:20 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-02 14:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:20 INFO   root: Running the uninstaller...
11-02 14:20 INFO   CommonBackend: This is the uninstaller running
11-02 14:20 DEBUG  WindowsFrontend: __init__...
11-02 14:20 DEBUG  WindowsFrontend: on_init...
11-02 14:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\translations, languages=['en_US', 'en']
11-02 14:20 INFO   root: Received settings
11-02 14:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\translations, languages=['en_US', 'en']
11-02 14:20 DEBUG  TaskList: # Running tasklist...
11-02 14:20 DEBUG  TaskList: ## Running Remove bootloader entry...
11-02 14:20 DEBUG  WindowsBackend: Could not find bcd id
11-02 14:20 DEBUG  WindowsBackend: undo_bootini C:
11-02 14:20 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 33085.7109375 mb free ntfs)
11-02 14:20 DEBUG  WindowsBackend: undo_bootini D:
11-02 14:20 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 89630.6640625 mb free ntfs)
11-02 14:20 DEBUG  WindowsBackend: undo_bootini E:
11-02 14:20 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 59381.9804688 mb free ntfs)
11-02 14:20 DEBUG  WindowsBackend: undo_bootini H:
11-02 14:20 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 422.1953125 mb free ntfs)
11-02 14:20 DEBUG  WindowsBackend: undo_bootini M:
11-02 14:20 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
11-02 14:20 DEBUG  TaskList: ## Finished Remove bootloader entry
11-02 14:20 DEBUG  TaskList: ## Running Remove target dir...
11-02 14:20 DEBUG  CommonBackend: Deleting D:\ubuntu
11-02 14:20 DEBUG  TaskList: ## Finished Remove target dir
11-02 14:20 DEBUG  TaskList: ## Running Remove registry key...
11-02 14:20 DEBUG  TaskList: ## Finished Remove registry key
11-02 14:20 DEBUG  TaskList: # Finished tasklist
11-02 14:20 INFO   root: Almost finished uninstalling
11-02 14:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl2EE2.tmp\translations, languages=['en_US', 'en']
11-02 14:20 INFO   root: Finished uninstallation
11-02 14:20 DEBUG  root: application.quit
11-02 14:20 DEBUG  WindowsFrontend: frontend.quit
11-02 14:20 DEBUG  WindowsFrontend: frontend.on_quit
11-02 14:20 DEBUG  root: application.on_quit
11-02 14:20 INFO   root: sys.exit
11-02 14:23 INFO   root: === wubi 12.10 rev273 ===
11-02 14:23 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
11-02 14:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-02 14:23 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\data
11-02 14:23 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\bin\7z.exe
11-02 14:23 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-02 14:23 DEBUG  CommonBackend: Fetching basic info...
11-02 14:23 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-02 14:23 DEBUG  CommonBackend: platform=win32
11-02 14:23 DEBUG  CommonBackend: osname=nt
11-02 14:23 DEBUG  CommonBackend: language=en_US
11-02 14:23 DEBUG  CommonBackend: encoding=cp1252
11-02 14:23 DEBUG  WindowsBackend: arch=amd64
11-02 14:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\data\isolist.ini
11-02 14:23 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-02 14:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-02 14:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-02 14:23 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-02 14:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-02 14:23 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-02 14:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-02 14:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-02 14:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-02 14:23 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-02 14:23 DEBUG  WindowsBackend: Fetching host info...
11-02 14:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-02 14:23 DEBUG  WindowsBackend: windows version=vista
11-02 14:23 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-02 14:23 DEBUG  WindowsBackend: windows_sp=Service Pack 1
11-02 14:23 DEBUG  WindowsBackend: windows_build=7601
11-02 14:23 DEBUG  WindowsBackend: gmt=5
11-02 14:23 DEBUG  WindowsBackend: country=US
11-02 14:23 DEBUG  WindowsBackend: timezone=America/New_York
11-02 14:23 DEBUG  WindowsBackend: windows_username=sandesh
11-02 14:23 DEBUG  WindowsBackend: user_full_name=sandesh
11-02 14:23 DEBUG  WindowsBackend: user_directory=
11-02 14:23 DEBUG  WindowsBackend: windows_language_code=1033
11-02 14:23 DEBUG  WindowsBackend: windows_language=English
11-02 14:23 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
11-02 14:23 DEBUG  WindowsBackend: bootloader=vista
11-02 14:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 35122.9765625 mb free ntfs)
11-02 14:23 DEBUG  WindowsBackend: drive=Drive(C: hd 35122.9765625 mb free ntfs)
11-02 14:23 DEBUG  WindowsBackend: drive=Drive(D: hd 89385.3789063 mb free ntfs)
11-02 14:23 DEBUG  WindowsBackend: drive=Drive(E: hd 59334.2304688 mb free ntfs)
11-02 14:23 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-02 14:23 DEBUG  WindowsBackend: drive=Drive(H: removable 422.1953125 mb free ntfs)
11-02 14:23 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
11-02 14:23 DEBUG  WindowsBackend: uninstaller_path=None
11-02 14:23 DEBUG  WindowsBackend: previous_target_dir=None
11-02 14:23 DEBUG  WindowsBackend: previous_distro_name=None
11-02 14:23 DEBUG  WindowsBackend: keyboard_id=67699721
11-02 14:23 DEBUG  WindowsBackend: keyboard_layout=us
11-02 14:23 DEBUG  WindowsBackend: keyboard_variant=
11-02 14:23 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-02 14:23 DEBUG  CommonBackend: locale=en_US.UTF-8
11-02 14:23 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
11-02 14:23 DEBUG  CommonBackend: Searching ISOs on USB devices
11-02 14:23 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
11-02 14:23 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
11-02 14:23 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
11-02 14:23 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
11-02 14:23 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
11-02 14:23 DEBUG  CommonBackend: Searching for local CDs
11-02 14:23 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp is a valid Kubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp is a valid Kubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp is a valid Mythbuntu CD
11-02 14:23 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp is a valid Mythbuntu CD
11-02 14:23 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp is a valid Edubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp is a valid Edubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp is a valid Lubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp is a valid Lubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-02 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-02 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-02 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-02 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-02 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-02 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-02 14:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-02 14:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether H:\ is a valid Edubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether H:\ is a valid Lubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-02 14:23 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-02 14:23 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:23 INFO   root: Running the installer...
11-02 14:23 DEBUG  WindowsFrontend: __init__...
11-02 14:23 DEBUG  WindowsFrontend: on_init...
11-02 14:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\translations, languages=['en_US', 'en']
11-02 14:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\translations, languages=['en_US', 'en']
11-02 14:23 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sandesh
11-02 14:23 INFO   root: Received settings
11-02 14:23 DEBUG  CommonBackend: Searching for local CD
11-02 14:23 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-02 14:23 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-02 14:23 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-02 14:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\translations, languages=['en_US', 'en']
11-02 14:23 DEBUG  TaskList: # Running tasklist...
11-02 14:23 DEBUG  TaskList: ## Running select_target_dir...
11-02 14:23 INFO   WindowsBackend: Installing into D:\ubuntu
11-02 14:23 DEBUG  TaskList: ## Finished select_target_dir
11-02 14:23 DEBUG  TaskList: ## Running create_dir_structure...
11-02 14:23 DEBUG  CommonBackend: Creating dir D:\ubuntu
11-02 14:23 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
11-02 14:23 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
11-02 14:23 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
11-02 14:23 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
11-02 14:23 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
11-02 14:23 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
11-02 14:23 DEBUG  TaskList: ## Finished create_dir_structure
11-02 14:23 DEBUG  TaskList: ## Running uncompress_target_dir...
11-02 14:23 DEBUG  TaskList: ## Finished uncompress_target_dir
11-02 14:23 DEBUG  TaskList: ## Running create_uninstaller...
11-02 14:23 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
11-02 14:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
11-02 14:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
11-02 14:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-02 14:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
11-02 14:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
11-02 14:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-02 14:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-02 14:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-02 14:23 DEBUG  TaskList: ## Finished create_uninstaller
11-02 14:23 DEBUG  TaskList: ## Running copy_installation_files...
11-02 14:23 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
11-02 14:23 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\winboot -> D:\ubuntu\winboot
11-02 14:23 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pylF01E.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
11-02 14:23 DEBUG  TaskList: ## Finished copy_installation_files
11-02 14:23 DEBUG  TaskList: ## Running get_iso...
11-02 14:23 DEBUG  CommonBackend: Trying to use pre-specified ISO D:\ubuntu-12.10-desktop-i386.iso
11-02 14:23 DEBUG  TaskList: New task is_valid_iso
11-02 14:23 DEBUG  TaskList: ### Running is_valid_iso...
11-02 14:23 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
11-02 14:23 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
11-02 14:23 DEBUG  TaskList: ### Finished is_valid_iso
11-02 14:23 DEBUG  TaskList: New task check_iso
11-02 14:23 DEBUG  TaskList: ### Running check_iso...
11-02 14:23 DEBUG  CommonBackend: Checking D:\ubuntu-12.10-desktop-i386.iso
11-02 14:23 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
11-02 14:23 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
11-02 14:23 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
11-02 14:23 DEBUG  TaskList: New task get_metalink
11-02 14:23 DEBUG  TaskList: #### Running get_metalink...
11-02 14:23 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) > D:\ubuntu\install
11-02 14:23 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
11-02 14:23 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) > D:\ubuntu\install
11-02 14:23 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10051, 'Network is unreachable')>
11-02 14:23 DEBUG  TaskList: #### Finished get_metalink
11-02 14:23 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for D:\ubuntu-12.10-desktop-i386.iso, ignoring
11-02 14:23 DEBUG  TaskList: ### Finished check_iso
11-02 14:23 DEBUG  TaskList: New task copy_file
11-02 14:23 DEBUG  CommonBackend: Copying D:\ubuntu-12.10-desktop-i386.iso > D:\ubuntu\install\installation.iso
11-02 14:23 DEBUG  TaskList: ### Running copy_file...
11-02 14:24 DEBUG  TaskList: ### Finished copy_file
11-02 14:24 DEBUG  TaskList: ## Finished get_iso
11-02 14:24 DEBUG  TaskList: ## Running extract_kernel...
11-02 14:24 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\installation.iso
11-02 14:24 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\installation.iso
11-02 14:24 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\installation.iso
11-02 14:24 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\installation.iso
11-02 14:24 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
11-02 14:24 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
11-02 14:24 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = dedeef44f082210eb0d605d21837feb5 == dedeef44f082210eb0d605d21837feb5
11-02 14:24 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
11-02 14:24 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = bf4099046c27293af1f7ec8c76baf1c7 == bf4099046c27293af1f7ec8c76baf1c7
11-02 14:24 DEBUG  TaskList: ## Finished extract_kernel
11-02 14:24 DEBUG  TaskList: ## Running choose_disk_sizes...
11-02 14:24 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
11-02 14:24 DEBUG  TaskList: ## Finished choose_disk_sizes
11-02 14:24 DEBUG  TaskList: ## Running create_preseed...
11-02 14:24 DEBUG  TaskList: ## Finished create_preseed
11-02 14:24 DEBUG  TaskList: ## Running modify_bootloader...
11-02 14:24 DEBUG  TaskList: New task modify_bcd
11-02 14:24 DEBUG  TaskList: ### Running modify_bcd...
11-02 14:24 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 35122.9765625 mb free ntfs)
11-02 14:24 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa55-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa55-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
11-02 14:24 DEBUG  TaskList: # Cancelling tasklist
11-02 14:24 DEBUG  TaskList: New task modify_bcd
11-02 14:24 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa55-4ca4-11e1-853b-984507711b55} device partition=D:
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
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa55-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
11-02 14:24 DEBUG  TaskList: New task modify_bcd
11-02 14:24 DEBUG  TaskList: New task modify_bcd
11-02 14:24 DEBUG  TaskList: New task modify_bcd
11-02 14:24 DEBUG  TaskList: ## Finished modify_bootloader
11-02 14:24 DEBUG  TaskList: # Finished tasklist
11-03 16:02 INFO   root: === wubi 12.10 rev273 ===
11-03 16:02 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
11-03 16:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
11-03 16:02 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\data
11-03 16:02 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\bin\7z.exe
11-03 16:02 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-03 16:02 DEBUG  CommonBackend: Fetching basic info...
11-03 16:02 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
11-03 16:02 DEBUG  CommonBackend: platform=win32
11-03 16:02 DEBUG  CommonBackend: osname=nt
11-03 16:02 DEBUG  CommonBackend: language=en_US
11-03 16:02 DEBUG  CommonBackend: encoding=cp1252
11-03 16:02 DEBUG  WindowsBackend: arch=amd64
11-03 16:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\data\isolist.ini
11-03 16:02 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-03 16:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 16:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 16:02 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-03 16:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 16:02 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-03 16:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 16:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 16:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 16:02 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-03 16:02 DEBUG  WindowsBackend: Fetching host info...
11-03 16:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 16:02 DEBUG  WindowsBackend: windows version=vista
11-03 16:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 16:02 DEBUG  WindowsBackend: windows_sp=Service Pack 1
11-03 16:02 DEBUG  WindowsBackend: windows_build=7601
11-03 16:02 DEBUG  WindowsBackend: gmt=5
11-03 16:02 DEBUG  WindowsBackend: country=US
11-03 16:02 DEBUG  WindowsBackend: timezone=America/New_York
11-03 16:02 DEBUG  WindowsBackend: windows_username=sandesh
11-03 16:02 DEBUG  WindowsBackend: user_full_name=sandesh
11-03 16:02 DEBUG  WindowsBackend: user_directory=
11-03 16:02 DEBUG  WindowsBackend: windows_language_code=1033
11-03 16:02 DEBUG  WindowsBackend: windows_language=English
11-03 16:02 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
11-03 16:02 DEBUG  WindowsBackend: bootloader=vista
11-03 16:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 34587.2890625 mb free ntfs)
11-03 16:02 DEBUG  WindowsBackend: drive=Drive(C: hd 34587.2890625 mb free ntfs)
11-03 16:02 DEBUG  WindowsBackend: drive=Drive(D: hd 85117.3632813 mb free ntfs)
11-03 16:02 DEBUG  WindowsBackend: drive=Drive(E: hd 59229.6171875 mb free ntfs)
11-03 16:02 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 16:02 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
11-03 16:02 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
11-03 16:02 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
11-03 16:02 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-03 16:02 DEBUG  WindowsBackend: keyboard_id=67699721
11-03 16:02 DEBUG  WindowsBackend: keyboard_layout=us
11-03 16:02 DEBUG  WindowsBackend: keyboard_variant=
11-03 16:02 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-03 16:02 DEBUG  CommonBackend: locale=en_US.UTF-8
11-03 16:02 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
11-03 16:02 DEBUG  CommonBackend: Searching ISOs on USB devices
11-03 16:02 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
11-03 16:02 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
11-03 16:02 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
11-03 16:02 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
11-03 16:02 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
11-03 16:02 DEBUG  CommonBackend: Searching for local CDs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 INFO   root: Running the uninstaller...
11-03 16:02 INFO   CommonBackend: This is the uninstaller running
11-03 16:02 DEBUG  WindowsFrontend: __init__...
11-03 16:02 DEBUG  WindowsFrontend: on_init...
11-03 16:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\translations, languages=['en_US', 'en']
11-03 16:02 INFO   root: === wubi 12.10 rev273 ===
11-03 16:02 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
11-03 16:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
11-03 16:02 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\data
11-03 16:02 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\bin\7z.exe
11-03 16:02 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-03 16:02 DEBUG  CommonBackend: Fetching basic info...
11-03 16:02 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
11-03 16:02 DEBUG  CommonBackend: platform=win32
11-03 16:02 DEBUG  CommonBackend: osname=nt
11-03 16:02 DEBUG  CommonBackend: language=en_US
11-03 16:02 DEBUG  CommonBackend: encoding=cp1252
11-03 16:02 DEBUG  WindowsBackend: arch=amd64
11-03 16:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\data\isolist.ini
11-03 16:02 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-03 16:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 16:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 16:02 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-03 16:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 16:02 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-03 16:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 16:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 16:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 16:02 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-03 16:02 DEBUG  WindowsBackend: Fetching host info...
11-03 16:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 16:02 DEBUG  WindowsBackend: windows version=vista
11-03 16:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 16:02 DEBUG  WindowsBackend: windows_sp=Service Pack 1
11-03 16:02 DEBUG  WindowsBackend: windows_build=7601
11-03 16:02 DEBUG  WindowsBackend: gmt=5
11-03 16:02 DEBUG  WindowsBackend: country=US
11-03 16:02 DEBUG  WindowsBackend: timezone=America/New_York
11-03 16:02 DEBUG  WindowsBackend: windows_username=sandesh
11-03 16:02 DEBUG  WindowsBackend: user_full_name=sandesh
11-03 16:02 DEBUG  WindowsBackend: user_directory=
11-03 16:02 DEBUG  WindowsBackend: windows_language_code=1033
11-03 16:02 DEBUG  WindowsBackend: windows_language=English
11-03 16:02 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
11-03 16:02 DEBUG  WindowsBackend: bootloader=vista
11-03 16:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 34577.5859375 mb free ntfs)
11-03 16:02 DEBUG  WindowsBackend: drive=Drive(C: hd 34577.5859375 mb free ntfs)
11-03 16:02 DEBUG  WindowsBackend: drive=Drive(D: hd 85117.3632813 mb free ntfs)
11-03 16:02 DEBUG  WindowsBackend: drive=Drive(E: hd 59229.3398438 mb free ntfs)
11-03 16:02 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 16:02 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
11-03 16:02 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
11-03 16:02 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
11-03 16:02 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-03 16:02 DEBUG  WindowsBackend: keyboard_id=67699721
11-03 16:02 DEBUG  WindowsBackend: keyboard_layout=us
11-03 16:02 DEBUG  WindowsBackend: keyboard_variant=
11-03 16:02 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-03 16:02 DEBUG  CommonBackend: locale=en_US.UTF-8
11-03 16:02 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
11-03 16:02 DEBUG  CommonBackend: Searching ISOs on USB devices
11-03 16:02 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
11-03 16:02 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
11-03 16:02 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
11-03 16:02 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
11-03 16:02 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
11-03 16:02 DEBUG  CommonBackend: Searching for local CDs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-03 16:02 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:02 INFO   root: Running the uninstaller...
11-03 16:02 INFO   CommonBackend: This is the uninstaller running
11-03 16:02 DEBUG  WindowsFrontend: __init__...
11-03 16:02 DEBUG  WindowsFrontend: on_init...
11-03 16:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\translations, languages=['en_US', 'en']
11-03 16:02 INFO   root: Received settings
11-03 16:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\translations, languages=['en_US', 'en']
11-03 16:02 DEBUG  TaskList: # Running tasklist...
11-03 16:02 DEBUG  TaskList: ## Running Remove bootloader entry...
11-03 16:02 DEBUG  WindowsBackend: Could not find bcd id
11-03 16:02 DEBUG  WindowsBackend: undo_bootini C:
11-03 16:02 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 34577.5859375 mb free ntfs)
11-03 16:02 DEBUG  WindowsBackend: undo_bootini D:
11-03 16:02 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 85117.3632813 mb free ntfs)
11-03 16:02 DEBUG  WindowsBackend: undo_bootini E:
11-03 16:02 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 59229.3398438 mb free ntfs)
11-03 16:02 DEBUG  WindowsBackend: undo_bootini M:
11-03 16:02 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
11-03 16:02 DEBUG  TaskList: ## Finished Remove bootloader entry
11-03 16:02 DEBUG  TaskList: ## Running Remove target dir...
11-03 16:02 DEBUG  CommonBackend: Deleting D:\ubuntu
11-03 16:02 DEBUG  TaskList: ## Finished Remove target dir
11-03 16:02 DEBUG  TaskList: ## Running Remove registry key...
11-03 16:02 DEBUG  TaskList: ## Finished Remove registry key
11-03 16:02 DEBUG  TaskList: # Finished tasklist
11-03 16:02 INFO   root: Almost finished uninstalling
11-03 16:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl2426.tmp\translations, languages=['en_US', 'en']
11-03 16:03 INFO   root: Finished uninstallation
11-03 16:03 DEBUG  root: application.quit
11-03 16:03 DEBUG  WindowsFrontend: frontend.quit
11-03 16:03 DEBUG  WindowsFrontend: frontend.on_quit
11-03 16:03 DEBUG  root: application.on_quit
11-03 16:03 INFO   root: sys.exit
11-03 16:03 INFO   root: === wubi 12.10 rev273 ===
11-03 16:03 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
11-03 16:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-03 16:03 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\data
11-03 16:03 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\bin\7z.exe
11-03 16:03 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-03 16:03 DEBUG  CommonBackend: Fetching basic info...
11-03 16:03 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-03 16:03 DEBUG  CommonBackend: platform=win32
11-03 16:03 DEBUG  CommonBackend: osname=nt
11-03 16:03 DEBUG  CommonBackend: language=en_US
11-03 16:03 DEBUG  CommonBackend: encoding=cp1252
11-03 16:03 DEBUG  WindowsBackend: arch=amd64
11-03 16:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\data\isolist.ini
11-03 16:03 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-03 16:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 16:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 16:03 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-03 16:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 16:03 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-03 16:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 16:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 16:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 16:03 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-03 16:03 DEBUG  WindowsBackend: Fetching host info...
11-03 16:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 16:03 DEBUG  WindowsBackend: windows version=vista
11-03 16:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 16:03 DEBUG  WindowsBackend: windows_sp=Service Pack 1
11-03 16:03 DEBUG  WindowsBackend: windows_build=7601
11-03 16:03 DEBUG  WindowsBackend: gmt=5
11-03 16:03 DEBUG  WindowsBackend: country=US
11-03 16:03 DEBUG  WindowsBackend: timezone=America/New_York
11-03 16:03 DEBUG  WindowsBackend: windows_username=sandesh
11-03 16:03 DEBUG  WindowsBackend: user_full_name=sandesh
11-03 16:03 DEBUG  WindowsBackend: user_directory=
11-03 16:03 DEBUG  WindowsBackend: windows_language_code=1033
11-03 16:03 DEBUG  WindowsBackend: windows_language=English
11-03 16:03 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
11-03 16:03 DEBUG  WindowsBackend: bootloader=vista
11-03 16:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 34576.5429688 mb free ntfs)
11-03 16:03 DEBUG  WindowsBackend: drive=Drive(C: hd 34576.5429688 mb free ntfs)
11-03 16:03 DEBUG  WindowsBackend: drive=Drive(D: hd 85894.3046875 mb free ntfs)
11-03 16:03 DEBUG  WindowsBackend: drive=Drive(E: hd 59228.5585938 mb free ntfs)
11-03 16:03 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 16:03 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
11-03 16:03 DEBUG  WindowsBackend: uninstaller_path=None
11-03 16:03 DEBUG  WindowsBackend: previous_target_dir=None
11-03 16:03 DEBUG  WindowsBackend: previous_distro_name=None
11-03 16:03 DEBUG  WindowsBackend: keyboard_id=67699721
11-03 16:03 DEBUG  WindowsBackend: keyboard_layout=us
11-03 16:03 DEBUG  WindowsBackend: keyboard_variant=
11-03 16:03 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-03 16:03 DEBUG  CommonBackend: locale=en_US.UTF-8
11-03 16:03 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
11-03 16:03 DEBUG  CommonBackend: Searching ISOs on USB devices
11-03 16:03 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
11-03 16:03 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
11-03 16:03 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
11-03 16:03 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
11-03 16:03 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
11-03 16:03 DEBUG  CommonBackend: Searching for local CDs
11-03 16:03 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp is a valid Ubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp is a valid Ubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp is a valid Kubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp is a valid Kubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp is a valid Mythbuntu CD
11-03 16:03 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp is a valid Mythbuntu CD
11-03 16:03 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp is a valid Edubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp is a valid Edubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp is a valid Lubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp is a valid Lubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-03 16:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-03 16:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-03 16:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-03 16:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-03 16:03 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-03 16:03 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:03 INFO   root: Running the installer...
11-03 16:03 DEBUG  WindowsFrontend: __init__...
11-03 16:03 DEBUG  WindowsFrontend: on_init...
11-03 16:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\translations, languages=['en_US', 'en']
11-03 16:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\translations, languages=['en_US', 'en']
11-03 16:03 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sandesh
11-03 16:03 INFO   root: Received settings
11-03 16:03 DEBUG  CommonBackend: Searching for local CD
11-03 16:03 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp is a valid Ubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:03 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-03 16:03 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\translations, languages=['en_US', 'en']
11-03 16:03 DEBUG  TaskList: # Running tasklist...
11-03 16:03 DEBUG  TaskList: ## Running select_target_dir...
11-03 16:03 INFO   WindowsBackend: Installing into D:\ubuntu
11-03 16:03 DEBUG  TaskList: ## Finished select_target_dir
11-03 16:03 DEBUG  TaskList: ## Running create_dir_structure...
11-03 16:03 DEBUG  CommonBackend: Creating dir D:\ubuntu
11-03 16:03 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
11-03 16:03 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
11-03 16:03 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
11-03 16:03 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
11-03 16:03 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
11-03 16:03 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
11-03 16:03 DEBUG  TaskList: ## Finished create_dir_structure
11-03 16:03 DEBUG  TaskList: ## Running uncompress_target_dir...
11-03 16:03 DEBUG  TaskList: ## Finished uncompress_target_dir
11-03 16:03 DEBUG  TaskList: ## Running create_uninstaller...
11-03 16:03 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
11-03 16:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
11-03 16:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
11-03 16:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-03 16:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
11-03 16:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
11-03 16:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-03 16:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-03 16:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-03 16:03 DEBUG  TaskList: ## Finished create_uninstaller
11-03 16:03 DEBUG  TaskList: ## Running copy_installation_files...
11-03 16:03 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
11-03 16:03 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\winboot -> D:\ubuntu\winboot
11-03 16:03 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl897D.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
11-03 16:03 DEBUG  TaskList: ## Finished copy_installation_files
11-03 16:03 DEBUG  TaskList: ## Running get_iso...
11-03 16:03 DEBUG  CommonBackend: Trying to use pre-specified ISO D:\ubuntu-12.10-desktop-i386.iso
11-03 16:03 DEBUG  TaskList: New task is_valid_iso
11-03 16:03 DEBUG  TaskList: ### Running is_valid_iso...
11-03 16:03 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
11-03 16:03 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
11-03 16:03 DEBUG  TaskList: ### Finished is_valid_iso
11-03 16:03 DEBUG  TaskList: New task check_iso
11-03 16:03 DEBUG  TaskList: ### Running check_iso...
11-03 16:03 DEBUG  CommonBackend: Checking D:\ubuntu-12.10-desktop-i386.iso
11-03 16:03 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
11-03 16:03 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
11-03 16:03 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
11-03 16:03 DEBUG  TaskList: New task get_metalink
11-03 16:03 DEBUG  TaskList: #### Running get_metalink...
11-03 16:03 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) > D:\ubuntu\install
11-03 16:03 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10060, 'Operation timed out')>
11-03 16:03 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) > D:\ubuntu\install
11-03 16:04 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10060, 'Operation timed out')>
11-03 16:04 DEBUG  TaskList: #### Finished get_metalink
11-03 16:04 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for D:\ubuntu-12.10-desktop-i386.iso, ignoring
11-03 16:04 DEBUG  TaskList: ### Finished check_iso
11-03 16:04 DEBUG  TaskList: New task copy_file
11-03 16:04 DEBUG  CommonBackend: Copying D:\ubuntu-12.10-desktop-i386.iso > D:\ubuntu\install\installation.iso
11-03 16:04 DEBUG  TaskList: ### Running copy_file...
11-03 16:04 DEBUG  TaskList: ### Finished copy_file
11-03 16:04 DEBUG  TaskList: ## Finished get_iso
11-03 16:04 DEBUG  TaskList: ## Running extract_kernel...
11-03 16:04 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\installation.iso
11-03 16:04 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\installation.iso
11-03 16:04 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\installation.iso
11-03 16:04 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\installation.iso
11-03 16:04 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
11-03 16:04 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
11-03 16:04 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = dedeef44f082210eb0d605d21837feb5 == dedeef44f082210eb0d605d21837feb5
11-03 16:04 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
11-03 16:04 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = bf4099046c27293af1f7ec8c76baf1c7 == bf4099046c27293af1f7ec8c76baf1c7
11-03 16:04 DEBUG  TaskList: ## Finished extract_kernel
11-03 16:04 DEBUG  TaskList: ## Running choose_disk_sizes...
11-03 16:04 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
11-03 16:04 DEBUG  TaskList: ## Finished choose_disk_sizes
11-03 16:04 DEBUG  TaskList: ## Running create_preseed...
11-03 16:04 DEBUG  TaskList: ## Finished create_preseed
11-03 16:04 DEBUG  TaskList: ## Running modify_bootloader...
11-03 16:04 DEBUG  TaskList: New task modify_bcd
11-03 16:04 DEBUG  TaskList: ### Running modify_bcd...
11-03 16:04 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 34576.5429688 mb free ntfs)
11-03 16:04 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa56-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa56-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
11-03 16:04 DEBUG  TaskList: # Cancelling tasklist
11-03 16:04 DEBUG  TaskList: New task modify_bcd
11-03 16:04 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa56-4ca4-11e1-853b-984507711b55} device partition=D:
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
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa56-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
11-03 16:04 DEBUG  TaskList: New task modify_bcd
11-03 16:04 DEBUG  TaskList: New task modify_bcd
11-03 16:04 DEBUG  TaskList: ## Finished modify_bootloader
11-03 16:04 DEBUG  TaskList: # Finished tasklist
11-03 16:05 INFO   root: === wubi 12.10 rev273 ===
11-03 16:05 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
11-03 16:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
11-03 16:05 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\data
11-03 16:05 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\bin\7z.exe
11-03 16:05 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-03 16:05 DEBUG  CommonBackend: Fetching basic info...
11-03 16:05 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
11-03 16:05 DEBUG  CommonBackend: platform=win32
11-03 16:05 DEBUG  CommonBackend: osname=nt
11-03 16:05 DEBUG  CommonBackend: language=en_US
11-03 16:05 DEBUG  CommonBackend: encoding=cp1252
11-03 16:05 DEBUG  WindowsBackend: arch=amd64
11-03 16:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\data\isolist.ini
11-03 16:05 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-03 16:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 16:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 16:05 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-03 16:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 16:05 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-03 16:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 16:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 16:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 16:05 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-03 16:05 DEBUG  WindowsBackend: Fetching host info...
11-03 16:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 16:05 DEBUG  WindowsBackend: windows version=vista
11-03 16:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 16:05 DEBUG  WindowsBackend: windows_sp=Service Pack 1
11-03 16:05 DEBUG  WindowsBackend: windows_build=7601
11-03 16:05 DEBUG  WindowsBackend: gmt=5
11-03 16:05 DEBUG  WindowsBackend: country=US
11-03 16:05 DEBUG  WindowsBackend: timezone=America/New_York
11-03 16:05 DEBUG  WindowsBackend: windows_username=sandesh
11-03 16:05 DEBUG  WindowsBackend: user_full_name=sandesh
11-03 16:05 DEBUG  WindowsBackend: user_directory=
11-03 16:05 DEBUG  WindowsBackend: windows_language_code=1033
11-03 16:05 DEBUG  WindowsBackend: windows_language=English
11-03 16:05 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
11-03 16:05 DEBUG  WindowsBackend: bootloader=vista
11-03 16:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 34576.7421875 mb free ntfs)
11-03 16:05 DEBUG  WindowsBackend: drive=Drive(C: hd 34576.7421875 mb free ntfs)
11-03 16:05 DEBUG  WindowsBackend: drive=Drive(D: hd 85117.3632813 mb free ntfs)
11-03 16:05 DEBUG  WindowsBackend: drive=Drive(E: hd 59225.6679688 mb free ntfs)
11-03 16:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 16:05 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
11-03 16:05 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
11-03 16:05 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
11-03 16:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-03 16:05 DEBUG  WindowsBackend: keyboard_id=67699721
11-03 16:05 DEBUG  WindowsBackend: keyboard_layout=us
11-03 16:05 DEBUG  WindowsBackend: keyboard_variant=
11-03 16:05 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-03 16:05 DEBUG  CommonBackend: locale=en_US.UTF-8
11-03 16:05 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
11-03 16:05 DEBUG  CommonBackend: Searching ISOs on USB devices
11-03 16:05 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
11-03 16:05 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
11-03 16:05 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
11-03 16:05 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
11-03 16:05 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
11-03 16:05 DEBUG  CommonBackend: Searching for local CDs
11-03 16:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp is a valid Ubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp is a valid Ubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp is a valid Kubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp is a valid Kubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp is a valid Mythbuntu CD
11-03 16:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp is a valid Mythbuntu CD
11-03 16:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp is a valid Edubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp is a valid Edubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp is a valid Lubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp is a valid Lubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-03 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-03 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-03 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-03 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-03 16:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-03 16:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:05 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-03 16:05 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:05 INFO   root: Running the uninstaller...
11-03 16:05 INFO   CommonBackend: This is the uninstaller running
11-03 16:05 DEBUG  WindowsFrontend: __init__...
11-03 16:05 DEBUG  WindowsFrontend: on_init...
11-03 16:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\translations, languages=['en_US', 'en']
11-03 16:05 INFO   root: === wubi 12.10 rev273 ===
11-03 16:05 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
11-03 16:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-03 16:05 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\data
11-03 16:05 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\bin\7z.exe
11-03 16:05 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-03 16:05 DEBUG  CommonBackend: Fetching basic info...
11-03 16:05 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-03 16:05 DEBUG  CommonBackend: platform=win32
11-03 16:05 DEBUG  CommonBackend: osname=nt
11-03 16:05 DEBUG  CommonBackend: language=en_US
11-03 16:05 DEBUG  CommonBackend: encoding=cp1252
11-03 16:05 DEBUG  WindowsBackend: arch=amd64
11-03 16:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\data\isolist.ini
11-03 16:05 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-03 16:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 16:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 16:05 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-03 16:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 16:05 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-03 16:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 16:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 16:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 16:05 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-03 16:05 DEBUG  WindowsBackend: Fetching host info...
11-03 16:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 16:05 DEBUG  WindowsBackend: windows version=vista
11-03 16:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 16:05 DEBUG  WindowsBackend: windows_sp=Service Pack 1
11-03 16:05 DEBUG  WindowsBackend: windows_build=7601
11-03 16:05 DEBUG  WindowsBackend: gmt=5
11-03 16:05 DEBUG  WindowsBackend: country=US
11-03 16:05 DEBUG  WindowsBackend: timezone=America/New_York
11-03 16:05 DEBUG  WindowsBackend: windows_username=sandesh
11-03 16:05 DEBUG  WindowsBackend: user_full_name=sandesh
11-03 16:05 DEBUG  WindowsBackend: user_directory=
11-03 16:05 DEBUG  WindowsBackend: windows_language_code=1033
11-03 16:05 DEBUG  WindowsBackend: windows_language=English
11-03 16:05 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
11-03 16:05 DEBUG  WindowsBackend: bootloader=vista
11-03 16:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 34547.9921875 mb free ntfs)
11-03 16:05 DEBUG  WindowsBackend: drive=Drive(C: hd 34547.9921875 mb free ntfs)
11-03 16:05 DEBUG  WindowsBackend: drive=Drive(D: hd 85117.3632813 mb free ntfs)
11-03 16:05 DEBUG  WindowsBackend: drive=Drive(E: hd 59238.9140625 mb free ntfs)
11-03 16:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 16:05 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
11-03 16:05 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
11-03 16:05 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
11-03 16:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-03 16:05 DEBUG  WindowsBackend: keyboard_id=67699721
11-03 16:05 DEBUG  WindowsBackend: keyboard_layout=us
11-03 16:05 DEBUG  WindowsBackend: keyboard_variant=
11-03 16:05 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-03 16:05 DEBUG  CommonBackend: locale=en_US.UTF-8
11-03 16:05 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
11-03 16:05 DEBUG  CommonBackend: Searching ISOs on USB devices
11-03 16:05 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
11-03 16:05 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
11-03 16:06 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
11-03 16:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
11-03 16:06 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
11-03 16:06 DEBUG  CommonBackend: Searching for local CDs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 INFO   root: Already installed, running the uninstaller...
11-03 16:06 INFO   root: Running the uninstaller...
11-03 16:06 INFO   CommonBackend: This is the uninstaller running
11-03 16:06 DEBUG  WindowsFrontend: __init__...
11-03 16:06 DEBUG  WindowsFrontend: on_init...
11-03 16:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\translations, languages=['en_US', 'en']
11-03 16:06 INFO   root: Received settings
11-03 16:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\translations, languages=['en_US', 'en']
11-03 16:06 DEBUG  TaskList: # Running tasklist...
11-03 16:06 DEBUG  TaskList: ## Running Remove bootloader entry...
11-03 16:06 DEBUG  WindowsBackend: Could not find bcd id
11-03 16:06 DEBUG  WindowsBackend: undo_bootini C:
11-03 16:06 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 34547.9921875 mb free ntfs)
11-03 16:06 DEBUG  WindowsBackend: undo_bootini D:
11-03 16:06 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 85117.3632813 mb free ntfs)
11-03 16:06 DEBUG  WindowsBackend: undo_bootini E:
11-03 16:06 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 59238.9140625 mb free ntfs)
11-03 16:06 DEBUG  WindowsBackend: undo_bootini M:
11-03 16:06 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
11-03 16:06 DEBUG  TaskList: ## Finished Remove bootloader entry
11-03 16:06 DEBUG  TaskList: ## Running Remove target dir...
11-03 16:06 DEBUG  CommonBackend: Deleting D:\ubuntu
11-03 16:06 DEBUG  TaskList: ## Finished Remove target dir
11-03 16:06 DEBUG  TaskList: ## Running Remove registry key...
11-03 16:06 DEBUG  TaskList: ## Finished Remove registry key
11-03 16:06 DEBUG  TaskList: # Finished tasklist
11-03 16:06 INFO   root: Almost finished uninstalling
11-03 16:06 INFO   root: Finished uninstallation
11-03 16:06 DEBUG  CommonBackend: Fetching basic info...
11-03 16:06 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-03 16:06 DEBUG  CommonBackend: platform=win32
11-03 16:06 DEBUG  CommonBackend: osname=nt
11-03 16:06 DEBUG  WindowsBackend: arch=amd64
11-03 16:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\data\isolist.ini
11-03 16:06 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-03 16:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-03 16:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-03 16:06 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-03 16:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-03 16:06 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-03 16:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-03 16:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-03 16:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-03 16:06 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-03 16:06 DEBUG  WindowsBackend: Fetching host info...
11-03 16:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-03 16:06 DEBUG  WindowsBackend: windows version=vista
11-03 16:06 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-03 16:06 DEBUG  WindowsBackend: windows_sp=Service Pack 1
11-03 16:06 DEBUG  WindowsBackend: windows_build=7601
11-03 16:06 DEBUG  WindowsBackend: gmt=5
11-03 16:06 DEBUG  WindowsBackend: country=US
11-03 16:06 DEBUG  WindowsBackend: timezone=America/New_York
11-03 16:06 DEBUG  WindowsBackend: windows_username=sandesh
11-03 16:06 DEBUG  WindowsBackend: user_full_name=sandesh
11-03 16:06 DEBUG  WindowsBackend: user_directory=
11-03 16:06 DEBUG  WindowsBackend: windows_language_code=1033
11-03 16:06 DEBUG  WindowsBackend: windows_language=English
11-03 16:06 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
11-03 16:06 DEBUG  WindowsBackend: bootloader=vista
11-03 16:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 34339.1523438 mb free ntfs)
11-03 16:06 DEBUG  WindowsBackend: drive=Drive(C: hd 34339.1523438 mb free ntfs)
11-03 16:06 DEBUG  WindowsBackend: drive=Drive(D: hd 85894.3046875 mb free ntfs)
11-03 16:06 DEBUG  WindowsBackend: drive=Drive(E: hd 59305.9492188 mb free ntfs)
11-03 16:06 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-03 16:06 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
11-03 16:06 DEBUG  WindowsBackend: uninstaller_path=None
11-03 16:06 DEBUG  WindowsBackend: previous_target_dir=None
11-03 16:06 DEBUG  WindowsBackend: previous_distro_name=None
11-03 16:06 DEBUG  WindowsBackend: keyboard_id=67699721
11-03 16:06 DEBUG  WindowsBackend: keyboard_layout=us
11-03 16:06 DEBUG  WindowsBackend: keyboard_variant=
11-03 16:06 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
11-03 16:06 DEBUG  CommonBackend: Checking pre-specified ISO D:\ubuntu-12.10-desktop-i386.iso
11-03 16:06 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
11-03 16:06 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
11-03 16:06 DEBUG  CommonBackend: Searching for local CDs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-03 16:06 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-03 16:06 INFO   root: Running the installer...
11-03 16:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\translations, languages=['en_US', 'en']
11-03 16:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl191F.tmp\translations, languages=['en_US', 'en']
11-03 16:06 INFO   WindowsFrontend: Operation cancelled
11-03 16:06 DEBUG  WindowsFrontend: frontend.quit
11-03 16:06 DEBUG  WindowsFrontend: frontend.on_quit
11-03 16:06 DEBUG  root: application.on_quit
11-03 16:06 INFO   root: sys.exit
11-03 16:07 INFO   root: Received settings
11-03 16:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\translations, languages=['en_US', 'en']
11-03 16:07 DEBUG  TaskList: # Running tasklist...
11-03 16:07 DEBUG  TaskList: ## Running Remove bootloader entry...
11-03 16:07 DEBUG  WindowsBackend: Could not find bcd id
11-03 16:07 DEBUG  WindowsBackend: undo_bootini C:
11-03 16:07 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 34576.7421875 mb free ntfs)
11-03 16:07 DEBUG  WindowsBackend: undo_bootini D:
11-03 16:07 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 85117.3632813 mb free ntfs)
11-03 16:07 DEBUG  WindowsBackend: undo_bootini E:
11-03 16:07 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 59225.6679688 mb free ntfs)
11-03 16:07 DEBUG  WindowsBackend: undo_bootini M:
11-03 16:07 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
11-03 16:07 DEBUG  TaskList: ## Finished Remove bootloader entry
11-03 16:07 DEBUG  TaskList: ## Running Remove target dir...
11-03 16:07 DEBUG  CommonBackend: Cannot find D:\ubuntu
11-03 16:07 DEBUG  TaskList: ## Finished Remove target dir
11-03 16:07 DEBUG  TaskList: ## Running Remove registry key...
11-03 16:07 ERROR  registry: Cannot delete registry key Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
[Errno 2] The system cannot find the file specified
Traceback (most recent call last):
  File "\lib\wubi\backends\win32\registry.py", line 56, in delete_key
WindowsError: [Errno 2] The system cannot find the file specified
11-03 16:07 DEBUG  TaskList: ## Finished Remove registry key
11-03 16:07 DEBUG  TaskList: # Finished tasklist
11-03 16:07 INFO   root: Almost finished uninstalling
11-03 16:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylF7AA.tmp\translations, languages=['en_US', 'en']
11-03 16:07 INFO   root: Finished uninstallation
11-03 16:07 DEBUG  root: application.quit
11-03 16:07 DEBUG  WindowsFrontend: frontend.quit
11-03 16:07 DEBUG  WindowsFrontend: frontend.on_quit
11-03 16:07 DEBUG  root: application.on_quit
11-03 16:07 INFO   root: sys.exit
11-03 16:07 INFO   root: Received settings
11-03 16:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\translations, languages=['en_US', 'en']
11-03 16:07 DEBUG  TaskList: # Running tasklist...
11-03 16:07 DEBUG  TaskList: ## Running Remove bootloader entry...
11-03 16:07 DEBUG  WindowsBackend: Could not find bcd id
11-03 16:07 DEBUG  WindowsBackend: undo_bootini C:
11-03 16:07 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 34587.2890625 mb free ntfs)
11-03 16:07 DEBUG  WindowsBackend: undo_bootini D:
11-03 16:07 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 85117.3632813 mb free ntfs)
11-03 16:07 DEBUG  WindowsBackend: undo_bootini E:
11-03 16:07 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 59229.6171875 mb free ntfs)
11-03 16:07 DEBUG  WindowsBackend: undo_bootini M:
11-03 16:07 DEBUG  WindowsBackend: undo_configsys Drive(M: removable 0.0 mb free )
11-03 16:07 DEBUG  TaskList: ## Finished Remove bootloader entry
11-03 16:07 DEBUG  TaskList: ## Running Remove target dir...
11-03 16:07 DEBUG  CommonBackend: Cannot find D:\ubuntu
11-03 16:07 DEBUG  TaskList: ## Finished Remove target dir
11-03 16:07 DEBUG  TaskList: ## Running Remove registry key...
11-03 16:07 ERROR  registry: Cannot delete registry key Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
[Errno 2] The system cannot find the file specified
Traceback (most recent call last):
  File "\lib\wubi\backends\win32\registry.py", line 56, in delete_key
WindowsError: [Errno 2] The system cannot find the file specified
11-03 16:07 DEBUG  TaskList: ## Finished Remove registry key
11-03 16:07 DEBUG  TaskList: # Finished tasklist
11-03 16:07 INFO   root: Almost finished uninstalling
11-03 16:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pylBA8B.tmp\translations, languages=['en_US', 'en']
11-03 16:07 INFO   root: Finished uninstallation
11-03 16:07 DEBUG  root: application.quit
11-03 16:07 DEBUG  WindowsFrontend: frontend.quit
11-03 16:07 DEBUG  WindowsFrontend: frontend.on_quit
11-03 16:07 DEBUG  root: application.on_quit
11-03 16:07 INFO   root: sys.exit
11-16 13:43 INFO   root: === wubi 12.10 rev273 ===
11-16 13:43 DEBUG  root: Logfile is c:\users\sandesh\appdata\local\temp\wubi-12.10-rev273.log
11-16 13:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
11-16 13:43 DEBUG  CommonBackend: data_dir=C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\data
11-16 13:43 DEBUG  WindowsBackend: 7z=C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\bin\7z.exe
11-16 13:43 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-16 13:43 DEBUG  CommonBackend: Fetching basic info...
11-16 13:43 DEBUG  CommonBackend: original_exe=D:\wubi.exe
11-16 13:43 DEBUG  CommonBackend: platform=win32
11-16 13:43 DEBUG  CommonBackend: osname=nt
11-16 13:43 DEBUG  CommonBackend: language=en_US
11-16 13:43 DEBUG  CommonBackend: encoding=cp1252
11-16 13:43 DEBUG  WindowsBackend: arch=amd64
11-16 13:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\data\isolist.ini
11-16 13:43 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-16 13:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-16 13:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-16 13:43 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-16 13:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-16 13:43 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-16 13:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-16 13:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-16 13:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-16 13:43 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-16 13:43 DEBUG  WindowsBackend: Fetching host info...
11-16 13:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-16 13:43 DEBUG  WindowsBackend: windows version=vista
11-16 13:43 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
11-16 13:43 DEBUG  WindowsBackend: windows_sp=Service Pack 1
11-16 13:43 DEBUG  WindowsBackend: windows_build=7601
11-16 13:43 DEBUG  WindowsBackend: gmt=5
11-16 13:43 DEBUG  WindowsBackend: country=US
11-16 13:43 DEBUG  WindowsBackend: timezone=America/New_York
11-16 13:43 DEBUG  WindowsBackend: windows_username=sandesh
11-16 13:43 DEBUG  WindowsBackend: user_full_name=sandesh
11-16 13:43 DEBUG  WindowsBackend: user_directory=
11-16 13:43 DEBUG  WindowsBackend: windows_language_code=1033
11-16 13:43 DEBUG  WindowsBackend: windows_language=English
11-16 13:43 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3-2350M CPU @ 2.30GHz
11-16 13:43 DEBUG  WindowsBackend: bootloader=vista
11-16 13:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29475.90625 mb free ntfs)
11-16 13:43 DEBUG  WindowsBackend: drive=Drive(C: hd 29475.90625 mb free ntfs)
11-16 13:43 DEBUG  WindowsBackend: drive=Drive(D: hd 41031.65625 mb free ntfs)
11-16 13:43 DEBUG  WindowsBackend: drive=Drive(E: hd 46903.1132813 mb free ntfs)
11-16 13:43 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-16 13:43 DEBUG  WindowsBackend: drive=Drive(G: hd 136595.992188 mb free ntfs)
11-16 13:43 DEBUG  WindowsBackend: drive=Drive(M: removable 0.0 mb free )
11-16 13:43 DEBUG  WindowsBackend: uninstaller_path=None
11-16 13:43 DEBUG  WindowsBackend: previous_target_dir=None
11-16 13:43 DEBUG  WindowsBackend: previous_distro_name=None
11-16 13:43 DEBUG  WindowsBackend: keyboard_id=67699721
11-16 13:43 DEBUG  WindowsBackend: keyboard_layout=us
11-16 13:43 DEBUG  WindowsBackend: keyboard_variant=
11-16 13:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-16 13:43 DEBUG  CommonBackend: locale=en_US.UTF-8
11-16 13:43 DEBUG  WindowsBackend: total_memory_mb=1950.2734375
11-16 13:43 DEBUG  CommonBackend: Searching ISOs on USB devices
11-16 13:43 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
11-16 13:43 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu-12.10-desktop-i386.iso
11-16 13:43 DEBUG  Distro:   parsing info from str=Ubuntu 12.10 "Quantal Quetzal" - Release i386 (20121017.2)
11-16 13:43 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.10', 'build': '20121017.2', 'codename': 'Quantal Quetzal', 'arch': 'i386'}
11-16 13:43 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
11-16 13:43 DEBUG  CommonBackend: Searching for local CDs
11-16 13:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp is a valid Ubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp is a valid Ubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp is a valid Kubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp is a valid Kubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp is a valid Mythbuntu CD
11-16 13:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp is a valid Mythbuntu CD
11-16 13:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp is a valid Edubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp is a valid Edubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp is a valid Lubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp is a valid Lubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-16 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-16 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-16 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-16 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-16 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-16 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-16 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-16 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-16 13:43 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
11-16 13:43 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether M:\ is a valid Edubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-16 13:43 DEBUG  Distro:   checking whether M:\ is a valid Lubuntu CD
11-16 13:43 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-16 13:43 INFO   root: Running the installer...
11-16 13:43 DEBUG  WindowsFrontend: __init__...
11-16 13:43 DEBUG  WindowsFrontend: on_init...
11-16 13:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\translations, languages=['en_US', 'en']
11-16 13:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\translations, languages=['en_US', 'en']
11-16 13:44 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sandesh
11-16 13:44 INFO   root: Received settings
11-16 13:44 DEBUG  CommonBackend: Searching for local CD
11-16 13:44 DEBUG  Distro:   checking whether C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp is a valid Ubuntu CD
11-16 13:44 DEBUG  Distro:     does not contain C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\casper\filesystem.squashfs
11-16 13:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-16 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-16 13:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-16 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-16 13:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-16 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-16 13:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-16 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-16 13:44 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
11-16 13:44 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
11-16 13:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\translations, languages=['en_US', 'en']
11-16 13:44 DEBUG  TaskList: # Running tasklist...
11-16 13:44 DEBUG  TaskList: ## Running select_target_dir...
11-16 13:44 INFO   WindowsBackend: Installing into D:\ubuntu
11-16 13:44 DEBUG  TaskList: ## Finished select_target_dir
11-16 13:44 DEBUG  TaskList: ## Running create_dir_structure...
11-16 13:44 DEBUG  CommonBackend: Creating dir D:\ubuntu
11-16 13:44 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
11-16 13:44 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
11-16 13:44 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
11-16 13:44 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
11-16 13:44 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
11-16 13:44 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
11-16 13:44 DEBUG  TaskList: ## Finished create_dir_structure
11-16 13:44 DEBUG  TaskList: ## Running uncompress_target_dir...
11-16 13:44 DEBUG  TaskList: ## Finished uncompress_target_dir
11-16 13:44 DEBUG  TaskList: ## Running create_uninstaller...
11-16 13:44 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
11-16 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
11-16 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
11-16 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-16 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
11-16 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
11-16 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-16 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-16 13:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-16 13:44 DEBUG  TaskList: ## Finished create_uninstaller
11-16 13:44 DEBUG  TaskList: ## Running copy_installation_files...
11-16 13:44 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
11-16 13:44 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\winboot -> D:\ubuntu\winboot
11-16 13:44 DEBUG  WindowsBackend: Copying C:\Users\sandesh\AppData\Local\Temp\pyl3D80.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
11-16 13:44 DEBUG  TaskList: ## Finished copy_installation_files
11-16 13:44 DEBUG  TaskList: ## Running get_iso...
11-16 13:44 DEBUG  CommonBackend: Trying to use pre-specified ISO D:\ubuntu-12.10-desktop-i386.iso
11-16 13:44 DEBUG  TaskList: New task is_valid_iso
11-16 13:44 DEBUG  TaskList: ### Running is_valid_iso...
11-16 13:44 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
11-16 13:44 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
11-16 13:44 DEBUG  TaskList: ### Finished is_valid_iso
11-16 13:44 DEBUG  TaskList: New task check_iso
11-16 13:44 DEBUG  TaskList: ### Running check_iso...
11-16 13:44 DEBUG  CommonBackend: Checking D:\ubuntu-12.10-desktop-i386.iso
11-16 13:44 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu-12.10-desktop-i386.iso
11-16 13:44 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu-12.10-desktop-i386.iso
11-16 13:44 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
11-16 13:44 DEBUG  TaskList: New task get_metalink
11-16 13:44 DEBUG  TaskList: #### Running get_metalink...
11-16 13:44 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) > D:\ubuntu\install
11-16 13:44 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink](http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10060, 'Operation timed out')>
11-16 13:44 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) > D:\ubuntu\install
11-16 13:44 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/quantal-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (10065, 'No route to host')>
11-16 13:44 DEBUG  TaskList: #### Finished get_metalink
11-16 13:44 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for D:\ubuntu-12.10-desktop-i386.iso, ignoring
11-16 13:44 DEBUG  TaskList: ### Finished check_iso
11-16 13:44 DEBUG  TaskList: New task copy_file
11-16 13:44 DEBUG  CommonBackend: Copying D:\ubuntu-12.10-desktop-i386.iso > D:\ubuntu\install\installation.iso
11-16 13:44 DEBUG  TaskList: ### Running copy_file...
11-16 13:45 DEBUG  TaskList: ### Finished copy_file
11-16 13:45 DEBUG  TaskList: ## Finished get_iso
11-16 13:45 DEBUG  TaskList: ## Running extract_kernel...
11-16 13:45 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\installation.iso
11-16 13:45 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\installation.iso
11-16 13:45 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\installation.iso
11-16 13:45 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\installation.iso
11-16 13:45 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
11-16 13:45 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
11-16 13:45 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = dedeef44f082210eb0d605d21837feb5 == dedeef44f082210eb0d605d21837feb5
11-16 13:45 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
11-16 13:45 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = bf4099046c27293af1f7ec8c76baf1c7 == bf4099046c27293af1f7ec8c76baf1c7
11-16 13:45 DEBUG  TaskList: ## Finished extract_kernel
11-16 13:45 DEBUG  TaskList: ## Running choose_disk_sizes...
11-16 13:45 DEBUG  WindowsBackend: total size=10000
  root=9744
  swap=256
  home=0
  usr=0
11-16 13:45 DEBUG  TaskList: ## Finished choose_disk_sizes
11-16 13:45 DEBUG  TaskList: ## Running create_preseed...
11-16 13:45 DEBUG  TaskList: ## Finished create_preseed
11-16 13:45 DEBUG  TaskList: ## Running modify_bootloader...
11-16 13:45 DEBUG  TaskList: New task modify_bcd
11-16 13:45 DEBUG  TaskList: ### Running modify_bcd...
11-16 13:45 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 29475.90625 mb free ntfs)
11-16 13:45 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa57-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa57-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
11-16 13:45 DEBUG  TaskList: # Cancelling tasklist
11-16 13:45 DEBUG  TaskList: New task modify_bcd
11-16 13:45 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa57-4ca4-11e1-853b-984507711b55} device partition=D:
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
>>command=C:\Windows\System32\bcdedit.exe /set {bb4afa57-4ca4-11e1-853b-984507711b55} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
11-16 13:45 DEBUG  TaskList: New task modify_bcd
11-16 13:45 DEBUG  TaskList: New task modify_bcd
11-16 13:45 DEBUG  TaskList: New task modify_bcd
11-16 13:45 DEBUG  TaskList: ## Finished modify_bootloader
11-16 13:45 DEBUG  TaskList: # Finished tasklist

---

### Post by bcbc on 2012-11-16
D: is a dynamic drive? You can't install wubi on it. (And ubuntu doesn't recognize dynamic drives so even if you can install it on C: or as a normal dual boot, you shouldn't). First convert from dynamic. This is not straightforward and Windows does not provide a way (other than deleting and recreating partitions). Some other partitioning tools can do it.

---

### Post by coolguysraju on 2012-11-16
thanks for the reply
but all drive of my laptop is dynamic,how to make drive compatible for linux

---

### Post by bcbc on 2012-11-16
See [http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)

or [http://ubuntuforums.org/showthread.php?t=1965823](http://ubuntuforums.org/showthread.php?t=1965823)

---

