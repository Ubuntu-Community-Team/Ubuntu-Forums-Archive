---
title: "Wubi 10.04 could not retrieve the required installation files"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by USFMD82 on 2010-11-29
Hey everyone I just tried for the second time to load Xubuntu again ( I recently formatted the drive it was on tor try to do a clean install when I start the DL it uninstalls any previous version then goes forward then about 2 hours later I get the error "Could not retrieve the required installation files" I have included the error log. Thanks in advance for any assistance!


> 11-27 15:13 INFO   root: === wubi 10.04.1 rev190 ===
11-27 15:13 DEBUG  root: Logfile is c:\docume~1\timber\locals~1\temp\wubi-10.04.1-rev190.log
11-27 15:13 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Timber\\My Documents\\Downloads\\wubi(2).exe"']
11-27 15:13 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp\data
11-27 15:13 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp\bin\7z.exe
11-27 15:13 DEBUG  CommonBackend: Fetching basic info...
11-27 15:13 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Timber\My Documents\Downloads\wubi(2).exe
11-27 15:13 DEBUG  CommonBackend: platform=win32
11-27 15:13 DEBUG  CommonBackend: osname=nt
11-27 15:13 DEBUG  CommonBackend: language=en_US
11-27 15:13 DEBUG  CommonBackend: encoding=cp1252
11-27 15:13 DEBUG  WindowsBackend: arch=amd64
11-27 15:13 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp\data\isolist.ini
11-27 15:13 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-27 15:13 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-27 15:13 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-27 15:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-27 15:13 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-27 15:13 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-27 15:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-27 15:13 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-27 15:13 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-27 15:13 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-27 15:13 DEBUG  WindowsBackend: Fetching host info...
11-27 15:13 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-27 15:13 DEBUG  WindowsBackend: windows version=xp
11-27 15:13 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-27 15:13 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-27 15:13 DEBUG  WindowsBackend: windows_build=2600
11-27 15:13 DEBUG  WindowsBackend: gmt=-5
11-27 15:13 DEBUG  WindowsBackend: country=US
11-27 15:13 DEBUG  WindowsBackend: timezone=America/New_York
11-27 15:13 DEBUG  WindowsBackend: windows_username=Timber
11-27 15:13 DEBUG  WindowsBackend: user_full_name=Timber
11-27 15:13 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Timber
11-27 15:13 DEBUG  WindowsBackend: windows_language_code=1033
11-27 15:13 DEBUG  WindowsBackend: windows_language=English
11-27 15:13 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 Mobile Technology ML-30
11-27 15:13 DEBUG  WindowsBackend: bootloader=xp
11-27 15:13 DEBUG  WindowsBackend: system_drive=Drive(C: hd 27369.5039063 mb free ntfs)
11-27 15:13 DEBUG  WindowsBackend: drive=Drive(C: hd 27369.5039063 mb free ntfs)
11-27 15:13 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-27 15:13 DEBUG  WindowsBackend: drive=Drive(E: hd 9956.42578125 mb free ntfs)
11-27 15:13 DEBUG  WindowsBackend: uninstaller_path=None
11-27 15:13 DEBUG  WindowsBackend: previous_target_dir=None
11-27 15:13 DEBUG  WindowsBackend: previous_distro_name=None
11-27 15:13 DEBUG  WindowsBackend: keyboard_id=67699721
11-27 15:13 DEBUG  WindowsBackend: keyboard_layout=us
11-27 15:13 DEBUG  WindowsBackend: keyboard_variant=
11-27 15:13 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-27 15:13 DEBUG  CommonBackend: locale=en_US.UTF-8
11-27 15:13 DEBUG  WindowsBackend: total_memory_mb=382.484375
11-27 15:13 DEBUG  CommonBackend: Searching ISOs on USB devices
11-27 15:13 DEBUG  CommonBackend: Searching for local CDs
11-27 15:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp is a valid Ubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp is a valid Ubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp is a valid Ubuntu Netbook CD
11-27 15:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp is a valid Kubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp is a valid Kubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp is a valid Kubuntu Netbook CD
11-27 15:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp is a valid Xubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp is a valid Xubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp is a valid Mythbuntu CD
11-27 15:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp is a valid Mythbuntu CD
11-27 15:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-27 15:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-27 15:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-27 15:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-27 15:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-27 15:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-27 15:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-27 15:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-27 15:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 15:13 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-27 15:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 15:13 INFO   root: Running the installer...
11-27 15:13 DEBUG  WindowsFrontend: __init__...
11-27 15:13 DEBUG  WindowsFrontend: on_init...
11-27 15:13 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp\translations, languages=['en_US', 'en']
11-27 15:13 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl99.tmp\translations, languages=['en_US', 'en']
11-27 16:52 INFO   root: === wubi 10.04.1 rev190 ===
11-27 16:52 DEBUG  root: Logfile is c:\docume~1\timber\locals~1\temp\wubi-10.04.1-rev190.log
11-27 16:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Timber\\My Documents\\Downloads\\wubi(2).exe"']
11-27 16:52 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\data
11-27 16:52 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\bin\7z.exe
11-27 16:52 DEBUG  CommonBackend: Fetching basic info...
11-27 16:52 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Timber\My Documents\Downloads\wubi(2).exe
11-27 16:52 DEBUG  CommonBackend: platform=win32
11-27 16:52 DEBUG  CommonBackend: osname=nt
11-27 16:52 DEBUG  CommonBackend: language=en_US
11-27 16:52 DEBUG  CommonBackend: encoding=cp1252
11-27 16:53 DEBUG  WindowsBackend: arch=amd64
11-27 16:53 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\data\isolist.ini
11-27 16:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-27 16:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-27 16:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-27 16:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-27 16:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-27 16:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-27 16:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-27 16:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-27 16:53 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-27 16:53 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-27 16:53 DEBUG  WindowsBackend: Fetching host info...
11-27 16:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-27 16:53 DEBUG  WindowsBackend: windows version=xp
11-27 16:53 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-27 16:53 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-27 16:53 DEBUG  WindowsBackend: windows_build=2600
11-27 16:53 DEBUG  WindowsBackend: gmt=-5
11-27 16:53 DEBUG  WindowsBackend: country=US
11-27 16:53 DEBUG  WindowsBackend: timezone=America/New_York
11-27 16:53 DEBUG  WindowsBackend: windows_username=Timber
11-27 16:53 DEBUG  WindowsBackend: user_full_name=Timber
11-27 16:53 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Timber
11-27 16:53 DEBUG  WindowsBackend: windows_language_code=1033
11-27 16:53 DEBUG  WindowsBackend: windows_language=English
11-27 16:53 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 Mobile Technology ML-30
11-27 16:53 DEBUG  WindowsBackend: bootloader=xp
11-27 16:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 27237.9375 mb free ntfs)
11-27 16:53 DEBUG  WindowsBackend: drive=Drive(C: hd 27237.9375 mb free ntfs)
11-27 16:53 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-27 16:53 DEBUG  WindowsBackend: drive=Drive(E: hd 9956.3828125 mb free ntfs)
11-27 16:53 DEBUG  WindowsBackend: uninstaller_path=None
11-27 16:53 DEBUG  WindowsBackend: previous_target_dir=None
11-27 16:53 DEBUG  WindowsBackend: previous_distro_name=None
11-27 16:53 DEBUG  WindowsBackend: keyboard_id=67699721
11-27 16:53 DEBUG  WindowsBackend: keyboard_layout=us
11-27 16:53 DEBUG  WindowsBackend: keyboard_variant=
11-27 16:53 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-27 16:53 DEBUG  CommonBackend: locale=en_US.UTF-8
11-27 16:53 DEBUG  WindowsBackend: total_memory_mb=382.484375
11-27 16:53 DEBUG  CommonBackend: Searching ISOs on USB devices
11-27 16:53 DEBUG  CommonBackend: Searching for local CDs
11-27 16:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu Netbook CD
11-27 16:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu Netbook CD
11-27 16:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Xubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Xubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Mythbuntu CD
11-27 16:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Mythbuntu CD
11-27 16:53 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-27 16:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-27 16:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-27 16:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-27 16:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-27 16:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-27 16:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-27 16:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-27 16:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 16:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-27 16:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 16:53 INFO   root: Running the installer...
11-27 16:53 DEBUG  WindowsFrontend: __init__...
11-27 16:53 DEBUG  WindowsFrontend: on_init...
11-27 16:53 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\translations, languages=['en_US', 'en']
11-27 16:53 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\translations, languages=['en_US', 'en']
11-27 16:54 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=6000MB, distro_name=Xubuntu, language=en_US, locale=en_US.UTF-8, username=timber
11-27 16:54 INFO   root: Received settings
11-27 16:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\translations, languages=['en_US', 'en']
11-27 16:54 DEBUG  TaskList: # Running tasklist...
11-27 16:54 DEBUG  TaskList: ## Running select_target_dir...
11-27 16:54 INFO   WindowsBackend: Installing into E:\ubuntu
11-27 16:54 DEBUG  TaskList: ## Finished select_target_dir
11-27 16:54 DEBUG  TaskList: ## Running create_dir_structure...
11-27 16:54 DEBUG  CommonBackend: Creating dir E:\ubuntu
11-27 16:54 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
11-27 16:54 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
11-27 16:54 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
11-27 16:54 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
11-27 16:54 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
11-27 16:54 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
11-27 16:54 DEBUG  TaskList: ## Finished create_dir_structure
11-27 16:54 DEBUG  TaskList: ## Running uncompress_target_dir...
11-27 16:54 DEBUG  TaskList: ## Finished uncompress_target_dir
11-27 16:54 DEBUG  TaskList: ## Running create_uninstaller...
11-27 16:54 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Timber\My Documents\Downloads\wubi(2).exe -> E:\ubuntu\uninstall-wubi.exe
11-27 16:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
11-27 16:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
11-27 16:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Xubuntu
11-27 16:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Xubuntu.ico
11-27 16:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
11-27 16:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Xubuntu
11-27 16:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.xubuntu.org](http://www.xubuntu.org)
11-27 16:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-27 16:54 DEBUG  TaskList: ## Finished create_uninstaller
11-27 16:54 DEBUG  TaskList: ## Running copy_installation_files...
11-27 16:54 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
11-27 16:54 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\winboot -> E:\ubuntu\winboot
11-27 16:54 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\data\images\Xubuntu.ico -> E:\ubuntu\Xubuntu.ico
11-27 16:54 DEBUG  TaskList: ## Finished copy_installation_files
11-27 16:54 DEBUG  TaskList: ## Running get_iso...
11-27 16:54 DEBUG  CommonBackend: Searching for local CD
11-27 16:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Xubuntu CD
11-27 16:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 16:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-27 16:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 16:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-27 16:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 16:54 DEBUG  CommonBackend: Searching for local ISO
11-27 16:54 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-27 16:54 DEBUG  TaskList: New task get_metalink
11-27 16:54 DEBUG  TaskList: ### Running get_metalink...
11-27 16:54 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.metalink](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.metalink) > E:\ubuntu\install
11-27 16:54 DEBUG  downloader: Download start filename=E:\ubuntu\install\xubuntu-10.04-desktop-amd64.metalink, url=http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.metalink, basename=xubuntu-10.04-desktop-amd64.metalink, length=1040, text=None
11-27 16:54 DEBUG  downloader: download finished (read 1040 bytes)
11-27 16:54 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink) > E:\ubuntu\install
11-27 16:54 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=286, text=None
11-27 16:54 DEBUG  downloader: download finished (read 286 bytes)
11-27 16:54 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink.gpg) > E:\ubuntu\install
11-27 16:54 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
11-27 16:54 DEBUG  downloader: download finished (read 189 bytes)
11-27 16:55 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
11-27 16:55 INFO   saplog: Checking block bindings..
11-27 16:55 INFO   saplog: Key verified successfully.
11-27 16:55 DEBUG  CommonBackend: metalink md5sums:
51280667f7b7be855a7d23ed66999e9b  xubuntu-10.04-alternate-amd64.metalink
2a2fab45952f209a298c5eb95b77647e  xubuntu-10.04-alternate-i386.metalink
d1d8cc67218541ead271d34354082a9e  xubuntu-10.04-desktop-amd64.metalink
6e8062756564c48d43f970bfa35f867a  xubuntu-10.04-desktop-i386.metalink

11-27 16:55 DEBUG  TaskList: ### Finished get_metalink
11-27 16:55 DEBUG  TaskList: New task download
11-27 16:55 DEBUG  TaskList: ### Running download...
11-27 16:55 DEBUG  btdownloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso.torrent) > E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-27 17:34 DEBUG  TaskList: ### Finished download
11-27 17:34 DEBUG  TaskList: New task check_iso
11-27 17:34 DEBUG  TaskList: ### Running check_iso...
11-27 17:34 DEBUG  CommonBackend: Checking E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-27 17:34 DEBUG  Distro:   checking Xubuntu ISO E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-27 17:34 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-27 17:34 DEBUG  Distro:   parsing info from str=Xubuntu 10.04 "Lucid Lynx" - Release amd64 (20100429)
11-27 17:34 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
11-27 17:34 DEBUG  Distro: wrong version: 10.04 != 10.04.1
11-27 17:34 DEBUG  TaskList: ### Finished check_iso
11-27 17:34 DEBUG  TaskList: New task download
11-27 17:34 DEBUG  TaskList: ### Running download...
11-27 17:34 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso) > E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-27 17:34 DEBUG  downloader: Download start filename=E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso, url=http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso, basename=xubuntu-10.04-desktop-amd64.iso, length=728844288, text=None
11-27 19:51 DEBUG  TaskList: ### Finished download
11-27 19:51 DEBUG  downloader: download finished (read 728844288 bytes)
11-27 19:51 DEBUG  TaskList: New task check_iso
11-27 19:51 DEBUG  TaskList: ### Running check_iso...
11-27 19:51 DEBUG  CommonBackend: Checking E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-27 19:51 DEBUG  Distro:   checking Xubuntu ISO E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-27 19:51 DEBUG  Distro: wrong version: 10.04 != 10.04.1
11-27 19:51 DEBUG  TaskList: ### Finished check_iso
11-27 19:51 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
11-27 19:51 DEBUG  TaskList: # Cancelling tasklist
11-27 19:51 DEBUG  TaskList: # Finished tasklist
11-27 19:51 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
11-27 22:15 INFO   root: === wubi 10.04.1 rev190 ===
11-27 22:15 DEBUG  root: Logfile is c:\docume~1\timber\locals~1\temp\wubi-10.04.1-rev190.log
11-27 22:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Timber\\My Documents\\Downloads\\wubi(2).exe"']
11-27 22:15 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\data
11-27 22:15 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\bin\7z.exe
11-27 22:15 DEBUG  CommonBackend: Fetching basic info...
11-27 22:15 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Timber\My Documents\Downloads\wubi(2).exe
11-27 22:15 DEBUG  CommonBackend: platform=win32
11-27 22:15 DEBUG  CommonBackend: osname=nt
11-27 22:15 DEBUG  CommonBackend: language=en_US
11-27 22:15 DEBUG  CommonBackend: encoding=cp1252
11-27 22:15 DEBUG  WindowsBackend: arch=amd64
11-27 22:15 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\data\isolist.ini
11-27 22:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-27 22:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-27 22:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-27 22:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-27 22:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-27 22:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-27 22:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-27 22:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-27 22:15 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-27 22:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-27 22:15 DEBUG  WindowsBackend: Fetching host info...
11-27 22:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-27 22:15 DEBUG  WindowsBackend: windows version=xp
11-27 22:15 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-27 22:15 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-27 22:15 DEBUG  WindowsBackend: windows_build=2600
11-27 22:15 DEBUG  WindowsBackend: gmt=-5
11-27 22:15 DEBUG  WindowsBackend: country=US
11-27 22:15 DEBUG  WindowsBackend: timezone=America/New_York
11-27 22:15 DEBUG  WindowsBackend: windows_username=Timber
11-27 22:15 DEBUG  WindowsBackend: user_full_name=Timber
11-27 22:15 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Timber
11-27 22:15 DEBUG  WindowsBackend: windows_language_code=1033
11-27 22:15 DEBUG  WindowsBackend: windows_language=English
11-27 22:15 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 Mobile Technology ML-30
11-27 22:15 DEBUG  WindowsBackend: bootloader=xp
11-27 22:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 25874.953125 mb free ntfs)
11-27 22:15 DEBUG  WindowsBackend: drive=Drive(C: hd 25874.953125 mb free ntfs)
11-27 22:15 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-27 22:15 DEBUG  WindowsBackend: drive=Drive(E: hd 9954.81640625 mb free ntfs)
11-27 22:15 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
11-27 22:15 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
11-27 22:15 DEBUG  WindowsBackend: previous_distro_name=Xubuntu
11-27 22:15 DEBUG  WindowsBackend: keyboard_id=67699721
11-27 22:15 DEBUG  WindowsBackend: keyboard_layout=us
11-27 22:15 DEBUG  WindowsBackend: keyboard_variant=
11-27 22:15 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-27 22:15 DEBUG  CommonBackend: locale=en_US.UTF-8
11-27 22:15 DEBUG  WindowsBackend: total_memory_mb=382.484375
11-27 22:15 DEBUG  CommonBackend: Searching ISOs on USB devices
11-27 22:15 DEBUG  CommonBackend: Searching for local CDs
11-27 22:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu Netbook CD
11-27 22:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu Netbook CD
11-27 22:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Xubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Xubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Mythbuntu CD
11-27 22:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Mythbuntu CD
11-27 22:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-27 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-27 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-27 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-27 22:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-27 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-27 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-27 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-27 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-27 22:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:15 INFO   root: Already installed, running the uninstaller...
11-27 22:15 INFO   root: Running the uninstaller...
11-27 22:15 INFO   CommonBackend: This is the uninstaller running
11-27 22:15 DEBUG  WindowsFrontend: __init__...
11-27 22:16 DEBUG  WindowsFrontend: on_init...
11-27 22:16 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\translations, languages=['en_US', 'en']
11-27 22:16 INFO   root: Received settings
11-27 22:16 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\translations, languages=['en_US', 'en']
11-27 22:16 DEBUG  TaskList: # Running tasklist...
11-27 22:16 DEBUG  TaskList: ## Running Backup ISO...
11-27 22:16 DEBUG  TaskList: ## Finished Backup ISO
11-27 22:16 DEBUG  TaskList: ## Running Remove bootloader entry...
11-27 22:16 ERROR  WindowsBackend: Cannot find bcdedit
11-27 22:16 DEBUG  WindowsBackend: undo_bootini C:
11-27 22:16 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 25874.953125 mb free ntfs)
11-27 22:16 DEBUG  WindowsBackend: undo_bootini E:
11-27 22:16 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 9954.81640625 mb free ntfs)
11-27 22:16 DEBUG  TaskList: ## Finished Remove bootloader entry
11-27 22:16 DEBUG  TaskList: ## Running Remove target dir...
11-27 22:16 DEBUG  CommonBackend: Deleting E:\ubuntu
11-27 22:16 DEBUG  TaskList: ## Finished Remove target dir
11-27 22:16 DEBUG  TaskList: ## Running Remove registry key...
11-27 22:16 DEBUG  TaskList: ## Finished Remove registry key
11-27 22:16 DEBUG  TaskList: # Finished tasklist
11-27 22:16 INFO   root: Almost finished uninstalling
11-27 22:16 INFO   root: Finished uninstallation
11-27 22:16 DEBUG  CommonBackend: Fetching basic info...
11-27 22:16 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Timber\My Documents\Downloads\wubi(2).exe
11-27 22:16 DEBUG  CommonBackend: platform=win32
11-27 22:16 DEBUG  CommonBackend: osname=nt
11-27 22:16 DEBUG  WindowsBackend: arch=amd64
11-27 22:16 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\data\isolist.ini
11-27 22:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-27 22:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-27 22:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-27 22:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-27 22:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-27 22:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-27 22:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-27 22:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-27 22:16 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-27 22:16 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-27 22:16 DEBUG  WindowsBackend: Fetching host info...
11-27 22:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-27 22:16 DEBUG  WindowsBackend: windows version=xp
11-27 22:16 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-27 22:16 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-27 22:16 DEBUG  WindowsBackend: windows_build=2600
11-27 22:16 DEBUG  WindowsBackend: gmt=-5
11-27 22:16 DEBUG  WindowsBackend: country=US
11-27 22:16 DEBUG  WindowsBackend: timezone=America/New_York
11-27 22:16 DEBUG  WindowsBackend: windows_username=Timber
11-27 22:16 DEBUG  WindowsBackend: user_full_name=Timber
11-27 22:16 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Timber
11-27 22:16 DEBUG  WindowsBackend: windows_language_code=1033
11-27 22:16 DEBUG  WindowsBackend: windows_language=English
11-27 22:16 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 Mobile Technology ML-30
11-27 22:16 DEBUG  WindowsBackend: bootloader=xp
11-27 22:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 25891.3125 mb free ntfs)
11-27 22:16 DEBUG  WindowsBackend: drive=Drive(C: hd 25891.3125 mb free ntfs)
11-27 22:16 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-27 22:16 DEBUG  WindowsBackend: drive=Drive(E: hd 9954.9140625 mb free ntfs)
11-27 22:16 DEBUG  WindowsBackend: uninstaller_path=None
11-27 22:16 DEBUG  WindowsBackend: previous_target_dir=None
11-27 22:16 DEBUG  WindowsBackend: previous_distro_name=None
11-27 22:16 DEBUG  WindowsBackend: keyboard_id=67699721
11-27 22:16 DEBUG  WindowsBackend: keyboard_layout=us
11-27 22:16 DEBUG  WindowsBackend: keyboard_variant=
11-27 22:16 DEBUG  WindowsBackend: total_memory_mb=382.484375
11-27 22:16 DEBUG  CommonBackend: Searching ISOs on USB devices
11-27 22:16 DEBUG  CommonBackend: Searching for local CDs
11-27 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu Netbook CD
11-27 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu Netbook CD
11-27 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Xubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Xubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Mythbuntu CD
11-27 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Mythbuntu CD
11-27 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-27 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-27 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-27 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-27 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-27 22:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-27 22:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-27 22:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-27 22:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-27 22:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:16 INFO   root: Running the installer...
11-27 22:16 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\translations, languages=['en_US', 'en']
11-27 22:16 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\translations, languages=['en_US', 'en']
11-27 22:17 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=6000MB, distro_name=Xubuntu, language=en_US, locale=en_US.UTF-8, username=timber
11-27 22:17 INFO   root: Received settings
11-27 22:17 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\translations, languages=['en_US', 'en']
11-27 22:17 DEBUG  TaskList: # Running tasklist...
11-27 22:17 DEBUG  TaskList: ## Running select_target_dir...
11-27 22:17 INFO   WindowsBackend: Installing into E:\ubuntu
11-27 22:17 DEBUG  TaskList: ## Finished select_target_dir
11-27 22:17 DEBUG  TaskList: ## Running create_dir_structure...
11-27 22:17 DEBUG  CommonBackend: Creating dir E:\ubuntu
11-27 22:17 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
11-27 22:17 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
11-27 22:17 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
11-27 22:17 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
11-27 22:17 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
11-27 22:17 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
11-27 22:17 DEBUG  TaskList: ## Finished create_dir_structure
11-27 22:17 DEBUG  TaskList: ## Running uncompress_target_dir...
11-27 22:17 DEBUG  TaskList: ## Finished uncompress_target_dir
11-27 22:17 DEBUG  TaskList: ## Running create_uninstaller...
11-27 22:17 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Timber\My Documents\Downloads\wubi(2).exe -> E:\ubuntu\uninstall-wubi.exe
11-27 22:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
11-27 22:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
11-27 22:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Xubuntu
11-27 22:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Xubuntu.ico
11-27 22:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
11-27 22:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Xubuntu
11-27 22:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.xubuntu.org](http://www.xubuntu.org)
11-27 22:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-27 22:17 DEBUG  TaskList: ## Finished create_uninstaller
11-27 22:17 DEBUG  TaskList: ## Running copy_installation_files...
11-27 22:17 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
11-27 22:17 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\winboot -> E:\ubuntu\winboot
11-27 22:17 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\data\images\Xubuntu.ico -> E:\ubuntu\Xubuntu.ico
11-27 22:17 DEBUG  TaskList: ## Finished copy_installation_files
11-27 22:17 DEBUG  TaskList: ## Running get_iso...
11-27 22:17 DEBUG  CommonBackend: Searching for local CD
11-27 22:17 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp is a valid Xubuntu CD
11-27 22:17 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs
11-27 22:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-27 22:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-27 22:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-27 22:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-27 22:17 DEBUG  CommonBackend: Searching for local ISO
11-27 22:17 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-27 22:17 DEBUG  TaskList: New task get_metalink
11-27 22:17 DEBUG  TaskList: ### Running get_metalink...
11-27 22:17 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.metalink](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.metalink) > E:\ubuntu\install
11-27 22:18 DEBUG  downloader: Download start filename=E:\ubuntu\install\xubuntu-10.04-desktop-amd64.metalink, url=http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.metalink, basename=xubuntu-10.04-desktop-amd64.metalink, length=1040, text=None
11-27 22:18 DEBUG  downloader: download finished (read 1040 bytes)
11-27 22:18 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink) > E:\ubuntu\install
11-27 22:18 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=286, text=None
11-27 22:18 DEBUG  downloader: download finished (read 286 bytes)
11-27 22:18 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink.gpg) > E:\ubuntu\install
11-27 22:18 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
11-27 22:18 DEBUG  downloader: download finished (read 189 bytes)
11-27 22:18 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
11-27 22:18 INFO   saplog: Checking block bindings..
11-27 22:18 INFO   saplog: Key verified successfully.
11-27 22:18 DEBUG  CommonBackend: metalink md5sums:
51280667f7b7be855a7d23ed66999e9b  xubuntu-10.04-alternate-amd64.metalink
2a2fab45952f209a298c5eb95b77647e  xubuntu-10.04-alternate-i386.metalink
d1d8cc67218541ead271d34354082a9e  xubuntu-10.04-desktop-amd64.metalink
6e8062756564c48d43f970bfa35f867a  xubuntu-10.04-desktop-i386.metalink

11-27 22:18 DEBUG  TaskList: ### Finished get_metalink
11-27 22:18 DEBUG  TaskList: New task download
11-27 22:18 DEBUG  TaskList: ### Running download...
11-27 22:18 DEBUG  btdownloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso.torrent) > E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-28 18:54 INFO   root: === wubi 10.04.1 rev190 ===
11-28 18:54 DEBUG  root: Logfile is c:\docume~1\timber\locals~1\temp\wubi-10.04.1-rev190.log
11-28 18:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Timber\\My Documents\\Downloads\\wubi(2).exe"']
11-28 18:54 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\data
11-28 18:54 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\bin\7z.exe
11-28 18:54 DEBUG  CommonBackend: Fetching basic info...
11-28 18:54 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Timber\My Documents\Downloads\wubi(2).exe
11-28 18:54 DEBUG  CommonBackend: platform=win32
11-28 18:54 DEBUG  CommonBackend: osname=nt
11-28 18:54 DEBUG  CommonBackend: language=en_US
11-28 18:54 DEBUG  CommonBackend: encoding=cp1252
11-28 18:54 DEBUG  WindowsBackend: arch=amd64
11-28 18:54 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\data\isolist.ini
11-28 18:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-28 18:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-28 18:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-28 18:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-28 18:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-28 18:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-28 18:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-28 18:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-28 18:54 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-28 18:54 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-28 18:54 DEBUG  WindowsBackend: Fetching host info...
11-28 18:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-28 18:54 DEBUG  WindowsBackend: windows version=xp
11-28 18:54 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-28 18:54 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-28 18:54 DEBUG  WindowsBackend: windows_build=2600
11-28 18:54 DEBUG  WindowsBackend: gmt=-5
11-28 18:54 DEBUG  WindowsBackend: country=US
11-28 18:54 DEBUG  WindowsBackend: timezone=America/New_York
11-28 18:54 DEBUG  WindowsBackend: windows_username=Timber
11-28 18:54 DEBUG  WindowsBackend: user_full_name=Timber
11-28 18:54 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Timber
11-28 18:54 DEBUG  WindowsBackend: windows_language_code=1033
11-28 18:54 DEBUG  WindowsBackend: windows_language=English
11-28 18:54 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 Mobile Technology ML-30
11-28 18:54 DEBUG  WindowsBackend: bootloader=xp
11-28 18:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 25781.5234375 mb free ntfs)
11-28 18:54 DEBUG  WindowsBackend: drive=Drive(C: hd 25781.5234375 mb free ntfs)
11-28 18:54 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-28 18:54 DEBUG  WindowsBackend: drive=Drive(E: hd 9649.859375 mb free ntfs)
11-28 18:54 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
11-28 18:54 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
11-28 18:54 DEBUG  WindowsBackend: previous_distro_name=Xubuntu
11-28 18:54 DEBUG  WindowsBackend: keyboard_id=67699721
11-28 18:54 DEBUG  WindowsBackend: keyboard_layout=us
11-28 18:54 DEBUG  WindowsBackend: keyboard_variant=
11-28 18:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-28 18:54 DEBUG  CommonBackend: locale=en_US.UTF-8
11-28 18:54 DEBUG  WindowsBackend: total_memory_mb=382.484375
11-28 18:54 DEBUG  CommonBackend: Searching ISOs on USB devices
11-28 18:54 DEBUG  CommonBackend: Searching for local CDs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Ubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Ubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Ubuntu Netbook CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Kubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Kubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Kubuntu Netbook CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Xubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Xubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Mythbuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Mythbuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 INFO   root: Already installed, running the uninstaller...
11-28 18:54 INFO   root: Running the uninstaller...
11-28 18:54 INFO   CommonBackend: This is the uninstaller running
11-28 18:54 DEBUG  WindowsFrontend: __init__...
11-28 18:54 DEBUG  WindowsFrontend: on_init...
11-28 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\translations, languages=['en_US', 'en']
11-28 18:54 INFO   root: Received settings
11-28 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\translations, languages=['en_US', 'en']
11-28 18:54 DEBUG  TaskList: # Running tasklist...
11-28 18:54 DEBUG  TaskList: ## Running Backup ISO...
11-28 18:54 DEBUG  TaskList: ## Finished Backup ISO
11-28 18:54 DEBUG  TaskList: ## Running Remove bootloader entry...
11-28 18:54 ERROR  WindowsBackend: Cannot find bcdedit
11-28 18:54 DEBUG  WindowsBackend: undo_bootini C:
11-28 18:54 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 25781.5234375 mb free ntfs)
11-28 18:54 DEBUG  WindowsBackend: undo_bootini E:
11-28 18:54 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 9649.859375 mb free ntfs)
11-28 18:54 DEBUG  TaskList: ## Finished Remove bootloader entry
11-28 18:54 DEBUG  TaskList: ## Running Remove target dir...
11-28 18:54 DEBUG  CommonBackend: Deleting E:\ubuntu
11-28 18:54 DEBUG  TaskList: ## Finished Remove target dir
11-28 18:54 DEBUG  TaskList: ## Running Remove registry key...
11-28 18:54 DEBUG  TaskList: ## Finished Remove registry key
11-28 18:54 DEBUG  TaskList: # Finished tasklist
11-28 18:54 INFO   root: Almost finished uninstalling
11-28 18:54 INFO   root: Finished uninstallation
11-28 18:54 DEBUG  CommonBackend: Fetching basic info...
11-28 18:54 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Timber\My Documents\Downloads\wubi(2).exe
11-28 18:54 DEBUG  CommonBackend: platform=win32
11-28 18:54 DEBUG  CommonBackend: osname=nt
11-28 18:54 DEBUG  WindowsBackend: arch=amd64
11-28 18:54 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\data\isolist.ini
11-28 18:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-28 18:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-28 18:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-28 18:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-28 18:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-28 18:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-28 18:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-28 18:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-28 18:54 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-28 18:54 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-28 18:54 DEBUG  WindowsBackend: Fetching host info...
11-28 18:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-28 18:54 DEBUG  WindowsBackend: windows version=xp
11-28 18:54 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-28 18:54 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-28 18:54 DEBUG  WindowsBackend: windows_build=2600
11-28 18:54 DEBUG  WindowsBackend: gmt=-5
11-28 18:54 DEBUG  WindowsBackend: country=US
11-28 18:54 DEBUG  WindowsBackend: timezone=America/New_York
11-28 18:54 DEBUG  WindowsBackend: windows_username=Timber
11-28 18:54 DEBUG  WindowsBackend: user_full_name=Timber
11-28 18:54 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Timber
11-28 18:54 DEBUG  WindowsBackend: windows_language_code=1033
11-28 18:54 DEBUG  WindowsBackend: windows_language=English
11-28 18:54 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 Mobile Technology ML-30
11-28 18:54 DEBUG  WindowsBackend: bootloader=xp
11-28 18:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 25781.4414063 mb free ntfs)
11-28 18:54 DEBUG  WindowsBackend: drive=Drive(C: hd 25781.4414063 mb free ntfs)
11-28 18:54 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-28 18:54 DEBUG  WindowsBackend: drive=Drive(E: hd 9953.453125 mb free ntfs)
11-28 18:54 DEBUG  WindowsBackend: uninstaller_path=None
11-28 18:54 DEBUG  WindowsBackend: previous_target_dir=None
11-28 18:54 DEBUG  WindowsBackend: previous_distro_name=None
11-28 18:54 DEBUG  WindowsBackend: keyboard_id=67699721
11-28 18:54 DEBUG  WindowsBackend: keyboard_layout=us
11-28 18:54 DEBUG  WindowsBackend: keyboard_variant=
11-28 18:54 DEBUG  WindowsBackend: total_memory_mb=382.484375
11-28 18:54 DEBUG  CommonBackend: Searching ISOs on USB devices
11-28 18:54 DEBUG  CommonBackend: Searching for local CDs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Ubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Ubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Ubuntu Netbook CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Kubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Kubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Kubuntu Netbook CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Xubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Xubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Mythbuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Mythbuntu CD
11-28 18:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-28 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-28 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:54 INFO   root: Running the installer...
11-28 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\translations, languages=['en_US', 'en']
11-28 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\translations, languages=['en_US', 'en']
11-28 18:55 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=6000MB, distro_name=Xubuntu, language=en_US, locale=en_US.UTF-8, username=timber
11-28 18:55 INFO   root: Received settings
11-28 18:55 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\translations, languages=['en_US', 'en']
11-28 18:55 DEBUG  TaskList: # Running tasklist...
11-28 18:55 DEBUG  TaskList: ## Running select_target_dir...
11-28 18:55 INFO   WindowsBackend: Installing into E:\ubuntu
11-28 18:55 DEBUG  TaskList: ## Finished select_target_dir
11-28 18:55 DEBUG  TaskList: ## Running create_dir_structure...
11-28 18:55 DEBUG  CommonBackend: Creating dir E:\ubuntu
11-28 18:55 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
11-28 18:55 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
11-28 18:55 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
11-28 18:55 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
11-28 18:55 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
11-28 18:55 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
11-28 18:55 DEBUG  TaskList: ## Finished create_dir_structure
11-28 18:55 DEBUG  TaskList: ## Running uncompress_target_dir...
11-28 18:55 DEBUG  TaskList: ## Finished uncompress_target_dir
11-28 18:55 DEBUG  TaskList: ## Running create_uninstaller...
11-28 18:55 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Timber\My Documents\Downloads\wubi(2).exe -> E:\ubuntu\uninstall-wubi.exe
11-28 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
11-28 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
11-28 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Xubuntu
11-28 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Xubuntu.ico
11-28 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
11-28 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Xubuntu
11-28 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.xubuntu.org](http://www.xubuntu.org)
11-28 18:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-28 18:55 DEBUG  TaskList: ## Finished create_uninstaller
11-28 18:55 DEBUG  TaskList: ## Running copy_installation_files...
11-28 18:55 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
11-28 18:55 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\winboot -> E:\ubuntu\winboot
11-28 18:55 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\data\images\Xubuntu.ico -> E:\ubuntu\Xubuntu.ico
11-28 18:55 DEBUG  TaskList: ## Finished copy_installation_files
11-28 18:55 DEBUG  TaskList: ## Running get_iso...
11-28 18:55 DEBUG  CommonBackend: Searching for local CD
11-28 18:55 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp is a valid Xubuntu CD
11-28 18:55 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs
11-28 18:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-28 18:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 18:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-28 18:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 18:55 DEBUG  CommonBackend: Searching for local ISO
11-28 18:55 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-28 18:55 DEBUG  TaskList: New task get_metalink
11-28 18:55 DEBUG  TaskList: ### Running get_metalink...
11-28 18:55 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.metalink](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.metalink) > E:\ubuntu\install
11-28 18:55 DEBUG  downloader: Download start filename=E:\ubuntu\install\xubuntu-10.04-desktop-amd64.metalink, url=http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.metalink, basename=xubuntu-10.04-desktop-amd64.metalink, length=1040, text=None
11-28 18:55 DEBUG  downloader: download finished (read 1040 bytes)
11-28 18:55 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink) > E:\ubuntu\install
11-28 18:55 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=286, text=None
11-28 18:55 DEBUG  downloader: download finished (read 286 bytes)
11-28 18:55 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink.gpg) > E:\ubuntu\install
11-28 18:55 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
11-28 18:55 DEBUG  downloader: download finished (read 189 bytes)
11-28 18:55 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
11-28 18:55 INFO   saplog: Checking block bindings..
11-28 18:55 INFO   saplog: Key verified successfully.
11-28 18:55 DEBUG  CommonBackend: metalink md5sums:
51280667f7b7be855a7d23ed66999e9b  xubuntu-10.04-alternate-amd64.metalink
2a2fab45952f209a298c5eb95b77647e  xubuntu-10.04-alternate-i386.metalink
d1d8cc67218541ead271d34354082a9e  xubuntu-10.04-desktop-amd64.metalink
6e8062756564c48d43f970bfa35f867a  xubuntu-10.04-desktop-i386.metalink

11-28 18:55 DEBUG  TaskList: ### Finished get_metalink
11-28 18:55 DEBUG  TaskList: New task download
11-28 18:55 DEBUG  TaskList: ### Running download...
11-28 18:55 DEBUG  btdownloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso.torrent) > E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-28 19:49 DEBUG  TaskList: ### Finished download
11-28 19:49 DEBUG  TaskList: New task check_iso
11-28 19:49 DEBUG  TaskList: ### Running check_iso...
11-28 19:49 DEBUG  CommonBackend: Checking E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-28 19:49 DEBUG  Distro:   checking Xubuntu ISO E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-28 19:50 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-28 19:50 DEBUG  Distro:   parsing info from str=Xubuntu 10.04 "Lucid Lynx" - Release amd64 (20100429)
11-28 19:50 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
11-28 19:50 DEBUG  Distro: wrong version: 10.04 != 10.04.1
11-28 19:50 DEBUG  TaskList: ### Finished check_iso
11-28 19:50 DEBUG  TaskList: New task download
11-28 19:50 DEBUG  TaskList: ### Running download...
11-28 19:50 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso) > E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-28 19:50 DEBUG  downloader: Download start filename=E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso, url=http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso, basename=xubuntu-10.04-desktop-amd64.iso, length=728844288, text=None
11-28 20:46 DEBUG  TaskList: ### Finished download
11-28 20:46 DEBUG  downloader: download finished (read 728844288 bytes)
11-28 20:46 DEBUG  TaskList: New task check_iso
11-28 20:46 DEBUG  TaskList: ### Running check_iso...
11-28 20:46 DEBUG  CommonBackend: Checking E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-28 20:46 DEBUG  Distro:   checking Xubuntu ISO E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-28 20:46 DEBUG  Distro: wrong version: 10.04 != 10.04.1
11-28 20:46 DEBUG  TaskList: ### Finished check_iso
11-28 20:46 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
11-28 20:46 DEBUG  TaskList: # Cancelling tasklist
11-28 20:46 DEBUG  TaskList: # Finished tasklist
11-28 20:46 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
11-28 22:34 INFO   root: === wubi 10.04.1 rev190 ===
11-28 22:34 DEBUG  root: Logfile is c:\docume~1\timber\locals~1\temp\wubi-10.04.1-rev190.log
11-28 22:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Timber\\My Documents\\Downloads\\wubi.exe"']
11-28 22:34 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\data
11-28 22:34 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\bin\7z.exe
11-28 22:34 DEBUG  CommonBackend: Fetching basic info...
11-28 22:34 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Timber\My Documents\Downloads\wubi.exe
11-28 22:34 DEBUG  CommonBackend: platform=win32
11-28 22:34 DEBUG  CommonBackend: osname=nt
11-28 22:34 DEBUG  CommonBackend: language=en_US
11-28 22:34 DEBUG  CommonBackend: encoding=cp1252
11-28 22:34 DEBUG  WindowsBackend: arch=amd64
11-28 22:34 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\data\isolist.ini
11-28 22:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-28 22:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-28 22:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-28 22:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-28 22:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-28 22:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-28 22:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-28 22:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-28 22:34 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-28 22:34 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-28 22:34 DEBUG  WindowsBackend: Fetching host info...
11-28 22:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-28 22:34 DEBUG  WindowsBackend: windows version=xp
11-28 22:34 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-28 22:34 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-28 22:34 DEBUG  WindowsBackend: windows_build=2600
11-28 22:34 DEBUG  WindowsBackend: gmt=-5
11-28 22:34 DEBUG  WindowsBackend: country=US
11-28 22:34 DEBUG  WindowsBackend: timezone=America/New_York
11-28 22:34 DEBUG  WindowsBackend: windows_username=Timber
11-28 22:34 DEBUG  WindowsBackend: user_full_name=Timber
11-28 22:34 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Timber
11-28 22:34 DEBUG  WindowsBackend: windows_language_code=1033
11-28 22:34 DEBUG  WindowsBackend: windows_language=English
11-28 22:34 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 Mobile Technology ML-30
11-28 22:34 DEBUG  WindowsBackend: bootloader=xp
11-28 22:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 27306.9023438 mb free ntfs)
11-28 22:34 DEBUG  WindowsBackend: drive=Drive(C: hd 27306.9023438 mb free ntfs)
11-28 22:34 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-28 22:34 DEBUG  WindowsBackend: drive=Drive(E: hd 9951.9921875 mb free ntfs)
11-28 22:34 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
11-28 22:34 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
11-28 22:34 DEBUG  WindowsBackend: previous_distro_name=Xubuntu
11-28 22:34 DEBUG  WindowsBackend: keyboard_id=67699721
11-28 22:34 DEBUG  WindowsBackend: keyboard_layout=us
11-28 22:34 DEBUG  WindowsBackend: keyboard_variant=
11-28 22:34 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-28 22:34 DEBUG  CommonBackend: locale=en_US.UTF-8
11-28 22:34 DEBUG  WindowsBackend: total_memory_mb=382.484375
11-28 22:34 DEBUG  CommonBackend: Searching ISOs on USB devices
11-28 22:34 DEBUG  CommonBackend: Searching for local CDs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Ubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Ubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Ubuntu Netbook CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Kubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Kubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Kubuntu Netbook CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Xubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Xubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Mythbuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Mythbuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 INFO   root: Already installed, running the uninstaller...
11-28 22:34 INFO   root: Running the uninstaller...
11-28 22:34 INFO   CommonBackend: This is the uninstaller running
11-28 22:34 DEBUG  WindowsFrontend: __init__...
11-28 22:34 DEBUG  WindowsFrontend: on_init...
11-28 22:34 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\translations, languages=['en_US', 'en']
11-28 22:34 INFO   root: Received settings
11-28 22:34 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\translations, languages=['en_US', 'en']
11-28 22:34 DEBUG  TaskList: # Running tasklist...
11-28 22:34 DEBUG  TaskList: ## Running Backup ISO...
11-28 22:34 DEBUG  TaskList: ## Finished Backup ISO
11-28 22:34 DEBUG  TaskList: ## Running Remove bootloader entry...
11-28 22:34 ERROR  WindowsBackend: Cannot find bcdedit
11-28 22:34 DEBUG  WindowsBackend: undo_bootini C:
11-28 22:34 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 27306.9023438 mb free ntfs)
11-28 22:34 DEBUG  WindowsBackend: undo_bootini E:
11-28 22:34 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 9951.9921875 mb free ntfs)
11-28 22:34 DEBUG  TaskList: ## Finished Remove bootloader entry
11-28 22:34 DEBUG  TaskList: ## Running Remove target dir...
11-28 22:34 DEBUG  CommonBackend: Deleting E:\ubuntu
11-28 22:34 DEBUG  TaskList: ## Finished Remove target dir
11-28 22:34 DEBUG  TaskList: ## Running Remove registry key...
11-28 22:34 DEBUG  TaskList: ## Finished Remove registry key
11-28 22:34 DEBUG  TaskList: # Finished tasklist
11-28 22:34 INFO   root: Almost finished uninstalling
11-28 22:34 INFO   root: Finished uninstallation
11-28 22:34 DEBUG  CommonBackend: Fetching basic info...
11-28 22:34 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Timber\My Documents\Downloads\wubi.exe
11-28 22:34 DEBUG  CommonBackend: platform=win32
11-28 22:34 DEBUG  CommonBackend: osname=nt
11-28 22:34 DEBUG  WindowsBackend: arch=amd64
11-28 22:34 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\data\isolist.ini
11-28 22:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-28 22:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-28 22:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-28 22:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-28 22:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-28 22:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-28 22:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-28 22:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-28 22:34 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-28 22:34 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-28 22:34 DEBUG  WindowsBackend: Fetching host info...
11-28 22:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-28 22:34 DEBUG  WindowsBackend: windows version=xp
11-28 22:34 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-28 22:34 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-28 22:34 DEBUG  WindowsBackend: windows_build=2600
11-28 22:34 DEBUG  WindowsBackend: gmt=-5
11-28 22:34 DEBUG  WindowsBackend: country=US
11-28 22:34 DEBUG  WindowsBackend: timezone=America/New_York
11-28 22:34 DEBUG  WindowsBackend: windows_username=Timber
11-28 22:34 DEBUG  WindowsBackend: user_full_name=Timber
11-28 22:34 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Timber
11-28 22:34 DEBUG  WindowsBackend: windows_language_code=1033
11-28 22:34 DEBUG  WindowsBackend: windows_language=English
11-28 22:34 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 Mobile Technology ML-30
11-28 22:34 DEBUG  WindowsBackend: bootloader=xp
11-28 22:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 27306.8320313 mb free ntfs)
11-28 22:34 DEBUG  WindowsBackend: drive=Drive(C: hd 27306.8320313 mb free ntfs)
11-28 22:34 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-28 22:34 DEBUG  WindowsBackend: drive=Drive(E: hd 9952.08984375 mb free ntfs)
11-28 22:34 DEBUG  WindowsBackend: uninstaller_path=None
11-28 22:34 DEBUG  WindowsBackend: previous_target_dir=None
11-28 22:34 DEBUG  WindowsBackend: previous_distro_name=None
11-28 22:34 DEBUG  WindowsBackend: keyboard_id=67699721
11-28 22:34 DEBUG  WindowsBackend: keyboard_layout=us
11-28 22:34 DEBUG  WindowsBackend: keyboard_variant=
11-28 22:34 DEBUG  WindowsBackend: total_memory_mb=382.484375
11-28 22:34 DEBUG  CommonBackend: Searching ISOs on USB devices
11-28 22:34 DEBUG  CommonBackend: Searching for local CDs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Ubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Ubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Ubuntu Netbook CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Kubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Kubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Kubuntu Netbook CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Xubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Xubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Mythbuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Mythbuntu CD
11-28 22:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-28 22:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-28 22:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:34 INFO   root: Running the installer...
11-28 22:34 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\translations, languages=['en_US', 'en']
11-28 22:34 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\translations, languages=['en_US', 'en']
11-28 22:35 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=9000MB, distro_name=Xubuntu, language=en_US, locale=en_US.UTF-8, username=timber
11-28 22:35 INFO   root: Received settings
11-28 22:35 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\translations, languages=['en_US', 'en']
11-28 22:35 DEBUG  TaskList: # Running tasklist...
11-28 22:35 DEBUG  TaskList: ## Running select_target_dir...
11-28 22:35 INFO   WindowsBackend: Installing into E:\ubuntu
11-28 22:35 DEBUG  TaskList: ## Finished select_target_dir
11-28 22:35 DEBUG  TaskList: ## Running create_dir_structure...
11-28 22:35 DEBUG  CommonBackend: Creating dir E:\ubuntu
11-28 22:35 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
11-28 22:35 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
11-28 22:35 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
11-28 22:35 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
11-28 22:35 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
11-28 22:35 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
11-28 22:35 DEBUG  TaskList: ## Finished create_dir_structure
11-28 22:35 DEBUG  TaskList: ## Running uncompress_target_dir...
11-28 22:35 DEBUG  TaskList: ## Finished uncompress_target_dir
11-28 22:35 DEBUG  TaskList: ## Running create_uninstaller...
11-28 22:35 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Timber\My Documents\Downloads\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
11-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
11-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
11-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Xubuntu
11-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Xubuntu.ico
11-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
11-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Xubuntu
11-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.xubuntu.org](http://www.xubuntu.org)
11-28 22:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-28 22:35 DEBUG  TaskList: ## Finished create_uninstaller
11-28 22:35 DEBUG  TaskList: ## Running copy_installation_files...
11-28 22:35 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
11-28 22:35 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\winboot -> E:\ubuntu\winboot
11-28 22:35 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\data\images\Xubuntu.ico -> E:\ubuntu\Xubuntu.ico
11-28 22:35 DEBUG  TaskList: ## Finished copy_installation_files
11-28 22:35 DEBUG  TaskList: ## Running get_iso...
11-28 22:35 DEBUG  CommonBackend: Searching for local CD
11-28 22:35 DEBUG  Distro:   checking whether C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp is a valid Xubuntu CD
11-28 22:35 DEBUG  Distro:     does not contain C:\DOCUME~1\Timber\LOCALS~1\Temp\pyl97.tmp\casper\filesystem.squashfs
11-28 22:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-28 22:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-28 22:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-28 22:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-28 22:35 DEBUG  CommonBackend: Searching for local ISO
11-28 22:35 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-28 22:35 DEBUG  TaskList: New task get_metalink
11-28 22:35 DEBUG  TaskList: ### Running get_metalink...
11-28 22:35 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.metalink](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.metalink) > E:\ubuntu\install
11-28 22:35 DEBUG  downloader: Download start filename=E:\ubuntu\install\xubuntu-10.04-desktop-amd64.metalink, url=http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.metalink, basename=xubuntu-10.04-desktop-amd64.metalink, length=1040, text=None
11-28 22:35 DEBUG  downloader: download finished (read 1040 bytes)
11-28 22:35 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink) > E:\ubuntu\install
11-28 22:35 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=286, text=None
11-28 22:35 DEBUG  downloader: download finished (read 286 bytes)
11-28 22:35 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink.gpg) > E:\ubuntu\install
11-28 22:35 DEBUG  downloader: Download start filename=E:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
11-28 22:35 DEBUG  downloader: download finished (read 189 bytes)
11-28 22:35 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
11-28 22:35 INFO   saplog: Checking block bindings..
11-28 22:35 INFO   saplog: Key verified successfully.
11-28 22:35 DEBUG  CommonBackend: metalink md5sums:
51280667f7b7be855a7d23ed66999e9b  xubuntu-10.04-alternate-amd64.metalink
2a2fab45952f209a298c5eb95b77647e  xubuntu-10.04-alternate-i386.metalink
d1d8cc67218541ead271d34354082a9e  xubuntu-10.04-desktop-amd64.metalink
6e8062756564c48d43f970bfa35f867a  xubuntu-10.04-desktop-i386.metalink

11-28 22:35 DEBUG  TaskList: ### Finished get_metalink
11-28 22:35 DEBUG  TaskList: New task download
11-28 22:35 DEBUG  TaskList: ### Running download...
11-28 22:35 DEBUG  btdownloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso.torrent) > E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-28 23:05 DEBUG  TaskList: ### Finished download
11-28 23:05 DEBUG  TaskList: New task check_iso
11-28 23:05 DEBUG  TaskList: ### Running check_iso...
11-28 23:05 DEBUG  CommonBackend: Checking E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-28 23:05 DEBUG  Distro:   checking Xubuntu ISO E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-28 23:05 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-28 23:05 DEBUG  Distro:   parsing info from str=Xubuntu 10.04 "Lucid Lynx" - Release amd64 (20100429)
11-28 23:05 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
11-28 23:05 DEBUG  Distro: wrong version: 10.04 != 10.04.1
11-28 23:05 DEBUG  TaskList: ### Finished check_iso
11-28 23:05 DEBUG  TaskList: New task download
11-28 23:05 DEBUG  TaskList: ### Running download...
11-28 23:05 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso](http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso) > E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-28 23:05 DEBUG  downloader: Download start filename=E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso, url=http://cdimage.ubuntu.com/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-amd64.iso, basename=xubuntu-10.04-desktop-amd64.iso, length=728844288, text=None
11-28 23:55 DEBUG  TaskList: ### Finished download
11-28 23:55 DEBUG  downloader: download finished (read 728844288 bytes)
11-28 23:55 DEBUG  TaskList: New task check_iso
11-28 23:55 DEBUG  TaskList: ### Running check_iso...
11-28 23:55 DEBUG  CommonBackend: Checking E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-28 23:55 DEBUG  Distro:   checking Xubuntu ISO E:\ubuntu\install\xubuntu-10.04-desktop-amd64.iso
11-28 23:55 DEBUG  Distro: wrong version: 10.04 != 10.04.1
11-28 23:55 DEBUG  TaskList: ### Finished check_iso
11-28 23:55 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
11-28 23:55 DEBUG  TaskList: # Cancelling tasklist
11-28 23:55 DEBUG  TaskList: # Finished tasklist
11-28 23:55 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files


---

### Post by bcbc on 2010-11-30
there is a bug with 10.04.1 - they released the wubi.exe so that it only accepts images that are also 10.04.1 but they didn't release a 10.04.1 Xubuntu.
So basically, it downloads xubuntu 10.04 and then rejects it.

You need either the 10.04 wubi.exe or the 10.10 wubi.exe

ps. don't update packages grub-pc and grub-common with wubi installs

---

### Post by USFMD82 on 2010-11-30
Thanks for the help, I'm a bit confused though. Where would I go to get the Wubi 10.10? and I'm not sure what you mean by dont load Grub. I remember when I had something like Grub before when I had xubuntu I had to have something added so I could watch you tube videos.

---

### Post by bcbc on 2010-11-30
> **USFMD82 said:**
> Thanks for the help, I'm a bit confused though. Where would I go to get the Wubi 10.10? and I'm not sure what you mean by dont load Grub. I remember when I had something like Grub before when I had xubuntu I had to have something added so I could watch you tube videos.

You can get the 10.10 version of wubi.exe at [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

I'm not saying don't load grub. Grub is required to boot wubi (not watch videos - that's flash or ubuntu-restricted-extras). I'm saying don't let the update-manager update packages grub-pc and grub-common. They are breaking wubi installs on 10.04 and potentially 10.10 at the moment. You can lock them permanently using Synaptic.

---

### Post by USFMD82 on 2010-12-01
Thank you, that link worked, I used the Wubi 10.10 and got it all set up last night!

---

