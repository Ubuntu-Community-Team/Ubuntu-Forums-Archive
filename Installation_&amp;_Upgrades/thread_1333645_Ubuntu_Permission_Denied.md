---
title: "Ubuntu Permission Denied"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by Sharp1331 on 2009-11-21
[FONT=times new roman]When i try installing ubuntu (inside windows) it won't work it gives me a permission denied error... I'm on the main administrator account of this computer and it's giving me this error. This sometimes happens to other programs too...[/FONT]
[FONT=times new roman]I attatched an image so you can see the error[/FONT]
 
[IMG]http://ubuntuforums.org/picture.php?albumid=1500&pictureid=5206[/IMG]
 
[FONT=times new roman]**_Log File:_**[/FONT]
 
 
```
[FONT=times new roman]_[COLOR=#0066cc]11-21 15:15 INFO root: === wubi 9.10ubuntu1 rev160 ===[/COLOR]_[/FONT]
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG root: Logfile is c:\docume~1\mostapha\locals~1\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\data[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\bin\7z.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Fetching basic info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: original_exe=E:\wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: platform=win32[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: osname=nt[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: language=en_US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: encoding=cp1252[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: arch=i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\data\isolist.ini[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Xubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Xubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: Fetching host info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows version=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_sp=Service Pack 3[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_build=2600[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: gmt=-5[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: country=US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: timezone=America/New_York[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_username=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: user_full_name=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_language_code=1033[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_language=English[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.40GHz[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: bootloader=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: system_drive=Drive(C: hd 54945.4765625 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: drive=Drive(C: hd 54945.4765625 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: drive=Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: keyboard_id=67699721[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: keyboard_layout=us[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: keyboard_variant=[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: python locale=('en_US', 'cp1252')[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: locale=en_US.UTF-8[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: total_memory_mb=1503.53125[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Searching for local CDs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem..squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: wrong arch: i386 != amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO Distro: Found a valid CD for Ubuntu: E:\[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO root: Running the CD menu...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsFrontend: __init__...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsFrontend: on_init...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO root: CD menu finished[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO root: Already installed, running the uninstaller...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO root: Running the uninstaller....[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO CommonBackend: This is the uninstaller running[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO WindowsFrontend: Operation cancelled[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsFrontend: frontend.quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsFrontend: frontend.on_quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG root: application.on_quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO root: sys.exit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO root: === wubi 9.10ubuntu1 rev160 ===[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG root: Logfile is c:\docume~1\mostapha\locals~1\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\data[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\bin\7z.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Fetching basic info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: original_exe=E:\wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: platform=win32[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: osname=nt[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: language=en_US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: encoding=cp1252[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: arch=i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\data\isolist.ini[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Xubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Xubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: Fetching host info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows version=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_sp=Service Pack 3[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_build=2600[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: gmt=-5[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: country=US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: timezone=America/New_York[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_username=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: user_full_name=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_language_code=1033[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_language=English[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.40GHz[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: bootloader=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: system_drive=Drive(C: hd 54945.3867188 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: drive=Drive(C: hd 54945.3867188 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: drive=Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: keyboard_id=67699721[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: keyboard_layout=us[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: keyboard_variant=[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: python locale=('en_US', 'cp1252')[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: locale=en_US.UTF-8[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: total_memory_mb=1503.53125[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Searching for local CDs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem..squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: wrong arch: i386 != amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO Distro: Found a valid CD for Ubuntu: E:\[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO root: Running the CD menu...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsFrontend: __init__...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsFrontend: on_init....[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO root: CD menu finished[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO root: Running the CD menu...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO WindowsFrontend: Operation cancelled[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsFrontend: frontend.quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsFrontend: frontend.on_quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG root: application.on_quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO root: sys.exit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO root: === wubi 9.10ubuntu1 rev160 ===[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG root: Logfile is c:\docume~1\mostapha\locals~1\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\data[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18..tmp\bin\7z.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Fetching basic info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: platform=win32[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: osname=nt[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: language=en_US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: encoding=cp1252[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: arch=i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\data\isolist.ini[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Xubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Xubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: Fetching host info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows version=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_sp=Service Pack 3[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_build=2600[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: gmt=-5[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: country=US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: timezone=America/New_York[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_username=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: user_full_name=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_language_code=1033[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_language=English[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.40GHz[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: bootloader=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: system_drive=Drive(C: hd 54944.6601563 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: drive=Drive(C: hd 54944.6601563 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: drive=Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: keyboard_id=67699721[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: keyboard_layout=us[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: keyboard_variant=[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: python locale=('en_US', 'cp1252')[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: locale=en_US.UTF-8[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: total_memory_mb=1503.53125[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Searching for local CDs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: wrong arch: i386 != amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO Distro: Found a valid CD for Ubuntu: E:\[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO root: Running the uninstaller...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO CommonBackend: This is the uninstaller running[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsFrontend: __init__...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsFrontend: on_init...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO root: Received settings[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: # Running tasklist...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: ## Running Backup ISO...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: ## Finished Backup ISO[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: ## Running Remove bootloader entry...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 ERROR WindowsBackend: Cannot find bcdedit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: undo_bootini C:[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: undo_configsys Drive(C: hd 54944.6601563 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: undo_bootini D:[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: undo_configsys Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: ## Finished Remove bootloader entry[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: ## Running Remove target dir...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Deleting C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: === wubi 9.10ubuntu1 rev160 ===[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG root: Logfile is c:\docume~1\mostapha\locals~1\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\data[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\bin\7z.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Fetching basic info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: original_exe=E:\wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: platform=win32[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: osname=nt[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: language=en_US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: encoding=cp1252[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: arch=i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\data\isolist.ini[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Xubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Xubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: Fetching host info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows version=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_sp=Service Pack 3[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_build=2600[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: gmt=-5[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: country=US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: timezone=America/New_York[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_username=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: user_full_name=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_language_code=1033[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_language=English[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.40GHz[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: bootloader=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: system_drive=Drive(C: hd 54944.5429688 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: drive=Drive(C: hd 54944.5429688 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: drive=Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: keyboard_id=67699721[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: keyboard_layout=us[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: keyboard_variant=[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: python locale=('en_US', 'cp1252')[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: locale=en_US.UTF-8[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: total_memory_mb=1503.53125[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Searching for local CDs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: wrong arch: i386 != amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO Distro: Found a valid CD for Ubuntu: E:\[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: Running the CD menu...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsFrontend: __init__...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsFrontend: on_init...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: CD menu finished[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: Already installed, running the uninstaller...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: Running the uninstaller...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO CommonBackend: This is the uninstaller running[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: Received settings[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: # Running tasklist...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: ## Running Backup ISO...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: ## Finished Backup ISO[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: ## Running Remove bootloader entry...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 ERROR WindowsBackend: Cannot find bcdedit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: undo_bootini C:[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: undo_configsys Drive(C: hd 54944.5429688 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: undo_bootini D:[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: undo_configsys Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: ## Finished Remove bootloader entry[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: ## Running Remove target dir...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Deleting C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO root: === wubi 9.10ubuntu1 rev160 ===[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG root: Logfile is c:\docume~1\mostapha\locals~1\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\data[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\bin\7z.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Fetching basic info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: original_exe=E:\wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: platform=win32[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: osname=nt[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: language=en_US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: encoding=cp1252[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: arch=i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\data\isolist.ini[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Xubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Xubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: Fetching host info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows version=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_sp=Service Pack 3[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_build=2600[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: gmt=-5[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: country=US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: timezone=America/New_York[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_username=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: user_full_name=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_language_code=1033[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_language=English[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.40GHz[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: bootloader=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: system_drive=Drive(C: hd 54944.4335938 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: drive=Drive(C: hd 54944.4335938 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: drive=Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: drive=Drive(E: cd 0..0 mb free cdfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: keyboard_id=67699721[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: keyboard_layout=us[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: keyboard_variant=[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: python locale=('en_US', 'cp1252')[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: locale=en_US.UTF-8[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: total_memory_mb=1503.53125[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Searching for local CDs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: wrong arch: i386 != amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO Distro: Found a valid CD for Ubuntu: E:\[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO root: Running the CD menu...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsFrontend: __init__...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsFrontend: on_init...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO root: CD menu finished[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO root: Running the installer...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=omar[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO root: Received settings[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: # Running tasklist...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running select_target_dir...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WindowsBackend: Installing into C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Finished select_target_dir[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running create_dir_structure...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\disks[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\install[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Finished create_dir_structure[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running uncompress_target_dir...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Finished uncompress_target_dir[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running create_uninstaller...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink[http://www.ubuntu.com/support]("http://www.ubuntu..com/support")[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Finished create_uninstaller[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running copy_installation_files...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: Copying C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: Copying C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\winboot -> C:\ubuntu\winboot[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: Copying C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Finished copy_installation_files[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running get_iso...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: New task copy_file[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ### Running copy_file...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 ERROR TaskList: [Errno 13] Permission denied[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]Traceback (most recent call last):[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\utils.py", line 209, in copy_file[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]IOError: [Errno 13] Permission denied[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG TaskList: # Cancelling tasklist[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 ERROR root: [Errno 13] Permission denied[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]Traceback (most recent call last):[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\application.py", line 56, in run[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\application.py", line 126, in select_task[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\application.py", line 194, in run_cd_menu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\application.py", line 118, in select_task[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\application.py", line 156, in run_installer[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\utils.py", line 209, in copy_file[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]IOError: [Errno 13] Permission denied[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG TaskList: New task check_iso[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG CommonBackend: Searching for local ISO[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG TaskList: New task get_metalink[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 ERROR TaskList: Cannot download the metalink and therefore the ISO[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]Traceback (most recent call last):[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\backend.py", line 492, in get_iso[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\backend.py", line 331, in download_iso[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]Exception: Cannot download the metalink and therefore the ISO[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG TaskList: # Cancelling tasklist[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG TaskList: # Finished tasklist[/COLOR][/FONT]_
```

---

### Post by Sharp1331 on 2009-11-21
[FONT=times new roman]When i try installing ubuntu (inside windows) it won't work it gives me a permission denied error... I'm on the main administrator account of this computer and it's giving me this error. This sometimes happens to other programs too...[/FONT]
[FONT=times new roman]I attatched an image so you can see the error[/FONT]
 
[IMG]http://ubuntuforums.org/picture.php?albumid=1500&pictureid=5206[/IMG]
 
[FONT=times new roman]**_Log File:_**[/FONT]
 
 
```
[FONT=times new roman]_[COLOR=#0066cc]11-21 15:15 INFO root: === wubi 9.10ubuntu1 rev160 ===[/COLOR]_[/FONT]
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG root: Logfile is c:\docume~1\mostapha\locals~1\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A. tmp\data[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\bi n\7z.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Fetching basic info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: original_exe=E:\wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: platform=win32[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: osname=nt[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: language=en_US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: encoding=cp1252[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: arch=i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.t mp\data\isolist.ini[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Xubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Xubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: Fetching host info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows version=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_sp=Service Pack 3[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_build=2600[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: gmt=-5[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: country=US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: timezone=America/New_York[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_username=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: user_full_name=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_language_code=1033[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_language=English[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.40GHz[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: bootloader=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: system_drive=Drive(C: hd 54945.4765625 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: drive=Drive(C: hd 54945.4765625 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: drive=Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: keyboard_id=67699721[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: keyboard_layout=us[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: keyboard_variant=[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: python locale=('en_US', 'cp1252')[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: locale=en_US.UTF-8[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: total_memory_mb=1503.53125[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Searching for local CDs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem..squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: wrong arch: i386 != amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO Distro: Found a valid CD for Ubuntu: E:\[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO root: Running the CD menu...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsFrontend: __init__...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsFrontend: on_init...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO root: CD menu finished[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO root: Already installed, running the uninstaller...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO root: Running the uninstaller....[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO CommonBackend: This is the uninstaller running[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO WindowsFrontend: Operation cancelled[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsFrontend: frontend.quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsFrontend: frontend.on_quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG root: application.on_quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO root: sys.exit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO root: === wubi 9.10ubuntu1 rev160 ===[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG root: Logfile is c:\docume~1\mostapha\locals~1\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B. tmp\data[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\bi n\7z.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Fetching basic info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: original_exe=E:\wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: platform=win32[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: osname=nt[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: language=en_US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: encoding=cp1252[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: arch=i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.t mp\data\isolist.ini[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Xubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Xubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: Fetching host info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows version=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_sp=Service Pack 3[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_build=2600[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: gmt=-5[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: country=US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: timezone=America/New_York[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_username=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: user_full_name=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_language_code=1033[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_language=English[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.40GHz[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: bootloader=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: system_drive=Drive(C: hd 54945.3867188 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: drive=Drive(C: hd 54945.3867188 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: drive=Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: keyboard_id=67699721[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: keyboard_layout=us[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: keyboard_variant=[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: python locale=('en_US', 'cp1252')[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: locale=en_US.UTF-8[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: total_memory_mb=1503.53125[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Searching for local CDs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem..squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: wrong arch: i386 != amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO Distro: Found a valid CD for Ubuntu: E:\[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO root: Running the CD menu...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsFrontend: __init__...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsFrontend: on_init....[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO root: CD menu finished[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO root: Running the CD menu...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO WindowsFrontend: Operation cancelled[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsFrontend: frontend.quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsFrontend: frontend.on_quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG root: application.on_quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO root: sys.exit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO root: === wubi 9.10ubuntu1 rev160 ===[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG root: Logfile is c:\docume~1\mostapha\locals~1\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18. tmp\data[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18..tmp\b in\7z.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Fetching basic info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: platform=win32[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: osname=nt[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: language=en_US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: encoding=cp1252[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: arch=i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.t mp\data\isolist.ini[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Xubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Xubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: Fetching host info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows version=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_sp=Service Pack 3[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_build=2600[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: gmt=-5[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: country=US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: timezone=America/New_York[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_username=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: user_full_name=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_language_code=1033[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_language=English[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.40GHz[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: bootloader=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: system_drive=Drive(C: hd 54944.6601563 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: drive=Drive(C: hd 54944.6601563 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: drive=Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: keyboard_id=67699721[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: keyboard_layout=us[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: keyboard_variant=[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: python locale=('en_US', 'cp1252')[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: locale=en_US.UTF-8[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: total_memory_mb=1503.53125[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Searching for local CDs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: wrong arch: i386 != amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO Distro: Found a valid CD for Ubuntu: E:\[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO root: Running the uninstaller...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO CommonBackend: This is the uninstaller running[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsFrontend: __init__...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsFrontend: on_init...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18 .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO root: Received settings[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18 .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: # Running tasklist...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: ## Running Backup ISO...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: ## Finished Backup ISO[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: ## Running Remove bootloader entry...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 ERROR WindowsBackend: Cannot find bcdedit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: undo_bootini C:[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: undo_configsys Drive(C: hd 54944.6601563 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: undo_bootini D:[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: undo_configsys Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: ## Finished Remove bootloader entry[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: ## Running Remove target dir...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Deleting C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: === wubi 9.10ubuntu1 rev160 ===[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG root: Logfile is c:\docume~1\mostapha\locals~1\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19. tmp\data[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\bi n\7z.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Fetching basic info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: original_exe=E:\wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: platform=win32[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: osname=nt[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: language=en_US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: encoding=cp1252[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: arch=i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.t mp\data\isolist.ini[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Xubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Xubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: Fetching host info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows version=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_sp=Service Pack 3[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_build=2600[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: gmt=-5[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: country=US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: timezone=America/New_York[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_username=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: user_full_name=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_language_code=1033[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_language=English[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.40GHz[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: bootloader=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: system_drive=Drive(C: hd 54944.5429688 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: drive=Drive(C: hd 54944.5429688 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: drive=Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: keyboard_id=67699721[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: keyboard_layout=us[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: keyboard_variant=[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: python locale=('en_US', 'cp1252')[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: locale=en_US.UTF-8[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: total_memory_mb=1503.53125[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Searching for local CDs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: wrong arch: i386 != amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO Distro: Found a valid CD for Ubuntu: E:\[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: Running the CD menu...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsFrontend: __init__...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsFrontend: on_init...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19 .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19 .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: CD menu finished[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: Already installed, running the uninstaller...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: Running the uninstaller...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO CommonBackend: This is the uninstaller running[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19 .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: Received settings[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19 .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: # Running tasklist...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: ## Running Backup ISO...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: ## Finished Backup ISO[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: ## Running Remove bootloader entry...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 ERROR WindowsBackend: Cannot find bcdedit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: undo_bootini C:[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: undo_configsys Drive(C: hd 54944.5429688 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: undo_bootini D:[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: undo_configsys Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: ## Finished Remove bootloader entry[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: ## Running Remove target dir...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Deleting C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO root: === wubi 9.10ubuntu1 rev160 ===[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG root: Logfile is c:\docume~1\mostapha\locals~1\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A. tmp\data[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\bi n\7z.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Fetching basic info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: original_exe=E:\wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: platform=win32[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: osname=nt[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: language=en_US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: encoding=cp1252[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: arch=i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.t mp\data\isolist.ini[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Xubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Xubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: Fetching host info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows version=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_sp=Service Pack 3[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_build=2600[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: gmt=-5[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: country=US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: timezone=America/New_York[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_username=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: user_full_name=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_language_code=1033[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_language=English[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.40GHz[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: bootloader=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: system_drive=Drive(C: hd 54944.4335938 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: drive=Drive(C: hd 54944.4335938 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: drive=Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: drive=Drive(E: cd 0..0 mb free cdfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: keyboard_id=67699721[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: keyboard_layout=us[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: keyboard_variant=[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: python locale=('en_US', 'cp1252')[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: locale=en_US.UTF-8[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: total_memory_mb=1503.53125[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Searching for local CDs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: wrong arch: i386 != amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO Distro: Found a valid CD for Ubuntu: E:\[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO root: Running the CD menu...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsFrontend: __init__...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsFrontend: on_init...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO root: CD menu finished[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO root: Running the installer...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=omar[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO root: Received settings[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: # Running tasklist...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running select_target_dir...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WindowsBackend: Installing into C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Finished select_target_dir[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running create_dir_structure...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\disks[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\install[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Finished create_dir_structure[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running uncompress_target_dir...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Finished uncompress_target_dir[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running create_uninstaller...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi InstallationDir C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayName Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayVersion 9.10ubuntu1-rev160[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi Publisher Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi URLInfoAbout [[COLOR=#444444]http://www.ubuntu.com[/COLOR]]("http://www.ubuntu.com/")[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi HelpLink[[COLOR=#444444]http://www.ubuntu.com/support[/COLOR]]("http://www.ubuntu..com/support")[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Finished create_uninstaller[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running copy_installation_files...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: Copying C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\data\ custom-installation -> C:\ubuntu\install\custom-installation[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: Copying C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\winbo ot -> C:\ubuntu\winboot[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: Copying C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\data\ images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Finished copy_installation_files[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running get_iso...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: New task copy_file[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ### Running copy_file...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 ERROR TaskList: [Errno 13] Permission denied[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]Traceback (most recent call last):[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\utils.py", line 209, in copy_file[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]IOError: [Errno 13] Permission denied[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG TaskList: # Cancelling tasklist[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 ERROR root: [Errno 13] Permission denied[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]Traceback (most recent call last):[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\application.py", line 56, in run[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\application.py", line 126, in select_task[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\application.py", line 194, in run_cd_menu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\application.py", line 118, in select_task[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\application.py", line 156, in run_installer[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\utils.py", line 209, in copy_file[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]IOError: [Errno 13] Permission denied[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG TaskList: New task check_iso[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG CommonBackend: Searching for local ISO[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG TaskList: New task get_metalink[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 ERROR TaskList: Cannot download the metalink and therefore the ISO[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]Traceback (most recent call last):[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\backend.py", line 492, in get_iso[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\backend.py", line 331, in download_iso[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]Exception: Cannot download the metalink and therefore the ISO[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG TaskList: # Cancelling tasklist[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG TaskList: # Finished tasklist[/COLOR][/FONT]_
```

---

### Post by Sharp1331 on 2009-11-21
[FONT=times new roman]When i try installing ubuntu (inside windows) it won't work it gives me a permission denied error... I'm on the main administrator account of this computer and it's giving me this error. This sometimes happens to other programs too...[/FONT]
[FONT=times new roman]I attatched an image so you can see the error[/FONT]

[IMG]http://ubuntuforums.org/picture.php?albumid=1500&pictureid=5206[/IMG]

[FONT=times new roman]**_Log File:_**[/FONT]

```

[FONT=times new roman]_[COLOR=#0066cc]11-21 15:15 INFO root: === wubi 9.10ubuntu1 rev160 ===[/COLOR]_[/FONT]
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG root: Logfile is c:\docume~1\mostapha\locals~1\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A. tmp\data[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\bi n\7z.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Fetching basic info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: original_exe=E:\wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: platform=win32[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: osname=nt[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: language=en_US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: encoding=cp1252[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: arch=i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.t mp\data\isolist.ini[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Xubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Xubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: Fetching host info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows version=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_sp=Service Pack 3[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_build=2600[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: gmt=-5[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: country=US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: timezone=America/New_York[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_username=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: user_full_name=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_language_code=1033[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: windows_language=English[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.40GHz[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: bootloader=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: system_drive=Drive(C: hd 54945.4765625 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: drive=Drive(C: hd 54945.4765625 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: drive=Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: keyboard_id=67699721[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: keyboard_layout=us[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: keyboard_variant=[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: python locale=('en_US', 'cp1252')[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: locale=en_US.UTF-8[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsBackend: total_memory_mb=1503.53125[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG CommonBackend: Searching for local CDs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem..squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: wrong arch: i386 != amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO Distro: Found a valid CD for Ubuntu: E:\[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO root: Running the CD menu...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsFrontend: __init__...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsFrontend: on_init...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO root: CD menu finished[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO root: Already installed, running the uninstaller...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO root: Running the uninstaller....[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO CommonBackend: This is the uninstaller running[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO WindowsFrontend: Operation cancelled[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsFrontend: frontend.quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG WindowsFrontend: frontend.on_quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 DEBUG root: application.on_quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:15 INFO root: sys.exit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO root: === wubi 9.10ubuntu1 rev160 ===[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG root: Logfile is c:\docume~1\mostapha\locals~1\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B. tmp\data[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\bi n\7z.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Fetching basic info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: original_exe=E:\wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: platform=win32[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: osname=nt[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: language=en_US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: encoding=cp1252[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: arch=i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.t mp\data\isolist.ini[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Xubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Xubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: Fetching host info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows version=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_sp=Service Pack 3[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_build=2600[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: gmt=-5[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: country=US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: timezone=America/New_York[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_username=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: user_full_name=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_language_code=1033[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: windows_language=English[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.40GHz[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: bootloader=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: system_drive=Drive(C: hd 54945.3867188 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: drive=Drive(C: hd 54945.3867188 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: drive=Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: keyboard_id=67699721[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: keyboard_layout=us[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: keyboard_variant=[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: python locale=('en_US', 'cp1252')[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: locale=en_US.UTF-8[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsBackend: total_memory_mb=1503.53125[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG CommonBackend: Searching for local CDs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem..squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: wrong arch: i386 != amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO Distro: Found a valid CD for Ubuntu: E:\[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO root: Running the CD menu...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsFrontend: __init__...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsFrontend: on_init....[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO root: CD menu finished[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO root: Running the CD menu...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl7B .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO WindowsFrontend: Operation cancelled[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsFrontend: frontend.quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG WindowsFrontend: frontend.on_quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 DEBUG root: application.on_quit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:16 INFO root: sys.exit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO root: === wubi 9.10ubuntu1 rev160 ===[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG root: Logfile is c:\docume~1\mostapha\locals~1\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18. tmp\data[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18..tmp\b in\7z.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Fetching basic info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: platform=win32[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: osname=nt[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: language=en_US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: encoding=cp1252[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: arch=i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.t mp\data\isolist.ini[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Xubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Xubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: Fetching host info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows version=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_sp=Service Pack 3[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_build=2600[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: gmt=-5[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: country=US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: timezone=America/New_York[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_username=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: user_full_name=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_language_code=1033[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: windows_language=English[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.40GHz[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: bootloader=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: system_drive=Drive(C: hd 54944.6601563 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: drive=Drive(C: hd 54944.6601563 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: drive=Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: keyboard_id=67699721[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: keyboard_layout=us[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: keyboard_variant=[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: python locale=('en_US', 'cp1252')[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: locale=en_US.UTF-8[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: total_memory_mb=1503.53125[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Searching for local CDs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: wrong arch: i386 != amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO Distro: Found a valid CD for Ubuntu: E:\[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO root: Running the uninstaller...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO CommonBackend: This is the uninstaller running[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsFrontend: __init__...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsFrontend: on_init...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18 .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO root: Received settings[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl18 .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: # Running tasklist...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: ## Running Backup ISO...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: ## Finished Backup ISO[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: ## Running Remove bootloader entry...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 ERROR WindowsBackend: Cannot find bcdedit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: undo_bootini C:[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: undo_configsys Drive(C: hd 54944.6601563 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: undo_bootini D:[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG WindowsBackend: undo_configsys Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: ## Finished Remove bootloader entry[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG TaskList: ## Running Remove target dir...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:29 DEBUG CommonBackend: Deleting C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: === wubi 9.10ubuntu1 rev160 ===[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG root: Logfile is c:\docume~1\mostapha\locals~1\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19. tmp\data[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\bi n\7z.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Fetching basic info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: original_exe=E:\wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: platform=win32[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: osname=nt[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: language=en_US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: encoding=cp1252[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: arch=i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.t mp\data\isolist.ini[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Xubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Xubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: Fetching host info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows version=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_sp=Service Pack 3[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_build=2600[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: gmt=-5[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: country=US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: timezone=America/New_York[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_username=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: user_full_name=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_language_code=1033[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: windows_language=English[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.40GHz[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: bootloader=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: system_drive=Drive(C: hd 54944.5429688 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: drive=Drive(C: hd 54944.5429688 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: drive=Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: keyboard_id=67699721[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: keyboard_layout=us[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: keyboard_variant=[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: python locale=('en_US', 'cp1252')[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: locale=en_US.UTF-8[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: total_memory_mb=1503.53125[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Searching for local CDs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: wrong arch: i386 != amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO Distro: Found a valid CD for Ubuntu: E:\[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: Running the CD menu...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsFrontend: __init__...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsFrontend: on_init...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19 .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19 .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: CD menu finished[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: Already installed, running the uninstaller...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: Running the uninstaller...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO CommonBackend: This is the uninstaller running[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19 .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO root: Received settings[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl19 .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: # Running tasklist...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: ## Running Backup ISO...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: ## Finished Backup ISO[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: ## Running Remove bootloader entry...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 ERROR WindowsBackend: Cannot find bcdedit[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: undo_bootini C:[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: undo_configsys Drive(C: hd 54944.5429688 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: undo_bootini D:[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG WindowsBackend: undo_configsys Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: ## Finished Remove bootloader entry[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG TaskList: ## Running Remove target dir...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:30 DEBUG CommonBackend: Deleting C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO root: === wubi 9.10ubuntu1 rev160 ===[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG root: Logfile is c:\docume~1\mostapha\locals~1\temp\wubi-9.10ubuntu1-rev160.log[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: data_dir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A. tmp\data[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: 7z=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\bi n\7z.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Fetching basic info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: original_exe=E:\wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: platform=win32[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: osname=nt[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: language=en_US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: encoding=cp1252[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: arch=i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.t mp\data\isolist.ini[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Xubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Xubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Kubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Mythbuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Ubuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Ubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Mythbuntu-amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro Kubuntu-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Adding distro UbuntuNetbookRemix-i386[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: Fetching host info...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows version=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_sp=Service Pack 3[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_build=2600[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: gmt=-5[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: country=US[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: timezone=America/New_York[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_username=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: user_full_name=Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Mostapha[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_language_code=1033[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: windows_language=English[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: processor_name= Intel(R) Pentium(R) 4 CPU 2.40GHz[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: bootloader=xp[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: system_drive=Drive(C: hd 54944.4335938 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: drive=Drive(C: hd 54944.4335938 mb free ntfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: drive=Drive(D: removable 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: drive=Drive(E: cd 0..0 mb free cdfs)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: drive=Drive(F: cd 0.0 mb free )[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: previous_distro_name=Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: keyboard_id=67699721[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: keyboard_layout=us[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: keyboard_variant=[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: python locale=('en_US', 'cp1252')[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: locale=en_US.UTF-8[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: total_memory_mb=1503.53125[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Searching ISOs on USB devices[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Searching for local CDs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\caspe r\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: wrong arch: i386 != amd64[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO Distro: Found a valid CD for Ubuntu: E:\[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO root: Running the CD menu...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsFrontend: __init__...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsFrontend: on_init...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO root: CD menu finished[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO root: Running the installer...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=omar[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO root: Received settings[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A .tmp\translations, languages=['en_US', 'en'][/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: # Running tasklist...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running select_target_dir...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 INFO WindowsBackend: Installing into C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Finished select_target_dir[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running create_dir_structure...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\disks[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\install[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Finished create_dir_structure[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running uncompress_target_dir...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Finished uncompress_target_dir[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running create_uninstaller...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi InstallationDir C:\ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayName Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi DisplayVersion 9.10ubuntu1-rev160[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi Publisher Ubuntu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi URLInfoAbout [[COLOR=#444444]http://www.ubuntu.com[/COLOR]]("http://www.ubuntu.com/")[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstal l\Wubi HelpLink[[COLOR=#444444]http://www.ubuntu.com/support[/COLOR]]("http://www.ubuntu..com/support")[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Finished create_uninstaller[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running copy_installation_files...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: Copying C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\data\ custom-installation -> C:\ubuntu\install\custom-installation[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: Copying C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\winbo ot -> C:\ubuntu\winboot[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG WindowsBackend: Copying C:\DOCUME~1\Mostapha\LOCALS~1\Temp\pyl1A.tmp\data\ images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Finished copy_installation_files[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ## Running get_iso...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: New task copy_file[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:31 DEBUG TaskList: ### Running copy_file...[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 ERROR TaskList: [Errno 13] Permission denied[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]Traceback (most recent call last):[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\utils.py", line 209, in copy_file[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]IOError: [Errno 13] Permission denied[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG TaskList: # Cancelling tasklist[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 ERROR root: [Errno 13] Permission denied[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]Traceback (most recent call last):[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\application.py", line 56, in run[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\application.py", line 126, in select_task[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\application.py", line 194, in run_cd_menu[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\application.py", line 118, in select_task[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\application.py", line 156, in run_installer[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\utils.py", line 209, in copy_file[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]IOError: [Errno 13] Permission denied[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG TaskList: New task check_iso[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG CommonBackend: Searching for local ISO[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG TaskList: New task get_metalink[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 ERROR TaskList: Cannot download the metalink and therefore the ISO[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]Traceback (most recent call last):[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\backend.py", line 492, in get_iso[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]File "\lib\wubi\backends\common\backend.py", line 331, in download_iso[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]Exception: Cannot download the metalink and therefore the ISO[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG TaskList: # Cancelling tasklist[/COLOR][/FONT]_
_[FONT=times new roman][COLOR=#0066cc]11-21 15:36 DEBUG TaskList: # Finished tasklist[/COLOR][/FONT]_
```
[]("http://ubuntuforums.org/showthread.php?p=8362835#post8362835")

---

### Post by iMisspell on 2009-11-21
Cant help you with your question but can offer alittle advice.
Post a larger picture (or post a small picture like you did but link that small pic to a larger one).
When you post a long log file place it in the forums code tags [HTML]```
 long log ... info 
```[/HTML]

_

---

### Post by wilee-nilee on 2009-11-21
This is one of three identical threads.
[http://ubuntuforums.org/showthread.php?t=1333733](http://ubuntuforums.org/showthread.php?t=1333733)
[http://ubuntuforums.org/showthread.php?t=1333645](http://ubuntuforums.org/showthread.php?t=1333645)
This is suspicious at the least.

---

### Post by cariboo on 2009-11-21
Please don't create multiple threads on the same problem. I have merged your three threads.

---

### Post by Sharp1331 on 2009-11-22
I tried Karmic Koala And Samething...
Im burning at the lowest speed I can go which is 4x 705kb/s
Also, When I Boot From Ubuntu LiveCd, I click english then install and it freezes for a while and then says 
Title - I/O error reading boot cd
Message - Reboot (button)

---

### Post by Sharp1331 on 2009-11-22
Help??

---

