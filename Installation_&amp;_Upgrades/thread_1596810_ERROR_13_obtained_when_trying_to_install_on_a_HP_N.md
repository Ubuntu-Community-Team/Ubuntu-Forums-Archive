---
title: "ERROR 13 obtained when trying to install on a HP NX6110 machine"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by bijorium on 2010-10-14
After a long hiatus, I decided to download and install ubuntu 10.10. 

Everything seems fine until I get this response>>>

I could not make any sense out of it so I thought I would post it out here. Any help would be appreciated.

10-14 21:08 INFO   root: === wubi 10.10 rev197 ===
10-14 21:08 DEBUG  root: Logfile is c:\docume~1\ucheza\locals~1\temp\wubi-10.10-rev197.log
10-14 21:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
10-14 21:08 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\data
10-14 21:08 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\bin\7z.exe
10-14 21:08 DEBUG  CommonBackend: Fetching basic info...
10-14 21:08 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-14 21:08 DEBUG  CommonBackend: platform=win32
10-14 21:08 DEBUG  CommonBackend: osname=nt
10-14 21:08 DEBUG  CommonBackend: language=en_US
10-14 21:08 DEBUG  CommonBackend: encoding=cp1252
10-14 21:08 DEBUG  WindowsBackend: arch=i386
10-14 21:08 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\data\isolist.ini
10-14 21:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-14 21:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-14 21:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-14 21:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-14 21:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-14 21:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-14 21:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-14 21:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-14 21:08 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-14 21:08 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-14 21:08 DEBUG  WindowsBackend: Fetching host info...
10-14 21:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-14 21:08 DEBUG  WindowsBackend: windows version=xp
10-14 21:08 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-14 21:08 DEBUG  WindowsBackend: windows_sp=Service Pack 2
10-14 21:08 DEBUG  WindowsBackend: windows_build=2600
10-14 21:08 DEBUG  WindowsBackend: gmt=0
10-14 21:08 DEBUG  WindowsBackend: country=US
10-14 21:08 DEBUG  WindowsBackend: timezone=America/New_York
10-14 21:08 DEBUG  WindowsBackend: windows_username=Ucheza
10-14 21:08 DEBUG  WindowsBackend: user_full_name=Ucheza
10-14 21:08 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Ucheza
10-14 21:08 DEBUG  WindowsBackend: windows_language_code=1033
10-14 21:08 DEBUG  WindowsBackend: windows_language=English
10-14 21:08 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1.86GHz
10-14 21:08 DEBUG  WindowsBackend: bootloader=xp
10-14 21:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 44875.9140625 mb free ntfs)
10-14 21:08 DEBUG  WindowsBackend: drive=Drive(C: hd 44875.9140625 mb free ntfs)
10-14 21:08 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
10-14 21:08 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
10-14 21:08 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-14 21:08 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-14 21:08 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-14 21:08 DEBUG  WindowsBackend: keyboard_id=67699721
10-14 21:08 DEBUG  WindowsBackend: keyboard_layout=us
10-14 21:08 DEBUG  WindowsBackend: keyboard_variant=
10-14 21:08 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-14 21:08 DEBUG  CommonBackend: locale=en_US.UTF-8
10-14 21:08 DEBUG  WindowsBackend: total_memory_mb=503.359375
10-14 21:08 DEBUG  CommonBackend: Searching ISOs on USB devices
10-14 21:08 DEBUG  CommonBackend: Searching for local CDs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Ubuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Ubuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Ubuntu Netbook CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Kubuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Kubuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Kubuntu Netbook CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Xubuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Xubuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Mythbuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Mythbuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 21:08 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
10-14 21:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
10-14 21:08 DEBUG  Distro: wrong arch: i386 != amd64
10-14 21:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 21:08 INFO   Distro: Found a valid CD for Ubuntu: D:\
10-14 21:08 INFO   root: Running the CD menu...
10-14 21:08 DEBUG  WindowsFrontend: __init__...
10-14 21:08 DEBUG  WindowsFrontend: on_init...
10-14 21:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\translations, languages=['en_US', 'en']
10-14 21:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\translations, languages=['en_US', 'en']
10-14 21:08 INFO   root: CD menu finished
10-14 21:08 INFO   root: Already installed, running the uninstaller...
10-14 21:08 INFO   root: Running the uninstaller...
10-14 21:08 INFO   CommonBackend: This is the uninstaller running
10-14 21:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\translations, languages=['en_US', 'en']
10-14 21:08 INFO   root: Received settings
10-14 21:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\translations, languages=['en_US', 'en']
10-14 21:08 DEBUG  TaskList: # Running tasklist...
10-14 21:08 DEBUG  TaskList: ## Running Backup ISO...
10-14 21:08 DEBUG  TaskList: ## Finished Backup ISO
10-14 21:08 DEBUG  TaskList: ## Running Remove bootloader entry...
10-14 21:08 ERROR  WindowsBackend: Cannot find bcdedit
10-14 21:08 DEBUG  WindowsBackend: undo_bootini C:
10-14 21:08 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 44875.9140625 mb free ntfs)
10-14 21:08 DEBUG  TaskList: ## Finished Remove bootloader entry
10-14 21:08 DEBUG  TaskList: ## Running Remove target dir...
10-14 21:08 DEBUG  CommonBackend: Deleting C:\ubuntu
10-14 21:08 DEBUG  TaskList: ## Finished Remove target dir
10-14 21:08 DEBUG  TaskList: ## Running Remove registry key...
10-14 21:08 DEBUG  TaskList: ## Finished Remove registry key
10-14 21:08 DEBUG  TaskList: # Finished tasklist
10-14 21:08 INFO   root: Almost finished uninstalling
10-14 21:08 INFO   root: Finished uninstallation
10-14 21:08 DEBUG  CommonBackend: Fetching basic info...
10-14 21:08 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-14 21:08 DEBUG  CommonBackend: platform=win32
10-14 21:08 DEBUG  CommonBackend: osname=nt
10-14 21:08 DEBUG  WindowsBackend: arch=i386
10-14 21:08 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\data\isolist.ini
10-14 21:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-14 21:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-14 21:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-14 21:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-14 21:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-14 21:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-14 21:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-14 21:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-14 21:08 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-14 21:08 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-14 21:08 DEBUG  WindowsBackend: Fetching host info...
10-14 21:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-14 21:08 DEBUG  WindowsBackend: windows version=xp
10-14 21:08 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-14 21:08 DEBUG  WindowsBackend: windows_sp=Service Pack 2
10-14 21:08 DEBUG  WindowsBackend: windows_build=2600
10-14 21:08 DEBUG  WindowsBackend: gmt=0
10-14 21:08 DEBUG  WindowsBackend: country=US
10-14 21:08 DEBUG  WindowsBackend: timezone=America/New_York
10-14 21:08 DEBUG  WindowsBackend: windows_username=Ucheza
10-14 21:08 DEBUG  WindowsBackend: user_full_name=Ucheza
10-14 21:08 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Ucheza
10-14 21:08 DEBUG  WindowsBackend: windows_language_code=1033
10-14 21:08 DEBUG  WindowsBackend: windows_language=English
10-14 21:08 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1.86GHz
10-14 21:08 DEBUG  WindowsBackend: bootloader=xp
10-14 21:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 44878.4140625 mb free ntfs)
10-14 21:08 DEBUG  WindowsBackend: drive=Drive(C: hd 44878.4140625 mb free ntfs)
10-14 21:08 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
10-14 21:08 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
10-14 21:08 DEBUG  WindowsBackend: uninstaller_path=None
10-14 21:08 DEBUG  WindowsBackend: previous_target_dir=None
10-14 21:08 DEBUG  WindowsBackend: previous_distro_name=None
10-14 21:08 DEBUG  WindowsBackend: keyboard_id=67699721
10-14 21:08 DEBUG  WindowsBackend: keyboard_layout=us
10-14 21:08 DEBUG  WindowsBackend: keyboard_variant=
10-14 21:08 DEBUG  WindowsBackend: total_memory_mb=503.359375
10-14 21:08 DEBUG  CommonBackend: Searching ISOs on USB devices
10-14 21:08 DEBUG  CommonBackend: Searching for local CDs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Ubuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Ubuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Ubuntu Netbook CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Kubuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Kubuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Kubuntu Netbook CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Xubuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Xubuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Mythbuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp is a valid Mythbuntu CD
10-14 21:08 DEBUG  Distro:     does not contain C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\casper\filesystem.squashfs
10-14 21:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 21:08 DEBUG  Distro: wrong arch: i386 != amd64
10-14 21:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-14 21:08 INFO   Distro: Found a valid CD for Ubuntu: D:\
10-14 21:08 INFO   root: Running the installer...
10-14 21:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\translations, languages=['en_US', 'en']
10-14 21:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\translations, languages=['en_US', 'en']
10-14 21:09 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=olaiwola
10-14 21:09 INFO   root: Received settings
10-14 21:09 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\translations, languages=['en_US', 'en']
10-14 21:09 DEBUG  TaskList: # Running tasklist...
10-14 21:09 DEBUG  TaskList: ## Running select_target_dir...
10-14 21:09 INFO   WindowsBackend: Installing into C:\ubuntu
10-14 21:09 DEBUG  TaskList: ## Finished select_target_dir
10-14 21:09 DEBUG  TaskList: ## Running create_dir_structure...
10-14 21:09 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-14 21:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-14 21:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-14 21:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-14 21:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-14 21:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-14 21:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-14 21:09 DEBUG  TaskList: ## Finished create_dir_structure
10-14 21:09 DEBUG  TaskList: ## Running uncompress_target_dir...
10-14 21:09 DEBUG  TaskList: ## Finished uncompress_target_dir
10-14 21:09 DEBUG  TaskList: ## Running create_uninstaller...
10-14 21:09 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-14 21:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-14 21:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-14 21:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-14 21:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-14 21:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
10-14 21:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-14 21:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-14 21:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-14 21:09 DEBUG  TaskList: ## Finished create_uninstaller
10-14 21:09 DEBUG  TaskList: ## Running copy_installation_files...
10-14 21:09 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-14 21:09 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\winboot -> C:\ubuntu\winboot
10-14 21:09 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Ucheza\LOCALS~1\Temp\pyl25.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-14 21:09 DEBUG  TaskList: ## Finished copy_installation_files
10-14 21:09 DEBUG  TaskList: ## Running get_iso...
10-14 21:09 DEBUG  TaskList: New task copy_file
10-14 21:09 DEBUG  TaskList: ### Running copy_file...
10-14 21:09 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
10-14 21:09 DEBUG  TaskList: # Cancelling tasklist
10-14 21:09 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
10-14 21:09 DEBUG  TaskList: New task check_iso
10-14 21:09 DEBUG  CommonBackend: Searching for local ISO
10-14 21:09 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-14 21:09 DEBUG  TaskList: New task get_metalink
10-14 21:09 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-14 21:09 DEBUG  TaskList: # Cancelling tasklist
10-14 21:09 DEBUG  TaskList: # Finished tasklist

---

