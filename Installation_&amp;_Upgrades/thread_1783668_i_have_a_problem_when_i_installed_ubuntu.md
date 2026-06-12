---
title: "i have a problem when i installed ubuntu"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by knight night on 2011-06-16
i have a problem when i installed ubuntu
via usb drive and cd .. and i try it in windows xp and windows 7
it's a same problem .. but this is the error message

" permission denied "
the log
"    06-14 22:07 INFO   root: === wubi 10.04.2 rev191 ===
06-14 22:07 DEBUG  root: Logfile is c:\docume~1\adminu~1\locals~1\temp\wubi-10.04.2-rev191.log
06-14 22:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
06-14 22:07 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\data
06-14 22:07 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\bin\7z.exe
06-14 22:07 DEBUG  CommonBackend: Fetching basic info...
06-14 22:07 DEBUG  CommonBackend: original_exe=E:\wubi.exe
06-14 22:07 DEBUG  CommonBackend: platform=win32
06-14 22:07 DEBUG  CommonBackend: osname=nt
06-14 22:07 DEBUG  CommonBackend: language=ar_AE
06-14 22:07 DEBUG  CommonBackend: encoding=cp1256
06-14 22:07 DEBUG  WindowsBackend: arch=i386
06-14 22:07 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\data\isolist.ini
06-14 22:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-14 22:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-14 22:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-14 22:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-14 22:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-14 22:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-14 22:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-14 22:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-14 22:07 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-14 22:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-14 22:07 DEBUG  WindowsBackend: Fetching host info...
06-14 22:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-14 22:07 DEBUG  WindowsBackend: windows version=xp
06-14 22:07 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-14 22:07 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-14 22:07 DEBUG  WindowsBackend: windows_build=2600
06-14 22:07 DEBUG  WindowsBackend: gmt=2
06-14 22:07 DEBUG  WindowsBackend: country=AE
06-14 22:07 DEBUG  WindowsBackend: timezone=Asia/Dubai
06-14 22:07 DEBUG  WindowsBackend: windows_username=AdminUser
06-14 22:07 DEBUG  WindowsBackend: user_full_name=AdminUser
06-14 22:07 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\AdminUser
06-14 22:07 DEBUG  WindowsBackend: windows_language_code=1025
06-14 22:07 DEBUG  WindowsBackend: windows_language=Arabic
06-14 22:07 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 3.00GHz
06-14 22:07 DEBUG  WindowsBackend: bootloader=xp
06-14 22:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9515.7890625 mb free ntfs)
06-14 22:07 DEBUG  WindowsBackend: drive=Drive(C: hd 9515.7890625 mb free ntfs)
06-14 22:07 DEBUG  WindowsBackend: drive=Drive(D: hd 4372.75 mb free ntfs)
06-14 22:07 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
06-14 22:07 DEBUG  WindowsBackend: uninstaller_path=None
06-14 22:07 DEBUG  WindowsBackend: previous_target_dir=None
06-14 22:07 DEBUG  WindowsBackend: previous_distro_name=None
06-14 22:07 DEBUG  WindowsBackend: keyboard_id=67699721
06-14 22:07 DEBUG  WindowsBackend: keyboard_layout=us
06-14 22:07 DEBUG  WindowsBackend: keyboard_variant=
06-14 22:07 DEBUG  CommonBackend: python locale=('ar_AE', 'cp1256')
06-14 22:07 DEBUG  CommonBackend: locale=ar_AE.UTF-8
06-14 22:07 DEBUG  WindowsBackend: total_memory_mb=502.98046875
06-14 22:07 DEBUG  CommonBackend: Searching ISOs on USB devices
06-14 22:07 DEBUG  CommonBackend: Searching for local CDs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu Netbook CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu Netbook CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-14 22:07 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release i386 (20110211.1)
06-14 22:07 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
06-14 22:07 DEBUG  Distro: wrong arch: i386 != amd64
06-14 22:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-14 22:07 INFO   Distro: Found a valid CD for Ubuntu: E:\
06-14 22:07 INFO   root: Running the CD menu...
06-14 22:07 DEBUG  WindowsFrontend: __init__...
06-14 22:07 DEBUG  WindowsFrontend: on_init...
06-14 22:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['ar_AE', 'ar']
06-14 22:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['ar_AE', 'ar']
06-14 22:07 INFO   root: === wubi 10.04.2 rev191 ===
06-14 22:07 DEBUG  root: Logfile is c:\docume~1\adminu~1\locals~1\temp\wubi-10.04.2-rev191.log
06-14 22:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
06-14 22:07 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp\data
06-14 22:07 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp\bin\7z.exe
06-14 22:07 DEBUG  CommonBackend: Fetching basic info...
06-14 22:07 DEBUG  CommonBackend: original_exe=E:\wubi.exe
06-14 22:07 DEBUG  CommonBackend: platform=win32
06-14 22:07 DEBUG  CommonBackend: osname=nt
06-14 22:07 DEBUG  CommonBackend: language=ar_AE
06-14 22:07 DEBUG  CommonBackend: encoding=cp1256
06-14 22:07 DEBUG  WindowsBackend: arch=i386
06-14 22:07 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp\data\isolist.ini
06-14 22:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-14 22:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-14 22:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-14 22:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-14 22:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-14 22:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-14 22:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-14 22:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-14 22:07 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-14 22:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-14 22:07 DEBUG  WindowsBackend: Fetching host info...
06-14 22:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-14 22:07 DEBUG  WindowsBackend: windows version=xp
06-14 22:07 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-14 22:07 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-14 22:07 DEBUG  WindowsBackend: windows_build=2600
06-14 22:07 DEBUG  WindowsBackend: gmt=2
06-14 22:07 DEBUG  WindowsBackend: country=AE
06-14 22:07 DEBUG  WindowsBackend: timezone=Asia/Dubai
06-14 22:07 DEBUG  WindowsBackend: windows_username=AdminUser
06-14 22:07 DEBUG  WindowsBackend: user_full_name=AdminUser
06-14 22:07 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\AdminUser
06-14 22:07 DEBUG  WindowsBackend: windows_language_code=1025
06-14 22:07 DEBUG  WindowsBackend: windows_language=Arabic
06-14 22:07 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 3.00GHz
06-14 22:07 DEBUG  WindowsBackend: bootloader=xp
06-14 22:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9510.4375 mb free ntfs)
06-14 22:07 DEBUG  WindowsBackend: drive=Drive(C: hd 9510.4375 mb free ntfs)
06-14 22:07 DEBUG  WindowsBackend: drive=Drive(D: hd 4372.75 mb free ntfs)
06-14 22:07 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
06-14 22:07 DEBUG  WindowsBackend: uninstaller_path=None
06-14 22:07 DEBUG  WindowsBackend: previous_target_dir=None
06-14 22:07 DEBUG  WindowsBackend: previous_distro_name=None
06-14 22:07 DEBUG  WindowsBackend: keyboard_id=67699721
06-14 22:07 DEBUG  WindowsBackend: keyboard_layout=us
06-14 22:07 DEBUG  WindowsBackend: keyboard_variant=
06-14 22:07 DEBUG  CommonBackend: python locale=('ar_AE', 'cp1256')
06-14 22:07 DEBUG  CommonBackend: locale=ar_AE.UTF-8
06-14 22:07 DEBUG  WindowsBackend: total_memory_mb=502.98046875
06-14 22:07 DEBUG  CommonBackend: Searching ISOs on USB devices
06-14 22:07 DEBUG  CommonBackend: Searching for local CDs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu Netbook CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu Netbook CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
06-14 22:07 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-14 22:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-14 22:07 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release i386 (20110211.1)
06-14 22:07 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
06-14 22:07 DEBUG  Distro: wrong arch: i386 != amd64
06-14 22:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-14 22:07 INFO   Distro: Found a valid CD for Ubuntu: E:\
06-14 22:07 INFO   root: Running the CD menu...
06-14 22:07 DEBUG  WindowsFrontend: __init__...
06-14 22:07 DEBUG  WindowsFrontend: on_init...
06-14 22:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['ar_AE', 'ar']
06-14 22:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['ar_AE', 'ar']
06-14 22:07 INFO   WindowsFrontend: Operation cancelled
06-14 22:07 DEBUG  WindowsFrontend: frontend.quit
06-14 22:07 DEBUG  WindowsFrontend: frontend.on_quit
06-14 22:07 DEBUG  root: application.on_quit
06-14 22:07 INFO   root: sys.exit
06-14 22:07 INFO   root: CD menu finished
06-14 22:07 INFO   root: Running the installer...
06-14 22:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['ar_AE', 'ar']
06-14 22:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['ar_AE', 'ar']
06-14 22:08 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=6000MB, distro_name=Ubuntu, language=ar_AE, locale=ar_AE.UTF-8, username=pc-3
06-14 22:08 INFO   root: Received settings
06-14 22:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['ar_AE', 'ar']
06-14 22:08 DEBUG  TaskList: # Running tasklist...
06-14 22:08 DEBUG  TaskList: ## Running select_target_dir...
06-14 22:08 INFO   WindowsBackend: Installing into C:\ubuntu
06-14 22:08 DEBUG  TaskList: ## Finished select_target_dir
06-14 22:08 DEBUG  TaskList: ## Running create_dir_structure...
06-14 22:08 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-14 22:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-14 22:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-14 22:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-14 22:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-14 22:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-14 22:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-14 22:08 DEBUG  TaskList: ## Finished create_dir_structure
06-14 22:08 DEBUG  TaskList: ## Running uncompress_target_dir...
06-14 22:08 DEBUG  TaskList: ## Finished uncompress_target_dir
06-14 22:08 DEBUG  TaskList: ## Running create_uninstaller...
06-14 22:08 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-14 22:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
06-14 22:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
06-14 22:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-14 22:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
06-14 22:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.2-rev191
06-14 22:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-14 22:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-14 22:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-14 22:08 DEBUG  TaskList: ## Finished create_uninstaller
06-14 22:08 DEBUG  TaskList: ## Running copy_installation_files...
06-14 22:08 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
06-14 22:08 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\winboot -> C:\ubuntu\winboot
06-14 22:08 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl6.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
06-14 22:08 DEBUG  TaskList: ## Finished copy_installation_files
06-14 22:08 DEBUG  TaskList: ## Running get_iso...
06-14 22:08 DEBUG  TaskList: New task copy_file
06-14 22:08 DEBUG  TaskList: ### Running copy_file...
06-14 22:14 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
06-14 22:14 DEBUG  TaskList: # Cancelling tasklist
06-14 22:14 DEBUG  TaskList: New task check_iso
06-14 22:14 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
06-14 22:14 DEBUG  CommonBackend: Searching for local ISO
06-14 22:14 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-14 22:14 DEBUG  TaskList: New task get_metalink
06-14 22:14 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
06-14 22:14 DEBUG  TaskList: # Cancelling tasklist
06-14 22:14 DEBUG  TaskList: # Finished tasklist
06-14 22:16 INFO   root: === wubi 10.04.2 rev191 ===
06-14 22:16 DEBUG  root: Logfile is c:\docume~1\adminu~1\locals~1\temp\wubi-10.04.2-rev191.log
06-14 22:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
06-14 22:16 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp\data
06-14 22:16 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp\bin\7z.exe
06-14 22:16 DEBUG  CommonBackend: Fetching basic info...
06-14 22:16 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
06-14 22:16 DEBUG  CommonBackend: platform=win32
06-14 22:16 DEBUG  CommonBackend: osname=nt
06-14 22:16 DEBUG  CommonBackend: language=ar_AE
06-14 22:16 DEBUG  CommonBackend: encoding=cp1256
06-14 22:16 DEBUG  WindowsBackend: arch=i386
06-14 22:16 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp\data\isolist.ini
06-14 22:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-14 22:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-14 22:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-14 22:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-14 22:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-14 22:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-14 22:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-14 22:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-14 22:16 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-14 22:16 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-14 22:16 DEBUG  WindowsBackend: Fetching host info...
06-14 22:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-14 22:16 DEBUG  WindowsBackend: windows version=xp
06-14 22:16 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-14 22:16 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-14 22:16 DEBUG  WindowsBackend: windows_build=2600
06-14 22:16 DEBUG  WindowsBackend: gmt=2
06-14 22:16 DEBUG  WindowsBackend: country=AE
06-14 22:16 DEBUG  WindowsBackend: timezone=Asia/Dubai
06-14 22:16 DEBUG  WindowsBackend: windows_username=AdminUser
06-14 22:16 DEBUG  WindowsBackend: user_full_name=AdminUser
06-14 22:16 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\AdminUser
06-14 22:16 DEBUG  WindowsBackend: windows_language_code=1025
06-14 22:16 DEBUG  WindowsBackend: windows_language=Arabic
06-14 22:16 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 3.00GHz
06-14 22:16 DEBUG  WindowsBackend: bootloader=xp
06-14 22:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8714.66796875 mb free ntfs)
06-14 22:16 DEBUG  WindowsBackend: drive=Drive(C: hd 8714.66796875 mb free ntfs)
06-14 22:16 DEBUG  WindowsBackend: drive=Drive(D: hd 4372.75 mb free ntfs)
06-14 22:16 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
06-14 22:16 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-14 22:16 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-14 22:16 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-14 22:16 DEBUG  WindowsBackend: keyboard_id=67699721
06-14 22:16 DEBUG  WindowsBackend: keyboard_layout=us
06-14 22:16 DEBUG  WindowsBackend: keyboard_variant=
06-14 22:16 DEBUG  CommonBackend: python locale=('ar_AE', 'cp1256')
06-14 22:16 DEBUG  CommonBackend: locale=ar_AE.UTF-8
06-14 22:16 DEBUG  WindowsBackend: total_memory_mb=502.98046875
06-14 22:16 DEBUG  CommonBackend: Searching ISOs on USB devices
06-14 22:16 DEBUG  CommonBackend: Searching for local CDs
06-14 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
06-14 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
06-14 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu Netbook CD
06-14 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
06-14 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
06-14 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu Netbook CD
06-14 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
06-14 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
06-14 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
06-14 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
06-14 22:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-14 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-14 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-14 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-14 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-14 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-14 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-14 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-14 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-14 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-14 22:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-14 22:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-14 22:16 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release i386 (20110211.1)
06-14 22:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
06-14 22:16 DEBUG  Distro: wrong arch: i386 != amd64
06-14 22:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-14 22:16 INFO   Distro: Found a valid CD for Ubuntu: E:\
06-14 22:16 INFO   root: Running the uninstaller...
06-14 22:16 INFO   CommonBackend: This is the uninstaller running
06-14 22:16 DEBUG  WindowsFrontend: __init__...
06-14 22:16 DEBUG  WindowsFrontend: on_init...
06-14 22:16 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINU~1\LOCALS~1\Temp\pyl8.tmp\translations, languages=['ar_AE', 'ar']

also i try this v  Ubuntu 11.04
                   Ubuntu 10.10

Thank a lot

---

### Post by mörgæs on 2011-06-16
Hi, welcome to the fora.

If you have problems with Wubi, this thread is the best to consult:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by uRock on 2011-06-16
Duplicate post in Wubi Mega Thread.

Thread Closed

---

