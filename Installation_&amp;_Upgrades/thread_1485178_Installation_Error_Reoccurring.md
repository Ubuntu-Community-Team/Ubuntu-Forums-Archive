---
title: "Installation Error Reoccurring"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by furqanbhai on 2010-05-16
Hi guys... please need a permanent fix on this. I have been using Ubuntu since 8.04 and I encountered this problem only in 9.10 and now in 10.04 as well. I get an error and a file named "wubi-10.04-rev189" is generated in my temp folder. I am attaching the log file as well as the error snap. Please give me a permanent fix which will also help me in future versions as well. Thanks a Million in advance to you guys out there.




Sorry cant attach - Size too big





05-16 02:45 INFO   root: === wubi 10.04 rev189 ===
05-16 02:45 DEBUG  root: Logfile is c:\docume~1\furqan\locals~1\temp\wubi-10.04-rev189.log
05-16 02:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
05-16 02:45 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp\data
05-16 02:45 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp\bin\7z.exe
05-16 02:45 DEBUG  CommonBackend: Fetching basic info...
05-16 02:45 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
05-16 02:45 DEBUG  CommonBackend: platform=win32
05-16 02:45 DEBUG  CommonBackend: osname=nt
05-16 02:45 DEBUG  CommonBackend: language=en_US
05-16 02:45 DEBUG  CommonBackend: encoding=cp1252
05-16 02:45 DEBUG  WindowsBackend: arch=amd64
05-16 02:45 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp\data\isolist.ini
05-16 02:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 02:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 02:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 02:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 02:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 02:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 02:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 02:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 02:45 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-16 02:45 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 02:45 DEBUG  WindowsBackend: Fetching host info...
05-16 02:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 02:45 DEBUG  WindowsBackend: windows version=xp
05-16 02:45 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-16 02:45 DEBUG  WindowsBackend: windows_sp=Service Pack 2
05-16 02:45 DEBUG  WindowsBackend: windows_build=2600
05-16 02:45 DEBUG  WindowsBackend: gmt=5
05-16 02:45 DEBUG  WindowsBackend: country=US
05-16 02:45 DEBUG  WindowsBackend: timezone=America/New_York
05-16 02:45 DEBUG  WindowsBackend: windows_username=Furqan
05-16 02:45 DEBUG  WindowsBackend: user_full_name=Furqan
05-16 02:45 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Furqan
05-16 02:45 DEBUG  WindowsBackend: windows_language_code=1033
05-16 02:45 DEBUG  WindowsBackend: windows_language=English
05-16 02:45 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E4600  @ 2.40GHz
05-16 02:45 DEBUG  WindowsBackend: bootloader=xp
05-16 02:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 17459.0429688 mb free ntfs)
05-16 02:45 DEBUG  WindowsBackend: drive=Drive(C: hd 17459.0429688 mb free ntfs)
05-16 02:45 DEBUG  WindowsBackend: drive=Drive(D: hd 14593.2929688 mb free ntfs)
05-16 02:45 DEBUG  WindowsBackend: drive=Drive(E: hd 14858.4570313 mb free ntfs)
05-16 02:45 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-16 02:45 DEBUG  WindowsBackend: uninstaller_path=None
05-16 02:45 DEBUG  WindowsBackend: previous_target_dir=None
05-16 02:45 DEBUG  WindowsBackend: previous_distro_name=None
05-16 02:45 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 02:45 DEBUG  WindowsBackend: keyboard_layout=us
05-16 02:45 DEBUG  WindowsBackend: keyboard_variant=
05-16 02:45 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-16 02:45 DEBUG  CommonBackend: locale=en_US.UTF-8
05-16 02:45 DEBUG  WindowsBackend: total_memory_mb=895.16796875
05-16 02:45 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 02:45 DEBUG  CommonBackend: Searching for local CDs
05-16 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp is a valid Ubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp is a valid Ubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp is a valid Ubuntu Netbook CD
05-16 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp is a valid Kubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp is a valid Kubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp is a valid Kubuntu Netbook CD
05-16 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp is a valid Xubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp is a valid Xubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp is a valid Mythbuntu CD
05-16 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp is a valid Mythbuntu CD
05-16 02:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl55.tmp\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-16 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 02:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-16 02:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-16 02:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 02:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 02:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-16 02:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
05-16 02:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-16 02:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-16 02:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 02:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-16 02:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 02:45 INFO   root: Running the uninstaller...
05-16 02:45 ERROR  root: No previous target dir found, exiting
05-16 02:45 DEBUG  root: application.quit
05-16 02:45 DEBUG  root: application.on_quit
05-16 02:45 INFO   root: sys.exit
05-16 02:45 INFO   root: Quitting application
05-16 11:45 INFO   root: === wubi 10.04 rev189 ===
05-16 11:45 DEBUG  root: Logfile is c:\docume~1\furqan\locals~1\temp\wubi-10.04-rev189.log
05-16 11:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
05-16 11:45 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\data
05-16 11:45 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\bin\7z.exe
05-16 11:45 DEBUG  CommonBackend: Fetching basic info...
05-16 11:45 DEBUG  CommonBackend: original_exe=F:\wubi.exe
05-16 11:45 DEBUG  CommonBackend: platform=win32
05-16 11:45 DEBUG  CommonBackend: osname=nt
05-16 11:45 DEBUG  CommonBackend: language=en_US
05-16 11:45 DEBUG  CommonBackend: encoding=cp1252
05-16 11:45 DEBUG  WindowsBackend: arch=amd64
05-16 11:45 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\data\isolist.ini
05-16 11:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 11:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 11:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 11:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 11:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 11:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 11:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 11:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 11:45 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-16 11:45 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 11:45 DEBUG  WindowsBackend: Fetching host info...
05-16 11:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 11:45 DEBUG  WindowsBackend: windows version=xp
05-16 11:45 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-16 11:45 DEBUG  WindowsBackend: windows_sp=Service Pack 2
05-16 11:45 DEBUG  WindowsBackend: windows_build=2600
05-16 11:45 DEBUG  WindowsBackend: gmt=5
05-16 11:45 DEBUG  WindowsBackend: country=US
05-16 11:45 DEBUG  WindowsBackend: timezone=America/New_York
05-16 11:45 DEBUG  WindowsBackend: windows_username=Furqan
05-16 11:45 DEBUG  WindowsBackend: user_full_name=Furqan
05-16 11:45 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Furqan
05-16 11:45 DEBUG  WindowsBackend: windows_language_code=1033
05-16 11:45 DEBUG  WindowsBackend: windows_language=English
05-16 11:45 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E4600  @ 2.40GHz
05-16 11:45 DEBUG  WindowsBackend: bootloader=xp
05-16 11:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 15522.8789063 mb free ntfs)
05-16 11:45 DEBUG  WindowsBackend: drive=Drive(C: hd 15522.8789063 mb free ntfs)
05-16 11:45 DEBUG  WindowsBackend: drive=Drive(D: hd 15292.3789063 mb free ntfs)
05-16 11:45 DEBUG  WindowsBackend: drive=Drive(E: hd 16935.140625 mb free ntfs)
05-16 11:45 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-16 11:45 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
05-16 11:45 DEBUG  WindowsBackend: uninstaller_path=None
05-16 11:45 DEBUG  WindowsBackend: previous_target_dir=None
05-16 11:45 DEBUG  WindowsBackend: previous_distro_name=None
05-16 11:45 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 11:45 DEBUG  WindowsBackend: keyboard_layout=us
05-16 11:45 DEBUG  WindowsBackend: keyboard_variant=
05-16 11:45 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-16 11:45 DEBUG  CommonBackend: locale=en_US.UTF-8
05-16 11:45 DEBUG  WindowsBackend: total_memory_mb=895.16796875
05-16 11:45 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 11:45 DEBUG  CommonBackend: Searching for local CDs
05-16 11:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp is a valid Ubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp is a valid Ubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp is a valid Ubuntu Netbook CD
05-16 11:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp is a valid Kubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp is a valid Kubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp is a valid Kubuntu Netbook CD
05-16 11:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp is a valid Xubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp is a valid Xubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp is a valid Mythbuntu CD
05-16 11:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp is a valid Mythbuntu CD
05-16 11:45 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 11:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-16 11:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 11:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 11:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-16 11:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-16 11:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 11:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 11:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 11:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 11:45 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
05-16 11:45 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
05-16 11:45 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-16 11:45 INFO   root: Running the CD menu...
05-16 11:45 DEBUG  WindowsFrontend: __init__...
05-16 11:45 DEBUG  WindowsFrontend: on_init...
05-16 11:45 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\translations, languages=['en_US', 'en']
05-16 11:45 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\translations, languages=['en_US', 'en']
05-16 11:45 INFO   root: CD menu finished
05-16 11:45 INFO   root: Running the installer...
05-16 11:45 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\translations, languages=['en_US', 'en']
05-16 11:45 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\translations, languages=['en_US', 'en']
05-16 11:46 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=9000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=mohammed
05-16 11:46 INFO   root: Received settings
05-16 11:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\translations, languages=['en_US', 'en']
05-16 11:46 DEBUG  TaskList: # Running tasklist...
05-16 11:46 DEBUG  TaskList: ## Running select_target_dir...
05-16 11:46 INFO   WindowsBackend: Installing into D:\ubuntu
05-16 11:46 DEBUG  TaskList: ## Finished select_target_dir
05-16 11:46 DEBUG  TaskList: ## Running create_dir_structure...
05-16 11:46 DEBUG  CommonBackend: Creating dir D:\ubuntu
05-16 11:46 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
05-16 11:46 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
05-16 11:46 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
05-16 11:46 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
05-16 11:46 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
05-16 11:46 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
05-16 11:46 DEBUG  TaskList: ## Finished create_dir_structure
05-16 11:46 DEBUG  TaskList: ## Running uncompress_target_dir...
05-16 11:46 DEBUG  TaskList: ## Finished uncompress_target_dir
05-16 11:46 DEBUG  TaskList: ## Running create_uninstaller...
05-16 11:46 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
05-16 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
05-16 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
05-16 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-16 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
05-16 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
05-16 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-16 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-16 11:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-16 11:46 DEBUG  TaskList: ## Finished create_uninstaller
05-16 11:46 DEBUG  TaskList: ## Running copy_installation_files...
05-16 11:46 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
05-16 11:46 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\winboot -> D:\ubuntu\winboot
05-16 11:46 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B7.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
05-16 11:46 DEBUG  TaskList: ## Finished copy_installation_files
05-16 11:46 DEBUG  TaskList: ## Running get_iso...
05-16 11:46 DEBUG  TaskList: New task copy_file
05-16 11:46 DEBUG  TaskList: ### Running copy_file...
05-16 11:48 DEBUG  TaskList: ### Finished copy_file
05-16 11:48 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
05-16 11:48 DEBUG  TaskList: # Cancelling tasklist
05-16 11:48 DEBUG  TaskList: New task check_iso
05-16 11:48 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
05-16 11:48 DEBUG  CommonBackend: Searching for local ISO
05-16 11:48 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-16 11:48 DEBUG  TaskList: New task get_metalink
05-16 11:48 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-16 11:48 DEBUG  TaskList: # Cancelling tasklist
05-16 11:48 DEBUG  TaskList: # Finished tasklist
05-16 11:50 INFO   root: === wubi 10.04 rev189 ===
05-16 11:50 DEBUG  root: Logfile is c:\docume~1\furqan\locals~1\temp\wubi-10.04-rev189.log
05-16 11:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
05-16 11:50 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\data
05-16 11:50 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\bin\7z.exe
05-16 11:50 DEBUG  CommonBackend: Fetching basic info...
05-16 11:50 DEBUG  CommonBackend: original_exe=F:\wubi.exe
05-16 11:50 DEBUG  CommonBackend: platform=win32
05-16 11:50 DEBUG  CommonBackend: osname=nt
05-16 11:50 DEBUG  CommonBackend: language=en_US
05-16 11:50 DEBUG  CommonBackend: encoding=cp1252
05-16 11:50 DEBUG  WindowsBackend: arch=amd64
05-16 11:50 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\data\isolist.ini
05-16 11:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 11:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 11:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 11:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 11:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 11:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 11:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 11:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 11:50 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-16 11:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 11:50 DEBUG  WindowsBackend: Fetching host info...
05-16 11:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 11:50 DEBUG  WindowsBackend: windows version=xp
05-16 11:50 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-16 11:50 DEBUG  WindowsBackend: windows_sp=Service Pack 2
05-16 11:50 DEBUG  WindowsBackend: windows_build=2600
05-16 11:50 DEBUG  WindowsBackend: gmt=5
05-16 11:50 DEBUG  WindowsBackend: country=US
05-16 11:50 DEBUG  WindowsBackend: timezone=America/New_York
05-16 11:50 DEBUG  WindowsBackend: windows_username=Furqan
05-16 11:50 DEBUG  WindowsBackend: user_full_name=Furqan
05-16 11:50 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Furqan
05-16 11:50 DEBUG  WindowsBackend: windows_language_code=1033
05-16 11:50 DEBUG  WindowsBackend: windows_language=English
05-16 11:50 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E4600  @ 2.40GHz
05-16 11:50 DEBUG  WindowsBackend: bootloader=xp
05-16 11:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 15522.8398438 mb free ntfs)
05-16 11:50 DEBUG  WindowsBackend: drive=Drive(C: hd 15522.8398438 mb free ntfs)
05-16 11:50 DEBUG  WindowsBackend: drive=Drive(D: hd 14591.828125 mb free ntfs)
05-16 11:50 DEBUG  WindowsBackend: drive=Drive(E: hd 16935.140625 mb free ntfs)
05-16 11:50 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-16 11:50 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
05-16 11:50 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
05-16 11:50 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
05-16 11:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-16 11:50 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 11:50 DEBUG  WindowsBackend: keyboard_layout=us
05-16 11:50 DEBUG  WindowsBackend: keyboard_variant=
05-16 11:50 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-16 11:50 DEBUG  CommonBackend: locale=en_US.UTF-8
05-16 11:50 DEBUG  WindowsBackend: total_memory_mb=895.16796875
05-16 11:50 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 11:50 DEBUG  CommonBackend: Searching for local CDs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Ubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Ubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Ubuntu Netbook CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Kubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Kubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Kubuntu Netbook CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Xubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Xubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Mythbuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Mythbuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 11:50 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
05-16 11:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
05-16 11:50 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-16 11:50 INFO   root: Running the CD menu...
05-16 11:50 DEBUG  WindowsFrontend: __init__...
05-16 11:50 DEBUG  WindowsFrontend: on_init...
05-16 11:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\translations, languages=['en_US', 'en']
05-16 11:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\translations, languages=['en_US', 'en']
05-16 11:50 INFO   root: CD menu finished
05-16 11:50 INFO   root: Already installed, running the uninstaller...
05-16 11:50 INFO   root: Running the uninstaller...
05-16 11:50 INFO   CommonBackend: This is the uninstaller running
05-16 11:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\translations, languages=['en_US', 'en']
05-16 11:50 INFO   root: Received settings
05-16 11:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\translations, languages=['en_US', 'en']
05-16 11:50 DEBUG  TaskList: # Running tasklist...
05-16 11:50 DEBUG  TaskList: ## Running Backup ISO...
05-16 11:50 DEBUG  TaskList: ## Finished Backup ISO
05-16 11:50 DEBUG  TaskList: ## Running Remove bootloader entry...
05-16 11:50 ERROR  WindowsBackend: Cannot find bcdedit
05-16 11:50 DEBUG  WindowsBackend: undo_bootini C:
05-16 11:50 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 15522.8398438 mb free ntfs)
05-16 11:50 DEBUG  WindowsBackend: undo_bootini D:
05-16 11:50 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 14591.828125 mb free ntfs)
05-16 11:50 DEBUG  WindowsBackend: undo_bootini E:
05-16 11:50 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 16935.140625 mb free ntfs)
05-16 11:50 DEBUG  TaskList: ## Finished Remove bootloader entry
05-16 11:50 DEBUG  TaskList: ## Running Remove target dir...
05-16 11:50 DEBUG  CommonBackend: Deleting D:\ubuntu
05-16 11:50 DEBUG  TaskList: ## Finished Remove target dir
05-16 11:50 DEBUG  TaskList: ## Running Remove registry key...
05-16 11:50 DEBUG  TaskList: ## Finished Remove registry key
05-16 11:50 DEBUG  TaskList: # Finished tasklist
05-16 11:50 INFO   root: Almost finished uninstalling
05-16 11:50 INFO   root: Finished uninstallation
05-16 11:50 DEBUG  CommonBackend: Fetching basic info...
05-16 11:50 DEBUG  CommonBackend: original_exe=F:\wubi.exe
05-16 11:50 DEBUG  CommonBackend: platform=win32
05-16 11:50 DEBUG  CommonBackend: osname=nt
05-16 11:50 DEBUG  WindowsBackend: arch=amd64
05-16 11:50 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\data\isolist.ini
05-16 11:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 11:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 11:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 11:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 11:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 11:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 11:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 11:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 11:50 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-16 11:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 11:50 DEBUG  WindowsBackend: Fetching host info...
05-16 11:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 11:50 DEBUG  WindowsBackend: windows version=xp
05-16 11:50 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-16 11:50 DEBUG  WindowsBackend: windows_sp=Service Pack 2
05-16 11:50 DEBUG  WindowsBackend: windows_build=2600
05-16 11:50 DEBUG  WindowsBackend: gmt=5
05-16 11:50 DEBUG  WindowsBackend: country=US
05-16 11:50 DEBUG  WindowsBackend: timezone=America/New_York
05-16 11:50 DEBUG  WindowsBackend: windows_username=Furqan
05-16 11:50 DEBUG  WindowsBackend: user_full_name=Furqan
05-16 11:50 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Furqan
05-16 11:50 DEBUG  WindowsBackend: windows_language_code=1033
05-16 11:50 DEBUG  WindowsBackend: windows_language=English
05-16 11:50 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E4600  @ 2.40GHz
05-16 11:50 DEBUG  WindowsBackend: bootloader=xp
05-16 11:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 15522.8320313 mb free ntfs)
05-16 11:50 DEBUG  WindowsBackend: drive=Drive(C: hd 15522.8320313 mb free ntfs)
05-16 11:50 DEBUG  WindowsBackend: drive=Drive(D: hd 15292.34375 mb free ntfs)
05-16 11:50 DEBUG  WindowsBackend: drive=Drive(E: hd 16935.3320313 mb free ntfs)
05-16 11:50 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-16 11:50 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
05-16 11:50 DEBUG  WindowsBackend: uninstaller_path=None
05-16 11:50 DEBUG  WindowsBackend: previous_target_dir=None
05-16 11:50 DEBUG  WindowsBackend: previous_distro_name=None
05-16 11:50 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 11:50 DEBUG  WindowsBackend: keyboard_layout=us
05-16 11:50 DEBUG  WindowsBackend: keyboard_variant=
05-16 11:50 DEBUG  WindowsBackend: total_memory_mb=895.16796875
05-16 11:50 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 11:50 DEBUG  CommonBackend: Searching for local CDs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Ubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Ubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Ubuntu Netbook CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Kubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Kubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Kubuntu Netbook CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Xubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Xubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Mythbuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp is a valid Mythbuntu CD
05-16 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 11:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 11:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 11:50 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-16 11:50 INFO   root: Running the installer...
05-16 11:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\translations, languages=['en_US', 'en']
05-16 11:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1B8.tmp\translations, languages=['en_US', 'en']
05-16 11:51 INFO   WindowsFrontend: Operation cancelled
05-16 11:51 DEBUG  WindowsFrontend: frontend.quit
05-16 11:51 DEBUG  WindowsFrontend: frontend.on_quit
05-16 11:51 DEBUG  root: application.on_quit
05-16 11:51 INFO   root: sys.exit
05-17 00:05 INFO   root: === wubi 10.04 rev189 ===
05-17 00:05 DEBUG  root: Logfile is c:\docume~1\furqan\locals~1\temp\wubi-10.04-rev189.log
05-17 00:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
05-17 00:05 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\data
05-17 00:05 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
05-17 00:05 DEBUG  CommonBackend: Fetching basic info...
05-17 00:05 DEBUG  CommonBackend: original_exe=F:\wubi.exe
05-17 00:05 DEBUG  CommonBackend: platform=win32
05-17 00:05 DEBUG  CommonBackend: osname=nt
05-17 00:05 DEBUG  CommonBackend: language=en_US
05-17 00:05 DEBUG  CommonBackend: encoding=cp1252
05-17 00:05 DEBUG  WindowsBackend: arch=amd64
05-17 00:05 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
05-17 00:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-17 00:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-17 00:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-17 00:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-17 00:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-17 00:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-17 00:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-17 00:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-17 00:05 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-17 00:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-17 00:05 DEBUG  WindowsBackend: Fetching host info...
05-17 00:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-17 00:05 DEBUG  WindowsBackend: windows version=xp
05-17 00:05 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-17 00:05 DEBUG  WindowsBackend: windows_sp=Service Pack 2
05-17 00:05 DEBUG  WindowsBackend: windows_build=2600
05-17 00:05 DEBUG  WindowsBackend: gmt=5
05-17 00:05 DEBUG  WindowsBackend: country=US
05-17 00:05 DEBUG  WindowsBackend: timezone=America/New_York
05-17 00:05 DEBUG  WindowsBackend: windows_username=Furqan
05-17 00:05 DEBUG  WindowsBackend: user_full_name=Furqan
05-17 00:05 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Furqan
05-17 00:05 DEBUG  WindowsBackend: windows_language_code=1033
05-17 00:05 DEBUG  WindowsBackend: windows_language=English
05-17 00:05 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E4600  @ 2.40GHz
05-17 00:05 DEBUG  WindowsBackend: bootloader=xp
05-17 00:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 15503.765625 mb free ntfs)
05-17 00:05 DEBUG  WindowsBackend: drive=Drive(C: hd 15503.765625 mb free ntfs)
05-17 00:05 DEBUG  WindowsBackend: drive=Drive(D: hd 14591.8320313 mb free ntfs)
05-17 00:05 DEBUG  WindowsBackend: drive=Drive(E: hd 16935.3242188 mb free ntfs)
05-17 00:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-17 00:05 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
05-17 00:05 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
05-17 00:05 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
05-17 00:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-17 00:05 DEBUG  WindowsBackend: keyboard_id=67699721
05-17 00:05 DEBUG  WindowsBackend: keyboard_layout=us
05-17 00:05 DEBUG  WindowsBackend: keyboard_variant=
05-17 00:05 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-17 00:05 DEBUG  CommonBackend: locale=en_US.UTF-8
05-17 00:05 DEBUG  WindowsBackend: total_memory_mb=895.16796875
05-17 00:05 DEBUG  CommonBackend: Searching ISOs on USB devices
05-17 00:05 DEBUG  CommonBackend: Searching for local CDs
05-17 00:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
05-17 00:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
05-17 00:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
05-17 00:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
05-17 00:05 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-17 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-17 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-17 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-17 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-17 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-17 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-17 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-17 00:05 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
05-17 00:05 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
05-17 00:05 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-17 00:05 INFO   root: Running the CD menu...
05-17 00:05 DEBUG  WindowsFrontend: __init__...
05-17 00:05 DEBUG  WindowsFrontend: on_init...
05-17 00:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
05-17 00:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
05-17 00:06 INFO   root: === wubi 10.04 rev189 ===
05-17 00:06 DEBUG  root: Logfile is c:\docume~1\furqan\locals~1\temp\wubi-10.04-rev189.log
05-17 00:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
05-17 00:06 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\data
05-17 00:06 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\bin\7z.exe
05-17 00:06 DEBUG  CommonBackend: Fetching basic info...
05-17 00:06 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
05-17 00:06 DEBUG  CommonBackend: platform=win32
05-17 00:06 DEBUG  CommonBackend: osname=nt
05-17 00:06 DEBUG  CommonBackend: language=en_US
05-17 00:06 DEBUG  CommonBackend: encoding=cp1252
05-17 00:06 DEBUG  WindowsBackend: arch=amd64
05-17 00:06 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\data\isolist.ini
05-17 00:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-17 00:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-17 00:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-17 00:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-17 00:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-17 00:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-17 00:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-17 00:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-17 00:06 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-17 00:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-17 00:06 DEBUG  WindowsBackend: Fetching host info...
05-17 00:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-17 00:06 DEBUG  WindowsBackend: windows version=xp
05-17 00:06 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-17 00:06 DEBUG  WindowsBackend: windows_sp=Service Pack 2
05-17 00:06 DEBUG  WindowsBackend: windows_build=2600
05-17 00:06 DEBUG  WindowsBackend: gmt=5
05-17 00:06 DEBUG  WindowsBackend: country=US
05-17 00:06 DEBUG  WindowsBackend: timezone=America/New_York
05-17 00:06 DEBUG  WindowsBackend: windows_username=Furqan
05-17 00:06 DEBUG  WindowsBackend: user_full_name=Furqan
05-17 00:06 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Furqan
05-17 00:06 DEBUG  WindowsBackend: windows_language_code=1033
05-17 00:06 DEBUG  WindowsBackend: windows_language=English
05-17 00:06 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E4600  @ 2.40GHz
05-17 00:06 DEBUG  WindowsBackend: bootloader=xp
05-17 00:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 15496.0351563 mb free ntfs)
05-17 00:06 DEBUG  WindowsBackend: drive=Drive(C: hd 15496.0351563 mb free ntfs)
05-17 00:06 DEBUG  WindowsBackend: drive=Drive(D: hd 14591.8320313 mb free ntfs)
05-17 00:06 DEBUG  WindowsBackend: drive=Drive(E: hd 16935.3242188 mb free ntfs)
05-17 00:06 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-17 00:06 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
05-17 00:06 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
05-17 00:06 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
05-17 00:06 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-17 00:06 DEBUG  WindowsBackend: keyboard_id=67699721
05-17 00:06 DEBUG  WindowsBackend: keyboard_layout=us
05-17 00:06 DEBUG  WindowsBackend: keyboard_variant=
05-17 00:06 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-17 00:06 DEBUG  CommonBackend: locale=en_US.UTF-8
05-17 00:06 DEBUG  WindowsBackend: total_memory_mb=895.16796875
05-17 00:06 DEBUG  CommonBackend: Searching ISOs on USB devices
05-17 00:06 DEBUG  CommonBackend: Searching for local CDs
05-17 00:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Netbook CD
05-17 00:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
05-17 00:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
05-17 00:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
05-17 00:06 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-17 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-17 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-17 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-17 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-17 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-17 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-17 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-17 00:06 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
05-17 00:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
05-17 00:06 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-17 00:06 INFO   root: Running the uninstaller...
05-17 00:06 INFO   CommonBackend: This is the uninstaller running
05-17 00:06 DEBUG  WindowsFrontend: __init__...
05-17 00:06 DEBUG  WindowsFrontend: on_init...
05-17 00:06 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
05-17 00:07 INFO   root: Received settings
05-17 00:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
05-17 00:07 DEBUG  TaskList: # Running tasklist...
05-17 00:07 DEBUG  TaskList: ## Running Backup ISO...
05-17 00:07 DEBUG  TaskList: ## Finished Backup ISO
05-17 00:07 DEBUG  TaskList: ## Running Remove bootloader entry...
05-17 00:07 ERROR  WindowsBackend: Cannot find bcdedit
05-17 00:07 DEBUG  WindowsBackend: undo_bootini C:
05-17 00:07 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 15496.0351563 mb free ntfs)
05-17 00:07 DEBUG  WindowsBackend: undo_bootini D:
05-17 00:07 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 14591.8320313 mb free ntfs)
05-17 00:07 DEBUG  WindowsBackend: undo_bootini E:
05-17 00:07 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 16935.3242188 mb free ntfs)
05-17 00:07 DEBUG  TaskList: ## Finished Remove bootloader entry
05-17 00:07 DEBUG  TaskList: ## Running Remove target dir...
05-17 00:07 DEBUG  CommonBackend: Deleting D:\ubuntu
05-17 00:07 DEBUG  TaskList: ## Finished Remove target dir
05-17 00:07 DEBUG  TaskList: ## Running Remove registry key...
05-17 00:07 DEBUG  TaskList: ## Finished Remove registry key
05-17 00:07 DEBUG  TaskList: # Finished tasklist
05-17 00:07 INFO   root: Almost finished uninstalling
05-17 00:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
05-17 00:07 INFO   root: Finished uninstallation
05-17 00:07 DEBUG  root: application.quit
05-17 00:07 DEBUG  WindowsFrontend: frontend.quit
05-17 00:07 DEBUG  WindowsFrontend: frontend.on_quit
05-17 00:07 DEBUG  root: application.on_quit
05-17 00:07 INFO   root: sys.exit
05-17 00:07 INFO   root: CD menu finished
05-17 00:07 INFO   root: Running the installer...
05-17 00:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
05-17 00:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
05-17 00:08 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=mohammed
05-17 00:08 INFO   root: Received settings
05-17 00:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
05-17 00:08 DEBUG  TaskList: # Running tasklist...
05-17 00:08 DEBUG  TaskList: ## Running select_target_dir...
05-17 00:08 INFO   WindowsBackend: Installing into D:\ubuntu
05-17 00:08 DEBUG  TaskList: ## Finished select_target_dir
05-17 00:08 DEBUG  TaskList: ## Running create_dir_structure...
05-17 00:08 DEBUG  CommonBackend: Creating dir D:\ubuntu
05-17 00:08 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
05-17 00:08 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
05-17 00:08 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
05-17 00:08 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
05-17 00:08 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
05-17 00:08 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
05-17 00:08 DEBUG  TaskList: ## Finished create_dir_structure
05-17 00:08 DEBUG  TaskList: ## Running uncompress_target_dir...
05-17 00:08 DEBUG  TaskList: ## Finished uncompress_target_dir
05-17 00:08 DEBUG  TaskList: ## Running create_uninstaller...
05-17 00:08 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
05-17 00:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
05-17 00:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
05-17 00:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-17 00:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
05-17 00:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
05-17 00:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-17 00:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-17 00:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-17 00:08 DEBUG  TaskList: ## Finished create_uninstaller
05-17 00:08 DEBUG  TaskList: ## Running copy_installation_files...
05-17 00:08 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
05-17 00:08 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\winboot -> D:\ubuntu\winboot
05-17 00:08 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
05-17 00:08 DEBUG  TaskList: ## Finished copy_installation_files
05-17 00:08 DEBUG  TaskList: ## Running get_iso...
05-17 00:08 DEBUG  TaskList: New task copy_file
05-17 00:08 DEBUG  TaskList: ### Running copy_file...
05-17 00:10 DEBUG  TaskList: ### Finished copy_file
05-17 00:10 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
05-17 00:10 DEBUG  TaskList: # Cancelling tasklist
05-17 00:10 DEBUG  TaskList: New task check_iso
05-17 00:10 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
05-17 00:10 DEBUG  CommonBackend: Searching for local ISO
05-17 00:10 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-17 00:10 DEBUG  TaskList: New task get_metalink
05-17 00:10 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-17 00:10 DEBUG  TaskList: # Cancelling tasklist
05-17 00:10 DEBUG  TaskList: # Finished tasklist
05-17 00:11 INFO   root: === wubi 10.04 rev189 ===
05-17 00:11 DEBUG  root: Logfile is c:\docume~1\furqan\locals~1\temp\wubi-10.04-rev189.log
05-17 00:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
05-17 00:11 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\data
05-17 00:11 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\bin\7z.exe
05-17 00:11 DEBUG  CommonBackend: Fetching basic info...
05-17 00:11 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
05-17 00:11 DEBUG  CommonBackend: platform=win32
05-17 00:11 DEBUG  CommonBackend: osname=nt
05-17 00:11 DEBUG  CommonBackend: language=en_US
05-17 00:11 DEBUG  CommonBackend: encoding=cp1252
05-17 00:11 DEBUG  WindowsBackend: arch=amd64
05-17 00:11 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\data\isolist.ini
05-17 00:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-17 00:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-17 00:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-17 00:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-17 00:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-17 00:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-17 00:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-17 00:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-17 00:11 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-17 00:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-17 00:11 DEBUG  WindowsBackend: Fetching host info...
05-17 00:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-17 00:11 DEBUG  WindowsBackend: windows version=xp
05-17 00:11 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-17 00:11 DEBUG  WindowsBackend: windows_sp=Service Pack 2
05-17 00:11 DEBUG  WindowsBackend: windows_build=2600
05-17 00:11 DEBUG  WindowsBackend: gmt=5
05-17 00:11 DEBUG  WindowsBackend: country=US
05-17 00:11 DEBUG  WindowsBackend: timezone=America/New_York
05-17 00:11 DEBUG  WindowsBackend: windows_username=Furqan
05-17 00:11 DEBUG  WindowsBackend: user_full_name=Furqan
05-17 00:11 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Furqan
05-17 00:11 DEBUG  WindowsBackend: windows_language_code=1033
05-17 00:11 DEBUG  WindowsBackend: windows_language=English
05-17 00:11 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E4600  @ 2.40GHz
05-17 00:11 DEBUG  WindowsBackend: bootloader=xp
05-17 00:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 15499.6835938 mb free ntfs)
05-17 00:11 DEBUG  WindowsBackend: drive=Drive(C: hd 15499.6835938 mb free ntfs)
05-17 00:11 DEBUG  WindowsBackend: drive=Drive(D: hd 14590.40625 mb free ntfs)
05-17 00:11 DEBUG  WindowsBackend: drive=Drive(E: hd 16935.2265625 mb free ntfs)
05-17 00:11 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
05-17 00:11 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
05-17 00:11 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
05-17 00:11 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
05-17 00:11 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-17 00:11 DEBUG  WindowsBackend: keyboard_id=67699721
05-17 00:11 DEBUG  WindowsBackend: keyboard_layout=us
05-17 00:11 DEBUG  WindowsBackend: keyboard_variant=
05-17 00:11 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-17 00:11 DEBUG  CommonBackend: locale=en_US.UTF-8
05-17 00:11 DEBUG  WindowsBackend: total_memory_mb=895.16796875
05-17 00:11 DEBUG  CommonBackend: Searching ISOs on USB devices
05-17 00:11 DEBUG  CommonBackend: Searching for local CDs
05-17 00:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu Netbook CD
05-17 00:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu Netbook CD
05-17 00:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
05-17 00:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
05-17 00:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-17 00:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-17 00:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-17 00:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
05-17 00:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-17 00:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-17 00:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-17 00:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-17 00:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-17 00:11 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
05-17 00:11 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
05-17 00:11 INFO   Distro: Found a valid CD for Ubuntu: F:\
05-17 00:11 INFO   root: Running the uninstaller...
05-17 00:11 INFO   CommonBackend: This is the uninstaller running
05-17 00:11 DEBUG  WindowsFrontend: __init__...
05-17 00:11 DEBUG  WindowsFrontend: on_init...
05-17 00:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
05-17 00:11 INFO   root: Received settings
05-17 00:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
05-17 00:11 DEBUG  TaskList: # Running tasklist...
05-17 00:11 DEBUG  TaskList: ## Running Backup ISO...
05-17 00:11 DEBUG  TaskList: ## Finished Backup ISO
05-17 00:11 DEBUG  TaskList: ## Running Remove bootloader entry...
05-17 00:11 ERROR  WindowsBackend: Cannot find bcdedit
05-17 00:11 DEBUG  WindowsBackend: undo_bootini C:
05-17 00:11 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 15499.6835938 mb free ntfs)
05-17 00:11 DEBUG  WindowsBackend: undo_bootini D:
05-17 00:11 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 14590.40625 mb free ntfs)
05-17 00:11 DEBUG  WindowsBackend: undo_bootini E:
05-17 00:11 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 16935.2265625 mb free ntfs)
05-17 00:11 DEBUG  TaskList: ## Finished Remove bootloader entry
05-17 00:11 DEBUG  TaskList: ## Running Remove target dir...
05-17 00:11 DEBUG  CommonBackend: Deleting D:\ubuntu
05-17 00:11 DEBUG  TaskList: ## Finished Remove target dir
05-17 00:11 DEBUG  TaskList: ## Running Remove registry key...
05-17 00:11 DEBUG  TaskList: ## Finished Remove registry key
05-17 00:11 DEBUG  TaskList: # Finished tasklist
05-17 00:11 INFO   root: Almost finished uninstalling
05-17 00:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
05-17 00:11 INFO   root: Finished uninstallation
05-17 00:11 DEBUG  root: application.quit
05-17 00:11 DEBUG  WindowsFrontend: frontend.quit
05-17 00:11 DEBUG  WindowsFrontend: frontend.on_quit
05-17 00:11 DEBUG  root: application.on_quit
05-17 00:11 INFO   root: sys.exit

---

