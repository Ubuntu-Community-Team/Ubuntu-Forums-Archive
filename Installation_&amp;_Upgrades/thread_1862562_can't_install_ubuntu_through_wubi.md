---
title: "can't install ubuntu through wubi"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by jo53_4 on 2011-10-16
im trying to install ubuntu on my laptop through wubi. i ve downloaded the live cd for ubuntu 11.10, putted the disc on the tray. everything goes well until it says 0 seconds remaining. i ve tried multiple times and i always keep ending with the same error 
:(
[ATTACH]204585[/ATTACH]

[ATTACH]204586[/ATTACH]

---

### Post by bcbc on 2011-10-16
Look in the %temp% directory - post the contents of wubi-11.10-rev241.log here between [CODE [SIZE="1"][/SIZE]][/CODE] tags (click on # above)

---

### Post by jo53_4 on 2011-10-18
thank you for answering my post :), this is the contents from ubuntu 11.04 since its the one i want to install, noticed the contents from ubuntu 11.04 to 11.10 were very different while having the same issue on both versions, thanks

```
10-16 18:41 INFO   root: === wubi 11.04 rev211 ===
10-16 18:41 DEBUG  root: Logfile is c:\users\jo53_4\appdata\local\temp\wubi-11.04-rev211.log
10-16 18:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
10-16 18:41 DEBUG  CommonBackend: data_dir=C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\data
10-16 18:41 DEBUG  WindowsBackend: 7z=C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\bin\7z.exe
10-16 18:41 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-16 18:41 DEBUG  CommonBackend: Fetching basic info...
10-16 18:41 DEBUG  CommonBackend: original_exe=E:\wubi.exe
10-16 18:41 DEBUG  CommonBackend: platform=win32
10-16 18:41 DEBUG  CommonBackend: osname=nt
10-16 18:41 DEBUG  CommonBackend: language=en_US
10-16 18:41 DEBUG  CommonBackend: encoding=cp1252
10-16 18:41 DEBUG  WindowsBackend: arch=amd64
10-16 18:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\data\isolist.ini
10-16 18:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-16 18:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-16 18:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-16 18:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-16 18:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-16 18:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-16 18:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-16 18:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-16 18:41 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-16 18:41 DEBUG  WindowsBackend: Fetching host info...
10-16 18:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-16 18:41 DEBUG  WindowsBackend: windows version=vista
10-16 18:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-16 18:41 DEBUG  WindowsBackend: windows_sp=None
10-16 18:41 DEBUG  WindowsBackend: windows_build=7601
10-16 18:41 DEBUG  WindowsBackend: gmt=-4
10-16 18:41 DEBUG  WindowsBackend: country=US
10-16 18:41 DEBUG  WindowsBackend: timezone=America/New_York
10-16 18:41 DEBUG  WindowsBackend: windows_username=JO53_4
10-16 18:41 DEBUG  WindowsBackend: user_full_name=JO53_4
10-16 18:41 DEBUG  WindowsBackend: user_directory=C:\Users\JO53_4
10-16 18:41 DEBUG  WindowsBackend: windows_language_code=1033
10-16 18:41 DEBUG  WindowsBackend: windows_language=English
10-16 18:41 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
10-16 18:41 DEBUG  WindowsBackend: bootloader=vista
10-16 18:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 333132.03125 mb free ntfs)
10-16 18:41 DEBUG  WindowsBackend: drive=Drive(C: hd 333132.03125 mb free ntfs)
10-16 18:41 DEBUG  WindowsBackend: drive=Drive(D: hd 2068.62890625 mb free ntfs)
10-16 18:41 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
10-16 18:41 DEBUG  WindowsBackend: uninstaller_path=None
10-16 18:41 DEBUG  WindowsBackend: previous_target_dir=None
10-16 18:41 DEBUG  WindowsBackend: previous_distro_name=None
10-16 18:41 DEBUG  WindowsBackend: keyboard_id=67699721
10-16 18:41 DEBUG  WindowsBackend: keyboard_layout=us
10-16 18:41 DEBUG  WindowsBackend: keyboard_variant=
10-16 18:41 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-16 18:41 DEBUG  CommonBackend: locale=en_US.UTF-8
10-16 18:41 DEBUG  WindowsBackend: total_memory_mb=3837.82421875
10-16 18:41 DEBUG  CommonBackend: Searching ISOs on USB devices
10-16 18:41 DEBUG  CommonBackend: Searching for local CDs
10-16 18:41 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp is a valid Ubuntu CD
10-16 18:41 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp is a valid Ubuntu CD
10-16 18:41 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp is a valid Ubuntu Netbook CD
10-16 18:41 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp is a valid Kubuntu CD
10-16 18:41 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp is a valid Kubuntu CD
10-16 18:41 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp is a valid Xubuntu CD
10-16 18:41 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp is a valid Xubuntu CD
10-16 18:41 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp is a valid Mythbuntu CD
10-16 18:41 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp is a valid Mythbuntu CD
10-16 18:41 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 18:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 18:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-16 18:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 18:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 18:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-16 18:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-16 18:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 18:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 18:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-16 18:41 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
10-16 18:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
10-16 18:41 INFO   Distro: Found a valid CD for Ubuntu: E:\
10-16 18:41 INFO   root: Running the CD menu...
10-16 18:41 DEBUG  WindowsFrontend: __init__...
10-16 18:41 DEBUG  WindowsFrontend: on_init...
10-16 18:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\translations, languages=['en_US', 'en']
10-16 18:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\translations, languages=['en_US', 'en']
10-16 18:41 INFO   root: CD menu finished
10-16 18:41 INFO   root: Running the installer...
10-16 18:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\translations, languages=['en_US', 'en']
10-16 18:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\translations, languages=['en_US', 'en']
10-16 18:42 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jo53_4
10-16 18:42 INFO   root: Received settings
10-16 18:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\translations, languages=['en_US', 'en']
10-16 18:42 DEBUG  TaskList: # Running tasklist...
10-16 18:42 DEBUG  TaskList: ## Running select_target_dir...
10-16 18:42 INFO   WindowsBackend: Installing into C:\ubuntu
10-16 18:42 DEBUG  TaskList: ## Finished select_target_dir
10-16 18:42 DEBUG  TaskList: ## Running create_dir_structure...
10-16 18:42 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-16 18:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-16 18:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-16 18:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-16 18:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-16 18:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-16 18:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-16 18:42 DEBUG  TaskList: ## Finished create_dir_structure
10-16 18:42 DEBUG  TaskList: ## Running uncompress_target_dir...
10-16 18:42 DEBUG  TaskList: ## Finished uncompress_target_dir
10-16 18:42 DEBUG  TaskList: ## Running create_uninstaller...
10-16 18:42 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-16 18:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-16 18:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-16 18:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-16 18:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-16 18:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
10-16 18:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-16 18:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
10-16 18:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
10-16 18:42 DEBUG  TaskList: ## Finished create_uninstaller
10-16 18:42 DEBUG  TaskList: ## Running copy_installation_files...
10-16 18:42 DEBUG  WindowsBackend: Copying C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-16 18:42 DEBUG  WindowsBackend: Copying C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\winboot -> C:\ubuntu\winboot
10-16 18:42 DEBUG  WindowsBackend: Copying C:\Users\JO53_4\AppData\Local\Temp\pylEA0.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-16 18:42 DEBUG  TaskList: ## Finished copy_installation_files
10-16 18:42 DEBUG  TaskList: ## Running get_iso...
10-16 18:42 DEBUG  TaskList: New task copy_file
10-16 18:42 DEBUG  TaskList: ### Running copy_file...
10-16 18:46 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
10-16 18:46 DEBUG  TaskList: # Cancelling tasklist
10-16 18:46 DEBUG  TaskList: New task check_iso
10-16 18:46 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
10-16 18:46 DEBUG  CommonBackend: Searching for local ISO
10-16 18:46 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-16 18:46 DEBUG  TaskList: New task get_metalink
10-16 18:46 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-16 18:46 DEBUG  TaskList: # Cancelling tasklist
10-16 18:46 DEBUG  TaskList: # Finished tasklist
10-16 18:49 INFO   root: === wubi 11.04 rev211 ===
10-16 18:49 DEBUG  root: Logfile is c:\users\jo53_4\appdata\local\temp\wubi-11.04-rev211.log
10-16 18:49 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
10-16 18:49 DEBUG  CommonBackend: data_dir=C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\data
10-16 18:49 DEBUG  WindowsBackend: 7z=C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\bin\7z.exe
10-16 18:49 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-16 18:49 DEBUG  CommonBackend: Fetching basic info...
10-16 18:49 DEBUG  CommonBackend: original_exe=E:\wubi.exe
10-16 18:49 DEBUG  CommonBackend: platform=win32
10-16 18:49 DEBUG  CommonBackend: osname=nt
10-16 18:49 DEBUG  CommonBackend: language=en_US
10-16 18:49 DEBUG  CommonBackend: encoding=cp1252
10-16 18:49 DEBUG  WindowsBackend: arch=amd64
10-16 18:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\data\isolist.ini
10-16 18:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-16 18:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-16 18:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-16 18:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-16 18:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-16 18:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-16 18:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-16 18:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-16 18:49 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-16 18:49 DEBUG  WindowsBackend: Fetching host info...
10-16 18:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-16 18:49 DEBUG  WindowsBackend: windows version=vista
10-16 18:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-16 18:49 DEBUG  WindowsBackend: windows_sp=None
10-16 18:49 DEBUG  WindowsBackend: windows_build=7601
10-16 18:49 DEBUG  WindowsBackend: gmt=-4
10-16 18:49 DEBUG  WindowsBackend: country=US
10-16 18:49 DEBUG  WindowsBackend: timezone=America/New_York
10-16 18:49 DEBUG  WindowsBackend: windows_username=JO53_4
10-16 18:49 DEBUG  WindowsBackend: user_full_name=JO53_4
10-16 18:49 DEBUG  WindowsBackend: user_directory=C:\Users\JO53_4
10-16 18:49 DEBUG  WindowsBackend: windows_language_code=1033
10-16 18:49 DEBUG  WindowsBackend: windows_language=English
10-16 18:49 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
10-16 18:49 DEBUG  WindowsBackend: bootloader=vista
10-16 18:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 332427.371094 mb free ntfs)
10-16 18:49 DEBUG  WindowsBackend: drive=Drive(C: hd 332427.371094 mb free ntfs)
10-16 18:49 DEBUG  WindowsBackend: drive=Drive(D: hd 2068.62890625 mb free ntfs)
10-16 18:49 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
10-16 18:49 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-16 18:49 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-16 18:49 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-16 18:49 DEBUG  WindowsBackend: keyboard_id=67699721
10-16 18:49 DEBUG  WindowsBackend: keyboard_layout=us
10-16 18:49 DEBUG  WindowsBackend: keyboard_variant=
10-16 18:49 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-16 18:49 DEBUG  CommonBackend: locale=en_US.UTF-8
10-16 18:49 DEBUG  WindowsBackend: total_memory_mb=3837.82421875
10-16 18:49 DEBUG  CommonBackend: Searching ISOs on USB devices
10-16 18:49 DEBUG  CommonBackend: Searching for local CDs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Ubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Ubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Ubuntu Netbook CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Kubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Kubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Xubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Xubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Mythbuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Mythbuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-16 18:49 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
10-16 18:49 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
10-16 18:49 INFO   Distro: Found a valid CD for Ubuntu: E:\
10-16 18:49 INFO   root: Running the CD menu...
10-16 18:49 DEBUG  WindowsFrontend: __init__...
10-16 18:49 DEBUG  WindowsFrontend: on_init...
10-16 18:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\translations, languages=['en_US', 'en']
10-16 18:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\translations, languages=['en_US', 'en']
10-16 18:49 INFO   root: CD menu finished
10-16 18:49 INFO   root: Already installed, running the uninstaller...
10-16 18:49 INFO   root: Running the uninstaller...
10-16 18:49 INFO   CommonBackend: This is the uninstaller running
10-16 18:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\translations, languages=['en_US', 'en']
10-16 18:49 INFO   root: Received settings
10-16 18:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\translations, languages=['en_US', 'en']
10-16 18:49 DEBUG  TaskList: # Running tasklist...
10-16 18:49 DEBUG  TaskList: ## Running Backup ISO...
10-16 18:49 DEBUG  TaskList: ## Finished Backup ISO
10-16 18:49 DEBUG  TaskList: ## Running Remove bootloader entry...
10-16 18:49 DEBUG  WindowsBackend: Could not find bcd id
10-16 18:49 DEBUG  WindowsBackend: undo_bootini C:
10-16 18:49 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 332427.371094 mb free ntfs)
10-16 18:49 DEBUG  WindowsBackend: undo_bootini D:
10-16 18:49 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2068.62890625 mb free ntfs)
10-16 18:49 DEBUG  TaskList: ## Finished Remove bootloader entry
10-16 18:49 DEBUG  TaskList: ## Running Remove target dir...
10-16 18:49 DEBUG  CommonBackend: Deleting C:\ubuntu
10-16 18:49 DEBUG  TaskList: ## Finished Remove target dir
10-16 18:49 DEBUG  TaskList: ## Running Remove registry key...
10-16 18:49 DEBUG  TaskList: ## Finished Remove registry key
10-16 18:49 DEBUG  TaskList: # Finished tasklist
10-16 18:49 INFO   root: Almost finished uninstalling
10-16 18:49 INFO   root: Finished uninstallation
10-16 18:49 DEBUG  CommonBackend: Fetching basic info...
10-16 18:49 DEBUG  CommonBackend: original_exe=E:\wubi.exe
10-16 18:49 DEBUG  CommonBackend: platform=win32
10-16 18:49 DEBUG  CommonBackend: osname=nt
10-16 18:49 DEBUG  WindowsBackend: arch=amd64
10-16 18:49 DEBUG  CommonBackend: Parsing isolist=C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\data\isolist.ini
10-16 18:49 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-16 18:49 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-16 18:49 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-16 18:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-16 18:49 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-16 18:49 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-16 18:49 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-16 18:49 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-16 18:49 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-16 18:49 DEBUG  WindowsBackend: Fetching host info...
10-16 18:49 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-16 18:49 DEBUG  WindowsBackend: windows version=vista
10-16 18:49 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-16 18:49 DEBUG  WindowsBackend: windows_sp=None
10-16 18:49 DEBUG  WindowsBackend: windows_build=7601
10-16 18:49 DEBUG  WindowsBackend: gmt=-4
10-16 18:49 DEBUG  WindowsBackend: country=US
10-16 18:49 DEBUG  WindowsBackend: timezone=America/New_York
10-16 18:49 DEBUG  WindowsBackend: windows_username=JO53_4
10-16 18:49 DEBUG  WindowsBackend: user_full_name=JO53_4
10-16 18:49 DEBUG  WindowsBackend: user_directory=C:\Users\JO53_4
10-16 18:49 DEBUG  WindowsBackend: windows_language_code=1033
10-16 18:49 DEBUG  WindowsBackend: windows_language=English
10-16 18:49 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
10-16 18:49 DEBUG  WindowsBackend: bootloader=vista
10-16 18:49 DEBUG  WindowsBackend: system_drive=Drive(C: hd 333126.003906 mb free ntfs)
10-16 18:49 DEBUG  WindowsBackend: drive=Drive(C: hd 333126.003906 mb free ntfs)
10-16 18:49 DEBUG  WindowsBackend: drive=Drive(D: hd 2068.62890625 mb free ntfs)
10-16 18:49 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
10-16 18:49 DEBUG  WindowsBackend: uninstaller_path=None
10-16 18:49 DEBUG  WindowsBackend: previous_target_dir=None
10-16 18:49 DEBUG  WindowsBackend: previous_distro_name=None
10-16 18:49 DEBUG  WindowsBackend: keyboard_id=67699721
10-16 18:49 DEBUG  WindowsBackend: keyboard_layout=us
10-16 18:49 DEBUG  WindowsBackend: keyboard_variant=
10-16 18:49 DEBUG  WindowsBackend: total_memory_mb=3837.82421875
10-16 18:49 DEBUG  CommonBackend: Searching ISOs on USB devices
10-16 18:49 DEBUG  CommonBackend: Searching for local CDs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Ubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Ubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Ubuntu Netbook CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Kubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Kubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Xubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Xubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Mythbuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp is a valid Mythbuntu CD
10-16 18:49 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 18:49 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 18:49 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-16 18:49 INFO   Distro: Found a valid CD for Ubuntu: E:\
10-16 18:49 INFO   root: Running the installer...
10-16 18:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\translations, languages=['en_US', 'en']
10-16 18:49 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\translations, languages=['en_US', 'en']
10-16 18:50 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jo53_4
10-16 18:50 INFO   root: Received settings
10-16 18:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\translations, languages=['en_US', 'en']
10-16 18:50 DEBUG  TaskList: # Running tasklist...
10-16 18:50 DEBUG  TaskList: ## Running select_target_dir...
10-16 18:50 INFO   WindowsBackend: Installing into C:\ubuntu
10-16 18:50 DEBUG  TaskList: ## Finished select_target_dir
10-16 18:50 DEBUG  TaskList: ## Running create_dir_structure...
10-16 18:50 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-16 18:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-16 18:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-16 18:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-16 18:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-16 18:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-16 18:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-16 18:50 DEBUG  TaskList: ## Finished create_dir_structure
10-16 18:50 DEBUG  TaskList: ## Running uncompress_target_dir...
10-16 18:50 DEBUG  TaskList: ## Finished uncompress_target_dir
10-16 18:50 DEBUG  TaskList: ## Running create_uninstaller...
10-16 18:50 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-16 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-16 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-16 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-16 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-16 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
10-16 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-16 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
10-16 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
10-16 18:50 DEBUG  TaskList: ## Finished create_uninstaller
10-16 18:50 DEBUG  TaskList: ## Running copy_installation_files...
10-16 18:50 DEBUG  WindowsBackend: Copying C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-16 18:50 DEBUG  WindowsBackend: Copying C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\winboot -> C:\ubuntu\winboot
10-16 18:50 DEBUG  WindowsBackend: Copying C:\Users\JO53_4\AppData\Local\Temp\pylD133.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-16 18:50 DEBUG  TaskList: ## Finished copy_installation_files
10-16 18:50 DEBUG  TaskList: ## Running get_iso...
10-16 18:50 DEBUG  TaskList: New task copy_file
10-16 18:50 DEBUG  TaskList: ### Running copy_file...
10-16 18:54 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
10-16 18:54 DEBUG  TaskList: # Cancelling tasklist
10-16 18:54 DEBUG  TaskList: New task check_iso
10-16 18:54 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
10-16 18:54 DEBUG  CommonBackend: Searching for local ISO
10-16 18:54 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-16 18:54 DEBUG  TaskList: New task get_metalink
10-16 18:54 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-16 18:54 DEBUG  TaskList: # Cancelling tasklist
10-16 18:54 DEBUG  TaskList: # Finished tasklist
10-16 19:04 INFO   root: === wubi 11.04 rev211 ===
10-16 19:04 DEBUG  root: Logfile is c:\users\jo53_4\appdata\local\temp\wubi-11.04-rev211.log
10-16 19:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
10-16 19:04 DEBUG  CommonBackend: data_dir=C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp\data
10-16 19:04 DEBUG  WindowsBackend: 7z=C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp\bin\7z.exe
10-16 19:04 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-16 19:04 DEBUG  CommonBackend: Fetching basic info...
10-16 19:04 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
10-16 19:04 DEBUG  CommonBackend: platform=win32
10-16 19:04 DEBUG  CommonBackend: osname=nt
10-16 19:04 DEBUG  CommonBackend: language=en_US
10-16 19:04 DEBUG  CommonBackend: encoding=cp1252
10-16 19:04 DEBUG  WindowsBackend: arch=amd64
10-16 19:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp\data\isolist.ini
10-16 19:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-16 19:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-16 19:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-16 19:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-16 19:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-16 19:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-16 19:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-16 19:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-16 19:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-16 19:04 DEBUG  WindowsBackend: Fetching host info...
10-16 19:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-16 19:04 DEBUG  WindowsBackend: windows version=vista
10-16 19:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-16 19:04 DEBUG  WindowsBackend: windows_sp=None
10-16 19:04 DEBUG  WindowsBackend: windows_build=7601
10-16 19:04 DEBUG  WindowsBackend: gmt=-4
10-16 19:04 DEBUG  WindowsBackend: country=US
10-16 19:04 DEBUG  WindowsBackend: timezone=America/New_York
10-16 19:04 DEBUG  WindowsBackend: windows_username=JO53_4
10-16 19:04 DEBUG  WindowsBackend: user_full_name=JO53_4
10-16 19:04 DEBUG  WindowsBackend: user_directory=C:\Users\JO53_4
10-16 19:04 DEBUG  WindowsBackend: windows_language_code=1033
10-16 19:04 DEBUG  WindowsBackend: windows_language=English
10-16 19:04 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
10-16 19:04 DEBUG  WindowsBackend: bootloader=vista
10-16 19:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 332203.984375 mb free ntfs)
10-16 19:04 DEBUG  WindowsBackend: drive=Drive(C: hd 332203.984375 mb free ntfs)
10-16 19:04 DEBUG  WindowsBackend: drive=Drive(D: hd 2068.62890625 mb free ntfs)
10-16 19:04 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-16 19:04 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-16 19:04 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-16 19:04 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-16 19:04 DEBUG  WindowsBackend: keyboard_id=67699721
10-16 19:04 DEBUG  WindowsBackend: keyboard_layout=us
10-16 19:04 DEBUG  WindowsBackend: keyboard_variant=
10-16 19:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-16 19:04 DEBUG  CommonBackend: locale=en_US.UTF-8
10-16 19:04 DEBUG  WindowsBackend: total_memory_mb=3837.82421875
10-16 19:04 DEBUG  CommonBackend: Searching ISOs on USB devices
10-16 19:04 DEBUG  CommonBackend: Searching for local CDs
10-16 19:04 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp is a valid Ubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp is a valid Ubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp is a valid Ubuntu Netbook CD
10-16 19:04 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp is a valid Kubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp is a valid Kubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp is a valid Xubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp is a valid Xubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp is a valid Mythbuntu CD
10-16 19:04 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp is a valid Mythbuntu CD
10-16 19:04 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-16 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-16 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-16 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-16 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 19:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-16 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 19:04 INFO   root: Running the uninstaller...
10-16 19:04 INFO   CommonBackend: This is the uninstaller running
10-16 19:04 DEBUG  WindowsFrontend: __init__...
10-16 19:04 DEBUG  WindowsFrontend: on_init...
10-16 19:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp\translations, languages=['en_US', 'en']
10-16 19:04 INFO   root: Received settings
10-16 19:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp\translations, languages=['en_US', 'en']
10-16 19:04 DEBUG  TaskList: # Running tasklist...
10-16 19:04 DEBUG  TaskList: ## Running Backup ISO...
10-16 19:04 DEBUG  TaskList: ## Finished Backup ISO
10-16 19:05 DEBUG  TaskList: ## Running Remove bootloader entry...
10-16 19:05 DEBUG  WindowsBackend: Could not find bcd id
10-16 19:05 DEBUG  WindowsBackend: undo_bootini C:
10-16 19:05 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 332203.984375 mb free ntfs)
10-16 19:05 DEBUG  WindowsBackend: undo_bootini D:
10-16 19:05 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2068.62890625 mb free ntfs)
10-16 19:05 DEBUG  TaskList: ## Finished Remove bootloader entry
10-16 19:05 DEBUG  TaskList: ## Running Remove target dir...
10-16 19:05 DEBUG  CommonBackend: Deleting C:\ubuntu
10-16 19:05 DEBUG  TaskList: ## Finished Remove target dir
10-16 19:05 DEBUG  TaskList: ## Running Remove registry key...
10-16 19:05 DEBUG  TaskList: ## Finished Remove registry key
10-16 19:05 DEBUG  TaskList: # Finished tasklist
10-16 19:05 INFO   root: Almost finished uninstalling
10-16 19:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylBF39.tmp\translations, languages=['en_US', 'en']
10-16 19:05 INFO   root: Finished uninstallation
10-16 19:05 DEBUG  root: application.quit
10-16 19:05 DEBUG  WindowsFrontend: frontend.quit
10-16 19:05 DEBUG  WindowsFrontend: frontend.on_quit
10-16 19:05 DEBUG  root: application.on_quit
10-16 19:05 INFO   root: sys.exit
10-17 23:58 INFO   root: === wubi 11.04 rev211 ===
10-17 23:58 DEBUG  root: Logfile is c:\users\jo53_4\appdata\local\temp\wubi-11.04-rev211.log
10-17 23:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
10-17 23:58 DEBUG  CommonBackend: data_dir=C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\data
10-17 23:58 DEBUG  WindowsBackend: 7z=C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\bin\7z.exe
10-17 23:58 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-17 23:58 DEBUG  CommonBackend: Fetching basic info...
10-17 23:58 DEBUG  CommonBackend: original_exe=E:\wubi.exe
10-17 23:58 DEBUG  CommonBackend: platform=win32
10-17 23:58 DEBUG  CommonBackend: osname=nt
10-17 23:58 DEBUG  CommonBackend: language=en_US
10-17 23:58 DEBUG  CommonBackend: encoding=cp1252
10-17 23:58 DEBUG  WindowsBackend: arch=amd64
10-17 23:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\data\isolist.ini
10-17 23:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-17 23:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-17 23:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-17 23:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-17 23:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-17 23:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-17 23:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-17 23:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-17 23:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-17 23:58 DEBUG  WindowsBackend: Fetching host info...
10-17 23:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-17 23:58 DEBUG  WindowsBackend: windows version=vista
10-17 23:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-17 23:58 DEBUG  WindowsBackend: windows_sp=None
10-17 23:58 DEBUG  WindowsBackend: windows_build=7601
10-17 23:58 DEBUG  WindowsBackend: gmt=-4
10-17 23:58 DEBUG  WindowsBackend: country=US
10-17 23:58 DEBUG  WindowsBackend: timezone=America/New_York
10-17 23:58 DEBUG  WindowsBackend: windows_username=JO53_4
10-17 23:58 DEBUG  WindowsBackend: user_full_name=JO53_4
10-17 23:58 DEBUG  WindowsBackend: user_directory=C:\Users\JO53_4
10-17 23:58 DEBUG  WindowsBackend: windows_language_code=1033
10-17 23:58 DEBUG  WindowsBackend: windows_language=English
10-17 23:58 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
10-17 23:58 DEBUG  WindowsBackend: bootloader=vista
10-17 23:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 333246.722656 mb free ntfs)
10-17 23:58 DEBUG  WindowsBackend: drive=Drive(C: hd 333246.722656 mb free ntfs)
10-17 23:58 DEBUG  WindowsBackend: drive=Drive(D: hd 13132.3203125 mb free ntfs)
10-17 23:58 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
10-17 23:58 DEBUG  WindowsBackend: uninstaller_path=None
10-17 23:58 DEBUG  WindowsBackend: previous_target_dir=None
10-17 23:58 DEBUG  WindowsBackend: previous_distro_name=None
10-17 23:58 DEBUG  WindowsBackend: keyboard_id=67699721
10-17 23:58 DEBUG  WindowsBackend: keyboard_layout=us
10-17 23:58 DEBUG  WindowsBackend: keyboard_variant=
10-17 23:58 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-17 23:58 DEBUG  CommonBackend: locale=en_US.UTF-8
10-17 23:58 DEBUG  WindowsBackend: total_memory_mb=3837.82421875
10-17 23:58 DEBUG  CommonBackend: Searching ISOs on USB devices
10-17 23:58 DEBUG  CommonBackend: Searching for local CDs
10-17 23:58 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp is a valid Ubuntu CD
10-17 23:58 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp is a valid Ubuntu CD
10-17 23:58 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp is a valid Ubuntu Netbook CD
10-17 23:58 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp is a valid Kubuntu CD
10-17 23:58 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp is a valid Kubuntu CD
10-17 23:58 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp is a valid Xubuntu CD
10-17 23:58 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp is a valid Xubuntu CD
10-17 23:58 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp is a valid Mythbuntu CD
10-17 23:58 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp is a valid Mythbuntu CD
10-17 23:58 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-17 23:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-17 23:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-17 23:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-17 23:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-17 23:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-17 23:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-17 23:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-17 23:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-17 23:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-17 23:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-17 23:59 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
10-17 23:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
10-17 23:59 INFO   Distro: Found a valid CD for Ubuntu: E:\
10-17 23:59 INFO   root: Running the CD menu...
10-17 23:59 DEBUG  WindowsFrontend: __init__...
10-17 23:59 DEBUG  WindowsFrontend: on_init...
10-17 23:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\translations, languages=['en_US', 'en']
10-17 23:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\translations, languages=['en_US', 'en']
10-17 23:59 INFO   root: CD menu finished
10-17 23:59 INFO   root: Running the installer...
10-17 23:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\translations, languages=['en_US', 'en']
10-17 23:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\translations, languages=['en_US', 'en']
10-18 00:00 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=15000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jo53_4
10-18 00:00 INFO   root: Received settings
10-18 00:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\translations, languages=['en_US', 'en']
10-18 00:00 DEBUG  TaskList: # Running tasklist...
10-18 00:00 DEBUG  TaskList: ## Running select_target_dir...
10-18 00:00 INFO   WindowsBackend: Installing into C:\ubuntu
10-18 00:00 DEBUG  TaskList: ## Finished select_target_dir
10-18 00:00 DEBUG  TaskList: ## Running create_dir_structure...
10-18 00:00 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-18 00:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-18 00:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-18 00:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-18 00:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-18 00:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-18 00:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-18 00:00 DEBUG  TaskList: ## Finished create_dir_structure
10-18 00:00 DEBUG  TaskList: ## Running uncompress_target_dir...
10-18 00:00 DEBUG  TaskList: ## Finished uncompress_target_dir
10-18 00:00 DEBUG  TaskList: ## Running create_uninstaller...
10-18 00:00 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-18 00:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-18 00:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-18 00:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-18 00:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-18 00:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
10-18 00:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-18 00:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
10-18 00:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
10-18 00:00 DEBUG  TaskList: ## Finished create_uninstaller
10-18 00:00 DEBUG  TaskList: ## Running copy_installation_files...
10-18 00:00 DEBUG  WindowsBackend: Copying C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-18 00:00 DEBUG  WindowsBackend: Copying C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\winboot -> C:\ubuntu\winboot
10-18 00:00 DEBUG  WindowsBackend: Copying C:\Users\JO53_4\AppData\Local\Temp\pylA073.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-18 00:00 DEBUG  TaskList: ## Finished copy_installation_files
10-18 00:00 DEBUG  TaskList: ## Running get_iso...
10-18 00:00 DEBUG  TaskList: New task copy_file
10-18 00:00 DEBUG  TaskList: ### Running copy_file...
10-18 00:04 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
10-18 00:04 DEBUG  TaskList: # Cancelling tasklist
10-18 00:04 DEBUG  TaskList: New task check_iso
10-18 00:04 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
10-18 00:04 DEBUG  CommonBackend: Searching for local ISO
10-18 00:04 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-18 00:04 DEBUG  TaskList: New task get_metalink
10-18 00:04 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-18 00:04 DEBUG  TaskList: # Cancelling tasklist
10-18 00:04 DEBUG  TaskList: # Finished tasklist

```

---

### Post by jo53_4 on 2011-10-18
ubuntu 11.10 in case you may want to compare them, thanks

```
10-16 21:14 INFO   root: === wubi 11.10 rev241 ===
10-16 21:14 DEBUG  root: Logfile is c:\users\jo53_4\appdata\local\temp\wubi-11.10-rev241.log
10-16 21:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
10-16 21:14 DEBUG  CommonBackend: data_dir=C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\data
10-16 21:14 DEBUG  WindowsBackend: 7z=C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\bin\7z.exe
10-16 21:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-16 21:14 DEBUG  CommonBackend: Fetching basic info...
10-16 21:14 DEBUG  CommonBackend: original_exe=E:\wubi.exe
10-16 21:14 DEBUG  CommonBackend: platform=win32
10-16 21:14 DEBUG  CommonBackend: osname=nt
10-16 21:14 DEBUG  CommonBackend: language=en_US
10-16 21:14 DEBUG  CommonBackend: encoding=cp1252
10-16 21:14 DEBUG  WindowsBackend: arch=amd64
10-16 21:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\data\isolist.ini
10-16 21:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-16 21:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-16 21:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-16 21:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-16 21:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-16 21:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-16 21:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-16 21:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-16 21:14 DEBUG  WindowsBackend: Fetching host info...
10-16 21:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-16 21:14 DEBUG  WindowsBackend: windows version=vista
10-16 21:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-16 21:14 DEBUG  WindowsBackend: windows_sp=None
10-16 21:14 DEBUG  WindowsBackend: windows_build=7601
10-16 21:14 DEBUG  WindowsBackend: gmt=-4
10-16 21:14 DEBUG  WindowsBackend: country=US
10-16 21:14 DEBUG  WindowsBackend: timezone=America/New_York
10-16 21:14 DEBUG  WindowsBackend: windows_username=JO53_4
10-16 21:14 DEBUG  WindowsBackend: user_full_name=JO53_4
10-16 21:14 DEBUG  WindowsBackend: user_directory=C:\Users\JO53_4
10-16 21:14 DEBUG  WindowsBackend: windows_language_code=1033
10-16 21:14 DEBUG  WindowsBackend: windows_language=English
10-16 21:14 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
10-16 21:14 DEBUG  WindowsBackend: bootloader=vista
10-16 21:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 333558.871094 mb free ntfs)
10-16 21:14 DEBUG  WindowsBackend: drive=Drive(C: hd 333558.871094 mb free ntfs)
10-16 21:14 DEBUG  WindowsBackend: drive=Drive(D: hd 2068.62890625 mb free ntfs)
10-16 21:14 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
10-16 21:14 DEBUG  WindowsBackend: uninstaller_path=None
10-16 21:14 DEBUG  WindowsBackend: previous_target_dir=None
10-16 21:14 DEBUG  WindowsBackend: previous_distro_name=None
10-16 21:14 DEBUG  WindowsBackend: keyboard_id=67699721
10-16 21:14 DEBUG  WindowsBackend: keyboard_layout=us
10-16 21:14 DEBUG  WindowsBackend: keyboard_variant=
10-16 21:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-16 21:14 DEBUG  CommonBackend: locale=en_US.UTF-8
10-16 21:14 DEBUG  WindowsBackend: total_memory_mb=3837.82421875
10-16 21:14 DEBUG  CommonBackend: Searching ISOs on USB devices
10-16 21:14 DEBUG  CommonBackend: Searching for local CDs
10-16 21:14 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp is a valid Ubuntu CD
10-16 21:14 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp is a valid Ubuntu CD
10-16 21:14 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp is a valid Kubuntu CD
10-16 21:14 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp is a valid Kubuntu CD
10-16 21:14 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp is a valid Xubuntu CD
10-16 21:14 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp is a valid Xubuntu CD
10-16 21:14 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp is a valid Mythbuntu CD
10-16 21:14 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp is a valid Mythbuntu CD
10-16 21:14 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 21:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 21:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 21:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 21:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-16 21:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-16 21:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 21:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 21:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-16 21:14 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
10-16 21:14 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
10-16 21:14 INFO   Distro: Found a valid CD for Ubuntu: E:\
10-16 21:14 INFO   root: Running the CD menu...
10-16 21:14 DEBUG  WindowsFrontend: __init__...
10-16 21:14 DEBUG  WindowsFrontend: on_init...
10-16 21:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\translations, languages=['en_US', 'en']
10-16 21:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\translations, languages=['en_US', 'en']
10-16 21:15 INFO   root: CD menu finished
10-16 21:15 INFO   root: Running the installer...
10-16 21:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\translations, languages=['en_US', 'en']
10-16 21:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\translations, languages=['en_US', 'en']
10-16 21:15 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=15000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jo53_4
10-16 21:15 INFO   root: Received settings
10-16 21:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\translations, languages=['en_US', 'en']
10-16 21:15 DEBUG  TaskList: # Running tasklist...
10-16 21:15 DEBUG  TaskList: ## Running select_target_dir...
10-16 21:15 INFO   WindowsBackend: Installing into C:\ubuntu
10-16 21:15 DEBUG  TaskList: ## Finished select_target_dir
10-16 21:15 DEBUG  TaskList: ## Running create_dir_structure...
10-16 21:15 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-16 21:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-16 21:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-16 21:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-16 21:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-16 21:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-16 21:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-16 21:15 DEBUG  TaskList: ## Finished create_dir_structure
10-16 21:15 DEBUG  TaskList: ## Running uncompress_target_dir...
10-16 21:15 DEBUG  TaskList: ## Finished uncompress_target_dir
10-16 21:15 DEBUG  TaskList: ## Running create_uninstaller...
10-16 21:15 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-16 21:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-16 21:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-16 21:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-16 21:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-16 21:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
10-16 21:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-16 21:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
10-16 21:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
10-16 21:15 DEBUG  TaskList: ## Finished create_uninstaller
10-16 21:15 DEBUG  TaskList: ## Running copy_installation_files...
10-16 21:15 DEBUG  WindowsBackend: Copying C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-16 21:15 DEBUG  WindowsBackend: Copying C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\winboot -> C:\ubuntu\winboot
10-16 21:15 DEBUG  WindowsBackend: Copying C:\Users\JO53_4\AppData\Local\Temp\pyl1370.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-16 21:15 DEBUG  TaskList: ## Finished copy_installation_files
10-16 21:15 DEBUG  TaskList: ## Running get_iso...
10-16 21:15 DEBUG  TaskList: New task copy_file
10-16 21:15 DEBUG  TaskList: ### Running copy_file...
10-16 21:20 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 202, in copy_file
IOError: [Errno 13] Permission denied
10-16 21:20 DEBUG  TaskList: # Cancelling tasklist
10-16 21:20 DEBUG  TaskList: New task check_iso
10-16 21:20 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 202, in copy_file
IOError: [Errno 13] Permission denied
10-16 21:20 ERROR  TaskList: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
10-16 21:20 DEBUG  TaskList: # Cancelling tasklist
10-16 21:20 DEBUG  TaskList: # Finished tasklist
10-16 21:22 INFO   root: === wubi 11.10 rev241 ===
10-16 21:22 DEBUG  root: Logfile is c:\users\jo53_4\appdata\local\temp\wubi-11.10-rev241.log
10-16 21:22 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
10-16 21:22 DEBUG  CommonBackend: data_dir=C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp\data
10-16 21:22 DEBUG  WindowsBackend: 7z=C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp\bin\7z.exe
10-16 21:22 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-16 21:22 DEBUG  CommonBackend: Fetching basic info...
10-16 21:22 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
10-16 21:22 DEBUG  CommonBackend: platform=win32
10-16 21:22 DEBUG  CommonBackend: osname=nt
10-16 21:22 DEBUG  CommonBackend: language=en_US
10-16 21:22 DEBUG  CommonBackend: encoding=cp1252
10-16 21:22 DEBUG  WindowsBackend: arch=amd64
10-16 21:22 DEBUG  CommonBackend: Parsing isolist=C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp\data\isolist.ini
10-16 21:22 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-16 21:22 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-16 21:22 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-16 21:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-16 21:22 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-16 21:22 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-16 21:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-16 21:22 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-16 21:22 DEBUG  WindowsBackend: Fetching host info...
10-16 21:22 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-16 21:22 DEBUG  WindowsBackend: windows version=vista
10-16 21:22 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
10-16 21:22 DEBUG  WindowsBackend: windows_sp=None
10-16 21:22 DEBUG  WindowsBackend: windows_build=7601
10-16 21:22 DEBUG  WindowsBackend: gmt=-4
10-16 21:22 DEBUG  WindowsBackend: country=US
10-16 21:22 DEBUG  WindowsBackend: timezone=America/New_York
10-16 21:22 DEBUG  WindowsBackend: windows_username=JO53_4
10-16 21:22 DEBUG  WindowsBackend: user_full_name=JO53_4
10-16 21:22 DEBUG  WindowsBackend: user_directory=C:\Users\JO53_4
10-16 21:22 DEBUG  WindowsBackend: windows_language_code=1033
10-16 21:22 DEBUG  WindowsBackend: windows_language=English
10-16 21:22 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
10-16 21:22 DEBUG  WindowsBackend: bootloader=vista
10-16 21:22 DEBUG  WindowsBackend: system_drive=Drive(C: hd 332860.195313 mb free ntfs)
10-16 21:22 DEBUG  WindowsBackend: drive=Drive(C: hd 332860.195313 mb free ntfs)
10-16 21:22 DEBUG  WindowsBackend: drive=Drive(D: hd 2068.62890625 mb free ntfs)
10-16 21:22 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-16 21:22 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-16 21:22 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-16 21:22 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-16 21:22 DEBUG  WindowsBackend: keyboard_id=67699721
10-16 21:22 DEBUG  WindowsBackend: keyboard_layout=us
10-16 21:22 DEBUG  WindowsBackend: keyboard_variant=
10-16 21:22 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-16 21:22 DEBUG  CommonBackend: locale=en_US.UTF-8
10-16 21:22 DEBUG  WindowsBackend: total_memory_mb=3837.82421875
10-16 21:22 DEBUG  CommonBackend: Searching ISOs on USB devices
10-16 21:22 DEBUG  CommonBackend: Searching for local CDs
10-16 21:22 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp is a valid Ubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp is a valid Ubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp is a valid Kubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp is a valid Kubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp is a valid Xubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp is a valid Xubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp is a valid Mythbuntu CD
10-16 21:22 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp is a valid Mythbuntu CD
10-16 21:22 DEBUG  Distro:     does not contain C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 21:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-16 21:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-16 21:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-16 21:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 21:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-16 21:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-16 21:22 INFO   root: Running the uninstaller...
10-16 21:22 INFO   CommonBackend: This is the uninstaller running
10-16 21:22 DEBUG  WindowsFrontend: __init__...
10-16 21:22 DEBUG  WindowsFrontend: on_init...
10-16 21:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp\translations, languages=['en_US', 'en']
10-16 21:22 INFO   root: Received settings
10-16 21:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp\translations, languages=['en_US', 'en']
10-16 21:22 DEBUG  TaskList: # Running tasklist...
10-16 21:22 DEBUG  TaskList: ## Running Remove bootloader entry...
10-16 21:22 DEBUG  WindowsBackend: Could not find bcd id
10-16 21:22 DEBUG  WindowsBackend: undo_bootini C:
10-16 21:22 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 332860.195313 mb free ntfs)
10-16 21:22 DEBUG  WindowsBackend: undo_bootini D:
10-16 21:22 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2068.62890625 mb free ntfs)
10-16 21:22 DEBUG  TaskList: ## Finished Remove bootloader entry
10-16 21:22 DEBUG  TaskList: ## Running Remove target dir...
10-16 21:22 DEBUG  CommonBackend: Deleting C:\ubuntu
10-16 21:22 DEBUG  TaskList: ## Finished Remove target dir
10-16 21:22 DEBUG  TaskList: ## Running Remove registry key...
10-16 21:22 DEBUG  TaskList: ## Finished Remove registry key
10-16 21:22 DEBUG  TaskList: # Finished tasklist
10-16 21:22 INFO   root: Almost finished uninstalling
10-16 21:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JO53_4\AppData\Local\Temp\pyl5BC5.tmp\translations, languages=['en_US', 'en']
10-16 21:22 INFO   root: Finished uninstallation
10-16 21:22 DEBUG  root: application.quit
10-16 21:22 DEBUG  WindowsFrontend: frontend.quit
10-16 21:22 DEBUG  WindowsFrontend: frontend.on_quit
10-16 21:22 DEBUG  root: application.on_quit
10-16 21:22 INFO   root: sys.exit

```

---

### Post by dFlyer on 2011-10-18
Did you install wubi or the live cd?
Why not install a truly dual boot system?

---

### Post by bcbc on 2011-10-18
Both of them indicate errors when copying the ISO from the CD to the local drive. Wubi copies the ISO before running the md5 check so I can't say exactly why the copy failed. A bad burn is likely though (this is relatively common).

So... I'd suggest to follow closely the instructions here: [www.ubuntu.com/download/ubuntu/download](www.ubuntu.com/download/ubuntu/download) (step 2, Show me how) or create a bootable USB. This is useful to install a real dual boot (which is a good idea - but wubi is great to try out Ubuntu easily).

In fact Wubi doesn't require the CD or USB - just download the ISO, place it in the same directory as wubi.exe, make sure you remove the bad CD's from the computer first, and run wubi. Then it will find the iso and use it.
The only caveat is that the wubi.exe version must match the ISO, so get them from the same place:
11.04: [http://releases.ubuntu.com/11.04/](http://releases.ubuntu.com/11.04/)
11.10: [http://releases.ubuntu.com/11.10/](http://releases.ubuntu.com/11.10/)

---

### Post by jo53_4 on 2011-10-18
> **dFlyer said:**
> Did you install wubi or the live cd?
Why not install a truly dual boot system?

wubi on the ubuntu iso i burned to a cd

dual boot? I am a noob, i dont know how :( sorry

when i was on middle school i used to get ubuntu cd s trough ship it 
and i used to boot them on my moms pc

now that im almost finishing my bachelor s degree i really depend on my laptop for most of the classes. im tired of windows so i thought i could just install ubuntu on windows with wubi

use ubuntu for everything and windows just for office, but no luck

thanks for answering my post :)

---

### Post by jo53_4 on 2011-10-18
> **bcbc said:**
> Both of them indicate errors when copying the ISO from the CD to the local drive. Wubi copies the ISO before running the md5 check so I can't say exactly why the copy failed. A bad burn is likely though (this is relatively common).

So... I'd suggest to follow closely the instructions here: [www.ubuntu.com/download/ubuntu/download](www.ubuntu.com/download/ubuntu/download) (step 2, Show me how) or create a bootable USB. This is useful to install a real dual boot (which is a good idea - but wubi is great to try out Ubuntu easily).

In fact Wubi doesn't require the CD or USB - just download the ISO, place it in the same directory as wubi.exe, make sure you remove the bad CD's from the computer first, and run wubi. Then it will find the iso and use it.
The only caveat is that the wubi.exe version must match the ISO, so get them from the same place:
11.04: [http://releases.ubuntu.com/11.04/](http://releases.ubuntu.com/11.04/)
11.10: [http://releases.ubuntu.com/11.10/](http://releases.ubuntu.com/11.10/)

tried kubuntu and the same happened, dont know whats wrong,thanks for the tips ill download the iso s again along with wubi and then try

---

### Post by sailthesea on 2011-10-18
> **jo53_4 said:**
> wubi on the ubuntu iso i burned to a cd

dual boot? I am a noob, i dont know how :( sorry

when i was on middle school i used to get ubuntu cd s trough ship it 
and i used to boot them on my moms pc

now that im almost finishing my bachelor s degree i really depend on my laptop for most of the classes. im tired of windows so **i thought i could just install ubuntu on windows with wubi**

use ubuntu for everything and windows just for office, but no luck

thanks for answering my post :)

 That's pretty much how Wubi works, If you ditch the cd for now and simply download Wubi in to your Windows install and ensure you have the correct version it will run within Windows (As detailed above).
 I know in the past Wubi has been a little behind the Ubuntu release as there usually technical issues to address.
 On the other hand the CD you have may be live session enabled try booting from it as you did previously, try without installing first. Dual booting isn't too hard if you follow the various guides availiable and the instructions on the installer itself. 

** DON'T try this without having made complete backups of everything however**
 I can never stress that enough 

Good luck and don't give up.

---

### Post by jo53_4 on 2011-10-18
> **sailthesea said:**
> That's pretty much how Wubi works, If you ditch the cd for now and simply download Wubi in to your Windows install and ensure you have the correct version it will run within Windows (As detailed above).
 I know in the past Wubi has been a little behind the Ubuntu release as there usually technical issues to address.
 On the other hand the CD you have may be live session enabled try booting from it as you did previously, try without installing first. Dual booting isn't too hard if you follow the various guides availiable and the instructions on the installer itself. 

** DON'T try this without having made complete backups of everything however**
 I can never stress that enough 

Good luck and don't give up.

thanks, i ll do that

---

### Post by jo53_4 on 2011-10-18
thank you all for your help

I have downloaded wubi 11.04 and ubuntu 11.04 after 15 minutes of searching for them:(

they are on the same folder and everything worked so i guess this post its solved:D

still the main reason i wanted to install wubi and ubuntu from the CD was because that way i could give the cds to my friends who know even less of this than me so they could try it on their pc s, hope the cds work on theirs

thanks, for everything

---

### Post by Cruzgerman216 on 2012-02-20
> **bcbc said:**
> Look in the %temp% directory - post the contents of wubi-11.10-rev241.log here between [CODE [SIZE="1"][/SIZE]][/CODE] tags (click on # above)


where do we put %temp% ?

---

