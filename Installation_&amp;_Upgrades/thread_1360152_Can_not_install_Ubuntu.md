---
title: "Can not install Ubuntu"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by ucjhd on 2009-12-20
I can not install or view Ubuntu on one of my PC's. On another there are no problems which indicate the installation CD is OK.
 
The installation from e.g. inside Windows XP seems to run as expected right until the last sec where I get a pop up telling me 'Permission denied'. The log file looks as below. Anyone having any idea what is going wrong or how to solve it.
 
Can add that if I try to boot directly from the CD I get the menu where I can select to view or install Ubuntu, but in neither of the options I succed.  
 
 
12-20 20:58 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-20 20:58 DEBUG  root: Logfile is c:\docume~1\medion~1\lokale~1\temp\wubi-9.10ubuntu1-rev160.log
12-20 20:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="L:\\Install Ubuntu\\wubi.exe"']
12-20 20:58 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp\data
12-20 20:58 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp\bin\7z.exe
12-20 20:58 DEBUG  CommonBackend: Fetching basic info...
12-20 20:58 DEBUG  CommonBackend: original_exe=L:\Install Ubuntu\wubi.exe
12-20 20:58 DEBUG  CommonBackend: platform=win32
12-20 20:58 DEBUG  CommonBackend: osname=nt
12-20 20:58 DEBUG  CommonBackend: language=da_DK
12-20 20:58 DEBUG  CommonBackend: encoding=cp1252
12-20 20:58 DEBUG  WindowsBackend: arch=i386
12-20 20:58 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp\data\isolist.ini
12-20 20:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-20 20:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-20 20:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-20 20:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-20 20:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-20 20:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-20 20:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-20 20:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-20 20:58 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-20 20:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-20 20:58 DEBUG  WindowsBackend: Fetching host info...
12-20 20:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-20 20:58 DEBUG  WindowsBackend: windows version=xp
12-20 20:58 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-20 20:58 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-20 20:58 DEBUG  WindowsBackend: windows_build=2600
12-20 20:58 DEBUG  WindowsBackend: gmt=1
12-20 20:58 DEBUG  WindowsBackend: country=IT
12-20 20:58 DEBUG  WindowsBackend: timezone=Europe/Rome
12-20 20:58 DEBUG  WindowsBackend: windows_username=Medion Life
12-20 20:58 DEBUG  WindowsBackend: user_full_name=Medion Life
12-20 20:58 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Medion Life
12-20 20:58 DEBUG  WindowsBackend: windows_language_code=1030
12-20 20:58 DEBUG  WindowsBackend: windows_language=Danish
12-20 20:58 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 3.00GHz
12-20 20:58 DEBUG  WindowsBackend: bootloader=xp
12-20 20:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14969.8046875 mb free ntfs)
12-20 20:58 DEBUG  WindowsBackend: drive=Drive(C: hd 14969.8046875 mb free ntfs)
12-20 20:58 DEBUG  WindowsBackend: drive=Drive(D: hd 51040.9921875 mb free ntfs)
12-20 20:58 DEBUG  WindowsBackend: drive=Drive(E: hd 2173.5390625 mb free fat32)
12-20 20:58 DEBUG  WindowsBackend: drive=Drive(F: hd 15580.28125 mb free fat32)
12-20 20:58 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-20 20:59 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-20 20:59 DEBUG  root: Logfile is c:\docume~1\medion~1\lokale~1\temp\wubi-9.10ubuntu1-rev160.log
12-20 20:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
12-20 20:59 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp\data
12-20 20:59 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp\bin\7z.exe
12-20 20:59 DEBUG  CommonBackend: Fetching basic info...
12-20 20:59 DEBUG  CommonBackend: original_exe=G:\wubi.exe
12-20 20:59 DEBUG  CommonBackend: platform=win32
12-20 20:59 DEBUG  CommonBackend: osname=nt
12-20 20:59 DEBUG  CommonBackend: language=da_DK
12-20 20:59 DEBUG  CommonBackend: encoding=cp1252
12-20 20:59 DEBUG  WindowsBackend: arch=i386
12-20 20:59 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp\data\isolist.ini
12-20 20:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-20 20:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-20 20:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-20 20:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-20 20:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-20 20:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-20 20:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-20 20:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-20 20:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-20 20:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-20 20:59 DEBUG  WindowsBackend: Fetching host info...
12-20 20:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-20 20:59 DEBUG  WindowsBackend: windows version=xp
12-20 20:59 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-20 20:59 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-20 20:59 DEBUG  WindowsBackend: windows_build=2600
12-20 20:59 DEBUG  WindowsBackend: gmt=1
12-20 20:59 DEBUG  WindowsBackend: country=IT
12-20 20:59 DEBUG  WindowsBackend: timezone=Europe/Rome
12-20 20:59 DEBUG  WindowsBackend: windows_username=Medion Life
12-20 20:59 DEBUG  WindowsBackend: user_full_name=Medion Life
12-20 20:59 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Medion Life
12-20 20:59 DEBUG  WindowsBackend: windows_language_code=1030
12-20 20:59 DEBUG  WindowsBackend: windows_language=Danish
12-20 20:59 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 3.00GHz
12-20 20:59 DEBUG  WindowsBackend: bootloader=xp
12-20 20:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14963.0 mb free ntfs)
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(C: hd 14963.0 mb free ntfs)
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(D: hd 51040.9921875 mb free ntfs)
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(E: hd 2173.5390625 mb free fat32)
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(F: hd 15580.28125 mb free fat32)
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(L: removable 3055.703125 mb free fat32)
12-20 20:59 DEBUG  WindowsBackend: uninstaller_path=None
12-20 20:59 DEBUG  WindowsBackend: previous_target_dir=None
12-20 20:59 DEBUG  WindowsBackend: previous_distro_name=None
12-20 20:59 DEBUG  WindowsBackend: keyboard_id=67503110
12-20 20:59 DEBUG  WindowsBackend: keyboard_layout=it
12-20 20:59 DEBUG  WindowsBackend: keyboard_variant=
12-20 20:59 DEBUG  CommonBackend: python locale=('da_DK', 'cp1252')
12-20 20:59 DEBUG  CommonBackend: locale=da_DK.UTF-8
12-20 20:59 DEBUG  WindowsBackend: total_memory_mb=1023.48046875
12-20 20:59 DEBUG  CommonBackend: Searching ISOs on USB devices
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(L: removable 3055.703125 mb free fat32)
12-20 20:59 DEBUG  WindowsBackend: uninstaller_path=None
12-20 20:59 DEBUG  WindowsBackend: previous_target_dir=None
12-20 20:59 DEBUG  WindowsBackend: previous_distro_name=None
12-20 20:59 DEBUG  WindowsBackend: keyboard_id=67503110
12-20 20:59 DEBUG  WindowsBackend: keyboard_layout=it
12-20 20:59 DEBUG  WindowsBackend: keyboard_variant=
12-20 20:59 DEBUG  CommonBackend: python locale=('da_DK', 'cp1252')
12-20 20:59 DEBUG  CommonBackend: locale=da_DK.UTF-8
12-20 20:59 DEBUG  WindowsBackend: total_memory_mb=1023.48046875
12-20 20:59 DEBUG  CommonBackend: Searching ISOs on USB devices
12-20 20:59 DEBUG  CommonBackend: Searching for local CDs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp is a valid Ubuntu Netbook Remix CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp is a valid Kubuntu Netbook CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
12-20 20:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
12-20 20:59 DEBUG  Distro: wrong arch: i386 != amd64
12-20 20:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  CommonBackend: Searching for local CDs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp is a valid Ubuntu Netbook Remix CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp is a valid Kubuntu Netbook CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp\casper\filesystem.squashfs
12-20 20:59 INFO   Distro: Found a valid CD for Ubuntu: G:\
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp is a valid Xubuntu CD
12-20 20:59 INFO   root: Running the CD menu...
12-20 20:59 DEBUG  WindowsFrontend: __init__...
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  WindowsFrontend: on_init...
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-20 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp\translations, languages=['da_DK', 'da']
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
12-20 20:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
12-20 20:59 DEBUG  Distro: wrong arch: i386 != amd64
12-20 20:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-20 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE6.tmp\translations, languages=['da_DK', 'da']
12-20 20:59 INFO   Distro: Found a valid CD for Ubuntu: G:\
12-20 20:59 INFO   root: Running the CD menu...
12-20 20:59 DEBUG  WindowsFrontend: __init__...
12-20 20:59 DEBUG  WindowsFrontend: on_init...
12-20 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp\translations, languages=['da_DK', 'da']
12-20 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylE9.tmp\translations, languages=['da_DK', 'da']
12-20 20:59 DEBUG  WindowsFrontend: frontend.on_quit
12-20 20:59 DEBUG  root: application.on_quit
12-20 20:59 INFO   root: sys.exit
12-20 20:59 DEBUG  WindowsFrontend: frontend.on_quit
12-20 20:59 DEBUG  root: application.on_quit
12-20 20:59 INFO   root: sys.exit
12-20 20:59 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-20 20:59 DEBUG  root: Logfile is c:\docume~1\medion~1\lokale~1\temp\wubi-9.10ubuntu1-rev160.log
12-20 20:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="L:\\Install Ubuntu\\wubi.exe"']
12-20 20:59 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\data
12-20 20:59 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\bin\7z.exe
12-20 20:59 DEBUG  CommonBackend: Fetching basic info...
12-20 20:59 DEBUG  CommonBackend: original_exe=L:\Install Ubuntu\wubi.exe
12-20 20:59 DEBUG  CommonBackend: platform=win32
12-20 20:59 DEBUG  CommonBackend: osname=nt
12-20 20:59 DEBUG  CommonBackend: language=da_DK
12-20 20:59 DEBUG  CommonBackend: encoding=cp1252
12-20 20:59 DEBUG  WindowsBackend: arch=i386
12-20 20:59 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\data\isolist.ini
12-20 20:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-20 20:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-20 20:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-20 20:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-20 20:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-20 20:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-20 20:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-20 20:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-20 20:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-20 20:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-20 20:59 DEBUG  WindowsBackend: Fetching host info...
12-20 20:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-20 20:59 DEBUG  WindowsBackend: windows version=xp
12-20 20:59 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-20 20:59 DEBUG  WindowsBackend: windows_sp=Service Pack 3
12-20 20:59 DEBUG  WindowsBackend: windows_build=2600
12-20 20:59 DEBUG  WindowsBackend: gmt=1
12-20 20:59 DEBUG  WindowsBackend: country=IT
12-20 20:59 DEBUG  WindowsBackend: timezone=Europe/Rome
12-20 20:59 DEBUG  WindowsBackend: windows_username=Medion Life
12-20 20:59 DEBUG  WindowsBackend: user_full_name=Medion Life
12-20 20:59 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Medion Life
12-20 20:59 DEBUG  WindowsBackend: windows_language_code=1030
12-20 20:59 DEBUG  WindowsBackend: windows_language=Danish
12-20 20:59 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 3.00GHz
12-20 20:59 DEBUG  WindowsBackend: bootloader=xp
12-20 20:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14969.9023438 mb free ntfs)
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(C: hd 14969.9023438 mb free ntfs)
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(D: hd 51040.9921875 mb free ntfs)
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(E: hd 2173.5390625 mb free fat32)
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(F: hd 15580.28125 mb free fat32)
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
12-20 20:59 DEBUG  WindowsBackend: drive=Drive(L: removable 3055.703125 mb free fat32)
12-20 20:59 DEBUG  WindowsBackend: uninstaller_path=None
12-20 20:59 DEBUG  WindowsBackend: previous_target_dir=None
12-20 20:59 DEBUG  WindowsBackend: previous_distro_name=None
12-20 20:59 DEBUG  WindowsBackend: keyboard_id=67503110
12-20 20:59 DEBUG  WindowsBackend: keyboard_layout=it
12-20 20:59 DEBUG  WindowsBackend: keyboard_variant=
12-20 20:59 DEBUG  CommonBackend: python locale=('da_DK', 'cp1252')
12-20 20:59 DEBUG  CommonBackend: locale=da_DK.UTF-8
12-20 20:59 DEBUG  WindowsBackend: total_memory_mb=1023.48046875
12-20 20:59 DEBUG  CommonBackend: Searching ISOs on USB devices
12-20 20:59 DEBUG  CommonBackend: Searching for local CDs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp is a valid Ubuntu Netbook Remix CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp is a valid Kubuntu Netbook CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-20 20:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-20 20:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-20 20:59 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
12-20 20:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
12-20 20:59 DEBUG  Distro: wrong arch: i386 != amd64
12-20 20:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-20 20:59 INFO   Distro: Found a valid CD for Ubuntu: G:\
12-20 20:59 INFO   root: Running the CD menu...
12-20 20:59 DEBUG  WindowsFrontend: __init__...
12-20 20:59 DEBUG  WindowsFrontend: on_init...
12-20 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\translations, languages=['da_DK', 'da']
12-20 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\translations, languages=['da_DK', 'da']
12-20 20:59 INFO   root: CD menu finished
12-20 20:59 INFO   root: Running the installer...
12-20 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\translations, languages=['da_DK', 'da']
12-20 21:00 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\translations, languages=['da_DK', 'da']
12-20 21:00 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=9000MB, distro_name=Ubuntu, language=da_DK, locale=da_DK.UTF-8, username=medionlife
12-20 21:00 INFO   root: Received settings
12-20 21:00 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\translations, languages=['da_DK', 'da']
12-20 21:00 DEBUG  TaskList: # Running tasklist...
12-20 21:00 DEBUG  TaskList: ## Running select_target_dir...
12-20 21:00 INFO   WindowsBackend: Installing into C:\ubuntu
12-20 21:00 DEBUG  TaskList: ## Finished select_target_dir
12-20 21:00 DEBUG  TaskList: ## Running create_dir_structure...
12-20 21:00 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-20 21:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-20 21:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-20 21:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-20 21:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-20 21:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-20 21:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-20 21:00 DEBUG  TaskList: ## Finished create_dir_structure
12-20 21:00 DEBUG  TaskList: ## Running uncompress_target_dir...
12-20 21:00 DEBUG  TaskList: ## Finished uncompress_target_dir
12-20 21:00 DEBUG  TaskList: ## Running create_uninstaller...
12-20 21:00 DEBUG  WindowsBackend: Copying uninstaller L:\Install Ubuntu\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-20 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-20 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-20 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-20 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-20 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
12-20 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-20 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-20 21:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-20 21:00 DEBUG  TaskList: ## Finished create_uninstaller
12-20 21:00 DEBUG  TaskList: ## Running copy_installation_files...
12-20 21:00 DEBUG  WindowsBackend: Copying C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
12-20 21:00 DEBUG  WindowsBackend: Copying C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\winboot -> C:\ubuntu\winboot
12-20 21:00 DEBUG  WindowsBackend: Copying C:\DOCUME~1\MEDION~1\LOKALE~1\Temp\pylEF.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
12-20 21:00 DEBUG  TaskList: ## Finished copy_installation_files
12-20 21:00 DEBUG  TaskList: ## Running get_iso...
12-20 21:00 DEBUG  TaskList: New task copy_file
12-20 21:00 DEBUG  TaskList: ### Running copy_file...
12-20 21:03 DEBUG  TaskList: ### Finished copy_file
12-20 21:03 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
12-20 21:03 DEBUG  TaskList: # Cancelling tasklist
12-20 21:03 DEBUG  TaskList: New task check_iso
12-20 21:03 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
12-20 21:03 DEBUG  CommonBackend: Searching for local ISO
12-20 21:03 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-20 21:03 DEBUG  TaskList: New task get_metalink
12-20 21:03 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
12-20 21:03 DEBUG  TaskList: # Cancelling tasklist
12-20 21:03 DEBUG  TaskList: # Finished tasklist

---

### Post by phillw on 2009-12-20
Okay - firstly, please use the WUBI tag for wubi problems - it just makes it a bit easier for us all !!

One thing to check is that you are doing the install of Wubi with administrator privalidges.
(Yes, we've all done it -- even when we *think* we haven't !!) -- Permission denied is a good indicator of this one

another 'gotcha' is to clean the cd/dvd drive with one of the cleaning discs. As your cd works fine on other machines, it is either
1) operator error ;-)
2) kit fault.

Let's try to take the human out of the equation before we blame the machine - lol

Regards,

Phill.

---

