---
title: "Ubuntu CD doesn't boot!"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by Dunk1994 on 2010-02-25
Hi,

I place the CD into my disk drive and it autoruns, I click 'Demo and Full Installation', select 'Reboot Now' and click 'Ok'. My computer then simply restarts without booting the CD ;)

I have tried to install the CD Boot Helper but this fails too, and an error box appears stating: 

'An error occured: Permission denied'

It then tells me to see a log file for further info on the error, this file reads:

02-25 19:12 INFO   root: === wubi 9.10ubuntu1 rev160 ===
02-25 19:12 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-9.10ubuntu1-rev160.log
02-25 19:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
02-25 19:12 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\data
02-25 19:12 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\bin\7z.exe
02-25 19:12 DEBUG  CommonBackend: Fetching basic info...
02-25 19:12 DEBUG  CommonBackend: original_exe=D:\wubi.exe
02-25 19:12 DEBUG  CommonBackend: platform=win32
02-25 19:12 DEBUG  CommonBackend: osname=nt
02-25 19:12 DEBUG  CommonBackend: language=en_GB
02-25 19:12 DEBUG  CommonBackend: encoding=cp1252
02-25 19:12 DEBUG  WindowsBackend: arch=i386
02-25 19:12 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\data\isolist.ini
02-25 19:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-25 19:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-25 19:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-25 19:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-25 19:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-25 19:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-25 19:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-25 19:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-25 19:12 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-25 19:12 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-25 19:12 DEBUG  WindowsBackend: Fetching host info...
02-25 19:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-25 19:12 DEBUG  WindowsBackend: windows version=xp
02-25 19:12 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-25 19:12 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-25 19:12 DEBUG  WindowsBackend: windows_build=2600
02-25 19:12 DEBUG  WindowsBackend: gmt=0
02-25 19:12 DEBUG  WindowsBackend: country=GB
02-25 19:12 DEBUG  WindowsBackend: timezone=Europe/London
02-25 19:12 DEBUG  WindowsBackend: windows_username=Owner
02-25 19:12 DEBUG  WindowsBackend: user_full_name=Owner
02-25 19:12 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
02-25 19:12 DEBUG  WindowsBackend: windows_language_code=1033
02-25 19:12 DEBUG  WindowsBackend: windows_language=English
02-25 19:12 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) M processor         1.40GHz
02-25 19:12 DEBUG  WindowsBackend: bootloader=xp
02-25 19:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 22678.6875 mb free ntfs)
02-25 19:12 DEBUG  WindowsBackend: drive=Drive(C: hd 22678.6875 mb free ntfs)
02-25 19:12 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-25 19:12 DEBUG  WindowsBackend: uninstaller_path=None
02-25 19:12 DEBUG  WindowsBackend: previous_target_dir=None
02-25 19:12 DEBUG  WindowsBackend: previous_distro_name=None
02-25 19:12 DEBUG  WindowsBackend: keyboard_id=134809609
02-25 19:12 DEBUG  WindowsBackend: keyboard_layout=gb
02-25 19:12 DEBUG  WindowsBackend: keyboard_variant=
02-25 19:12 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-25 19:12 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-25 19:12 DEBUG  WindowsBackend: total_memory_mb=477.484375
02-25 19:12 DEBUG  CommonBackend: Searching ISOs on USB devices
02-25 19:12 DEBUG  CommonBackend: Searching for local CDs
02-25 19:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp is a valid Ubuntu CD
02-25 19:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
02-25 19:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp is a valid Ubuntu CD
02-25 19:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
02-25 19:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp is a valid Ubuntu Netbook Remix CD
02-25 19:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
02-25 19:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp is a valid Kubuntu CD
02-25 19:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
02-25 19:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp is a valid Kubuntu CD
02-25 19:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
02-25 19:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp is a valid Kubuntu Netbook CD
02-25 19:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
02-25 19:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp is a valid Xubuntu CD
02-25 19:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
02-25 19:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp is a valid Xubuntu CD
02-25 19:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
02-25 19:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp is a valid Mythbuntu CD
02-25 19:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
02-25 19:12 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp is a valid Mythbuntu CD
02-25 19:12 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
02-25 19:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 19:12 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
02-25 19:12 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
02-25 19:12 DEBUG  Distro: wrong arch: i386 != amd64
02-25 19:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 19:12 INFO   Distro: Found a valid CD for Ubuntu: D:\
02-25 19:12 INFO   root: Running the CD menu...
02-25 19:12 DEBUG  WindowsFrontend: __init__...
02-25 19:12 DEBUG  WindowsFrontend: on_init...
02-25 19:12 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\translations, languages=['en_GB', 'en']
02-25 19:12 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\translations, languages=['en_GB', 'en']
02-25 19:13 INFO   root: CD menu finished
02-25 19:13 INFO   root: Running the CD boot helper...
02-25 19:13 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\translations, languages=['en_GB', 'en']
02-25 19:13 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\translations, languages=['en_GB', 'en']
02-25 19:13 INFO   root: CD boot helper confirmed
02-25 19:13 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\translations, languages=['en_GB', 'en']
02-25 19:13 DEBUG  TaskList: # Running tasklist...
02-25 19:13 DEBUG  TaskList: ## Running select_target_dir...
02-25 19:13 INFO   WindowsBackend: Installing into C:\ubuntu
02-25 19:13 DEBUG  TaskList: ## Finished select_target_dir
02-25 19:13 DEBUG  TaskList: ## Running create_dir_structure...
02-25 19:13 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-25 19:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-25 19:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-25 19:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-25 19:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-25 19:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-25 19:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-25 19:13 DEBUG  TaskList: ## Finished create_dir_structure
02-25 19:13 DEBUG  TaskList: ## Running uncompress_target_dir...
02-25 19:13 DEBUG  TaskList: ## Finished uncompress_target_dir
02-25 19:13 DEBUG  TaskList: ## Running create_uninstaller...
02-25 19:13 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-25 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-25 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-25 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-25 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-25 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
02-25 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-25 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-25 19:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-25 19:13 DEBUG  TaskList: ## Finished create_uninstaller
02-25 19:13 DEBUG  TaskList: ## Running copy_installation_files...
02-25 19:13 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-25 19:13 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\winboot -> C:\ubuntu\winboot
02-25 19:13 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pylF.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
02-25 19:13 DEBUG  TaskList: ## Finished copy_installation_files
02-25 19:13 DEBUG  TaskList: ## Running use_cd...
02-25 19:13 DEBUG  TaskList: New task copy_file
02-25 19:13 DEBUG  TaskList: ### Running copy_file...
02-25 19:17 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
02-25 19:17 DEBUG  TaskList: # Cancelling tasklist
02-25 19:17 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
02-25 19:17 DEBUG  TaskList: New task check_iso
02-25 19:17 DEBUG  TaskList: ## Finished use_cd
02-25 19:17 DEBUG  TaskList: # Finished tasklist
02-25 19:26 INFO   root: === wubi 9.10ubuntu1 rev160 ===
02-25 19:26 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-9.10ubuntu1-rev160.log
02-25 19:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
02-25 19:26 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\data
02-25 19:26 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
02-25 19:26 DEBUG  CommonBackend: Fetching basic info...
02-25 19:26 DEBUG  CommonBackend: original_exe=D:\wubi.exe
02-25 19:26 DEBUG  CommonBackend: platform=win32
02-25 19:26 DEBUG  CommonBackend: osname=nt
02-25 19:26 DEBUG  CommonBackend: language=en_GB
02-25 19:26 DEBUG  CommonBackend: encoding=cp1252
02-25 19:26 DEBUG  WindowsBackend: arch=i386
02-25 19:26 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
02-25 19:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-25 19:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-25 19:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-25 19:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-25 19:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-25 19:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-25 19:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-25 19:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-25 19:26 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-25 19:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-25 19:26 DEBUG  WindowsBackend: Fetching host info...
02-25 19:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-25 19:26 DEBUG  WindowsBackend: windows version=xp
02-25 19:26 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-25 19:26 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-25 19:26 DEBUG  WindowsBackend: windows_build=2600
02-25 19:26 DEBUG  WindowsBackend: gmt=0
02-25 19:26 DEBUG  WindowsBackend: country=GB
02-25 19:26 DEBUG  WindowsBackend: timezone=Europe/London
02-25 19:26 DEBUG  WindowsBackend: windows_username=Owner
02-25 19:26 DEBUG  WindowsBackend: user_full_name=Owner
02-25 19:26 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
02-25 19:26 DEBUG  WindowsBackend: windows_language_code=1033
02-25 19:26 DEBUG  WindowsBackend: windows_language=English
02-25 19:26 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) M processor         1.40GHz
02-25 19:26 DEBUG  WindowsBackend: bootloader=xp
02-25 19:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 22121.4257813 mb free ntfs)
02-25 19:26 DEBUG  WindowsBackend: drive=Drive(C: hd 22121.4257813 mb free ntfs)
02-25 19:26 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-25 19:26 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-25 19:26 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-25 19:26 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-25 19:26 DEBUG  WindowsBackend: keyboard_id=134809609
02-25 19:26 DEBUG  WindowsBackend: keyboard_layout=gb
02-25 19:26 DEBUG  WindowsBackend: keyboard_variant=
02-25 19:26 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-25 19:26 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-25 19:26 DEBUG  WindowsBackend: total_memory_mb=477.484375
02-25 19:26 DEBUG  CommonBackend: Searching ISOs on USB devices
02-25 19:26 DEBUG  CommonBackend: Searching for local CDs
02-25 19:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
02-25 19:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
02-25 19:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook Remix CD
02-25 19:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
02-25 19:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
02-25 19:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
02-25 19:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
02-25 19:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
02-25 19:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
02-25 19:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:26 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
02-25 19:26 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 19:26 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
02-25 19:26 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
02-25 19:26 DEBUG  Distro: wrong arch: i386 != amd64
02-25 19:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 19:26 INFO   Distro: Found a valid CD for Ubuntu: D:\
02-25 19:26 INFO   root: Running the CD menu...
02-25 19:26 DEBUG  WindowsFrontend: __init__...
02-25 19:26 DEBUG  WindowsFrontend: on_init...
02-25 19:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_GB', 'en']
02-25 19:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_GB', 'en']
02-25 19:27 INFO   root: CD menu finished
02-25 19:27 INFO   root: Already installed, running the uninstaller...
02-25 19:27 INFO   root: Running the uninstaller...
02-25 19:27 INFO   CommonBackend: This is the uninstaller running
02-25 19:27 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_GB', 'en']
02-25 19:28 INFO   root: Received settings
02-25 19:28 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_GB', 'en']
02-25 19:28 DEBUG  TaskList: # Running tasklist...
02-25 19:28 DEBUG  TaskList: ## Running Backup ISO...
02-25 19:28 DEBUG  TaskList: ## Finished Backup ISO
02-25 19:28 DEBUG  TaskList: ## Running Remove bootloader entry...
02-25 19:28 ERROR  WindowsBackend: Cannot find bcdedit
02-25 19:28 DEBUG  WindowsBackend: undo_bootini C:
02-25 19:28 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 22121.4257813 mb free ntfs)
02-25 19:28 DEBUG  TaskList: ## Finished Remove bootloader entry
02-25 19:28 DEBUG  TaskList: ## Running Remove target dir...
02-25 19:28 DEBUG  CommonBackend: Deleting C:\ubuntu
02-25 19:28 DEBUG  TaskList: ## Finished Remove target dir
02-25 19:28 DEBUG  TaskList: ## Running Remove registry key...
02-25 19:28 DEBUG  TaskList: ## Finished Remove registry key
02-25 19:28 DEBUG  TaskList: # Finished tasklist
02-25 19:28 INFO   root: Almost finished uninstalling
02-25 19:28 INFO   root: Finished uninstallation
02-25 19:28 DEBUG  CommonBackend: Fetching basic info...
02-25 19:28 DEBUG  CommonBackend: original_exe=D:\wubi.exe
02-25 19:28 DEBUG  CommonBackend: platform=win32
02-25 19:28 DEBUG  CommonBackend: osname=nt
02-25 19:28 DEBUG  WindowsBackend: arch=i386
02-25 19:28 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
02-25 19:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-25 19:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-25 19:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-25 19:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-25 19:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-25 19:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-25 19:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-25 19:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-25 19:28 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-25 19:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-25 19:28 DEBUG  WindowsBackend: Fetching host info...
02-25 19:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-25 19:28 DEBUG  WindowsBackend: windows version=xp
02-25 19:28 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-25 19:28 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-25 19:28 DEBUG  WindowsBackend: windows_build=2600
02-25 19:28 DEBUG  WindowsBackend: gmt=0
02-25 19:28 DEBUG  WindowsBackend: country=GB
02-25 19:28 DEBUG  WindowsBackend: timezone=Europe/London
02-25 19:28 DEBUG  WindowsBackend: windows_username=Owner
02-25 19:28 DEBUG  WindowsBackend: user_full_name=Owner
02-25 19:28 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
02-25 19:28 DEBUG  WindowsBackend: windows_language_code=1033
02-25 19:28 DEBUG  WindowsBackend: windows_language=English
02-25 19:28 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) M processor         1.40GHz
02-25 19:28 DEBUG  WindowsBackend: bootloader=xp
02-25 19:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 22680.9492188 mb free ntfs)
02-25 19:28 DEBUG  WindowsBackend: drive=Drive(C: hd 22680.9492188 mb free ntfs)
02-25 19:28 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-25 19:28 DEBUG  WindowsBackend: uninstaller_path=None
02-25 19:28 DEBUG  WindowsBackend: previous_target_dir=None
02-25 19:28 DEBUG  WindowsBackend: previous_distro_name=None
02-25 19:28 DEBUG  WindowsBackend: keyboard_id=134809609
02-25 19:28 DEBUG  WindowsBackend: keyboard_layout=gb
02-25 19:28 DEBUG  WindowsBackend: keyboard_variant=
02-25 19:28 DEBUG  WindowsBackend: total_memory_mb=477.484375
02-25 19:28 DEBUG  CommonBackend: Searching ISOs on USB devices
02-25 19:28 DEBUG  CommonBackend: Searching for local CDs
02-25 19:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
02-25 19:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
02-25 19:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook Remix CD
02-25 19:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
02-25 19:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
02-25 19:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
02-25 19:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
02-25 19:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
02-25 19:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
02-25 19:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
02-25 19:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
02-25 19:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 19:28 DEBUG  Distro: wrong arch: i386 != amd64
02-25 19:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 19:28 INFO   Distro: Found a valid CD for Ubuntu: D:\
02-25 19:28 INFO   root: Running the CD boot helper...
02-25 19:28 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_GB', 'en']
02-25 19:28 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_GB', 'en']
02-25 19:28 INFO   root: CD boot helper confirmed
02-25 19:28 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_GB', 'en']
02-25 19:28 DEBUG  TaskList: # Running tasklist...
02-25 19:28 DEBUG  TaskList: ## Running select_target_dir...
02-25 19:28 INFO   WindowsBackend: Installing into C:\ubuntu
02-25 19:28 DEBUG  TaskList: ## Finished select_target_dir
02-25 19:28 DEBUG  TaskList: ## Running create_dir_structure...
02-25 19:28 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-25 19:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-25 19:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-25 19:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-25 19:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-25 19:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-25 19:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-25 19:28 DEBUG  TaskList: ## Finished create_dir_structure
02-25 19:28 DEBUG  TaskList: ## Running uncompress_target_dir...
02-25 19:28 DEBUG  TaskList: ## Finished uncompress_target_dir
02-25 19:28 DEBUG  TaskList: ## Running create_uninstaller...
02-25 19:28 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-25 19:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-25 19:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-25 19:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-25 19:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-25 19:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
02-25 19:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-25 19:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-25 19:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-25 19:28 DEBUG  TaskList: ## Finished create_uninstaller
02-25 19:28 DEBUG  TaskList: ## Running copy_installation_files...
02-25 19:28 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-25 19:28 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\winboot -> C:\ubuntu\winboot
02-25 19:28 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl1.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
02-25 19:28 DEBUG  TaskList: ## Finished copy_installation_files
02-25 19:28 DEBUG  TaskList: ## Running use_cd...
02-25 19:28 DEBUG  TaskList: New task copy_file
02-25 19:28 DEBUG  TaskList: ### Running copy_file...
02-25 19:32 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
02-25 19:32 DEBUG  TaskList: # Cancelling tasklist
02-25 19:32 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
02-25 19:32 DEBUG  TaskList: New task check_iso
02-25 19:32 DEBUG  TaskList: ## Finished use_cd
02-25 19:32 DEBUG  TaskList: # Finished tasklist
02-25 20:04 INFO   root: === wubi 9.10ubuntu1 rev160 ===
02-25 20:04 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-9.10ubuntu1-rev160.log
02-25 20:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
02-25 20:04 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\data
02-25 20:04 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\bin\7z.exe
02-25 20:04 DEBUG  CommonBackend: Fetching basic info...
02-25 20:04 DEBUG  CommonBackend: original_exe=D:\wubi.exe
02-25 20:04 DEBUG  CommonBackend: platform=win32
02-25 20:04 DEBUG  CommonBackend: osname=nt
02-25 20:04 DEBUG  CommonBackend: language=en_GB
02-25 20:04 DEBUG  CommonBackend: encoding=cp1252
02-25 20:04 DEBUG  WindowsBackend: arch=i386
02-25 20:04 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\data\isolist.ini
02-25 20:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-25 20:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-25 20:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-25 20:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-25 20:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-25 20:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-25 20:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-25 20:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-25 20:04 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-25 20:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-25 20:04 DEBUG  WindowsBackend: Fetching host info...
02-25 20:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-25 20:04 DEBUG  WindowsBackend: windows version=xp
02-25 20:04 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-25 20:04 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-25 20:04 DEBUG  WindowsBackend: windows_build=2600
02-25 20:04 DEBUG  WindowsBackend: gmt=0
02-25 20:04 DEBUG  WindowsBackend: country=GB
02-25 20:04 DEBUG  WindowsBackend: timezone=Europe/London
02-25 20:04 DEBUG  WindowsBackend: windows_username=Owner
02-25 20:04 DEBUG  WindowsBackend: user_full_name=Owner
02-25 20:04 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
02-25 20:04 DEBUG  WindowsBackend: windows_language_code=1033
02-25 20:04 DEBUG  WindowsBackend: windows_language=English
02-25 20:04 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) M processor         1.40GHz
02-25 20:04 DEBUG  WindowsBackend: bootloader=xp
02-25 20:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 22115.4453125 mb free ntfs)
02-25 20:04 DEBUG  WindowsBackend: drive=Drive(C: hd 22115.4453125 mb free ntfs)
02-25 20:04 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-25 20:04 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-25 20:04 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-25 20:04 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-25 20:04 DEBUG  WindowsBackend: keyboard_id=134809609
02-25 20:04 DEBUG  WindowsBackend: keyboard_layout=gb
02-25 20:04 DEBUG  WindowsBackend: keyboard_variant=
02-25 20:04 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-25 20:04 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-25 20:04 DEBUG  WindowsBackend: total_memory_mb=477.484375
02-25 20:04 DEBUG  CommonBackend: Searching ISOs on USB devices
02-25 20:04 DEBUG  CommonBackend: Searching for local CDs
02-25 20:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
02-25 20:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
02-25 20:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Netbook Remix CD
02-25 20:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
02-25 20:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
02-25 20:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
02-25 20:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
02-25 20:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
02-25 20:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
02-25 20:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:04 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
02-25 20:04 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 20:04 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
02-25 20:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
02-25 20:04 DEBUG  Distro: wrong arch: i386 != amd64
02-25 20:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 20:04 INFO   Distro: Found a valid CD for Ubuntu: D:\
02-25 20:04 INFO   root: Running the CD menu...
02-25 20:04 DEBUG  WindowsFrontend: __init__...
02-25 20:04 DEBUG  WindowsFrontend: on_init...
02-25 20:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_GB', 'en']
02-25 20:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_GB', 'en']
02-25 20:14 INFO   root: CD menu finished
02-25 20:14 INFO   root: Already installed, running the uninstaller...
02-25 20:14 INFO   root: Running the uninstaller...
02-25 20:14 INFO   CommonBackend: This is the uninstaller running
02-25 20:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_GB', 'en']
02-25 20:14 INFO   root: Received settings
02-25 20:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_GB', 'en']
02-25 20:14 DEBUG  TaskList: # Running tasklist...
02-25 20:14 DEBUG  TaskList: ## Running Backup ISO...
02-25 20:14 DEBUG  TaskList: ## Finished Backup ISO
02-25 20:14 DEBUG  TaskList: ## Running Remove bootloader entry...
02-25 20:14 ERROR  WindowsBackend: Cannot find bcdedit
02-25 20:14 DEBUG  WindowsBackend: undo_bootini C:
02-25 20:14 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 22115.4453125 mb free ntfs)
02-25 20:14 DEBUG  TaskList: ## Finished Remove bootloader entry
02-25 20:14 DEBUG  TaskList: ## Running Remove target dir...
02-25 20:14 DEBUG  CommonBackend: Deleting C:\ubuntu
02-25 20:14 DEBUG  TaskList: ## Finished Remove target dir
02-25 20:14 DEBUG  TaskList: ## Running Remove registry key...
02-25 20:14 DEBUG  TaskList: ## Finished Remove registry key
02-25 20:14 DEBUG  TaskList: # Finished tasklist
02-25 20:14 INFO   root: Almost finished uninstalling
02-25 20:14 INFO   root: Finished uninstallation
02-25 20:14 DEBUG  CommonBackend: Fetching basic info...
02-25 20:14 DEBUG  CommonBackend: original_exe=D:\wubi.exe
02-25 20:14 DEBUG  CommonBackend: platform=win32
02-25 20:14 DEBUG  CommonBackend: osname=nt
02-25 20:14 DEBUG  WindowsBackend: arch=i386
02-25 20:14 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\data\isolist.ini
02-25 20:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-25 20:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-25 20:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-25 20:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-25 20:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-25 20:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-25 20:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-25 20:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-25 20:14 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-25 20:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-25 20:14 DEBUG  WindowsBackend: Fetching host info...
02-25 20:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-25 20:14 DEBUG  WindowsBackend: windows version=xp
02-25 20:14 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-25 20:14 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-25 20:14 DEBUG  WindowsBackend: windows_build=2600
02-25 20:14 DEBUG  WindowsBackend: gmt=0
02-25 20:14 DEBUG  WindowsBackend: country=GB
02-25 20:14 DEBUG  WindowsBackend: timezone=Europe/London
02-25 20:14 DEBUG  WindowsBackend: windows_username=Owner
02-25 20:14 DEBUG  WindowsBackend: user_full_name=Owner
02-25 20:14 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
02-25 20:14 DEBUG  WindowsBackend: windows_language_code=1033
02-25 20:14 DEBUG  WindowsBackend: windows_language=English
02-25 20:14 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) M processor         1.40GHz
02-25 20:14 DEBUG  WindowsBackend: bootloader=xp
02-25 20:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 22673.0078125 mb free ntfs)
02-25 20:14 DEBUG  WindowsBackend: drive=Drive(C: hd 22673.0078125 mb free ntfs)
02-25 20:14 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-25 20:14 DEBUG  WindowsBackend: uninstaller_path=None
02-25 20:14 DEBUG  WindowsBackend: previous_target_dir=None
02-25 20:14 DEBUG  WindowsBackend: previous_distro_name=None
02-25 20:14 DEBUG  WindowsBackend: keyboard_id=134809609
02-25 20:14 DEBUG  WindowsBackend: keyboard_layout=gb
02-25 20:14 DEBUG  WindowsBackend: keyboard_variant=
02-25 20:14 DEBUG  WindowsBackend: total_memory_mb=477.484375
02-25 20:14 DEBUG  CommonBackend: Searching ISOs on USB devices
02-25 20:14 DEBUG  CommonBackend: Searching for local CDs
02-25 20:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
02-25 20:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
02-25 20:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Netbook Remix CD
02-25 20:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
02-25 20:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
02-25 20:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
02-25 20:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
02-25 20:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
02-25 20:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
02-25 20:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
02-25 20:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
02-25 20:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 20:14 DEBUG  Distro: wrong arch: i386 != amd64
02-25 20:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 20:14 INFO   Distro: Found a valid CD for Ubuntu: D:\
02-25 20:14 INFO   root: Running the CD boot helper...
02-25 20:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_GB', 'en']
02-25 20:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_GB', 'en']
02-25 20:14 INFO   root: CD boot helper confirmed
02-25 20:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_GB', 'en']
02-25 20:14 DEBUG  TaskList: # Running tasklist...
02-25 20:14 DEBUG  TaskList: ## Running select_target_dir...
02-25 20:14 INFO   WindowsBackend: Installing into C:\ubuntu
02-25 20:14 DEBUG  TaskList: ## Finished select_target_dir
02-25 20:14 DEBUG  TaskList: ## Running create_dir_structure...
02-25 20:14 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-25 20:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-25 20:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-25 20:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-25 20:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-25 20:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-25 20:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-25 20:14 DEBUG  TaskList: ## Finished create_dir_structure
02-25 20:14 DEBUG  TaskList: ## Running uncompress_target_dir...
02-25 20:14 DEBUG  TaskList: ## Finished uncompress_target_dir
02-25 20:14 DEBUG  TaskList: ## Running create_uninstaller...
02-25 20:14 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-25 20:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-25 20:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-25 20:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-25 20:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-25 20:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
02-25 20:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-25 20:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-25 20:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-25 20:14 DEBUG  TaskList: ## Finished create_uninstaller
02-25 20:14 DEBUG  TaskList: ## Running copy_installation_files...
02-25 20:14 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-25 20:14 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\winboot -> C:\ubuntu\winboot
02-25 20:14 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl2.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
02-25 20:14 DEBUG  TaskList: ## Finished copy_installation_files
02-25 20:14 DEBUG  TaskList: ## Running use_cd...
02-25 20:14 DEBUG  TaskList: New task copy_file
02-25 20:14 DEBUG  TaskList: ### Running copy_file...
02-25 20:19 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
02-25 20:19 DEBUG  TaskList: # Cancelling tasklist
02-25 20:19 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
02-25 20:19 DEBUG  TaskList: New task check_iso
02-25 20:19 DEBUG  TaskList: ## Finished use_cd
02-25 20:19 DEBUG  TaskList: # Finished tasklist

How can I successfully install Ubuntu?

Thanks in advance,

Duncan :D

---

### Post by Mark Phelps on 2010-02-26
You would do better NOT trying to force an installation until you've tried it out first.  There could be hardware and/or driver issues.

Next time you boot using the CD, select the first option of trying it out without installing.  And ... be patient.  It could take several minutes before it finishes loading and presents you witha desktop.

Once into Ubuntu, check to see if all your hardware works.  Anything that does not work in LiveCD mode will range from trivial to impossible to fix after installation.

---

### Post by gordintoronto on 2010-02-26
You need to go into the BIOS settings on your computer, and tell it to boot from CD first, hard drive second.

---

