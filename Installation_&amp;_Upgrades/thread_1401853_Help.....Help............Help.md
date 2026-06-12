---
title: "Help.....Help............Help"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by rascall on 2010-02-08
I have installed Ubuntu 9.10 from a live CD alongside windows xp, all was working fine then suddenly it would only boot to grub when ubuntu was selected. I decided to reinstall (having not read the solutions on here) after reinstall if I try and boot ubuntu I get "cannot find hal32.dll" If I try to boot from the live CD it fails and the following is displayed, ""invalid argument" see wubi log, end part of which is daisplayed below
> Ubuntu CD
02-07 23:20 DEBUG Distro: does not contain C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp is a valid Ubuntu CD
02-07 23:20 DEBUG Distro: does not contain C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp is a valid Ubuntu Netbook Remix CD
02-07 23:20 DEBUG Distro: does not contain C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp is a valid Kubuntu CD
02-07 23:20 DEBUG Distro: does not contain C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp is a valid Kubuntu CD
02-07 23:20 DEBUG Distro: does not contain C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp is a valid Kubuntu Netbook CD
02-07 23:20 DEBUG Distro: does not contain C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp is a valid Xubuntu CD
02-07 23:20 DEBUG Distro: does not contain C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp is a valid Xubuntu CD
02-07 23:20 DEBUG Distro: does not contain C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp is a valid Mythbuntu CD
02-07 23:20 DEBUG Distro: does not contain C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp is a valid Mythbuntu CD
02-07 23:20 DEBUG Distro: does not contain C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
02-07 23:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
02-07 23:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-07 23:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
02-07 23:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
02-07 23:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
02-07 23:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
02-07 23:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
02-07 23:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
02-07 23:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
02-07 23:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
02-07 23:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
02-07 23:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-07 23:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
02-07 23:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
02-07 23:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
02-07 23:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
02-07 23:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
02-07 23:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
02-07 23:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
02-07 23:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
02-07 23:20 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
02-07 23:20 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
02-07 23:20 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
02-07 23:20 INFO Distro: Found a valid CD for Ubuntu: F:\
02-07 23:20 INFO root: Running the CD menu...
02-07 23:20 DEBUG WindowsFrontend: __init__...
02-07 23:20 DEBUG WindowsFrontend: on_init...
02-07 23:20 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\translations, languages=['en_GB', 'en']
02-07 23:20 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\translations, languages=['en_GB', 'en']
02-07 23:20 INFO root: CD menu finished
02-07 23:20 INFO root: Running the installer...
02-07 23:20 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\translations, languages=['en_GB', 'en']
02-07 23:20 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\translations, languages=['en_GB', 'en']
02-07 23:21 DEBUG WinuiInstallationPage: target_drive=D:, installation_size=17000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=russell
02-07 23:21 INFO root: Received settings
02-07 23:21 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\translations, languages=['en_GB', 'en']
02-07 23:21 DEBUG TaskList: # Running tasklist...
02-07 23:21 DEBUG TaskList: ## Running select_target_dir...
02-07 23:21 INFO WindowsBackend: Installing into D:\ubuntu
02-07 23:21 DEBUG TaskList: ## Finished select_target_dir
02-07 23:21 DEBUG TaskList: ## Running create_dir_structure...
02-07 23:21 DEBUG CommonBackend: Creating dir D:\ubuntu
02-07 23:21 DEBUG CommonBackend: Creating dir D:\ubuntu\disks
02-07 23:21 DEBUG CommonBackend: Creating dir D:\ubuntu\install
02-07 23:21 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot
02-07 23:21 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot
02-07 23:21 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
02-07 23:21 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot\grub
02-07 23:21 DEBUG TaskList: ## Finished create_dir_structure
02-07 23:21 DEBUG TaskList: ## Running uncompress_target_dir...
02-07 23:21 DEBUG TaskList: ## Finished uncompress_target_dir
02-07 23:21 DEBUG TaskList: ## Running create_uninstaller...
02-07 23:21 DEBUG WindowsBackend: Copying uninstaller F:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
02-07 23:21 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
02-07 23:21 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
02-07 23:21 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-07 23:21 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
02-07 23:21 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
02-07 23:21 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-07 23:21 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-07 23:21 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-07 23:21 DEBUG TaskList: ## Finished create_uninstaller
02-07 23:21 DEBUG TaskList: ## Running copy_installation_files...
02-07 23:21 DEBUG WindowsBackend: Copying C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
02-07 23:21 DEBUG WindowsBackend: Copying C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\winboot -> D:\ubuntu\winboot
02-07 23:21 DEBUG WindowsBackend: Copying C:\DOCUME~1\Russell\LOCALS~1\Temp\pyl84.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
02-07 23:21 DEBUG TaskList: ## Finished copy_installation_files
02-07 23:21 DEBUG TaskList: ## Running get_iso...
02-07 23:21 DEBUG TaskList: New task copy_file
02-07 23:21 DEBUG TaskList: ### Running copy_file...
02-07 23:22 ERROR TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
02-07 23:22 DEBUG TaskList: # Cancelling tasklist
02-07 23:22 ERROR root: [Errno 22] Invalid argument
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 126, in select_task
File "\lib\wubi\application.py", line 194, in run_cd_menu
File "\lib\wubi\application.py", line 118, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
02-07 23:22 DEBUG TaskList: New task check_iso
02-07 23:22 DEBUG CommonBackend: Searching for local ISO
02-07 23:22 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
02-07 23:22 DEBUG TaskList: New task get_metalink
02-07 23:22 ERROR TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
02-07 23:22 DEBUG TaskList: # Cancelling tasklist
02-07 23:22 DEBUG TaskList: # Finished tasklist,
 
I have tried every password from here and all those from the accounts I set up in ubuntu. The same happens with the password request if I reinstall ...help. Win XP still boots no problem
 
Any help much appreciated
 
Regards
 
Russell

---

