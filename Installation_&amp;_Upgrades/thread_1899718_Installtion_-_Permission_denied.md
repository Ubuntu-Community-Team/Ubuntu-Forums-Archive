---
title: "Installtion - Permission denied??"
date: 2011-12-24
forum: Installation &amp; Upgrades
---

### Post by ZmrAbdulla on 2011-12-24
I am trying to install Ubuntu inside windows.. getting an error log as follows.
 
```
12-23 21:31 INFO root: === wubi 11.04 rev211 ===
12-23 21:31 DEBUG root: Logfile is c:\docume~1\zameer~1\locals~1\temp\wubi-11.04-rev211.log
12-23 21:31 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Zameer Abdulla\\Desktop\\wubi.exe"']
12-23 21:31 DEBUG CommonBackend: data_dir=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp\data
12-23 21:31 DEBUG WindowsBackend: 7z=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp\bin\7z.exe
12-23 21:31 DEBUG WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
12-23 21:31 DEBUG CommonBackend: Fetching basic info...
12-23 21:31 DEBUG CommonBackend: original_exe=C:\Documents and Settings\Zameer Abdulla\Desktop\wubi.exe
12-23 21:31 DEBUG CommonBackend: platform=win32
12-23 21:31 DEBUG CommonBackend: osname=nt
12-23 21:31 DEBUG CommonBackend: language=en_US
12-23 21:31 DEBUG CommonBackend: encoding=cp1252
12-23 21:31 DEBUG WindowsBackend: arch=i386
12-23 21:31 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp\data\isolist.ini
12-23 21:31 DEBUG CommonBackend: Adding distro Xubuntu-i386
12-23 21:31 DEBUG CommonBackend: Adding distro Xubuntu-amd64
12-23 21:31 DEBUG CommonBackend: Adding distro Kubuntu-amd64
12-23 21:31 DEBUG CommonBackend: Adding distro Mythbuntu-i386
12-23 21:31 DEBUG CommonBackend: Adding distro Ubuntu-amd64
12-23 21:31 DEBUG CommonBackend: Adding distro Ubuntu-i386
12-23 21:31 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
12-23 21:31 DEBUG CommonBackend: Adding distro Kubuntu-i386
12-23 21:31 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
12-23 21:31 DEBUG WindowsBackend: Fetching host info...
12-23 21:31 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-23 21:31 DEBUG WindowsBackend: windows version=xp
12-23 21:31 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
12-23 21:31 DEBUG WindowsBackend: windows_sp=Service Pack 3
12-23 21:31 DEBUG WindowsBackend: windows_build=2600
12-23 21:31 DEBUG WindowsBackend: gmt=4
12-23 21:31 DEBUG WindowsBackend: country=US
12-23 21:31 DEBUG WindowsBackend: timezone=America/New_York
12-23 21:31 DEBUG WindowsBackend: windows_username=Zameer Abdulla
12-23 21:31 DEBUG WindowsBackend: user_full_name=Zameer Abdulla
12-23 21:31 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Zameer Abdulla
12-23 21:31 DEBUG WindowsBackend: windows_language_code=1033
12-23 21:31 DEBUG WindowsBackend: windows_language=English
12-23 21:31 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 1.60GHz
12-23 21:31 DEBUG WindowsBackend: bootloader=xp
12-23 21:31 DEBUG WindowsBackend: system_drive=Drive(C: hd 54849.7890625 mb free ntfs)
12-23 21:31 DEBUG WindowsBackend: drive=Drive(C: hd 54849.7890625 mb free ntfs)
12-23 21:31 DEBUG WindowsBackend: drive=Drive(D: hd 90922.796875 mb free ntfs)
12-23 21:31 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-23 21:31 DEBUG WindowsBackend: drive=Drive(F: hd 20469.359375 mb free fat32)
12-23 21:31 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-23 21:31 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
12-23 21:31 DEBUG WindowsBackend: previous_distro_name=Xubuntu
12-23 21:31 DEBUG WindowsBackend: keyboard_id=67699721
12-23 21:31 DEBUG WindowsBackend: keyboard_layout=us
12-23 21:31 DEBUG WindowsBackend: keyboard_variant=
12-23 21:31 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
12-23 21:31 DEBUG CommonBackend: locale=en_US.UTF-8
12-23 21:31 DEBUG WindowsBackend: total_memory_mb=895.421875
12-23 21:31 DEBUG CommonBackend: Searching ISOs on USB devices
12-23 21:31 DEBUG CommonBackend: Searching for local CDs
12-23 21:31 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp is a valid Ubuntu CD
12-23 21:31 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp is a valid Ubuntu CD
12-23 21:31 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp is a valid Ubuntu Netbook CD
12-23 21:31 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp is a valid Kubuntu CD
12-23 21:31 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp is a valid Kubuntu CD
12-23 21:31 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp is a valid Xubuntu CD
12-23 21:31 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp is a valid Xubuntu CD
12-23 21:31 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp is a valid Mythbuntu CD
12-23 21:31 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp is a valid Mythbuntu CD
12-23 21:31 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
12-23 21:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
12-23 21:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
12-23 21:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
12-23 21:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
12-23 21:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
12-23 21:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
12-23 21:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
12-23 21:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
12-23 21:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
12-23 21:31 DEBUG Distro: parsing info from str=Linux Mint 12 "Lisa" - Release i386 (20111120)
12-23 21:31 DEBUG Distro: parsed info={'name': 'Linux Mint', 'subversion': 'Release', 'version': '12', 'build': '20111120', 'codename': 'Lisa', 'arch': 'i386'}
12-23 21:31 DEBUG Distro: wrong name: Linux Mint != Ubuntu
12-23 21:31 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
12-23 21:31 DEBUG Distro: wrong name: Linux Mint != Ubuntu
12-23 21:31 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
12-23 21:31 DEBUG Distro: wrong name: Linux Mint != Ubuntu Netbook
12-23 21:31 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
12-23 21:31 DEBUG Distro: wrong name: Linux Mint != Kubuntu
12-23 21:31 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
12-23 21:31 DEBUG Distro: wrong name: Linux Mint != Kubuntu
12-23 21:31 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
12-23 21:31 DEBUG Distro: wrong name: Linux Mint != Xubuntu
12-23 21:31 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
12-23 21:31 DEBUG Distro: wrong name: Linux Mint != Xubuntu
12-23 21:31 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
12-23 21:31 DEBUG Distro: wrong name: Linux Mint != Mythbuntu
12-23 21:31 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
12-23 21:31 DEBUG Distro: wrong name: Linux Mint != Mythbuntu
12-23 21:31 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
12-23 21:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
12-23 21:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
12-23 21:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
12-23 21:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
12-23 21:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
12-23 21:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
12-23 21:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
12-23 21:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:31 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
12-23 21:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:31 INFO root: Already installed, running the uninstaller...
12-23 21:31 INFO root: Running the uninstaller...
12-23 21:31 INFO CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
12-23 21:31 DEBUG root: application.quit
12-23 21:31 DEBUG root: application.on_quit
12-23 21:31 INFO root: sys.exit
12-23 21:31 INFO root: Quitting application
12-23 21:35 INFO root: === wubi 11.04 rev211 ===
12-23 21:35 DEBUG root: Logfile is c:\docume~1\zameer~1\locals~1\temp\wubi-11.04-rev211.log
12-23 21:35 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Zameer Abdulla\\Desktop\\wubi.exe"']
12-23 21:35 DEBUG CommonBackend: data_dir=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\data
12-23 21:35 DEBUG WindowsBackend: 7z=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\bin\7z.exe
12-23 21:35 DEBUG WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
12-23 21:35 DEBUG CommonBackend: Fetching basic info...
12-23 21:35 DEBUG CommonBackend: original_exe=C:\Documents and Settings\Zameer Abdulla\Desktop\wubi.exe
12-23 21:35 DEBUG CommonBackend: platform=win32
12-23 21:35 DEBUG CommonBackend: osname=nt
12-23 21:35 DEBUG CommonBackend: language=en_US
12-23 21:35 DEBUG CommonBackend: encoding=cp1252
12-23 21:35 DEBUG WindowsBackend: arch=i386
12-23 21:35 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\data\isolist.ini
12-23 21:35 DEBUG CommonBackend: Adding distro Xubuntu-i386
12-23 21:35 DEBUG CommonBackend: Adding distro Xubuntu-amd64
12-23 21:35 DEBUG CommonBackend: Adding distro Kubuntu-amd64
12-23 21:35 DEBUG CommonBackend: Adding distro Mythbuntu-i386
12-23 21:35 DEBUG CommonBackend: Adding distro Ubuntu-amd64
12-23 21:35 DEBUG CommonBackend: Adding distro Ubuntu-i386
12-23 21:35 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
12-23 21:35 DEBUG CommonBackend: Adding distro Kubuntu-i386
12-23 21:35 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
12-23 21:35 DEBUG WindowsBackend: Fetching host info...
12-23 21:35 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-23 21:35 DEBUG WindowsBackend: windows version=xp
12-23 21:35 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
12-23 21:35 DEBUG WindowsBackend: windows_sp=Service Pack 3
12-23 21:35 DEBUG WindowsBackend: windows_build=2600
12-23 21:35 DEBUG WindowsBackend: gmt=4
12-23 21:35 DEBUG WindowsBackend: country=US
12-23 21:35 DEBUG WindowsBackend: timezone=America/New_York
12-23 21:35 DEBUG WindowsBackend: windows_username=Zameer Abdulla
12-23 21:35 DEBUG WindowsBackend: user_full_name=Zameer Abdulla
12-23 21:35 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Zameer Abdulla
12-23 21:35 DEBUG WindowsBackend: windows_language_code=1033
12-23 21:35 DEBUG WindowsBackend: windows_language=English
12-23 21:35 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 1.60GHz
12-23 21:35 DEBUG WindowsBackend: bootloader=xp
12-23 21:35 DEBUG WindowsBackend: system_drive=Drive(C: hd 55059.625 mb free ntfs)
12-23 21:35 DEBUG WindowsBackend: drive=Drive(C: hd 55059.625 mb free ntfs)
12-23 21:35 DEBUG WindowsBackend: drive=Drive(D: hd 90922.796875 mb free ntfs)
12-23 21:35 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-23 21:35 DEBUG WindowsBackend: drive=Drive(F: hd 20469.34375 mb free fat32)
12-23 21:35 DEBUG WindowsBackend: uninstaller_path=None
12-23 21:35 DEBUG WindowsBackend: previous_target_dir=None
12-23 21:35 DEBUG WindowsBackend: previous_distro_name=None
12-23 21:35 DEBUG WindowsBackend: keyboard_id=67699721
12-23 21:35 DEBUG WindowsBackend: keyboard_layout=us
12-23 21:35 DEBUG WindowsBackend: keyboard_variant=
12-23 21:35 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
12-23 21:35 DEBUG CommonBackend: locale=en_US.UTF-8
12-23 21:35 DEBUG WindowsBackend: total_memory_mb=895.421875
12-23 21:35 DEBUG CommonBackend: Searching ISOs on USB devices
12-23 21:35 DEBUG CommonBackend: Searching for local CDs
12-23 21:35 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp is a valid Ubuntu CD
12-23 21:35 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp is a valid Ubuntu CD
12-23 21:35 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp is a valid Ubuntu Netbook CD
12-23 21:35 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp is a valid Kubuntu CD
12-23 21:35 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp is a valid Kubuntu CD
12-23 21:35 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp is a valid Xubuntu CD
12-23 21:35 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp is a valid Xubuntu CD
12-23 21:35 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp is a valid Mythbuntu CD
12-23 21:35 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp is a valid Mythbuntu CD
12-23 21:35 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
12-23 21:35 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
12-23 21:35 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
12-23 21:35 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
12-23 21:35 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
12-23 21:35 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
12-23 21:35 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
12-23 21:35 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
12-23 21:35 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
12-23 21:35 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
12-23 21:35 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
12-23 21:35 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
12-23 21:35 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
12-23 21:35 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
12-23 21:35 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
12-23 21:35 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
12-23 21:35 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
12-23 21:35 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
12-23 21:35 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
12-23 21:35 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
12-23 21:35 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
12-23 21:35 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
12-23 21:35 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
12-23 21:35 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
12-23 21:35 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
12-23 21:35 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
12-23 21:35 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
12-23 21:35 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:35 INFO root: Running the installer...
12-23 21:35 DEBUG WindowsFrontend: __init__...
12-23 21:35 DEBUG WindowsFrontend: on_init...
12-23 21:35 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\translations, languages=['en_US', 'en']
12-23 21:35 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\translations, languages=['en_US', 'en']
12-23 21:35 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=zameerabdulla
12-23 21:35 INFO root: Received settings
12-23 21:35 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\translations, languages=['en_US', 'en']
12-23 21:35 DEBUG TaskList: # Running tasklist...
12-23 21:35 DEBUG TaskList: ## Running select_target_dir...
12-23 21:35 INFO WindowsBackend: Installing into C:\ubuntu
12-23 21:35 DEBUG TaskList: ## Finished select_target_dir
12-23 21:35 DEBUG TaskList: ## Running create_dir_structure...
12-23 21:35 DEBUG CommonBackend: Creating dir C:\ubuntu
12-23 21:35 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
12-23 21:35 DEBUG CommonBackend: Creating dir C:\ubuntu\install
12-23 21:35 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
12-23 21:35 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
12-23 21:35 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-23 21:35 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-23 21:35 DEBUG TaskList: ## Finished create_dir_structure
12-23 21:35 DEBUG TaskList: ## Running uncompress_target_dir...
12-23 21:35 DEBUG TaskList: ## Finished uncompress_target_dir
12-23 21:35 DEBUG TaskList: ## Running create_uninstaller...
12-23 21:35 DEBUG WindowsBackend: Copying uninstaller C:\Documents and Settings\Zameer Abdulla\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-23 21:35 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-23 21:35 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-23 21:35 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-23 21:35 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-23 21:35 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
12-23 21:35 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-23 21:35 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-23 21:35 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-23 21:35 DEBUG TaskList: ## Finished create_uninstaller
12-23 21:35 DEBUG TaskList: ## Running copy_installation_files...
12-23 21:35 DEBUG WindowsBackend: Copying C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
12-23 21:35 DEBUG WindowsBackend: Copying C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\winboot -> C:\ubuntu\winboot
12-23 21:35 DEBUG WindowsBackend: Copying C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
12-23 21:35 DEBUG TaskList: ## Finished copy_installation_files
12-23 21:35 DEBUG TaskList: ## Running get_iso...
12-23 21:35 DEBUG CommonBackend: Searching for local CD
12-23 21:35 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp is a valid Ubuntu CD
12-23 21:35 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
12-23 21:35 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-23 21:35 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
12-23 21:36 DEBUG Distro: parsing info from str=Xubuntu 10.04 "Lucid Lynx" - Release i386 (20100429)
12-23 21:36 DEBUG Distro: parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
12-23 21:36 DEBUG Distro: wrong name: Xubuntu != Ubuntu
12-23 21:36 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
12-23 21:36 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-23 21:36 DEBUG CommonBackend: Searching for local ISO
12-23 21:36 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
12-23 21:36 DEBUG TaskList: New task get_metalink
12-23 21:36 DEBUG TaskList: ### Running get_metalink...
12-23 21:36 DEBUG downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > C:\ubuntu\install
12-23 21:37 DEBUG downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink, basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
12-23 21:37 DEBUG downloader: download finished (read 28158 bytes)
12-23 21:37 DEBUG downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
12-23 21:37 DEBUG downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
12-23 21:37 DEBUG downloader: download finished (read 874 bytes)
12-23 21:37 DEBUG downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
12-23 21:37 DEBUG downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
12-23 21:37 DEBUG downloader: download finished (read 198 bytes)
12-23 21:37 INFO saplog: Verified a signature from ID:'46181433FBB75451'.
12-23 21:37 INFO saplog: Checking block bindings..
12-23 21:37 INFO saplog: Key verified successfully.
12-23 21:37 DEBUG CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65 ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3 ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2 ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488 ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1 ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1 ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449 ubuntu-11.04-server-i386.metalink
12-23 21:37 DEBUG TaskList: ### Finished get_metalink
12-23 21:37 DEBUG TaskList: New task download
12-23 21:37 DEBUG TaskList: ### Running download...
12-23 21:37 DEBUG btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
12-24 00:02 INFO WindowsFrontend: Operation cancelled
12-24 00:02 DEBUG WindowsFrontend: frontend.quit
12-24 00:02 DEBUG WindowsFrontend: frontend.on_quit
12-24 00:02 DEBUG WindowsFrontend: stopping remaining background tasks: 'tasklist'
12-24 00:02 DEBUG TaskList: # Cancelling tasklist
12-24 00:02 DEBUG TaskList: ### Finished download
12-24 00:02 DEBUG WindowsFrontend: Task cancellation timed out, the program will exit anyway
12-24 00:02 DEBUG root: application.on_quit
12-24 00:02 DEBUG root: Forceful exit
12-24 00:02 INFO root: sys.exit
12-24 13:17 INFO root: === wubi 11.04 rev211 ===
12-24 13:17 DEBUG root: Logfile is c:\docume~1\zameer~1\locals~1\temp\wubi-11.04-rev211.log
12-24 13:17 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Zameer Abdulla\\Desktop\\wubi.exe"']
12-24 13:17 DEBUG CommonBackend: data_dir=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\data
12-24 13:17 DEBUG WindowsBackend: 7z=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
12-24 13:17 DEBUG WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
12-24 13:17 DEBUG CommonBackend: Fetching basic info...
12-24 13:17 DEBUG CommonBackend: original_exe=C:\Documents and Settings\Zameer Abdulla\Desktop\wubi.exe
12-24 13:17 DEBUG CommonBackend: platform=win32
12-24 13:17 DEBUG CommonBackend: osname=nt
12-24 13:17 DEBUG CommonBackend: language=en_US
12-24 13:17 DEBUG CommonBackend: encoding=cp1252
12-24 13:17 DEBUG WindowsBackend: arch=i386
12-24 13:17 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
12-24 13:17 DEBUG CommonBackend: Adding distro Xubuntu-i386
12-24 13:17 DEBUG CommonBackend: Adding distro Xubuntu-amd64
12-24 13:17 DEBUG CommonBackend: Adding distro Kubuntu-amd64
12-24 13:17 DEBUG CommonBackend: Adding distro Mythbuntu-i386
12-24 13:17 DEBUG CommonBackend: Adding distro Ubuntu-amd64
12-24 13:17 DEBUG CommonBackend: Adding distro Ubuntu-i386
12-24 13:17 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
12-24 13:17 DEBUG CommonBackend: Adding distro Kubuntu-i386
12-24 13:17 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
12-24 13:17 DEBUG WindowsBackend: Fetching host info...
12-24 13:17 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-24 13:17 DEBUG WindowsBackend: windows version=xp
12-24 13:17 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
12-24 13:17 DEBUG WindowsBackend: windows_sp=Service Pack 3
12-24 13:17 DEBUG WindowsBackend: windows_build=2600
12-24 13:17 DEBUG WindowsBackend: gmt=4
12-24 13:17 DEBUG WindowsBackend: country=US
12-24 13:17 DEBUG WindowsBackend: timezone=America/New_York
12-24 13:17 DEBUG WindowsBackend: windows_username=Zameer Abdulla
12-24 13:17 DEBUG WindowsBackend: user_full_name=Zameer Abdulla
12-24 13:17 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Zameer Abdulla
12-24 13:17 DEBUG WindowsBackend: windows_language_code=1033
12-24 13:17 DEBUG WindowsBackend: windows_language=English
12-24 13:17 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 1.60GHz
12-24 13:17 DEBUG WindowsBackend: bootloader=xp
12-24 13:17 DEBUG WindowsBackend: system_drive=Drive(C: hd 55006.7929688 mb free ntfs)
12-24 13:17 DEBUG WindowsBackend: drive=Drive(C: hd 55006.7929688 mb free ntfs)
12-24 13:17 DEBUG WindowsBackend: drive=Drive(D: hd 88272.5 mb free ntfs)
12-24 13:17 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-24 13:17 DEBUG WindowsBackend: drive=Drive(F: hd 5612.8125 mb free fat32)
12-24 13:17 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-24 13:17 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
12-24 13:17 DEBUG WindowsBackend: previous_distro_name=Ubuntu
12-24 13:17 DEBUG WindowsBackend: keyboard_id=67699721
12-24 13:17 DEBUG WindowsBackend: keyboard_layout=us
12-24 13:17 DEBUG WindowsBackend: keyboard_variant=
12-24 13:17 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
12-24 13:17 DEBUG CommonBackend: locale=en_US.UTF-8
12-24 13:17 DEBUG WindowsBackend: total_memory_mb=895.421875
12-24 13:17 DEBUG CommonBackend: Searching ISOs on USB devices
12-24 13:17 DEBUG Distro: checking Ubuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Ubuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Ubuntu Netbook ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Kubuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Kubuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Xubuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Xubuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Mythbuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Mythbuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Ubuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Ubuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Ubuntu Netbook ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Kubuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Kubuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Xubuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Xubuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Mythbuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Mythbuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG CommonBackend: Searching for local CDs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 INFO root: Already installed, running the uninstaller...
12-24 13:17 INFO root: Running the uninstaller...
12-24 13:17 INFO CommonBackend: This is the uninstaller running
12-24 13:17 DEBUG WindowsFrontend: __init__...
12-24 13:17 DEBUG WindowsFrontend: on_init...
12-24 13:17 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
12-24 13:17 INFO root: Received settings
12-24 13:17 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
12-24 13:17 DEBUG TaskList: # Running tasklist...
12-24 13:17 DEBUG TaskList: ## Running Backup ISO...
12-24 13:17 DEBUG TaskList: ## Finished Backup ISO
12-24 13:17 DEBUG TaskList: ## Running Remove bootloader entry...
12-24 13:17 ERROR WindowsBackend: Cannot find bcdedit
12-24 13:17 DEBUG WindowsBackend: undo_bootini C:
12-24 13:17 DEBUG WindowsBackend: undo_configsys Drive(C: hd 55006.7929688 mb free ntfs)
12-24 13:17 DEBUG WindowsBackend: undo_bootini D:
12-24 13:17 DEBUG WindowsBackend: undo_configsys Drive(D: hd 88272.5 mb free ntfs)
12-24 13:17 DEBUG WindowsBackend: undo_bootini F:
12-24 13:17 DEBUG WindowsBackend: undo_configsys Drive(F: hd 5612.8125 mb free fat32)
12-24 13:17 DEBUG TaskList: ## Finished Remove bootloader entry
12-24 13:17 DEBUG TaskList: ## Running Remove target dir...
12-24 13:17 DEBUG CommonBackend: Deleting C:\ubuntu
12-24 13:17 DEBUG TaskList: ## Finished Remove target dir
12-24 13:17 DEBUG TaskList: ## Running Remove registry key...
12-24 13:17 DEBUG TaskList: ## Finished Remove registry key
12-24 13:17 DEBUG TaskList: # Finished tasklist
12-24 13:17 INFO root: Almost finished uninstalling
12-24 13:17 INFO root: Finished uninstallation
12-24 13:17 DEBUG CommonBackend: Fetching basic info...
12-24 13:17 DEBUG CommonBackend: original_exe=C:\Documents and Settings\Zameer Abdulla\Desktop\wubi.exe
12-24 13:17 DEBUG CommonBackend: platform=win32
12-24 13:17 DEBUG CommonBackend: osname=nt
12-24 13:17 DEBUG WindowsBackend: arch=i386
12-24 13:17 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
12-24 13:17 DEBUG CommonBackend: Adding distro Xubuntu-i386
12-24 13:17 DEBUG CommonBackend: Adding distro Xubuntu-amd64
12-24 13:17 DEBUG CommonBackend: Adding distro Kubuntu-amd64
12-24 13:17 DEBUG CommonBackend: Adding distro Mythbuntu-i386
12-24 13:17 DEBUG CommonBackend: Adding distro Ubuntu-amd64
12-24 13:17 DEBUG CommonBackend: Adding distro Ubuntu-i386
12-24 13:17 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
12-24 13:17 DEBUG CommonBackend: Adding distro Kubuntu-i386
12-24 13:17 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
12-24 13:17 DEBUG WindowsBackend: Fetching host info...
12-24 13:17 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-24 13:17 DEBUG WindowsBackend: windows version=xp
12-24 13:17 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
12-24 13:17 DEBUG WindowsBackend: windows_sp=Service Pack 3
12-24 13:17 DEBUG WindowsBackend: windows_build=2600
12-24 13:17 DEBUG WindowsBackend: gmt=4
12-24 13:17 DEBUG WindowsBackend: country=US
12-24 13:17 DEBUG WindowsBackend: timezone=America/New_York
12-24 13:17 DEBUG WindowsBackend: windows_username=Zameer Abdulla
12-24 13:17 DEBUG WindowsBackend: user_full_name=Zameer Abdulla
12-24 13:17 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Zameer Abdulla
12-24 13:17 DEBUG WindowsBackend: windows_language_code=1033
12-24 13:17 DEBUG WindowsBackend: windows_language=English
12-24 13:17 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 1.60GHz
12-24 13:17 DEBUG WindowsBackend: bootloader=xp
12-24 13:17 DEBUG WindowsBackend: system_drive=Drive(C: hd 55245.484375 mb free ntfs)
12-24 13:17 DEBUG WindowsBackend: drive=Drive(C: hd 55245.484375 mb free ntfs)
12-24 13:17 DEBUG WindowsBackend: drive=Drive(D: hd 88272.5 mb free ntfs)
12-24 13:17 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-24 13:17 DEBUG WindowsBackend: drive=Drive(F: hd 5612.8125 mb free fat32)
12-24 13:17 DEBUG WindowsBackend: uninstaller_path=None
12-24 13:17 DEBUG WindowsBackend: previous_target_dir=None
12-24 13:17 DEBUG WindowsBackend: previous_distro_name=None
12-24 13:17 DEBUG WindowsBackend: keyboard_id=67699721
12-24 13:17 DEBUG WindowsBackend: keyboard_layout=us
12-24 13:17 DEBUG WindowsBackend: keyboard_variant=
12-24 13:17 DEBUG WindowsBackend: total_memory_mb=895.421875
12-24 13:17 DEBUG CommonBackend: Searching ISOs on USB devices
12-24 13:17 DEBUG Distro: checking Ubuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Ubuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Ubuntu Netbook ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Kubuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Kubuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Xubuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Xubuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Mythbuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Mythbuntu ISO F:\linuxmint-12-gnome-dvd-32bit.iso
12-24 13:17 DEBUG Distro: wrong size: 1077379072 > 900000000
12-24 13:17 DEBUG Distro: checking Ubuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Ubuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Ubuntu Netbook ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Kubuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Kubuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Xubuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Xubuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Mythbuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG Distro: checking Mythbuntu ISO F:\sabily-11.10-desktop-i386-full.iso
12-24 13:17 DEBUG Distro: wrong size: 1701632000 > 900000000
12-24 13:17 DEBUG CommonBackend: Searching for local CDs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 INFO root: Running the installer...
12-24 13:17 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
12-24 13:17 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
12-24 13:17 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=zameerabdulla
12-24 13:17 INFO root: Received settings
12-24 13:17 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
12-24 13:17 DEBUG TaskList: # Running tasklist...
12-24 13:17 DEBUG TaskList: ## Running select_target_dir...
12-24 13:17 INFO WindowsBackend: Installing into C:\ubuntu
12-24 13:17 DEBUG TaskList: ## Finished select_target_dir
12-24 13:17 DEBUG TaskList: ## Running create_dir_structure...
12-24 13:17 DEBUG CommonBackend: Creating dir C:\ubuntu
12-24 13:17 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
12-24 13:17 DEBUG CommonBackend: Creating dir C:\ubuntu\install
12-24 13:17 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
12-24 13:17 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
12-24 13:17 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-24 13:17 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-24 13:17 DEBUG TaskList: ## Finished create_dir_structure
12-24 13:17 DEBUG TaskList: ## Running uncompress_target_dir...
12-24 13:17 DEBUG TaskList: ## Finished uncompress_target_dir
12-24 13:17 DEBUG TaskList: ## Running create_uninstaller...
12-24 13:17 DEBUG WindowsBackend: Copying uninstaller C:\Documents and Settings\Zameer Abdulla\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-24 13:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-24 13:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-24 13:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-24 13:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-24 13:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
12-24 13:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-24 13:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-24 13:17 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-24 13:17 DEBUG TaskList: ## Finished create_uninstaller
12-24 13:17 DEBUG TaskList: ## Running copy_installation_files...
12-24 13:17 DEBUG WindowsBackend: Copying C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
12-24 13:17 DEBUG WindowsBackend: Copying C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\winboot -> C:\ubuntu\winboot
12-24 13:17 DEBUG WindowsBackend: Copying C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
12-24 13:17 DEBUG TaskList: ## Finished copy_installation_files
12-24 13:17 DEBUG TaskList: ## Running get_iso...
12-24 13:17 DEBUG CommonBackend: Searching for local CD
12-24 13:17 DEBUG Distro: checking whether C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain C:\DOCUME~1\ZAMEER~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
12-24 13:17 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
12-24 13:17 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
12-24 13:17 DEBUG CommonBackend: Searching for local ISO
12-24 13:17 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
12-24 13:17 DEBUG TaskList: New task get_metalink
12-24 13:17 DEBUG TaskList: ### Running get_metalink...
12-24 13:17 DEBUG downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > C:\ubuntu\install
12-24 13:17 DEBUG downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink, basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
12-24 13:17 DEBUG downloader: download finished (read 28158 bytes)
12-24 13:17 DEBUG downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
12-24 13:17 DEBUG downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
12-24 13:17 DEBUG downloader: download finished (read 874 bytes)
12-24 13:17 DEBUG downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
12-24 13:17 DEBUG downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
12-24 13:17 DEBUG downloader: download finished (read 198 bytes)
12-24 13:17 INFO saplog: Verified a signature from ID:'46181433FBB75451'.
12-24 13:17 INFO saplog: Checking block bindings..
12-24 13:17 INFO saplog: Key verified successfully.
12-24 13:17 DEBUG CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65 ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3 ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2 ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488 ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1 ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1 ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449 ubuntu-11.04-server-i386.metalink
12-24 13:17 DEBUG TaskList: ### Finished get_metalink
12-24 13:17 DEBUG TaskList: New task download
12-24 13:17 DEBUG TaskList: ### Running download...
12-24 13:17 DEBUG btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
12-24 14:52 ERROR TaskList: Traceback (most recent call last):
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
 
12-24 14:52 ERROR TaskList: Non fatal error Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
File "\lib\bittorrent\Rerequester.py", line 96, in fail
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request
in task download
12-24 14:52 DEBUG TaskList: ### Finished download
12-24 14:52 ERROR TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
12-24 14:52 DEBUG TaskList: # Cancelling tasklist
12-24 14:52 ERROR root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
Traceback (most recent call last):
File "\lib\wubi\application.py", line 57, in run
File "\lib\wubi\application.py", line 131, in select_task
File "\lib\wubi\application.py", line 157, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-i386.iso'
12-24 14:52 DEBUG TaskList: # Finished tasklist
```
 
 
What is the solution? I have tried with cd and wubi online version all gets fail.:confused:

---

### Post by darkod on 2011-12-24
1. It's better to use a proper dual boot and not a wubi install which works inside windows.

2. If you still prefer to use wubi, if you have vista or 7 when you are executing the wubi.exe don't do it with double click. Instead try with right-click and Run As Administrator... Windows permissions might be blocking it.

3. Another option to install wubi is downloading the ISO first, then use any program that can open an ISO file and extract the wubi.exe from the ISO (it's inside). Then put both the full ISO and the wubi.exe in the same folder and execute wubi.exe as above. In that case it will use the ISO and not try to download from the internet.

---

### Post by ZmrAbdulla on 2011-12-24
Actually this is for my children's PC. Their first choice is Windows. Optionally they need ubuntu actually Sabily (version of ubuntu) If I do a duel boot then linux will be their first choice that I don't want. My laptop I am running Mint perfectly for a couple of years.
 
I will try Run as Administrator..

---

### Post by darkod on 2011-12-24
You can select what OS you want to be default, it doesn't need to be ubuntu.

---

### Post by bcbc on 2011-12-24
The problem is that windows firewall (or your internet service provider?) is blocking the bittorrent client. You should have seen a popup asking you to allow 'pyrun.exe' access to your firewall.

You can also download the desktop CD ISO and save it in the same folder as wubi.exe before running. For 11.04 get them here:
[http://releases.ubuntu.com/11.04/](http://releases.ubuntu.com/11.04/)  (you need the 32-bit version)

In terms of installing sabily or some other distro you cannot do this with a normal wubi.exe as it's built specifically for the standard Ubuntu distros - and also each wubi is specific to a release.

You can probably add the sabily ppa once ubuntu is installed through wubi, but it looks like Sabily has it's own 'windows-installer': [http://www.sabily.org/wiki/index.php/Wisabi](http://www.sabily.org/wiki/index.php/Wisabi)

---

### Post by ZmrAbdulla on 2011-12-25
Problem was Admin rights.. I did it by choosing "Run As Administrator" it did the work. I did the unblocking of pyrun.exe too.
There were problems..
I downloaded the Sabily iso file and expanded to a folder with 7zip. Then tried running wubi(wisabi). It was still giving error message saying there is no media in the cd drive. buttons were CANCEL , RETRY , CONTINUE . After many random clicks on buttons it started. Then everything was smooth.
Now it is working smooth.

I read you can select default OS, but I don't want to play with it now.

Thanks to all..

---

