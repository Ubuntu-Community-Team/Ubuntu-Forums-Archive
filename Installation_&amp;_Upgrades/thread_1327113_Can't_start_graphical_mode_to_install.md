---
title: "Can't start graphical mode to install"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by shaoxuan on 2009-11-15
Hello,

I can't install Kubuntu 9.10 on my computer or using the Live-CD to test-drive, because it can't start the graphical mode when installing or live using, no matter how long I wait, only a command line prompt waiting me to type. But the screen is flicking every 10 seconds or so. Maybe the Display driver is wrong? my graphic card is nVidia 7300GT.

Sadly, the wubi install is also a failure, the log file is quoted below.

Please help me to install Kubuntu 9.10 into my computer, thanks.

> 11-15 17:10 INFO   root: === wubi 9.10ubuntu1 rev160 ===
11-15 17:10 DEBUG  root: Logfile is c:\users\yurippe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
11-15 17:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
11-15 17:10 DEBUG  CommonBackend: data_dir=C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\data
11-15 17:10 DEBUG  WindowsBackend: 7z=C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\bin\7z.exe
11-15 17:10 DEBUG  CommonBackend: Fetching basic info...
11-15 17:10 DEBUG  CommonBackend: original_exe=E:\wubi.exe
11-15 17:10 DEBUG  CommonBackend: platform=win32
11-15 17:10 DEBUG  CommonBackend: osname=nt
11-15 17:10 DEBUG  CommonBackend: language=zh_CN
11-15 17:10 DEBUG  CommonBackend: encoding=cp936
11-15 17:10 DEBUG  WindowsBackend: arch=i386
11-15 17:10 DEBUG  CommonBackend: Parsing isolist=C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\data\isolist.ini
11-15 17:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-15 17:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-15 17:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-15 17:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-15 17:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-15 17:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-15 17:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-15 17:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-15 17:10 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-15 17:10 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
11-15 17:10 DEBUG  WindowsBackend: Fetching host info...
11-15 17:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-15 17:10 DEBUG  WindowsBackend: windows version=vista
11-15 17:10 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-15 17:10 DEBUG  WindowsBackend: windows_sp=None
11-15 17:10 DEBUG  WindowsBackend: windows_build=7600
11-15 17:10 DEBUG  WindowsBackend: gmt=8
11-15 17:10 DEBUG  WindowsBackend: country=CN
11-15 17:10 DEBUG  WindowsBackend: timezone=Asia/Shanghai
11-15 17:10 DEBUG  WindowsBackend: windows_username=yurippe
11-15 17:10 DEBUG  WindowsBackend: user_full_name=yurippe
11-15 17:10 DEBUG  WindowsBackend: user_directory=C:\Users\yurippe
11-15 17:10 DEBUG  WindowsBackend: windows_language_code=1028
11-15 17:10 DEBUG  WindowsBackend: windows_language=Chinese (Traditional)
11-15 17:10 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 2.80GHz
11-15 17:10 DEBUG  WindowsBackend: bootloader=vista
11-15 17:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 26419.0976563 mb free ntfs)
11-15 17:10 DEBUG  WindowsBackend: drive=Drive(C: hd 26419.0976563 mb free ntfs)
11-15 17:10 DEBUG  WindowsBackend: drive=Drive(D: hd 212683.539063 mb free ntfs)
11-15 17:10 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-15 17:10 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-15 17:10 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-15 17:10 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-15 17:10 DEBUG  WindowsBackend: uninstaller_path=None
11-15 17:10 DEBUG  WindowsBackend: previous_target_dir=None
11-15 17:10 DEBUG  WindowsBackend: previous_distro_name=None
11-15 17:10 DEBUG  WindowsBackend: keyboard_id=134481924
11-15 17:10 DEBUG  WindowsBackend: keyboard_layout=cn
11-15 17:10 DEBUG  WindowsBackend: keyboard_variant=
11-15 17:10 DEBUG  CommonBackend: python locale=('zh_CN', 'cp936')
11-15 17:10 DEBUG  CommonBackend: locale=zh_CN.UTF-8
11-15 17:10 DEBUG  WindowsBackend: total_memory_mb=2047.5546875
11-15 17:10 DEBUG  CommonBackend: Searching ISOs on USB devices
11-15 17:10 DEBUG  CommonBackend: Searching for local CDs
11-15 17:10 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp is a valid Ubuntu CD
11-15 17:10 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp is a valid Ubuntu CD
11-15 17:10 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp is a valid Ubuntu Netbook Remix CD
11-15 17:10 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp is a valid Kubuntu CD
11-15 17:10 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp is a valid Kubuntu CD
11-15 17:10 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp is a valid Kubuntu Netbook CD
11-15 17:10 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp is a valid Xubuntu CD
11-15 17:10 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp is a valid Xubuntu CD
11-15 17:10 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp is a valid Mythbuntu CD
11-15 17:10 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp is a valid Mythbuntu CD
11-15 17:10 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-15 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-15 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
11-15 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-15 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-15 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-15 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-15 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-15 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-15 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-15 17:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-15 17:10 DEBUG  Distro:   parsing info from str=Kubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
11-15 17:10 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
11-15 17:10 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
11-15 17:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-15 17:10 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
11-15 17:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
11-15 17:10 DEBUG  Distro: wrong name: Kubuntu != Ubuntu Netbook Remix
11-15 17:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-15 17:10 DEBUG  Distro: wrong arch: i386 != amd64
11-15 17:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-15 17:10 INFO   Distro: Found a valid CD for Kubuntu: E:\
11-15 17:10 INFO   root: Running the CD menu...
11-15 17:10 DEBUG  WindowsFrontend: __init__...
11-15 17:10 DEBUG  WindowsFrontend: on_init...
11-15 17:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\translations, languages=['zh_CN', 'zh']
11-15 17:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\translations, languages=['zh_CN', 'zh']
11-15 17:11 INFO   root: CD menu finished
11-15 17:11 INFO   root: Running the installer...
11-15 17:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\translations, languages=['zh_CN', 'zh']
11-15 17:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\translations, languages=['zh_CN', 'zh']
11-15 17:13 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=30000MB, distro_name=Kubuntu, language=en_US, locale=en_US.UTF-8, username=yurippe
11-15 17:13 INFO   root: Received settings
11-15 17:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\translations, languages=['en_US', 'en']
11-15 17:13 DEBUG  TaskList: # Running tasklist...
11-15 17:13 DEBUG  TaskList: ## Running select_target_dir...
11-15 17:13 INFO   WindowsBackend: Installing into D:\ubuntu
11-15 17:13 DEBUG  TaskList: ## Finished select_target_dir
11-15 17:13 DEBUG  TaskList: ## Running create_dir_structure...
11-15 17:13 DEBUG  CommonBackend: Creating dir D:\ubuntu
11-15 17:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
11-15 17:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
11-15 17:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
11-15 17:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
11-15 17:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
11-15 17:13 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
11-15 17:13 DEBUG  TaskList: ## Finished create_dir_structure
11-15 17:13 DEBUG  TaskList: ## Running uncompress_target_dir...
11-15 17:13 DEBUG  TaskList: ## Finished uncompress_target_dir
11-15 17:13 DEBUG  TaskList: ## Running create_uninstaller...
11-15 17:13 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
11-15 17:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
11-15 17:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
11-15 17:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
11-15 17:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Kubuntu.ico
11-15 17:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
11-15 17:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
11-15 17:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
11-15 17:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-15 17:13 DEBUG  TaskList: ## Finished create_uninstaller
11-15 17:13 DEBUG  TaskList: ## Running copy_installation_files...
11-15 17:13 DEBUG  WindowsBackend: Copying C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
11-15 17:13 DEBUG  WindowsBackend: Copying C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\winboot -> D:\ubuntu\winboot
11-15 17:13 DEBUG  WindowsBackend: Copying C:\Users\yurippe\AppData\Local\Temp\pyl2169.tmp\data\images\Kubuntu.ico -> D:\ubuntu\Kubuntu.ico
11-15 17:13 DEBUG  TaskList: ## Finished copy_installation_files
11-15 17:13 DEBUG  TaskList: ## Running get_iso...
11-15 17:13 DEBUG  TaskList: New task copy_file
11-15 17:13 DEBUG  TaskList: ### Running copy_file...
11-15 17:16 DEBUG  TaskList: ### Finished copy_file
11-15 17:16 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
11-15 17:16 DEBUG  TaskList: # Cancelling tasklist
11-15 17:16 DEBUG  TaskList: New task check_iso
11-15 17:16 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
11-15 17:16 DEBUG  CommonBackend: Searching for local ISO
11-15 17:16 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-15 17:16 DEBUG  TaskList: New task get_metalink
11-15 17:16 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-15 17:16 DEBUG  TaskList: # Cancelling tasklist
11-15 17:16 DEBUG  TaskList: # Finished tasklist
11-15 17:19 INFO   root: === wubi 9.10ubuntu1 rev160 ===
11-15 17:19 DEBUG  root: Logfile is c:\users\yurippe\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
11-15 17:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
11-15 17:19 DEBUG  CommonBackend: data_dir=C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\data
11-15 17:19 DEBUG  WindowsBackend: 7z=C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\bin\7z.exe
11-15 17:19 DEBUG  CommonBackend: Fetching basic info...
11-15 17:19 DEBUG  CommonBackend: original_exe=E:\wubi.exe
11-15 17:19 DEBUG  CommonBackend: platform=win32
11-15 17:19 DEBUG  CommonBackend: osname=nt
11-15 17:19 DEBUG  CommonBackend: language=zh_CN
11-15 17:19 DEBUG  CommonBackend: encoding=cp936
11-15 17:19 DEBUG  WindowsBackend: arch=i386
11-15 17:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\data\isolist.ini
11-15 17:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-15 17:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-15 17:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-15 17:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-15 17:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-15 17:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-15 17:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-15 17:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-15 17:19 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-15 17:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
11-15 17:19 DEBUG  WindowsBackend: Fetching host info...
11-15 17:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-15 17:19 DEBUG  WindowsBackend: windows version=vista
11-15 17:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-15 17:19 DEBUG  WindowsBackend: windows_sp=None
11-15 17:19 DEBUG  WindowsBackend: windows_build=7600
11-15 17:19 DEBUG  WindowsBackend: gmt=8
11-15 17:19 DEBUG  WindowsBackend: country=CN
11-15 17:19 DEBUG  WindowsBackend: timezone=Asia/Shanghai
11-15 17:19 DEBUG  WindowsBackend: windows_username=yurippe
11-15 17:19 DEBUG  WindowsBackend: user_full_name=yurippe
11-15 17:19 DEBUG  WindowsBackend: user_directory=C:\Users\yurippe
11-15 17:19 DEBUG  WindowsBackend: windows_language_code=1028
11-15 17:19 DEBUG  WindowsBackend: windows_language=Chinese (Traditional)
11-15 17:19 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 2.80GHz
11-15 17:19 DEBUG  WindowsBackend: bootloader=vista
11-15 17:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 26418.828125 mb free ntfs)
11-15 17:19 DEBUG  WindowsBackend: drive=Drive(C: hd 26418.828125 mb free ntfs)
11-15 17:19 DEBUG  WindowsBackend: drive=Drive(D: hd 212000.011719 mb free ntfs)
11-15 17:19 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-15 17:19 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-15 17:19 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-15 17:19 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-15 17:19 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
11-15 17:19 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
11-15 17:19 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
11-15 17:19 DEBUG  WindowsBackend: keyboard_id=134481924
11-15 17:19 DEBUG  WindowsBackend: keyboard_layout=cn
11-15 17:19 DEBUG  WindowsBackend: keyboard_variant=
11-15 17:19 DEBUG  CommonBackend: python locale=('zh_CN', 'cp936')
11-15 17:19 DEBUG  CommonBackend: locale=zh_CN.UTF-8
11-15 17:19 DEBUG  WindowsBackend: total_memory_mb=2047.5546875
11-15 17:19 DEBUG  CommonBackend: Searching ISOs on USB devices
11-15 17:19 DEBUG  CommonBackend: Searching for local CDs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Ubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Ubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Ubuntu Netbook Remix CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Kubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Kubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Kubuntu Netbook CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Xubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Xubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Mythbuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Mythbuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-15 17:19 DEBUG  Distro:   parsing info from str=Kubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
11-15 17:19 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
11-15 17:19 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
11-15 17:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-15 17:19 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
11-15 17:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
11-15 17:19 DEBUG  Distro: wrong name: Kubuntu != Ubuntu Netbook Remix
11-15 17:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-15 17:19 DEBUG  Distro: wrong arch: i386 != amd64
11-15 17:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-15 17:19 INFO   Distro: Found a valid CD for Kubuntu: E:\
11-15 17:19 INFO   root: Running the CD menu...
11-15 17:19 DEBUG  WindowsFrontend: __init__...
11-15 17:19 DEBUG  WindowsFrontend: on_init...
11-15 17:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\translations, languages=['zh_CN', 'zh']
11-15 17:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\translations, languages=['zh_CN', 'zh']
11-15 17:19 INFO   root: CD menu finished
11-15 17:19 INFO   root: Already installed, running the uninstaller...
11-15 17:19 INFO   root: Running the uninstaller...
11-15 17:19 INFO   CommonBackend: This is the uninstaller running
11-15 17:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\translations, languages=['zh_CN', 'zh']
11-15 17:19 INFO   root: Received settings
11-15 17:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\translations, languages=['zh_CN', 'zh']
11-15 17:19 DEBUG  TaskList: # Running tasklist...
11-15 17:19 DEBUG  TaskList: ## Running &#22791;&#20221; ISO &#20809;&#30424;&#38236;&#20687;&#25991;&#20214;...
11-15 17:19 DEBUG  TaskList: ## Finished &#22791;&#20221; ISO &#20809;&#30424;&#38236;&#20687;&#25991;&#20214;
11-15 17:19 DEBUG  TaskList: ## Running &#21024;&#38500;&#24341;&#23548;&#39033;...
11-15 17:19 DEBUG  WindowsBackend: Could not find bcd id
11-15 17:19 DEBUG  WindowsBackend: undo_bootini C:
11-15 17:19 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 26418.828125 mb free ntfs)
11-15 17:19 DEBUG  WindowsBackend: undo_bootini D:
11-15 17:19 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 212000.011719 mb free ntfs)
11-15 17:19 DEBUG  WindowsBackend: undo_bootini G:
11-15 17:19 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
11-15 17:19 DEBUG  TaskList: ## Finished &#21024;&#38500;&#24341;&#23548;&#39033;
11-15 17:19 DEBUG  TaskList: ## Running &#21024;&#38500;&#30446;&#26631;&#30446;&#24405;...
11-15 17:19 DEBUG  CommonBackend: Deleting D:\ubuntu
11-15 17:19 DEBUG  TaskList: ## Finished &#21024;&#38500;&#30446;&#26631;&#30446;&#24405;
11-15 17:19 DEBUG  TaskList: ## Running &#21024;&#38500;&#27880;&#20876;&#34920;&#38190;&#20540;...
11-15 17:19 DEBUG  TaskList: ## Finished &#21024;&#38500;&#27880;&#20876;&#34920;&#38190;&#20540;
11-15 17:19 DEBUG  TaskList: # Finished tasklist
11-15 17:19 INFO   root: Almost finished uninstalling
11-15 17:19 INFO   root: Finished uninstallation
11-15 17:19 DEBUG  CommonBackend: Fetching basic info...
11-15 17:19 DEBUG  CommonBackend: original_exe=E:\wubi.exe
11-15 17:19 DEBUG  CommonBackend: platform=win32
11-15 17:19 DEBUG  CommonBackend: osname=nt
11-15 17:19 DEBUG  WindowsBackend: arch=i386
11-15 17:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\data\isolist.ini
11-15 17:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-15 17:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-15 17:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-15 17:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-15 17:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-15 17:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-15 17:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-15 17:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-15 17:19 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-15 17:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
11-15 17:19 DEBUG  WindowsBackend: Fetching host info...
11-15 17:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-15 17:19 DEBUG  WindowsBackend: windows version=vista
11-15 17:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-15 17:19 DEBUG  WindowsBackend: windows_sp=None
11-15 17:19 DEBUG  WindowsBackend: windows_build=7600
11-15 17:19 DEBUG  WindowsBackend: gmt=8
11-15 17:19 DEBUG  WindowsBackend: country=CN
11-15 17:19 DEBUG  WindowsBackend: timezone=Asia/Shanghai
11-15 17:19 DEBUG  WindowsBackend: windows_username=yurippe
11-15 17:19 DEBUG  WindowsBackend: user_full_name=yurippe
11-15 17:19 DEBUG  WindowsBackend: user_directory=C:\Users\yurippe
11-15 17:19 DEBUG  WindowsBackend: windows_language_code=1028
11-15 17:19 DEBUG  WindowsBackend: windows_language=Chinese (Traditional)
11-15 17:19 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) 4 CPU 2.80GHz
11-15 17:19 DEBUG  WindowsBackend: bootloader=vista
11-15 17:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 26418.7148438 mb free ntfs)
11-15 17:19 DEBUG  WindowsBackend: drive=Drive(C: hd 26418.7148438 mb free ntfs)
11-15 17:19 DEBUG  WindowsBackend: drive=Drive(D: hd 212683.539063 mb free ntfs)
11-15 17:19 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-15 17:19 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-15 17:19 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-15 17:19 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
11-15 17:19 DEBUG  WindowsBackend: uninstaller_path=None
11-15 17:19 DEBUG  WindowsBackend: previous_target_dir=None
11-15 17:19 DEBUG  WindowsBackend: previous_distro_name=None
11-15 17:19 DEBUG  WindowsBackend: keyboard_id=134481924
11-15 17:19 DEBUG  WindowsBackend: keyboard_layout=cn
11-15 17:19 DEBUG  WindowsBackend: keyboard_variant=
11-15 17:19 DEBUG  WindowsBackend: total_memory_mb=2047.5546875
11-15 17:19 DEBUG  CommonBackend: Searching ISOs on USB devices
11-15 17:19 DEBUG  CommonBackend: Searching for local CDs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Ubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Ubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Ubuntu Netbook Remix CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Kubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Kubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Kubuntu Netbook CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Xubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Xubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Mythbuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp is a valid Mythbuntu CD
11-15 17:19 DEBUG  Distro:     does not contain C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-15 17:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-15 17:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-15 17:19 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
11-15 17:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-15 17:19 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
11-15 17:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
11-15 17:19 DEBUG  Distro: wrong name: Kubuntu != Ubuntu Netbook Remix
11-15 17:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-15 17:20 DEBUG  Distro: wrong arch: i386 != amd64
11-15 17:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-15 17:20 INFO   Distro: Found a valid CD for Kubuntu: E:\
11-15 17:20 INFO   root: Running the installer...
11-15 17:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\translations, languages=['zh_CN', 'zh']
11-15 17:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\translations, languages=['zh_CN', 'zh']
11-15 17:20 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=14000MB, distro_name=Kubuntu, language=en_US, locale=en_US.UTF-8, username=yurippe
11-15 17:20 INFO   root: Received settings
11-15 17:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\translations, languages=['en_US', 'en']
11-15 17:20 DEBUG  TaskList: # Running tasklist...
11-15 17:20 DEBUG  TaskList: ## Running select_target_dir...
11-15 17:20 INFO   WindowsBackend: Installing into D:\ubuntu
11-15 17:20 DEBUG  TaskList: ## Finished select_target_dir
11-15 17:20 DEBUG  TaskList: ## Running create_dir_structure...
11-15 17:20 DEBUG  CommonBackend: Creating dir D:\ubuntu
11-15 17:20 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
11-15 17:20 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
11-15 17:20 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
11-15 17:20 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
11-15 17:20 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
11-15 17:20 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
11-15 17:20 DEBUG  TaskList: ## Finished create_dir_structure
11-15 17:20 DEBUG  TaskList: ## Running uncompress_target_dir...
11-15 17:20 DEBUG  TaskList: ## Finished uncompress_target_dir
11-15 17:20 DEBUG  TaskList: ## Running create_uninstaller...
11-15 17:20 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
11-15 17:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
11-15 17:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
11-15 17:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
11-15 17:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Kubuntu.ico
11-15 17:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
11-15 17:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
11-15 17:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
11-15 17:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-15 17:20 DEBUG  TaskList: ## Finished create_uninstaller
11-15 17:20 DEBUG  TaskList: ## Running copy_installation_files...
11-15 17:20 DEBUG  WindowsBackend: Copying C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
11-15 17:20 DEBUG  WindowsBackend: Copying C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\winboot -> D:\ubuntu\winboot
11-15 17:20 DEBUG  WindowsBackend: Copying C:\Users\yurippe\AppData\Local\Temp\pyl8FAD.tmp\data\images\Kubuntu.ico -> D:\ubuntu\Kubuntu.ico
11-15 17:20 DEBUG  TaskList: ## Finished copy_installation_files
11-15 17:20 DEBUG  TaskList: ## Running get_iso...
11-15 17:20 DEBUG  TaskList: New task copy_file
11-15 17:20 DEBUG  TaskList: ### Running copy_file...
11-15 17:31 DEBUG  TaskList: ### Finished copy_file
11-15 17:31 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
11-15 17:31 DEBUG  TaskList: # Cancelling tasklist
11-15 17:31 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
11-15 17:31 DEBUG  TaskList: New task check_iso
11-15 17:31 DEBUG  CommonBackend: Searching for local ISO
11-15 17:31 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-15 17:31 DEBUG  TaskList: New task get_metalink
11-15 17:31 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-15 17:31 DEBUG  TaskList: # Cancelling tasklist
11-15 17:31 DEBUG  TaskList: # Finished tasklist


---

### Post by stopping on 2009-11-16
Me too


I am having a hell of a time installing 9.10 with a new install of Windows 7. 

Mine is the 32bit...... ubuntu is not seeing Windows 7 in the installation partitioner but is in the live cd graphic mode.

The 9.10 cd wants to format the whole 250G hard disk even though 7 is on 60G of it.

Wubi also failed to see it and correct the boot menu/ grub.

---

### Post by shaoxuan on 2009-11-16
Mine is windows 7 too, I wanto to install kubuntu alongside with windows 7, but it seems that it's mission impossible.

I can't even get into graphical live cd mode. Only command line & flicking.

---

