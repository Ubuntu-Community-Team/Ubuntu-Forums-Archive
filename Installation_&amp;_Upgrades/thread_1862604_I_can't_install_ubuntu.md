---
title: "I can't install ubuntu"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by shriek11 on 2011-10-16
Hi guys,
 
I am having trouble installing ubuntu on windows laptop. I use the wubi.exe installer, but I get the message: **'Windowsbackend' object has no attribute 'iso_path".**
 
***Here is my log for it:***
 ```

10-16 11:08 INFO root: === wubi 11.10 rev241 ===
10-16 11:08 DEBUG root: Logfile is c:\users\mehaql\appdata\local\temp\wubi-11.10-rev241.log
10-16 11:08 DEBUG root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
10-16 11:08 DEBUG CommonBackend: data_dir=C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\data
10-16 11:08 DEBUG WindowsBackend: 7z=C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\bin\7z.exe
10-16 11:08 DEBUG WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-16 11:08 DEBUG CommonBackend: Fetching basic info...
10-16 11:08 DEBUG CommonBackend: original_exe=F:\wubi.exe
10-16 11:08 DEBUG CommonBackend: platform=win32
10-16 11:08 DEBUG CommonBackend: osname=nt
10-16 11:08 DEBUG CommonBackend: language=en_US
10-16 11:08 DEBUG CommonBackend: encoding=cp1252
10-16 11:08 DEBUG WindowsBackend: arch=amd64
10-16 11:08 DEBUG CommonBackend: Parsing isolist=C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\data\isolist.ini
10-16 11:08 DEBUG CommonBackend: Adding distro Xubuntu-i386
10-16 11:08 DEBUG CommonBackend: Adding distro Xubuntu-amd64
10-16 11:08 DEBUG CommonBackend: Adding distro Kubuntu-amd64
10-16 11:08 DEBUG CommonBackend: Adding distro Mythbuntu-i386
10-16 11:08 DEBUG CommonBackend: Adding distro Ubuntu-amd64
10-16 11:08 DEBUG CommonBackend: Adding distro Ubuntu-i386
10-16 11:08 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
10-16 11:08 DEBUG CommonBackend: Adding distro Kubuntu-i386
10-16 11:08 DEBUG WindowsBackend: Fetching host info...
10-16 11:08 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-16 11:08 DEBUG WindowsBackend: windows version=vista
10-16 11:08 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
10-16 11:08 DEBUG WindowsBackend: windows_sp=None
10-16 11:08 DEBUG WindowsBackend: windows_build=7601
10-16 11:08 DEBUG WindowsBackend: gmt=-6
10-16 11:08 DEBUG WindowsBackend: country=US
10-16 11:08 DEBUG WindowsBackend: timezone=America/Chicago
10-16 11:08 DEBUG WindowsBackend: windows_username=mehaqL
10-16 11:08 DEBUG WindowsBackend: user_full_name=mehaqL
10-16 11:08 DEBUG WindowsBackend: user_directory=C:\Users\mehaqL
10-16 11:08 DEBUG WindowsBackend: windows_language_code=1033
10-16 11:08 DEBUG WindowsBackend: windows_language=English
10-16 11:08 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
10-16 11:08 DEBUG WindowsBackend: bootloader=vista
10-16 11:08 DEBUG WindowsBackend: system_drive=Drive(C: hd 21408.3789063 mb free ntfs)
10-16 11:08 DEBUG WindowsBackend: drive=Drive(C: hd 21408.3789063 mb free ntfs)
10-16 11:08 DEBUG WindowsBackend: drive=Drive(D: hd 16797.2578125 mb free ntfs)
10-16 11:08 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-16 11:08 DEBUG WindowsBackend: drive=Drive(F: removable 3153.140625 mb free fat32)
10-16 11:08 DEBUG WindowsBackend: drive=Drive(G: removable 3537.96875 mb free fat32)
10-16 11:08 DEBUG WindowsBackend: uninstaller_path=None
10-16 11:08 DEBUG WindowsBackend: previous_target_dir=None
10-16 11:08 DEBUG WindowsBackend: previous_distro_name=None
10-16 11:08 DEBUG WindowsBackend: keyboard_id=67699721
10-16 11:08 DEBUG WindowsBackend: keyboard_layout=us
10-16 11:08 DEBUG WindowsBackend: keyboard_variant=
10-16 11:08 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
10-16 11:08 DEBUG CommonBackend: locale=en_US.UTF-8
10-16 11:08 DEBUG WindowsBackend: total_memory_mb=4030.87890625
10-16 11:08 DEBUG CommonBackend: Searching ISOs on USB devices
10-16 11:08 DEBUG CommonBackend: Searching for local CDs
10-16 11:08 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp is a valid Ubuntu CD
10-16 11:08 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp is a valid Ubuntu CD
10-16 11:08 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp is a valid Kubuntu CD
10-16 11:08 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp is a valid Kubuntu CD
10-16 11:08 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp is a valid Xubuntu CD
10-16 11:08 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp is a valid Xubuntu CD
10-16 11:08 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp is a valid Mythbuntu CD
10-16 11:08 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp is a valid Mythbuntu CD
10-16 11:08 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
10-16 11:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
10-16 11:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
10-16 11:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
10-16 11:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
10-16 11:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
10-16 11:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
10-16 11:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
10-16 11:08 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
10-16 11:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
10-16 11:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
10-16 11:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
10-16 11:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
10-16 11:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
10-16 11:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
10-16 11:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
10-16 11:08 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 11:08 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
10-16 11:08 DEBUG Distro: parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
10-16 11:08 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
10-16 11:08 INFO Distro: Found a valid CD for Ubuntu: F:\
10-16 11:08 INFO root: Running the CD menu...
10-16 11:08 DEBUG WindowsFrontend: __init__...
10-16 11:08 DEBUG WindowsFrontend: on_init...
10-16 11:08 INFO WinuiPage: appname=wubi, localedir=C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\translations, languages=['en_US', 'en']
10-16 11:08 INFO WinuiPage: appname=wubi, localedir=C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\translations, languages=['en_US', 'en']
10-16 11:08 INFO root: CD menu finished
10-16 11:08 INFO root: Running the installer...
10-16 11:08 INFO WinuiPage: appname=wubi, localedir=C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\translations, languages=['en_US', 'en']
10-16 11:08 INFO WinuiPage: appname=wubi, localedir=C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\translations, languages=['en_US', 'en']
10-16 11:08 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=13000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=mehaql
10-16 11:08 INFO root: Received settings
10-16 11:08 INFO WinuiPage: appname=wubi, localedir=C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\translations, languages=['en_US', 'en']
10-16 11:08 DEBUG TaskList: # Running tasklist...
10-16 11:08 DEBUG TaskList: ## Running select_target_dir...
10-16 11:08 INFO WindowsBackend: Installing into C:\ubuntu
10-16 11:08 DEBUG TaskList: ## Finished select_target_dir
10-16 11:08 DEBUG TaskList: ## Running create_dir_structure...
10-16 11:08 DEBUG CommonBackend: Creating dir C:\ubuntu
10-16 11:08 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
10-16 11:08 DEBUG CommonBackend: Creating dir C:\ubuntu\install
10-16 11:08 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
10-16 11:08 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
10-16 11:08 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-16 11:08 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-16 11:08 DEBUG TaskList: ## Finished create_dir_structure
10-16 11:08 DEBUG TaskList: ## Running uncompress_target_dir...
10-16 11:08 DEBUG TaskList: ## Finished uncompress_target_dir
10-16 11:08 DEBUG TaskList: ## Running create_uninstaller...
10-16 11:08 DEBUG WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-16 11:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-16 11:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-16 11:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-16 11:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-16 11:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
10-16 11:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-16 11:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [[COLOR=#0000ff]Homepage | Ubuntu[/COLOR]]("http://www.ubuntu.com/")
10-16 11:08 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [[COLOR=#0000ff]Support | Ubuntu[/COLOR]]("http://www.ubuntu.com/support")
10-16 11:08 DEBUG TaskList: ## Finished create_uninstaller
10-16 11:08 DEBUG TaskList: ## Running copy_installation_files...
10-16 11:08 DEBUG WindowsBackend: Copying C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-16 11:08 DEBUG WindowsBackend: Copying C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\winboot -> C:\ubuntu\winboot
10-16 11:08 DEBUG WindowsBackend: Copying C:\Users\mehaqL\AppData\Local\Temp\pylA3EC.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-16 11:08 DEBUG TaskList: ## Finished copy_installation_files
10-16 11:08 DEBUG TaskList: ## Running get_iso...
10-16 11:08 DEBUG TaskList: New task copy_file
10-16 11:08 DEBUG TaskList: ### Running copy_file...
10-16 11:12 DEBUG TaskList: ### Finished copy_file
10-16 11:12 DEBUG TaskList: New task check_iso
10-16 11:12 DEBUG TaskList: ### Running check_iso...
10-16 11:12 DEBUG CommonBackend: Checking C:\ubuntu\install\installation.iso
10-16 11:12 DEBUG Distro: checking Ubuntu ISO C:\ubuntu\install\installation.iso
10-16 11:12 DEBUG Distro: wrong size: 4043276800 > 900000000
10-16 11:12 DEBUG TaskList: ### Finished check_iso
10-16 11:12 ERROR TaskList: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
10-16 11:12 DEBUG TaskList: # Cancelling tasklist
10-16 11:12 DEBUG TaskList: # Finished tasklist
10-16 11:12 ERROR root: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
File "\lib\wubi\application.py", line 58, in run
File "\lib\wubi\application.py", line 130, in select_task
File "\lib\wubi\application.py", line 205, in run_cd_menu
File "\lib\wubi\application.py", line 120, in select_task
File "\lib\wubi\application.py", line 158, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
10-16 21:32 INFO root: === wubi 11.10 rev241 ===
10-16 21:32 DEBUG root: Logfile is c:\users\mehaql\appdata\local\temp\wubi-11.10-rev241.log
10-16 21:32 DEBUG root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
10-16 21:32 DEBUG CommonBackend: data_dir=C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp\data
10-16 21:32 DEBUG WindowsBackend: 7z=C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp\bin\7z.exe
10-16 21:32 DEBUG WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-16 21:32 DEBUG CommonBackend: Fetching basic info...
10-16 21:32 DEBUG CommonBackend: original_exe=F:\wubi.exe
10-16 21:32 DEBUG CommonBackend: platform=win32
10-16 21:32 DEBUG CommonBackend: osname=nt
10-16 21:32 DEBUG CommonBackend: language=en_US
10-16 21:32 DEBUG CommonBackend: encoding=cp1252
10-16 21:32 DEBUG WindowsBackend: arch=amd64
10-16 21:32 DEBUG CommonBackend: Parsing isolist=C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp\data\isolist.ini
10-16 21:32 DEBUG CommonBackend: Adding distro Xubuntu-i386
10-16 21:32 DEBUG CommonBackend: Adding distro Xubuntu-amd64
10-16 21:32 DEBUG CommonBackend: Adding distro Kubuntu-amd64
10-16 21:32 DEBUG CommonBackend: Adding distro Mythbuntu-i386
10-16 21:32 DEBUG CommonBackend: Adding distro Ubuntu-amd64
10-16 21:32 DEBUG CommonBackend: Adding distro Ubuntu-i386
10-16 21:32 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
10-16 21:32 DEBUG CommonBackend: Adding distro Kubuntu-i386
10-16 21:32 DEBUG WindowsBackend: Fetching host info...
10-16 21:32 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-16 21:32 DEBUG WindowsBackend: windows version=vista
10-16 21:32 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
10-16 21:32 DEBUG WindowsBackend: windows_sp=None
10-16 21:32 DEBUG WindowsBackend: windows_build=7601
10-16 21:32 DEBUG WindowsBackend: gmt=-6
10-16 21:32 DEBUG WindowsBackend: country=US
10-16 21:32 DEBUG WindowsBackend: timezone=America/Chicago
10-16 21:32 DEBUG WindowsBackend: windows_username=mehaqL
10-16 21:32 DEBUG WindowsBackend: user_full_name=mehaqL
10-16 21:32 DEBUG WindowsBackend: user_directory=C:\Users\mehaqL
10-16 21:32 DEBUG WindowsBackend: windows_language_code=1033
10-16 21:32 DEBUG WindowsBackend: windows_language=English
10-16 21:32 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
10-16 21:32 DEBUG WindowsBackend: bootloader=vista
10-16 21:32 DEBUG WindowsBackend: system_drive=Drive(C: hd 20537.328125 mb free ntfs)
10-16 21:32 DEBUG WindowsBackend: drive=Drive(C: hd 20537.328125 mb free ntfs)
10-16 21:32 DEBUG WindowsBackend: drive=Drive(D: hd 16797.2578125 mb free ntfs)
10-16 21:32 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-16 21:32 DEBUG WindowsBackend: drive=Drive(F: removable 2457.84765625 mb free fat32)
10-16 21:32 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-16 21:32 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
10-16 21:32 DEBUG WindowsBackend: previous_distro_name=Ubuntu
10-16 21:32 DEBUG WindowsBackend: keyboard_id=67699721
10-16 21:32 DEBUG WindowsBackend: keyboard_layout=us
10-16 21:32 DEBUG WindowsBackend: keyboard_variant=
10-16 21:32 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
10-16 21:32 DEBUG CommonBackend: locale=en_US.UTF-8
10-16 21:32 DEBUG WindowsBackend: total_memory_mb=4030.87890625
10-16 21:32 DEBUG CommonBackend: Searching ISOs on USB devices
10-16 21:32 DEBUG Distro: checking Ubuntu ISO F:\ubuntu-11.10-desktop-i386.iso
10-16 21:32 DEBUG WindowsBackend: extracting .disk\info from F:\ubuntu-11.10-desktop-i386.iso
10-16 21:32 DEBUG Distro: parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
10-16 21:32 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
10-16 21:32 INFO Distro: Found a valid iso for Ubuntu: F:\ubuntu-11.10-desktop-i386.iso
10-16 21:32 DEBUG CommonBackend: Searching for local CDs
10-16 21:32 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp is a valid Ubuntu CD
10-16 21:32 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp is a valid Ubuntu CD
10-16 21:32 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp is a valid Kubuntu CD
10-16 21:32 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp is a valid Kubuntu CD
10-16 21:32 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp is a valid Xubuntu CD
10-16 21:32 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp is a valid Xubuntu CD
10-16 21:32 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp is a valid Mythbuntu CD
10-16 21:32 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp is a valid Mythbuntu CD
10-16 21:32 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
10-16 21:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
10-16 21:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
10-16 21:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
10-16 21:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
10-16 21:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
10-16 21:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
10-16 21:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
10-16 21:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
10-16 21:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
10-16 21:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
10-16 21:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
10-16 21:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
10-16 21:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
10-16 21:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
10-16 21:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
10-16 21:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:32 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
10-16 21:32 DEBUG Distro: parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
10-16 21:32 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
10-16 21:32 INFO Distro: Found a valid CD for Ubuntu: F:\
10-16 21:32 INFO root: Running the CD menu...
10-16 21:32 DEBUG WindowsFrontend: __init__...
10-16 21:32 DEBUG WindowsFrontend: on_init...
10-16 21:32 INFO WinuiPage: appname=wubi, localedir=C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp\translations, languages=['en_US', 'en']
10-16 21:32 INFO WinuiPage: appname=wubi, localedir=C:\Users\mehaqL\AppData\Local\Temp\pyl3B3B.tmp\translations, languages=['en_US', 'en']
10-16 21:32 DEBUG WindowsFrontend: frontend.on_quit
10-16 21:32 DEBUG root: application.on_quit
10-16 21:32 INFO root: sys.exit
10-16 21:33 INFO root: === wubi 11.10 rev241 ===
10-16 21:33 DEBUG root: Logfile is c:\users\mehaql\appdata\local\temp\wubi-11.10-rev241.log
10-16 21:33 DEBUG root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
10-16 21:33 DEBUG CommonBackend: data_dir=C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\data
10-16 21:33 DEBUG WindowsBackend: 7z=C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\bin\7z.exe
10-16 21:33 DEBUG WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-16 21:33 DEBUG CommonBackend: Fetching basic info...
10-16 21:33 DEBUG CommonBackend: original_exe=F:\wubi.exe
10-16 21:33 DEBUG CommonBackend: platform=win32
10-16 21:33 DEBUG CommonBackend: osname=nt
10-16 21:33 DEBUG CommonBackend: language=en_US
10-16 21:33 DEBUG CommonBackend: encoding=cp1252
10-16 21:33 DEBUG WindowsBackend: arch=amd64
10-16 21:33 DEBUG CommonBackend: Parsing isolist=C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\data\isolist.ini
10-16 21:33 DEBUG CommonBackend: Adding distro Xubuntu-i386
10-16 21:33 DEBUG CommonBackend: Adding distro Xubuntu-amd64
10-16 21:33 DEBUG CommonBackend: Adding distro Kubuntu-amd64
10-16 21:33 DEBUG CommonBackend: Adding distro Mythbuntu-i386
10-16 21:33 DEBUG CommonBackend: Adding distro Ubuntu-amd64
10-16 21:33 DEBUG CommonBackend: Adding distro Ubuntu-i386
10-16 21:33 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
10-16 21:33 DEBUG CommonBackend: Adding distro Kubuntu-i386
10-16 21:33 DEBUG WindowsBackend: Fetching host info...
10-16 21:33 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-16 21:33 DEBUG WindowsBackend: windows version=vista
10-16 21:33 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
10-16 21:33 DEBUG WindowsBackend: windows_sp=None
10-16 21:33 DEBUG WindowsBackend: windows_build=7601
10-16 21:33 DEBUG WindowsBackend: gmt=-6
10-16 21:33 DEBUG WindowsBackend: country=US
10-16 21:33 DEBUG WindowsBackend: timezone=America/Chicago
10-16 21:33 DEBUG WindowsBackend: windows_username=mehaqL
10-16 21:33 DEBUG WindowsBackend: user_full_name=mehaqL
10-16 21:33 DEBUG WindowsBackend: user_directory=C:\Users\mehaqL
10-16 21:33 DEBUG WindowsBackend: windows_language_code=1033
10-16 21:33 DEBUG WindowsBackend: windows_language=English
10-16 21:33 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
10-16 21:33 DEBUG WindowsBackend: bootloader=vista
10-16 21:33 DEBUG WindowsBackend: system_drive=Drive(C: hd 19835.4921875 mb free ntfs)
10-16 21:33 DEBUG WindowsBackend: drive=Drive(C: hd 19835.4921875 mb free ntfs)
10-16 21:33 DEBUG WindowsBackend: drive=Drive(D: hd 16797.2578125 mb free ntfs)
10-16 21:33 DEBUG WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-16 21:33 DEBUG WindowsBackend: drive=Drive(F: removable 3153.140625 mb free fat32)
10-16 21:33 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-16 21:33 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
10-16 21:33 DEBUG WindowsBackend: previous_distro_name=Ubuntu
10-16 21:33 DEBUG WindowsBackend: keyboard_id=67699721
10-16 21:33 DEBUG WindowsBackend: keyboard_layout=us
10-16 21:33 DEBUG WindowsBackend: keyboard_variant=
10-16 21:33 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
10-16 21:33 DEBUG CommonBackend: locale=en_US.UTF-8
10-16 21:33 DEBUG WindowsBackend: total_memory_mb=4030.87890625
10-16 21:33 DEBUG CommonBackend: Searching ISOs on USB devices
10-16 21:33 DEBUG CommonBackend: Searching for local CDs
10-16 21:33 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp is a valid Ubuntu CD
10-16 21:33 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp is a valid Ubuntu CD
10-16 21:33 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp is a valid Kubuntu CD
10-16 21:33 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp is a valid Kubuntu CD
10-16 21:33 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp is a valid Xubuntu CD
10-16 21:33 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp is a valid Xubuntu CD
10-16 21:33 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp is a valid Mythbuntu CD
10-16 21:33 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp is a valid Mythbuntu CD
10-16 21:33 DEBUG Distro: does not contain C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
10-16 21:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
10-16 21:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
10-16 21:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
10-16 21:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
10-16 21:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
10-16 21:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
10-16 21:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
10-16 21:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
10-16 21:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
10-16 21:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
10-16 21:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
10-16 21:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
10-16 21:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
10-16 21:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
10-16 21:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
10-16 21:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
10-16 21:33 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
10-16 21:33 DEBUG Distro: parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
10-16 21:33 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
10-16 21:33 INFO Distro: Found a valid CD for Ubuntu: F:\
10-16 21:33 INFO root: Running the CD menu...
10-16 21:33 DEBUG WindowsFrontend: __init__...
10-16 21:33 DEBUG WindowsFrontend: on_init...
10-16 21:33 INFO WinuiPage: appname=wubi, localedir=C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\translations, languages=['en_US', 'en']
10-16 21:33 INFO WinuiPage: appname=wubi, localedir=C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\translations, languages=['en_US', 'en']
10-16 21:34 INFO root: CD menu finished
10-16 21:34 INFO root: Running the installer...
10-16 21:34 INFO WinuiPage: appname=wubi, localedir=C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\translations, languages=['en_US', 'en']
10-16 21:34 INFO WinuiPage: appname=wubi, localedir=C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\translations, languages=['en_US', 'en']
10-16 21:34 DEBUG WinuiInstallationPage: target_drive=C:, installation_size=12000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=mehaql
10-16 21:34 INFO root: Received settings
10-16 21:34 INFO WinuiPage: appname=wubi, localedir=C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\translations, languages=['en_US', 'en']
10-16 21:34 DEBUG TaskList: # Running tasklist...
10-16 21:34 DEBUG TaskList: ## Running select_target_dir...
10-16 21:34 INFO WindowsBackend: Installing into C:\ubuntu
10-16 21:34 DEBUG TaskList: ## Finished select_target_dir
10-16 21:34 DEBUG TaskList: ## Running create_dir_structure...
10-16 21:34 DEBUG CommonBackend: Creating dir C:\ubuntu
10-16 21:34 DEBUG CommonBackend: Creating dir C:\ubuntu\disks
10-16 21:34 DEBUG CommonBackend: Creating dir C:\ubuntu\install
10-16 21:34 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot
10-16 21:34 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot
10-16 21:34 DEBUG CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-16 21:34 DEBUG CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-16 21:34 DEBUG TaskList: ## Finished create_dir_structure
10-16 21:34 DEBUG TaskList: ## Running uncompress_target_dir...
10-16 21:34 DEBUG TaskList: ## Finished uncompress_target_dir
10-16 21:34 DEBUG TaskList: ## Running create_uninstaller...
10-16 21:34 DEBUG WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-16 21:34 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-16 21:34 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-16 21:34 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-16 21:34 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-16 21:34 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
10-16 21:34 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-16 21:34 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [[COLOR=#0000ff]Homepage | Ubuntu[/COLOR]]("http://www.ubuntu.com/")
10-16 21:34 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [[COLOR=#0000ff]Support | Ubuntu[/COLOR]]("http://www.ubuntu.com/support")
10-16 21:34 DEBUG TaskList: ## Finished create_uninstaller
10-16 21:34 DEBUG TaskList: ## Running copy_installation_files...
10-16 21:34 DEBUG WindowsBackend: Copying C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-16 21:34 DEBUG WindowsBackend: Copying C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\winboot -> C:\ubuntu\winboot
10-16 21:34 DEBUG WindowsBackend: Copying C:\Users\mehaqL\AppData\Local\Temp\pyl81FB.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-16 21:34 DEBUG TaskList: ## Finished copy_installation_files
10-16 21:34 DEBUG TaskList: ## Running get_iso...
10-16 21:34 DEBUG TaskList: New task copy_file
10-16 21:34 DEBUG TaskList: ### Running copy_file...
10-16 21:38 DEBUG TaskList: ### Finished copy_file
10-16 21:38 DEBUG TaskList: New task check_iso
10-16 21:38 DEBUG TaskList: ### Running check_iso...
10-16 21:38 DEBUG CommonBackend: Checking C:\ubuntu\install\installation.iso
10-16 21:38 DEBUG Distro: checking Ubuntu ISO C:\ubuntu\install\installation.iso
10-16 21:38 DEBUG Distro: wrong size: 4043276800 > 900000000
10-16 21:38 DEBUG TaskList: ### Finished check_iso
10-16 21:38 ERROR TaskList: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
10-16 21:38 DEBUG TaskList: # Cancelling tasklist
10-16 21:38 DEBUG TaskList: # Finished tasklist
10-16 21:38 ERROR root: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
File "\lib\wubi\application.py", line 58, in run
File "\lib\wubi\application.py", line 130, in select_task
File "\lib\wubi\application.py", line 205, in run_cd_menu
File "\lib\wubi\application.py", line 120, in select_task
File "\lib\wubi\application.py", line 158, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
```

---

### Post by shriek11 on 2011-10-16
I use a Mac and their system is based on linux, so I am hoping that using ubuntu on vaio would quiet down my fan, as is the case especially if I open chrome or firefox with couple of tabs even with no flash sites.  The fan is annoying in a class environment.

---

### Post by Bmonsterboy on 2011-10-16
OK, first, put that error message in a smaller size.

I prefer to install OS's via a live disk.

Download and burn a copy of the distro you want from [http://www.ubuntu.com/]("http://www.ubuntu.com/").
Then, reboot your computer, and before it starts loading your current OS, go into boot options.

Then follow the install process. 

This should work fine.

---

### Post by Bmonsterboy on 2011-10-16
> **shriek11 said:**
> I use a Mac and their system is based on linux, so I am hoping that using ubuntu on vaio would quiet down my fan, as is the case especially if I open chrome or firefox with couple of tabs even with no flash sites.  The fan is annoying in a class environment.

Some things that would help for the fan would be raising the laptop off the desk so the fan can get air freely. Also toning down your brightness can help too.

---

### Post by youngunix on 2011-10-16
> **shriek11 said:**
> I use a Mac and their system is based on linux, so I am hoping that using ubuntu on vaio would quiet down my fan, as is the case especially if I open chrome or firefox with couple of tabs even with no flash sites.  The fan is annoying in a class environment.


even if you use firefox or chrome on ubuntu, the fan will still run at higher RPMs. I had the same problem; the fan gets extremely loud and annoying. This happened on my laptop because of two reasons; hardware and software.

**Hardware**: I opened the back of my laptop removed the heatsinks/fan and found that the factory thermal paste is super dry, it took me an hour to remove it... I applied a new fresh thermal paste (high performance) and put everything back together, boot it up and starts running cooler than before, however...

**Software**: I found out that firefox uses a lot of resources, therefore making your laptop run hotter. 
Here is what you can do: on the top left corner on firefox, click on the **orange button**, then you'll get a **drop down menu **, go to **help**, then select [B]restart with add-ons disabled.
[/B]if after it restarts your laptop runs a bit cooler, then check the add-ons and try to remove useless and unnecessary ones.

good luck

---

### Post by shriek11 on 2011-10-17
I was able to install it on my other computer.  It seems the problem was that even though there is a program that prepares a bootable usb stick on ubuntu, the wubi installer still thinks of it as a dvd and it was copying the whole usb drive, but then failing to properly execute it.  I transfered the usb stick files to desktop and voila it worked.

As for ubuntu, it seems amateurish with flash problems (no offense intended) compared to OS X.  I do get that it would be like that since Apple has top notch developers and pours a lot of money into their system.  I am also unable to go into the files / docs of my windows partition, so I might just leave it to play with in free time or perhaps try fedora in the future.

---

### Post by ajgreeny on 2011-10-21
> **shriek11 said:**
> I was able to install it on my other computer.  It seems the problem was that even though there is a program that prepares a bootable usb stick on ubuntu, the wubi installer still thinks of it as a dvd and it was copying the whole usb drive, but then failing to properly execute it.  I transfered the usb stick files to desktop and voila it worked.
I would suggest that a proper partitioned install would be better than a  wubi installation, which is only meant as a test of the software and  hardware.
> As for ubuntu, it seems amateurish with flash problems (no offense intended) compared to OS X.  I do get that it would be like that since Apple has top notch developers and pours a lot of money into their system.  I am also unable to go into the files / docs of my windows partition, so I might just leave it to play with in free time or perhaps try fedora in the future.

Unfortunately whatever distro you choose, Suse, Fedora, etc etc. the flash player/plugin will be exactly the same, that is to say, poor in comparison with windows (and maybe mac), simply because Adobe do not put as much effort into the linux flashplugin.  I can't comment on flash in Macs in any detail, as I do not, and never have used one.  Unfortunately the open source flash alternative gnash is not nearly as good as the adobe version and does not work at all on some sites, though it is getting better and better.

---

