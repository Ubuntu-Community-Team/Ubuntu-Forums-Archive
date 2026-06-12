---
title: "Ubuntu 9.10 / Win 7 x64 OEM"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by Booster2ooo on 2009-12-13
Hello,

I'm trying to install Ubuntu 9.10 using Wubi on my Windows 7 x64 (OEM version). Unfortunatly, the installer displays an error at the end of files extraction: Invalid Arguments. I tried to run the install as an administrator, using Vista compatibility, shutting down my avg, didn't work. I though it might be a problem due to Active Python so I tried again after uninstalling A.Python but I still have the same result. Here is the .log file:

[quote="wubi-9.10ubuntu1-rev160.log"]12-13 10:35 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-13 10:35 DEBUG  root: Logfile is c:\users\booster\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-13 10:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
12-13 10:35 DEBUG  CommonBackend: data_dir=C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\data
12-13 10:35 DEBUG  WindowsBackend: 7z=C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\bin\7z.exe
12-13 10:35 DEBUG  CommonBackend: Fetching basic info...
12-13 10:35 DEBUG  CommonBackend: original_exe=F:\wubi.exe
12-13 10:35 DEBUG  CommonBackend: platform=win32
12-13 10:35 DEBUG  CommonBackend: osname=nt
12-13 10:35 DEBUG  CommonBackend: language=fr_BE
12-13 10:35 DEBUG  CommonBackend: encoding=cp1252
12-13 10:35 DEBUG  WindowsBackend: arch=amd64
12-13 10:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\data\isolist.ini
12-13 10:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-13 10:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-13 10:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-13 10:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-13 10:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-13 10:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-13 10:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-13 10:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-13 10:35 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-13 10:35 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-13 10:35 DEBUG  WindowsBackend: Fetching host info...
12-13 10:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-13 10:35 DEBUG  WindowsBackend: windows version=vista
12-13 10:35 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
12-13 10:35 DEBUG  WindowsBackend: windows_sp=None
12-13 10:35 DEBUG  WindowsBackend: windows_build=6000
12-13 10:35 DEBUG  WindowsBackend: gmt=1
12-13 10:35 DEBUG  WindowsBackend: country=IT
12-13 10:35 DEBUG  WindowsBackend: timezone=Europe/Rome
12-13 10:35 DEBUG  WindowsBackend: windows_username=Booster
12-13 10:35 DEBUG  WindowsBackend: user_full_name=Booster
12-13 10:35 DEBUG  WindowsBackend: user_directory=C:\Users\Booster
12-13 10:35 DEBUG  WindowsBackend: windows_language_code=1036
12-13 10:35 DEBUG  WindowsBackend: windows_language=French
12-13 10:35 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz
12-13 10:35 DEBUG  WindowsBackend: bootloader=vista
12-13 10:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 43896.5390625 mb free ntfs)
12-13 10:35 DEBUG  WindowsBackend: drive=Drive(C: hd 43896.5390625 mb free ntfs)
12-13 10:35 DEBUG  WindowsBackend: drive=Drive(D: hd 98168.4609375 mb free ntfs)
12-13 10:35 DEBUG  WindowsBackend: drive=Drive(E: hd 205052.019531 mb free ntfs)
12-13 10:35 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
12-13 10:35 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
12-13 10:35 DEBUG  WindowsBackend: uninstaller_path=None
12-13 10:35 DEBUG  WindowsBackend: previous_target_dir=None
12-13 10:35 DEBUG  WindowsBackend: previous_distro_name=None
12-13 10:35 DEBUG  WindowsBackend: keyboard_id=135464972
12-13 10:35 DEBUG  WindowsBackend: keyboard_layout=it
12-13 10:35 DEBUG  WindowsBackend: keyboard_variant=
12-13 10:35 DEBUG  CommonBackend: python locale=('fr_BE', 'cp1252')
12-13 10:35 DEBUG  CommonBackend: locale=fr_BE.UTF-8
12-13 10:35 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
12-13 10:35 DEBUG  CommonBackend: Searching ISOs on USB devices
12-13 10:35 DEBUG  CommonBackend: Searching for local CDs
12-13 10:35 DEBUG  Distro:   checking whether C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp is a valid Ubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp is a valid Ubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp is a valid Ubuntu Netbook Remix CD
12-13 10:35 DEBUG  Distro:     does not contain C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp is a valid Kubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp is a valid Kubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp is a valid Kubuntu Netbook CD
12-13 10:35 DEBUG  Distro:     does not contain C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp is a valid Xubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp is a valid Xubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp is a valid Mythbuntu CD
12-13 10:35 DEBUG  Distro:     does not contain C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp is a valid Mythbuntu CD
12-13 10:35 DEBUG  Distro:     does not contain C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-13 10:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-13 10:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-13 10:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-13 10:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
12-13 10:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-13 10:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-13 10:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-13 10:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-13 10:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-13 10:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-13 10:35 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
12-13 10:35 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
12-13 10:35 INFO   Distro: Found a valid CD for Ubuntu: F:\
12-13 10:35 INFO   root: Running the CD menu...
12-13 10:35 DEBUG  WindowsFrontend: __init__...
12-13 10:35 DEBUG  WindowsFrontend: on_init...
12-13 10:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\translations, languages=['fr_BE', 'fr']
12-13 10:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\translations, languages=['fr_BE', 'fr']
12-13 10:35 INFO   root: CD menu finished
12-13 10:35 INFO   root: Running the installer...
12-13 10:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\translations, languages=['fr_BE', 'fr']
12-13 10:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\translations, languages=['fr_BE', 'fr']
12-13 10:35 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=fr_FR, locale=fr_FR.UTF-8, username=booster
12-13 10:35 INFO   root: Received settings
12-13 10:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\translations, languages=['fr_FR', 'fr']
12-13 10:35 DEBUG  TaskList: # Running tasklist...
12-13 10:35 DEBUG  TaskList: ## Running select_target_dir...
12-13 10:35 INFO   WindowsBackend: Installing into C:\ubuntu
12-13 10:35 DEBUG  TaskList: ## Finished select_target_dir
12-13 10:35 DEBUG  TaskList: ## Running create_dir_structure...
12-13 10:35 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-13 10:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-13 10:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-13 10:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-13 10:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-13 10:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-13 10:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-13 10:35 DEBUG  TaskList: ## Finished create_dir_structure
12-13 10:35 DEBUG  TaskList: ## Running uncompress_target_dir...
12-13 10:35 DEBUG  TaskList: ## Finished uncompress_target_dir
12-13 10:35 DEBUG  TaskList: ## Running create_uninstaller...
12-13 10:35 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-13 10:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-13 10:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-13 10:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-13 10:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-13 10:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
12-13 10:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-13 10:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-13 10:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-13 10:35 DEBUG  TaskList: ## Finished create_uninstaller
12-13 10:35 DEBUG  TaskList: ## Running copy_installation_files...
12-13 10:35 DEBUG  WindowsBackend: Copying C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
12-13 10:35 DEBUG  WindowsBackend: Copying C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\winboot -> C:\ubuntu\winboot
12-13 10:35 DEBUG  WindowsBackend: Copying C:\Users\Booster\AppData\Local\Temp\pylDB03.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
12-13 10:35 DEBUG  TaskList: ## Finished copy_installation_files
12-13 10:35 DEBUG  TaskList: ## Running get_iso...
12-13 10:35 DEBUG  TaskList: New task copy_file
12-13 10:35 DEBUG  TaskList: ### Running copy_file...
12-13 10:40 DEBUG  TaskList: ### Finished copy_file
[COLOR=red]12-13 10:40 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
12-13 10:40 DEBUG  TaskList: # Cancelling tasklist
12-13 10:40 DEBUG  TaskList: New task check_iso
12-13 10:40 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
12-13 10:40 DEBUG  CommonBackend: Searching for local ISO
12-13 10:40 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-13 10:40 DEBUG  TaskList: New task get_metalink
12-13 10:40 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO[/COLOR]
12-13 10:40 DEBUG  TaskList: # Cancelling tasklist
12-13 10:40 DEBUG  TaskList: # Finished tasklist
[/quote]


Does anybody know a solution?
Thx

---

### Post by Booster2ooo on 2009-12-13
[COLOR=DarkGreen]SOLVED:[/COLOR]

I read some post on Google, here is how I solved this problem:
- Download last wubi.exe
- Get an ISO of Ubuntu
- Put wubi.exe and the ISO in the same dir
- Run wubi, continue when runpy.exe says that there is no CD

Anyway, it's still wierd we cannot install it from the CD ...

---

