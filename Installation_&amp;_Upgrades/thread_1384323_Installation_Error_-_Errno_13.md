---
title: "Installation Error - Errno 13"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by andycastille on 2010-01-18
When I tried to install Ubuntu inside Windows on Windows 7 Pro, which was in the worst condition, I got an error message. It told me to go to log file: "C:\Users\****\AppData\Local\Temp\wubi-9.10ubuntu1-rev160.log", so I opened it. It said:
```
01-18 08:13 INFO   root: === wubi 9.10ubuntu1 rev160 ===
01-18 08:13 DEBUG  root: Logfile is c:\users\andy\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
01-18 08:13 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
01-18 08:13 DEBUG  CommonBackend: data_dir=C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\data
01-18 08:13 DEBUG  WindowsBackend: 7z=C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\bin\7z.exe
01-18 08:13 DEBUG  CommonBackend: Fetching basic info...
01-18 08:13 DEBUG  CommonBackend: original_exe=D:\wubi.exe
01-18 08:13 DEBUG  CommonBackend: platform=win32
01-18 08:13 DEBUG  CommonBackend: osname=nt
01-18 08:13 DEBUG  CommonBackend: language=en_US
01-18 08:13 DEBUG  CommonBackend: encoding=cp1252
01-18 08:13 DEBUG  WindowsBackend: arch=amd64
01-18 08:13 DEBUG  CommonBackend: Parsing isolist=C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\data\isolist.ini
01-18 08:13 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-18 08:13 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-18 08:13 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-18 08:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-18 08:13 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-18 08:13 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-18 08:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-18 08:13 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-18 08:13 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-18 08:13 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-18 08:13 DEBUG  WindowsBackend: Fetching host info...
01-18 08:13 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-18 08:13 DEBUG  WindowsBackend: windows version=vista
01-18 08:13 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
01-18 08:13 DEBUG  WindowsBackend: windows_sp=None
01-18 08:13 DEBUG  WindowsBackend: windows_build=7600
01-18 08:13 DEBUG  WindowsBackend: gmt=-6
01-18 08:13 DEBUG  WindowsBackend: country=US
01-18 08:13 DEBUG  WindowsBackend: timezone=America/Chicago
01-18 08:13 DEBUG  WindowsBackend: windows_username=Andy
01-18 08:13 DEBUG  WindowsBackend: user_full_name=Andy
01-18 08:13 DEBUG  WindowsBackend: user_directory=C:\Users\Andy
01-18 08:13 DEBUG  WindowsBackend: windows_language_code=1033
01-18 08:13 DEBUG  WindowsBackend: windows_language=English
01-18 08:13 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
01-18 08:13 DEBUG  WindowsBackend: bootloader=vista
01-18 08:13 DEBUG  WindowsBackend: system_drive=Drive(C: hd 202858.316406 mb free ntfs)
01-18 08:13 DEBUG  WindowsBackend: drive=Drive(B: removable 0.0 mb free )
01-18 08:13 DEBUG  WindowsBackend: drive=Drive(C: hd 202858.316406 mb free ntfs)
01-18 08:13 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
01-18 08:13 DEBUG  WindowsBackend: uninstaller_path=None
01-18 08:13 DEBUG  WindowsBackend: previous_target_dir=None
01-18 08:13 DEBUG  WindowsBackend: previous_distro_name=None
01-18 08:13 DEBUG  WindowsBackend: keyboard_id=67699721
01-18 08:13 DEBUG  WindowsBackend: keyboard_layout=us
01-18 08:13 DEBUG  WindowsBackend: keyboard_variant=
01-18 08:13 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-18 08:13 DEBUG  CommonBackend: locale=en_US.UTF-8
01-18 08:13 DEBUG  WindowsBackend: total_memory_mb=2939.01953125
01-18 08:13 DEBUG  CommonBackend: Searching ISOs on USB devices
01-18 08:13 DEBUG  CommonBackend: Searching for local CDs
01-18 08:13 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
01-18 08:13 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
01-18 08:13 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
01-18 08:13 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
01-18 08:13 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
01-18 08:13 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
01-18 08:13 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
01-18 08:13 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
01-18 08:13 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
01-18 08:13 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
01-18 08:13 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp is a valid Ubuntu CD
01-18 08:13 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp is a valid Ubuntu CD
01-18 08:13 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp is a valid Ubuntu Netbook Remix CD
01-18 08:13 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp is a valid Kubuntu CD
01-18 08:13 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp is a valid Kubuntu CD
01-18 08:13 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp is a valid Kubuntu Netbook CD
01-18 08:13 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp is a valid Xubuntu CD
01-18 08:13 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp is a valid Xubuntu CD
01-18 08:13 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp is a valid Mythbuntu CD
01-18 08:13 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp is a valid Mythbuntu CD
01-18 08:13 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\casper\filesystem.squashfs
01-18 08:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-18 08:13 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
01-18 08:13 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
01-18 08:13 INFO   Distro: Found a valid CD for Ubuntu: D:\
01-18 08:13 INFO   root: Running the CD menu...
01-18 08:13 DEBUG  WindowsFrontend: __init__...
01-18 08:13 DEBUG  WindowsFrontend: on_init...
01-18 08:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\translations, languages=['en_US', 'en']
01-18 08:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\translations, languages=['en_US', 'en']
01-18 08:13 INFO   root: CD menu finished
01-18 08:13 INFO   root: Running the installer...
01-18 08:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\translations, languages=['en_US', 'en']
01-18 08:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\translations, languages=['en_US', 'en']
01-18 08:14 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=andy
01-18 08:14 INFO   root: Received settings
01-18 08:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\translations, languages=['en_US', 'en']
01-18 08:14 DEBUG  TaskList: # Running tasklist...
01-18 08:14 DEBUG  TaskList: ## Running select_target_dir...
01-18 08:14 INFO   WindowsBackend: Installing into C:\ubuntu
01-18 08:14 DEBUG  TaskList: ## Finished select_target_dir
01-18 08:14 DEBUG  TaskList: ## Running create_dir_structure...
01-18 08:14 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-18 08:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-18 08:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-18 08:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-18 08:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-18 08:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-18 08:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-18 08:14 DEBUG  TaskList: ## Finished create_dir_structure
01-18 08:14 DEBUG  TaskList: ## Running uncompress_target_dir...
01-18 08:14 DEBUG  TaskList: ## Finished uncompress_target_dir
01-18 08:14 DEBUG  TaskList: ## Running create_uninstaller...
01-18 08:14 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-18 08:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-18 08:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-18 08:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-18 08:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-18 08:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
01-18 08:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-18 08:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
01-18 08:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
01-18 08:14 DEBUG  TaskList: ## Finished create_uninstaller
01-18 08:14 DEBUG  TaskList: ## Running copy_installation_files...
01-18 08:14 DEBUG  WindowsBackend: Copying C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-18 08:14 DEBUG  WindowsBackend: Copying C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\winboot -> C:\ubuntu\winboot
01-18 08:14 DEBUG  WindowsBackend: Copying C:\Users\Andy\AppData\Local\Temp\pyl2206.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
01-18 08:14 DEBUG  TaskList: ## Finished copy_installation_files
01-18 08:14 DEBUG  TaskList: ## Running get_iso...
01-18 08:14 DEBUG  TaskList: New task copy_file
01-18 08:14 DEBUG  TaskList: ### Running copy_file...
01-18 08:15 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
01-18 08:15 DEBUG  TaskList: # Cancelling tasklist
01-18 08:15 DEBUG  TaskList: New task check_iso
01-18 08:15 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
01-18 08:15 DEBUG  CommonBackend: Searching for local ISO
01-18 08:15 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-18 08:15 DEBUG  TaskList: New task get_metalink
01-18 08:15 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
01-18 08:15 DEBUG  TaskList: # Cancelling tasklist
01-18 08:15 DEBUG  TaskList: # Finished tasklist
01-18 08:17 INFO   root: === wubi 9.10ubuntu1 rev160 ===
01-18 08:17 DEBUG  root: Logfile is c:\users\andy\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
01-18 08:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
01-18 08:17 DEBUG  CommonBackend: data_dir=C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\data
01-18 08:17 DEBUG  WindowsBackend: 7z=C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\bin\7z.exe
01-18 08:17 DEBUG  CommonBackend: Fetching basic info...
01-18 08:17 DEBUG  CommonBackend: original_exe=D:\wubi.exe
01-18 08:17 DEBUG  CommonBackend: platform=win32
01-18 08:17 DEBUG  CommonBackend: osname=nt
01-18 08:17 DEBUG  CommonBackend: language=en_US
01-18 08:17 DEBUG  CommonBackend: encoding=cp1252
01-18 08:17 DEBUG  WindowsBackend: arch=amd64
01-18 08:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\data\isolist.ini
01-18 08:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-18 08:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-18 08:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-18 08:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-18 08:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-18 08:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-18 08:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-18 08:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-18 08:17 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-18 08:17 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-18 08:17 DEBUG  WindowsBackend: Fetching host info...
01-18 08:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-18 08:17 DEBUG  WindowsBackend: windows version=vista
01-18 08:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
01-18 08:17 DEBUG  WindowsBackend: windows_sp=None
01-18 08:17 DEBUG  WindowsBackend: windows_build=7600
01-18 08:17 DEBUG  WindowsBackend: gmt=-6
01-18 08:17 DEBUG  WindowsBackend: country=US
01-18 08:17 DEBUG  WindowsBackend: timezone=America/Chicago
01-18 08:17 DEBUG  WindowsBackend: windows_username=Andy
01-18 08:17 DEBUG  WindowsBackend: user_full_name=Andy
01-18 08:17 DEBUG  WindowsBackend: user_directory=C:\Users\Andy
01-18 08:17 DEBUG  WindowsBackend: windows_language_code=1033
01-18 08:17 DEBUG  WindowsBackend: windows_language=English
01-18 08:17 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
01-18 08:17 DEBUG  WindowsBackend: bootloader=vista
01-18 08:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 202855.101563 mb free ntfs)
01-18 08:17 DEBUG  WindowsBackend: drive=Drive(B: removable 0.0 mb free )
01-18 08:17 DEBUG  WindowsBackend: drive=Drive(C: hd 202855.097656 mb free ntfs)
01-18 08:17 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
01-18 08:17 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-18 08:17 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-18 08:17 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-18 08:17 DEBUG  WindowsBackend: keyboard_id=67699721
01-18 08:17 DEBUG  WindowsBackend: keyboard_layout=us
01-18 08:17 DEBUG  WindowsBackend: keyboard_variant=
01-18 08:17 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-18 08:17 DEBUG  CommonBackend: locale=en_US.UTF-8
01-18 08:17 DEBUG  WindowsBackend: total_memory_mb=2939.01953125
01-18 08:17 DEBUG  CommonBackend: Searching ISOs on USB devices
01-18 08:17 DEBUG  CommonBackend: Searching for local CDs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Ubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Ubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Ubuntu Netbook Remix CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Kubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Kubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Kubuntu Netbook CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Xubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Xubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Mythbuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Mythbuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-18 08:17 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
01-18 08:17 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
01-18 08:17 INFO   Distro: Found a valid CD for Ubuntu: D:\
01-18 08:17 INFO   root: Running the CD menu...
01-18 08:17 DEBUG  WindowsFrontend: __init__...
01-18 08:17 DEBUG  WindowsFrontend: on_init...
01-18 08:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\translations, languages=['en_US', 'en']
01-18 08:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\translations, languages=['en_US', 'en']
01-18 08:17 INFO   root: CD menu finished
01-18 08:17 INFO   root: Already installed, running the uninstaller...
01-18 08:17 INFO   root: Running the uninstaller...
01-18 08:17 INFO   CommonBackend: This is the uninstaller running
01-18 08:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\translations, languages=['en_US', 'en']
01-18 08:17 INFO   root: Received settings
01-18 08:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\translations, languages=['en_US', 'en']
01-18 08:17 DEBUG  TaskList: # Running tasklist...
01-18 08:17 DEBUG  TaskList: ## Running Backup ISO...
01-18 08:17 DEBUG  TaskList: ## Finished Backup ISO
01-18 08:17 DEBUG  TaskList: ## Running Remove bootloader entry...
01-18 08:17 DEBUG  WindowsBackend: Could not find bcd id
01-18 08:17 DEBUG  WindowsBackend: undo_bootini B:
01-18 08:17 DEBUG  WindowsBackend: undo_configsys Drive(B: removable 0.0 mb free )
01-18 08:17 DEBUG  WindowsBackend: undo_bootini C:
01-18 08:17 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 202855.097656 mb free ntfs)
01-18 08:17 DEBUG  TaskList: ## Finished Remove bootloader entry
01-18 08:17 DEBUG  TaskList: ## Running Remove target dir...
01-18 08:17 DEBUG  CommonBackend: Deleting C:\ubuntu
01-18 08:17 DEBUG  TaskList: ## Finished Remove target dir
01-18 08:17 DEBUG  TaskList: ## Running Remove registry key...
01-18 08:17 DEBUG  TaskList: ## Finished Remove registry key
01-18 08:17 DEBUG  TaskList: # Finished tasklist
01-18 08:17 INFO   root: Almost finished uninstalling
01-18 08:17 INFO   root: Finished uninstallation
01-18 08:17 DEBUG  CommonBackend: Fetching basic info...
01-18 08:17 DEBUG  CommonBackend: original_exe=D:\wubi.exe
01-18 08:17 DEBUG  CommonBackend: platform=win32
01-18 08:17 DEBUG  CommonBackend: osname=nt
01-18 08:17 DEBUG  WindowsBackend: arch=amd64
01-18 08:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\data\isolist.ini
01-18 08:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-18 08:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-18 08:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-18 08:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-18 08:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-18 08:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-18 08:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-18 08:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-18 08:17 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-18 08:17 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-18 08:17 DEBUG  WindowsBackend: Fetching host info...
01-18 08:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-18 08:17 DEBUG  WindowsBackend: windows version=vista
01-18 08:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
01-18 08:17 DEBUG  WindowsBackend: windows_sp=None
01-18 08:17 DEBUG  WindowsBackend: windows_build=7600
01-18 08:17 DEBUG  WindowsBackend: gmt=-6
01-18 08:17 DEBUG  WindowsBackend: country=US
01-18 08:17 DEBUG  WindowsBackend: timezone=America/Chicago
01-18 08:17 DEBUG  WindowsBackend: windows_username=Andy
01-18 08:17 DEBUG  WindowsBackend: user_full_name=Andy
01-18 08:17 DEBUG  WindowsBackend: user_directory=C:\Users\Andy
01-18 08:17 DEBUG  WindowsBackend: windows_language_code=1033
01-18 08:17 DEBUG  WindowsBackend: windows_language=English
01-18 08:17 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
01-18 08:17 DEBUG  WindowsBackend: bootloader=vista
01-18 08:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 202856.621094 mb free ntfs)
01-18 08:17 DEBUG  WindowsBackend: drive=Drive(B: removable 0.0 mb free )
01-18 08:17 DEBUG  WindowsBackend: drive=Drive(C: hd 202856.621094 mb free ntfs)
01-18 08:17 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
01-18 08:17 DEBUG  WindowsBackend: uninstaller_path=None
01-18 08:17 DEBUG  WindowsBackend: previous_target_dir=None
01-18 08:17 DEBUG  WindowsBackend: previous_distro_name=None
01-18 08:17 DEBUG  WindowsBackend: keyboard_id=67699721
01-18 08:17 DEBUG  WindowsBackend: keyboard_layout=us
01-18 08:17 DEBUG  WindowsBackend: keyboard_variant=
01-18 08:17 DEBUG  WindowsBackend: total_memory_mb=2939.01953125
01-18 08:17 DEBUG  CommonBackend: Searching ISOs on USB devices
01-18 08:17 DEBUG  CommonBackend: Searching for local CDs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
01-18 08:17 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Ubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Ubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Ubuntu Netbook Remix CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Kubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Kubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Kubuntu Netbook CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Xubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Xubuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Mythbuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp is a valid Mythbuntu CD
01-18 08:17 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\casper\filesystem.squashfs
01-18 08:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-18 08:17 INFO   Distro: Found a valid CD for Ubuntu: D:\
01-18 08:17 INFO   root: Running the installer...
01-18 08:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\translations, languages=['en_US', 'en']
01-18 08:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\translations, languages=['en_US', 'en']
01-18 08:17 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=andy
01-18 08:17 INFO   root: Received settings
01-18 08:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\translations, languages=['en_US', 'en']
01-18 08:17 DEBUG  TaskList: # Running tasklist...
01-18 08:17 DEBUG  TaskList: ## Running select_target_dir...
01-18 08:17 INFO   WindowsBackend: Installing into C:\ubuntu
01-18 08:17 DEBUG  TaskList: ## Finished select_target_dir
01-18 08:17 DEBUG  TaskList: ## Running create_dir_structure...
01-18 08:17 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-18 08:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-18 08:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-18 08:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-18 08:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-18 08:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-18 08:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-18 08:17 DEBUG  TaskList: ## Finished create_dir_structure
01-18 08:17 DEBUG  TaskList: ## Running uncompress_target_dir...
01-18 08:17 DEBUG  TaskList: ## Finished uncompress_target_dir
01-18 08:17 DEBUG  TaskList: ## Running create_uninstaller...
01-18 08:17 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-18 08:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-18 08:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-18 08:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-18 08:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-18 08:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
01-18 08:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-18 08:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
01-18 08:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
01-18 08:17 DEBUG  TaskList: ## Finished create_uninstaller
01-18 08:17 DEBUG  TaskList: ## Running copy_installation_files...
01-18 08:17 DEBUG  WindowsBackend: Copying C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-18 08:17 DEBUG  WindowsBackend: Copying C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\winboot -> C:\ubuntu\winboot
01-18 08:17 DEBUG  WindowsBackend: Copying C:\Users\Andy\AppData\Local\Temp\pyl53C0.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
01-18 08:17 DEBUG  TaskList: ## Finished copy_installation_files
01-18 08:17 DEBUG  TaskList: ## Running get_iso...
01-18 08:17 DEBUG  TaskList: New task copy_file
01-18 08:17 DEBUG  TaskList: ### Running copy_file...
01-18 08:17 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
01-18 08:17 DEBUG  TaskList: # Cancelling tasklist
01-18 08:17 DEBUG  TaskList: New task check_iso
01-18 08:17 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
01-18 08:17 DEBUG  CommonBackend: Searching for local ISO
01-18 08:17 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-18 08:17 DEBUG  TaskList: New task get_metalink
01-18 08:17 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
01-18 08:17 DEBUG  TaskList: # Cancelling tasklist
01-18 08:17 DEBUG  TaskList: # Finished tasklist
01-18 08:20 INFO   root: === wubi 9.10ubuntu1 rev160 ===
01-18 08:20 DEBUG  root: Logfile is c:\users\andy\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
01-18 08:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
01-18 08:20 DEBUG  CommonBackend: data_dir=C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\data
01-18 08:20 DEBUG  WindowsBackend: 7z=C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\bin\7z.exe
01-18 08:20 DEBUG  CommonBackend: Fetching basic info...
01-18 08:20 DEBUG  CommonBackend: original_exe=D:\wubi.exe
01-18 08:20 DEBUG  CommonBackend: platform=win32
01-18 08:20 DEBUG  CommonBackend: osname=nt
01-18 08:20 DEBUG  CommonBackend: language=en_US
01-18 08:20 DEBUG  CommonBackend: encoding=cp1252
01-18 08:20 DEBUG  WindowsBackend: arch=amd64
01-18 08:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\data\isolist.ini
01-18 08:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-18 08:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-18 08:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-18 08:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-18 08:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-18 08:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-18 08:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-18 08:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-18 08:20 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-18 08:20 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-18 08:20 DEBUG  WindowsBackend: Fetching host info...
01-18 08:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-18 08:20 DEBUG  WindowsBackend: windows version=vista
01-18 08:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
01-18 08:20 DEBUG  WindowsBackend: windows_sp=None
01-18 08:20 DEBUG  WindowsBackend: windows_build=7600
01-18 08:20 DEBUG  WindowsBackend: gmt=-6
01-18 08:20 DEBUG  WindowsBackend: country=US
01-18 08:20 DEBUG  WindowsBackend: timezone=America/Chicago
01-18 08:20 DEBUG  WindowsBackend: windows_username=Andy
01-18 08:20 DEBUG  WindowsBackend: user_full_name=Andy
01-18 08:20 DEBUG  WindowsBackend: user_directory=C:\Users\Andy
01-18 08:20 DEBUG  WindowsBackend: windows_language_code=1033
01-18 08:20 DEBUG  WindowsBackend: windows_language=English
01-18 08:20 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
01-18 08:20 DEBUG  WindowsBackend: bootloader=vista
01-18 08:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 202854.976563 mb free ntfs)
01-18 08:20 DEBUG  WindowsBackend: drive=Drive(B: removable 0.0 mb free )
01-18 08:20 DEBUG  WindowsBackend: drive=Drive(C: hd 202854.976563 mb free ntfs)
01-18 08:20 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
01-18 08:20 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-18 08:20 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-18 08:20 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-18 08:20 DEBUG  WindowsBackend: keyboard_id=67699721
01-18 08:20 DEBUG  WindowsBackend: keyboard_layout=us
01-18 08:20 DEBUG  WindowsBackend: keyboard_variant=
01-18 08:20 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-18 08:20 DEBUG  CommonBackend: locale=en_US.UTF-8
01-18 08:20 DEBUG  WindowsBackend: total_memory_mb=2939.01953125
01-18 08:20 DEBUG  CommonBackend: Searching ISOs on USB devices
01-18 08:20 DEBUG  CommonBackend: Searching for local CDs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Ubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Ubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Ubuntu Netbook Remix CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Kubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Kubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Kubuntu Netbook CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Xubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Xubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Mythbuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Mythbuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-18 08:20 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
01-18 08:20 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
01-18 08:20 INFO   Distro: Found a valid CD for Ubuntu: D:\
01-18 08:20 INFO   root: Running the CD menu...
01-18 08:20 DEBUG  WindowsFrontend: __init__...
01-18 08:20 DEBUG  WindowsFrontend: on_init...
01-18 08:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\translations, languages=['en_US', 'en']
01-18 08:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\translations, languages=['en_US', 'en']
01-18 08:20 INFO   root: CD menu finished
01-18 08:20 INFO   root: Already installed, running the uninstaller...
01-18 08:20 INFO   root: Running the uninstaller...
01-18 08:20 INFO   CommonBackend: This is the uninstaller running
01-18 08:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\translations, languages=['en_US', 'en']
01-18 08:20 INFO   root: Received settings
01-18 08:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\translations, languages=['en_US', 'en']
01-18 08:20 DEBUG  TaskList: # Running tasklist...
01-18 08:20 DEBUG  TaskList: ## Running Backup ISO...
01-18 08:20 DEBUG  TaskList: ## Finished Backup ISO
01-18 08:20 DEBUG  TaskList: ## Running Remove bootloader entry...
01-18 08:20 DEBUG  WindowsBackend: Could not find bcd id
01-18 08:20 DEBUG  WindowsBackend: undo_bootini B:
01-18 08:20 DEBUG  WindowsBackend: undo_configsys Drive(B: removable 0.0 mb free )
01-18 08:20 DEBUG  WindowsBackend: undo_bootini C:
01-18 08:20 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 202854.976563 mb free ntfs)
01-18 08:20 DEBUG  TaskList: ## Finished Remove bootloader entry
01-18 08:20 DEBUG  TaskList: ## Running Remove target dir...
01-18 08:20 DEBUG  CommonBackend: Deleting C:\ubuntu
01-18 08:20 DEBUG  TaskList: ## Finished Remove target dir
01-18 08:20 DEBUG  TaskList: ## Running Remove registry key...
01-18 08:20 DEBUG  TaskList: ## Finished Remove registry key
01-18 08:20 DEBUG  TaskList: # Finished tasklist
01-18 08:20 INFO   root: Almost finished uninstalling
01-18 08:20 INFO   root: Finished uninstallation
01-18 08:20 DEBUG  CommonBackend: Fetching basic info...
01-18 08:20 DEBUG  CommonBackend: original_exe=D:\wubi.exe
01-18 08:20 DEBUG  CommonBackend: platform=win32
01-18 08:20 DEBUG  CommonBackend: osname=nt
01-18 08:20 DEBUG  WindowsBackend: arch=amd64
01-18 08:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\data\isolist.ini
01-18 08:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-18 08:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-18 08:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-18 08:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-18 08:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-18 08:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-18 08:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-18 08:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-18 08:20 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-18 08:20 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-18 08:20 DEBUG  WindowsBackend: Fetching host info...
01-18 08:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-18 08:20 DEBUG  WindowsBackend: windows version=vista
01-18 08:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
01-18 08:20 DEBUG  WindowsBackend: windows_sp=None
01-18 08:20 DEBUG  WindowsBackend: windows_build=7600
01-18 08:20 DEBUG  WindowsBackend: gmt=-6
01-18 08:20 DEBUG  WindowsBackend: country=US
01-18 08:20 DEBUG  WindowsBackend: timezone=America/Chicago
01-18 08:20 DEBUG  WindowsBackend: windows_username=Andy
01-18 08:20 DEBUG  WindowsBackend: user_full_name=Andy
01-18 08:20 DEBUG  WindowsBackend: user_directory=C:\Users\Andy
01-18 08:20 DEBUG  WindowsBackend: windows_language_code=1033
01-18 08:20 DEBUG  WindowsBackend: windows_language=English
01-18 08:20 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
01-18 08:20 DEBUG  WindowsBackend: bootloader=vista
01-18 08:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 202856.496094 mb free ntfs)
01-18 08:20 DEBUG  WindowsBackend: drive=Drive(B: removable 0.0 mb free )
01-18 08:20 DEBUG  WindowsBackend: drive=Drive(C: hd 202856.496094 mb free ntfs)
01-18 08:20 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
01-18 08:20 DEBUG  WindowsBackend: uninstaller_path=None
01-18 08:20 DEBUG  WindowsBackend: previous_target_dir=None
01-18 08:20 DEBUG  WindowsBackend: previous_distro_name=None
01-18 08:20 DEBUG  WindowsBackend: keyboard_id=67699721
01-18 08:20 DEBUG  WindowsBackend: keyboard_layout=us
01-18 08:20 DEBUG  WindowsBackend: keyboard_variant=
01-18 08:20 DEBUG  WindowsBackend: total_memory_mb=2939.01953125
01-18 08:20 DEBUG  CommonBackend: Searching ISOs on USB devices
01-18 08:20 DEBUG  CommonBackend: Searching for local CDs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
01-18 08:20 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Ubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Ubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Ubuntu Netbook Remix CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Kubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Kubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Kubuntu Netbook CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Xubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Xubuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Mythbuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylE767.tmp is a valid Mythbuntu CD
01-18 08:20 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\casper\filesystem.squashfs
01-18 08:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-18 08:20 INFO   Distro: Found a valid CD for Ubuntu: D:\
01-18 08:20 INFO   root: Running the installer...
01-18 08:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\translations, languages=['en_US', 'en']
01-18 08:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\translations, languages=['en_US', 'en']
01-18 08:22 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=andy
01-18 08:22 INFO   root: Received settings
01-18 08:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\translations, languages=['en_US', 'en']
01-18 08:22 DEBUG  TaskList: # Running tasklist...
01-18 08:22 DEBUG  TaskList: ## Running select_target_dir...
01-18 08:22 INFO   WindowsBackend: Installing into C:\ubuntu
01-18 08:22 DEBUG  TaskList: ## Finished select_target_dir
01-18 08:22 DEBUG  TaskList: ## Running create_dir_structure...
01-18 08:22 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-18 08:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-18 08:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-18 08:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-18 08:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-18 08:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-18 08:22 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-18 08:22 DEBUG  TaskList: ## Finished create_dir_structure
01-18 08:22 DEBUG  TaskList: ## Running uncompress_target_dir...
01-18 08:22 DEBUG  TaskList: ## Finished uncompress_target_dir
01-18 08:22 DEBUG  TaskList: ## Running create_uninstaller...
01-18 08:22 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-18 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-18 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-18 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-18 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-18 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
01-18 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-18 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
01-18 08:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
01-18 08:22 DEBUG  TaskList: ## Finished create_uninstaller
01-18 08:22 DEBUG  TaskList: ## Running copy_installation_files...
01-18 08:22 DEBUG  WindowsBackend: Copying C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-18 08:22 DEBUG  WindowsBackend: Copying C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\winboot -> C:\ubuntu\winboot
01-18 08:22 DEBUG  WindowsBackend: Copying C:\Users\Andy\AppData\Local\Temp\pylE767.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
01-18 08:22 DEBUG  TaskList: ## Finished copy_installation_files
01-18 08:22 DEBUG  TaskList: ## Running get_iso...
01-18 08:22 DEBUG  TaskList: New task copy_file
01-18 08:22 DEBUG  TaskList: ### Running copy_file...
01-18 08:22 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
01-18 08:22 DEBUG  TaskList: # Cancelling tasklist
01-18 08:22 DEBUG  TaskList: New task check_iso
01-18 08:22 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
01-18 08:22 DEBUG  CommonBackend: Searching for local ISO
01-18 08:22 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-18 08:22 DEBUG  TaskList: New task get_metalink
01-18 08:22 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
01-18 08:22 DEBUG  TaskList: # Cancelling tasklist
01-18 08:22 DEBUG  TaskList: # Finished tasklist
01-18 08:27 INFO   root: === wubi 9.10ubuntu1 rev160 ===
01-18 08:27 DEBUG  root: Logfile is c:\users\andy\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
01-18 08:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
01-18 08:27 DEBUG  CommonBackend: data_dir=C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\data
01-18 08:27 DEBUG  WindowsBackend: 7z=C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\bin\7z.exe
01-18 08:27 DEBUG  CommonBackend: Fetching basic info...
01-18 08:27 DEBUG  CommonBackend: original_exe=D:\wubi.exe
01-18 08:27 DEBUG  CommonBackend: platform=win32
01-18 08:27 DEBUG  CommonBackend: osname=nt
01-18 08:27 DEBUG  CommonBackend: language=en_US
01-18 08:27 DEBUG  CommonBackend: encoding=cp1252
01-18 08:27 DEBUG  WindowsBackend: arch=amd64
01-18 08:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\data\isolist.ini
01-18 08:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-18 08:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-18 08:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-18 08:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-18 08:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-18 08:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-18 08:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-18 08:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-18 08:27 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-18 08:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-18 08:27 DEBUG  WindowsBackend: Fetching host info...
01-18 08:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-18 08:27 DEBUG  WindowsBackend: windows version=vista
01-18 08:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
01-18 08:27 DEBUG  WindowsBackend: windows_sp=None
01-18 08:27 DEBUG  WindowsBackend: windows_build=7600
01-18 08:27 DEBUG  WindowsBackend: gmt=-6
01-18 08:27 DEBUG  WindowsBackend: country=US
01-18 08:27 DEBUG  WindowsBackend: timezone=America/Chicago
01-18 08:27 DEBUG  WindowsBackend: windows_username=Andy
01-18 08:27 DEBUG  WindowsBackend: user_full_name=Andy
01-18 08:27 DEBUG  WindowsBackend: user_directory=C:\Users\Andy
01-18 08:27 DEBUG  WindowsBackend: windows_language_code=1033
01-18 08:27 DEBUG  WindowsBackend: windows_language=English
01-18 08:27 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
01-18 08:27 DEBUG  WindowsBackend: bootloader=vista
01-18 08:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 202851.695313 mb free ntfs)
01-18 08:27 DEBUG  WindowsBackend: drive=Drive(B: removable 0.0 mb free )
01-18 08:27 DEBUG  WindowsBackend: drive=Drive(C: hd 202851.695313 mb free ntfs)
01-18 08:27 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
01-18 08:27 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-18 08:27 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-18 08:27 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-18 08:27 DEBUG  WindowsBackend: keyboard_id=67699721
01-18 08:27 DEBUG  WindowsBackend: keyboard_layout=us
01-18 08:27 DEBUG  WindowsBackend: keyboard_variant=
01-18 08:27 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-18 08:27 DEBUG  CommonBackend: locale=en_US.UTF-8
01-18 08:27 DEBUG  WindowsBackend: total_memory_mb=2939.01953125
01-18 08:27 DEBUG  CommonBackend: Searching ISOs on USB devices
01-18 08:27 DEBUG  CommonBackend: Searching for local CDs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Ubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Ubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Ubuntu Netbook Remix CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Kubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Kubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Kubuntu Netbook CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Xubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Xubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Mythbuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Mythbuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-18 08:27 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
01-18 08:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
01-18 08:27 INFO   Distro: Found a valid CD for Ubuntu: D:\
01-18 08:27 INFO   root: Running the CD menu...
01-18 08:27 DEBUG  WindowsFrontend: __init__...
01-18 08:27 DEBUG  WindowsFrontend: on_init...
01-18 08:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\translations, languages=['en_US', 'en']
01-18 08:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\translations, languages=['en_US', 'en']
01-18 08:27 INFO   root: CD menu finished
01-18 08:27 INFO   root: Already installed, running the uninstaller...
01-18 08:27 INFO   root: Running the uninstaller...
01-18 08:27 INFO   CommonBackend: This is the uninstaller running
01-18 08:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\translations, languages=['en_US', 'en']
01-18 08:27 INFO   root: Received settings
01-18 08:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\translations, languages=['en_US', 'en']
01-18 08:27 DEBUG  TaskList: # Running tasklist...
01-18 08:27 DEBUG  TaskList: ## Running Backup ISO...
01-18 08:27 DEBUG  TaskList: ## Finished Backup ISO
01-18 08:27 DEBUG  TaskList: ## Running Remove bootloader entry...
01-18 08:27 DEBUG  WindowsBackend: Could not find bcd id
01-18 08:27 DEBUG  WindowsBackend: undo_bootini B:
01-18 08:27 DEBUG  WindowsBackend: undo_configsys Drive(B: removable 0.0 mb free )
01-18 08:27 DEBUG  WindowsBackend: undo_bootini C:
01-18 08:27 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 202851.695313 mb free ntfs)
01-18 08:27 DEBUG  TaskList: ## Finished Remove bootloader entry
01-18 08:27 DEBUG  TaskList: ## Running Remove target dir...
01-18 08:27 DEBUG  CommonBackend: Deleting C:\ubuntu
01-18 08:27 DEBUG  TaskList: ## Finished Remove target dir
01-18 08:27 DEBUG  TaskList: ## Running Remove registry key...
01-18 08:27 DEBUG  TaskList: ## Finished Remove registry key
01-18 08:27 DEBUG  TaskList: # Finished tasklist
01-18 08:27 INFO   root: Almost finished uninstalling
01-18 08:27 INFO   root: Finished uninstallation
01-18 08:27 DEBUG  CommonBackend: Fetching basic info...
01-18 08:27 DEBUG  CommonBackend: original_exe=D:\wubi.exe
01-18 08:27 DEBUG  CommonBackend: platform=win32
01-18 08:27 DEBUG  CommonBackend: osname=nt
01-18 08:27 DEBUG  WindowsBackend: arch=amd64
01-18 08:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\data\isolist.ini
01-18 08:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-18 08:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-18 08:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-18 08:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-18 08:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-18 08:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-18 08:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-18 08:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-18 08:27 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-18 08:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
01-18 08:27 DEBUG  WindowsBackend: Fetching host info...
01-18 08:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-18 08:27 DEBUG  WindowsBackend: windows version=vista
01-18 08:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
01-18 08:27 DEBUG  WindowsBackend: windows_sp=None
01-18 08:27 DEBUG  WindowsBackend: windows_build=7600
01-18 08:27 DEBUG  WindowsBackend: gmt=-6
01-18 08:27 DEBUG  WindowsBackend: country=US
01-18 08:27 DEBUG  WindowsBackend: timezone=America/Chicago
01-18 08:27 DEBUG  WindowsBackend: windows_username=Andy
01-18 08:27 DEBUG  WindowsBackend: user_full_name=Andy
01-18 08:27 DEBUG  WindowsBackend: user_directory=C:\Users\Andy
01-18 08:27 DEBUG  WindowsBackend: windows_language_code=1033
01-18 08:27 DEBUG  WindowsBackend: windows_language=English
01-18 08:27 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4300  @ 2.10GHz
01-18 08:27 DEBUG  WindowsBackend: bootloader=vista
01-18 08:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 202853.210938 mb free ntfs)
01-18 08:27 DEBUG  WindowsBackend: drive=Drive(B: removable 0.0 mb free )
01-18 08:27 DEBUG  WindowsBackend: drive=Drive(C: hd 202853.210938 mb free ntfs)
01-18 08:27 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
01-18 08:27 DEBUG  WindowsBackend: uninstaller_path=None
01-18 08:27 DEBUG  WindowsBackend: previous_target_dir=None
01-18 08:27 DEBUG  WindowsBackend: previous_distro_name=None
01-18 08:27 DEBUG  WindowsBackend: keyboard_id=67699721
01-18 08:27 DEBUG  WindowsBackend: keyboard_layout=us
01-18 08:27 DEBUG  WindowsBackend: keyboard_variant=
01-18 08:27 DEBUG  WindowsBackend: total_memory_mb=2939.01953125
01-18 08:27 DEBUG  CommonBackend: Searching ISOs on USB devices
01-18 08:27 DEBUG  CommonBackend: Searching for local CDs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Ubuntu Netbook Remix CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Kubuntu Netbook CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Xubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether B:\ is a valid Mythbuntu CD
01-18 08:27 DEBUG  Distro:     does not contain B:\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Ubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Ubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Ubuntu Netbook Remix CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Kubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Kubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Kubuntu Netbook CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Xubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Xubuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Mythbuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp is a valid Mythbuntu CD
01-18 08:27 DEBUG  Distro:     does not contain C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\casper\filesystem.squashfs
01-18 08:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-18 08:27 INFO   Distro: Found a valid CD for Ubuntu: D:\
01-18 08:27 INFO   root: Running the installer...
01-18 08:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\translations, languages=['en_US', 'en']
01-18 08:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\translations, languages=['en_US', 'en']
01-18 08:27 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=andy
01-18 08:27 INFO   root: Received settings
01-18 08:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\translations, languages=['en_US', 'en']
01-18 08:27 DEBUG  TaskList: # Running tasklist...
01-18 08:27 DEBUG  TaskList: ## Running select_target_dir...
01-18 08:27 INFO   WindowsBackend: Installing into C:\ubuntu
01-18 08:27 DEBUG  TaskList: ## Finished select_target_dir
01-18 08:27 DEBUG  TaskList: ## Running create_dir_structure...
01-18 08:27 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-18 08:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-18 08:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-18 08:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-18 08:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-18 08:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-18 08:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-18 08:27 DEBUG  TaskList: ## Finished create_dir_structure
01-18 08:27 DEBUG  TaskList: ## Running uncompress_target_dir...
01-18 08:27 DEBUG  TaskList: ## Finished uncompress_target_dir
01-18 08:27 DEBUG  TaskList: ## Running create_uninstaller...
01-18 08:27 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-18 08:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-18 08:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-18 08:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-18 08:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-18 08:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
01-18 08:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-18 08:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
01-18 08:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
01-18 08:27 DEBUG  TaskList: ## Finished create_uninstaller
01-18 08:27 DEBUG  TaskList: ## Running copy_installation_files...
01-18 08:27 DEBUG  WindowsBackend: Copying C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-18 08:27 DEBUG  WindowsBackend: Copying C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\winboot -> C:\ubuntu\winboot
01-18 08:27 DEBUG  WindowsBackend: Copying C:\Users\Andy\AppData\Local\Temp\pylBDB8.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
01-18 08:27 DEBUG  TaskList: ## Finished copy_installation_files
01-18 08:27 DEBUG  TaskList: ## Running get_iso...
01-18 08:27 DEBUG  TaskList: New task copy_file
01-18 08:27 DEBUG  TaskList: ### Running copy_file...
01-18 08:28 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
01-18 08:28 DEBUG  TaskList: # Cancelling tasklist
01-18 08:28 DEBUG  TaskList: New task check_iso
01-18 08:28 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
01-18 08:28 DEBUG  CommonBackend: Searching for local ISO
01-18 08:28 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-18 08:28 DEBUG  TaskList: New task get_metalink
01-18 08:28 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
01-18 08:28 DEBUG  TaskList: # Cancelling tasklist
01-18 08:28 DEBUG  TaskList: # Finished tasklist
```

---

### Post by phillw on 2010-01-18
Hi,

I'm not really up to speed with Wubi, but I can give you a couple of pointers.

1) ensure you have administration privalidges - permission denied can be caused by a 'user' trying to do 'admin' stuff on Win.
2) there have been a few people having problems with Wubi on Win7. Now, as Wubi has been around a while & works .. and Win7 hasn't .... I'm not going to lay the blame, but it could be that Win7 is having a problem with Wubi - > !*wubi*  and *Win7* do not play nice. although I'm not sure how well **... **

Also --> [http://ubuntuforums.org/showthread.php?t=1346762](http://ubuntuforums.org/showthread.php?t=1346762)

So, IMHO, I'd get Win7 to make a free area of about 10GB, and put Ubuntu in as true dual boot. It's a 'real' install and much happier.

Regards,

Phill.

---

### Post by andycastille on 2010-01-18
I want to do that, but on my old laptop, I had to re-format the entire hard drive to remove it. I was *not *happy about loosing Windows.

---

### Post by andycastille on 2010-01-18
How do I remove it? I want to know before because Sony put all kinds of software on Windows, and they cost about $200 total by themselves.

---

### Post by adam814 on 2010-01-18
[http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html)

You *shouldn't* lose Windows that way as Windows itself does the resize.

---

### Post by andycastille on 2010-01-18
Um, no. I want to *delete *Ubuntu forever, not *re-size *it.

---

### Post by andycastille on 2010-01-18
I don't want to shrink it. I want to *delete it*. Like I said before.

---

### Post by phillw on 2010-01-18
Look at add/remove programmes and remove Wubi. If it isn't there, it didn't install - and from the look at that output - it doesn't look like it was successful.

As you're not dual-booting - there is no 'ubuntu' partiton to remove.

If you want to dual-boot, then under Win Vista / Win7 you can use windows itself to make an empty partition for ubuntu to use. --> [http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Likewise, if you decide to get rid of dual booting Ubuntu, reset the boot system back to Win from Grub --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  Then use the same system to delete the ubuntu area & grow your Win area back into it. There is no need to reformat disks to do these tasks, even with '98 and XP, you can use GParted to do the same thing - So, I don't know who told you to reformat / reinstall - Simply put - Don't reformat / re-install Win !!

Regards,

Phill.

---

### Post by andycastille on 2010-01-18
Well, OK. I'll try. I'll save the links in case I need them. As Ubuntu is such a great operating system that I might not have to. On account of the condition of my Windows 7. ](*,)
 
PS:
Thanks for the British spelling of programs! I live in the United States, and I don't like it. I saw on the sidebar that you live in England. Just so, if you ever think about coming to the United States, DO NOT CONTINUE!

---

### Post by phillw on 2010-01-18
It's not my fault you Americans cannot spell. So, stop calling that dogs-dinner of a language 'english' - call it american, or english for pre-school spelling classes :lolflag:

Having a dual boot installation is handy ... even more handy when a Win system dies, as the ubuntu system will allow you to recover your data from the failed Win area ... Gee, aren't we nice :D

Regards,

Phill.

---

### Post by andycastille on 2010-01-18
I always try. I try to be as British as possible. Like spelling Center Centre and Color Colour. I even renamed my Favorites folder to Favourites in Windows.:D

---

### Post by andycastille on 2010-01-18
I tried the full install. Went down to 'Install Ubuntu' and pressed Enter. A white Ubuntu logo  appeard and started flashing. It went for about 10 seconds, then a small white line appeared at the top left corner. It went for about 20 minutes, then I just shut it down by holding the power button. What happened and what is the fix?

---

### Post by andycastille on 2010-01-19
Notice the spelling of two pages on my website? ([www.computersrule.net]("http://www.computersrule.net"))
 
Software CentRE Downloads
Developer CentRE

---

### Post by andycastille on 2010-01-19
> **andycastille said:**
> I tried the full install. Went down to 'Install Ubuntu' and pressed Enter. A white Ubuntu logo appeard and started flashing. It went for about 10 seconds, then a small white line appeared at the top left corner. It went for about 20 minutes, then I just shut it down by holding the power button. What happened and what is the fix?
 
Like I said, is it a bad disc? I have a x64 computer, and the disc was x32. I downloaded the x64 version on my Ubuntu desktop computer, and I will have to burn it. I will post the results.

---

### Post by andycastille on 2010-01-19
:D Got it working!!! I just installed the x64 version inside Windows, and I ain't gonna go back to Windows for a long time! It froze every day. :lolflag: 

So, this problem is *solved!*

---

### Post by andycastille on 2010-01-19
Yeah, now how  do I install Skype? I downloaded it and when I opened it, it said:

Error: Dependency is not satisfiable: lib32stdc++6 (>= 4.1.1-21)

In the installation dialogue. How do I fix this?

---

### Post by andycastille on 2010-01-19
Ohh, flaggapoof. Why don't I just do the full install?

---

### Post by andycastille on 2010-01-21
Ubuntu took Windows 7 inside itself! If I remove Ubuntu, Windows 7 will be deleted too! How do I remove Ubuntu *without touching *Windows 7? But using Windows 7 to do it?

---

### Post by Meepz on 2010-11-24
> [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]                 **Re: Installation Error - Errno 13**             
                                                                :grin: Got it working!!! I just installed the x64 version inside Windows, and I ain't gonna go back to Windows for a long time! It froze every day. :lolflag: 

So, this problem is *solved!*
                                                                                               __________________
> **andycastille said:**
> Ubuntu took Windows 7 inside itself! If I remove Ubuntu, Windows 7 will be deleted too! How do I remove Ubuntu *without touching *Windows 7? But using Windows 7 to do it?


Shoudnt u first make up ur mind which one u wanna choose as UR system? 
sry for OT xD

---

### Post by Meepz on 2010-11-24
> [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]                 **Re: Installation Error - Errno 13**             
                                                                :grin: Got it working!!! I just installed the x64 version inside Windows, and I ain't gonna go back to Windows for a long time! It froze every day. :lolflag: 

So, this problem is *solved!*
                                                                                               __________________
> **andycastille said:**
> Ubuntu took Windows 7 inside itself! If I remove Ubuntu, Windows 7 will be deleted too! How do I remove Ubuntu *without touching *Windows 7? But using Windows 7 to do it?


Shoudnt u first make up ur mind which one u wanna choose as UR system? 
sry for OT xD

edit: also sry for bumping =S couldnt help it

---

