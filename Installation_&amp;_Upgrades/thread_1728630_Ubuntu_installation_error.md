---
title: "Ubuntu installation error"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by LLOORREENNN on 2011-04-14
Hi, I recently mounted the Ubuntu.iso (64Bit) and mounted it as a virtual drive, and launched the file wubi.exe to start the installation. I am then prompted with a window giving me 3 options. I chose "Install inside Windows". After a few seconds I get an error. "An error occured: Invalid argument. For more information, please see the log file c:\users\loren\appdata\temp\wubi-10.10-rev197.log" Here is the contents of wubi-10.10-rev197.log... yes, I also tried to install linux mint, and got the same error....

04-13 18:24 INFO   root: === wubi 10.10 rev197 ===
04-13 18:24 DEBUG  root: Logfile is c:\users\loren\appdata\local\temp\wubi-10.10-rev197.log
04-13 18:24 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
04-13 18:24 DEBUG  CommonBackend: data_dir=C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\data
04-13 18:24 DEBUG  WindowsBackend: 7z=C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\bin\7z.exe
04-13 18:24 DEBUG  CommonBackend: Fetching basic info...
04-13 18:24 DEBUG  CommonBackend: original_exe=E:\wubi.exe
04-13 18:24 DEBUG  CommonBackend: platform=win32
04-13 18:24 DEBUG  CommonBackend: osname=nt
04-13 18:24 DEBUG  CommonBackend: language=en_CA
04-13 18:24 DEBUG  CommonBackend: encoding=cp1252
04-13 18:24 DEBUG  WindowsBackend: arch=amd64
04-13 18:24 DEBUG  CommonBackend: Parsing isolist=C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\data\isolist.ini
04-13 18:24 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-13 18:24 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-13 18:24 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-13 18:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-13 18:24 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-13 18:24 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-13 18:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-13 18:24 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-13 18:24 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-13 18:24 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-13 18:24 DEBUG  WindowsBackend: Fetching host info...
04-13 18:24 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-13 18:24 DEBUG  WindowsBackend: windows version=vista
04-13 18:24 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-13 18:24 DEBUG  WindowsBackend: windows_sp=None
04-13 18:24 DEBUG  WindowsBackend: windows_build=7600
04-13 18:24 DEBUG  WindowsBackend: gmt=-8
04-13 18:24 DEBUG  WindowsBackend: country=CA
04-13 18:24 DEBUG  WindowsBackend: timezone=America/Vancouver
04-13 18:24 DEBUG  WindowsBackend: windows_username=Loren
04-13 18:24 DEBUG  WindowsBackend: user_full_name=Loren
04-13 18:24 DEBUG  WindowsBackend: user_directory=C:\Users\Loren
04-13 18:24 DEBUG  WindowsBackend: windows_language_code=1033
04-13 18:24 DEBUG  WindowsBackend: windows_language=English
04-13 18:24 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz
04-13 18:24 DEBUG  WindowsBackend: bootloader=vista
04-13 18:24 DEBUG  WindowsBackend: system_drive=Drive(C: hd 580301.773438 mb free ntfs)
04-13 18:24 DEBUG  WindowsBackend: drive=Drive(C: hd 580301.773438 mb free ntfs)
04-13 18:24 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-13 18:24 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-13 18:24 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
04-13 18:24 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
04-13 18:24 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
04-13 18:24 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
04-13 18:24 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
04-13 18:24 DEBUG  WindowsBackend: uninstaller_path=None
04-13 18:24 DEBUG  WindowsBackend: previous_target_dir=None
04-13 18:24 DEBUG  WindowsBackend: previous_distro_name=None
04-13 18:24 DEBUG  WindowsBackend: keyboard_id=67702793
04-13 18:24 DEBUG  WindowsBackend: keyboard_layout=us
04-13 18:24 DEBUG  WindowsBackend: keyboard_variant=
04-13 18:24 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
04-13 18:24 DEBUG  CommonBackend: locale=en_CA.UTF-8
04-13 18:24 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
04-13 18:24 DEBUG  CommonBackend: Searching ISOs on USB devices
04-13 18:24 DEBUG  CommonBackend: Searching for local CDs
04-13 18:24 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp is a valid Ubuntu CD
04-13 18:24 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp is a valid Ubuntu CD
04-13 18:24 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp is a valid Ubuntu Netbook CD
04-13 18:24 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp is a valid Kubuntu CD
04-13 18:24 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp is a valid Kubuntu CD
04-13 18:24 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp is a valid Kubuntu Netbook CD
04-13 18:24 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp is a valid Xubuntu CD
04-13 18:24 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp is a valid Xubuntu CD
04-13 18:24 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp is a valid Mythbuntu CD
04-13 18:24 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp is a valid Mythbuntu CD
04-13 18:24 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-13 18:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-13 18:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-13 18:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-13 18:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-13 18:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-13 18:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-13 18:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-13 18:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-13 18:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-13 18:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 18:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-13 18:24 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
04-13 18:24 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
04-13 18:24 INFO   Distro: Found a valid CD for Ubuntu: E:\
04-13 18:24 INFO   root: Running the CD menu...
04-13 18:24 DEBUG  WindowsFrontend: __init__...
04-13 18:24 DEBUG  WindowsFrontend: on_init...
04-13 18:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\translations, languages=['en_CA', 'en']
04-13 18:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\translations, languages=['en_CA', 'en']
04-13 18:24 INFO   root: CD menu finished
04-13 18:24 INFO   root: Running the installer...
04-13 18:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\translations, languages=['en_CA', 'en']
04-13 18:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\translations, languages=['en_CA', 'en']
04-13 18:24 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=loren
04-13 18:24 INFO   root: Received settings
04-13 18:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\translations, languages=['en_US', 'en']
04-13 18:24 DEBUG  TaskList: # Running tasklist...
04-13 18:24 DEBUG  TaskList: ## Running select_target_dir...
04-13 18:24 INFO   WindowsBackend: Installing into C:\ubuntu
04-13 18:24 DEBUG  TaskList: ## Finished select_target_dir
04-13 18:24 DEBUG  TaskList: ## Running create_dir_structure...
04-13 18:24 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-13 18:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-13 18:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-13 18:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-13 18:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-13 18:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-13 18:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-13 18:24 DEBUG  TaskList: ## Finished create_dir_structure
04-13 18:24 DEBUG  TaskList: ## Running uncompress_target_dir...
04-13 18:24 DEBUG  TaskList: ## Finished uncompress_target_dir
04-13 18:24 DEBUG  TaskList: ## Running create_uninstaller...
04-13 18:24 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-13 18:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-13 18:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-13 18:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-13 18:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-13 18:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-13 18:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-13 18:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-13 18:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-13 18:24 DEBUG  TaskList: ## Finished create_uninstaller
04-13 18:24 DEBUG  TaskList: ## Running copy_installation_files...
04-13 18:24 DEBUG  WindowsBackend: Copying C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-13 18:24 DEBUG  WindowsBackend: Copying C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\winboot -> C:\ubuntu\winboot
04-13 18:24 DEBUG  WindowsBackend: Copying C:\Users\Loren\AppData\Local\Temp\pyl1142.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-13 18:24 DEBUG  TaskList: ## Finished copy_installation_files
04-13 18:24 DEBUG  TaskList: ## Running get_iso...
04-13 18:24 DEBUG  TaskList: New task copy_file
04-13 18:24 DEBUG  TaskList: ### Running copy_file...
04-13 18:24 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
04-13 18:24 DEBUG  TaskList: # Cancelling tasklist
04-13 18:24 DEBUG  TaskList: New task check_iso
04-13 18:24 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
04-13 18:24 DEBUG  CommonBackend: Searching for local ISO
04-13 18:24 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-13 18:24 DEBUG  TaskList: New task get_metalink
04-13 18:24 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-13 18:24 DEBUG  TaskList: # Cancelling tasklist
04-13 18:24 DEBUG  TaskList: # Finished tasklist
04-13 20:44 INFO   root: === wubi 10.10 rev197 ===
04-13 20:44 DEBUG  root: Logfile is c:\users\loren\appdata\local\temp\wubi-10.10-rev197.log
04-13 20:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
04-13 20:44 DEBUG  CommonBackend: data_dir=C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\data
04-13 20:44 DEBUG  WindowsBackend: 7z=C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\bin\7z.exe
04-13 20:44 DEBUG  CommonBackend: Fetching basic info...
04-13 20:44 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-13 20:44 DEBUG  CommonBackend: platform=win32
04-13 20:44 DEBUG  CommonBackend: osname=nt
04-13 20:44 DEBUG  CommonBackend: language=en_CA
04-13 20:44 DEBUG  CommonBackend: encoding=cp1252
04-13 20:44 DEBUG  WindowsBackend: arch=amd64
04-13 20:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\data\isolist.ini
04-13 20:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-13 20:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-13 20:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-13 20:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-13 20:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-13 20:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-13 20:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-13 20:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-13 20:44 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-13 20:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-13 20:44 DEBUG  WindowsBackend: Fetching host info...
04-13 20:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-13 20:44 DEBUG  WindowsBackend: windows version=vista
04-13 20:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-13 20:44 DEBUG  WindowsBackend: windows_sp=None
04-13 20:44 DEBUG  WindowsBackend: windows_build=7600
04-13 20:44 DEBUG  WindowsBackend: gmt=-8
04-13 20:44 DEBUG  WindowsBackend: country=CA
04-13 20:44 DEBUG  WindowsBackend: timezone=America/Vancouver
04-13 20:44 DEBUG  WindowsBackend: windows_username=Loren
04-13 20:44 DEBUG  WindowsBackend: user_full_name=Loren
04-13 20:44 DEBUG  WindowsBackend: user_directory=C:\Users\Loren
04-13 20:44 DEBUG  WindowsBackend: windows_language_code=1033
04-13 20:44 DEBUG  WindowsBackend: windows_language=English
04-13 20:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz
04-13 20:44 DEBUG  WindowsBackend: bootloader=vista
04-13 20:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 578800.464844 mb free ntfs)
04-13 20:44 DEBUG  WindowsBackend: drive=Drive(C: hd 578800.464844 mb free ntfs)
04-13 20:44 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-13 20:44 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-13 20:44 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
04-13 20:44 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
04-13 20:44 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
04-13 20:44 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
04-13 20:44 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
04-13 20:44 DEBUG  WindowsBackend: drive=Drive(K: removable 1002.921875 mb free fat32)
04-13 20:44 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-13 20:44 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-13 20:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-13 20:44 DEBUG  WindowsBackend: keyboard_id=67702793
04-13 20:44 DEBUG  WindowsBackend: keyboard_layout=us
04-13 20:44 DEBUG  WindowsBackend: keyboard_variant=
04-13 20:44 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
04-13 20:44 DEBUG  CommonBackend: locale=en_CA.UTF-8
04-13 20:44 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
04-13 20:44 DEBUG  CommonBackend: Searching ISOs on USB devices
04-13 20:44 DEBUG  CommonBackend: Searching for local CDs
04-13 20:44 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp is a valid Ubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp is a valid Kubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:   parsing info from str=Linux Mint 10 "Julia" - Release amd64 (20101007)

04-13 20:44 DEBUG  Distro:   parsed info={'name': 'Linux Mint', 'subversion': 'Release', 'version': '10', 'build': '20101007', 'codename': 'Julia', 'arch': 'amd64'}
04-13 20:44 DEBUG  Distro: wrong name: Linux Mint != Ubuntu
04-13 20:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro: wrong name: Linux Mint != Ubuntu
04-13 20:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-13 20:44 DEBUG  Distro: wrong name: Linux Mint != Ubuntu Netbook
04-13 20:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro: wrong name: Linux Mint != Kubuntu
04-13 20:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro: wrong name: Linux Mint != Kubuntu
04-13 20:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-13 20:44 DEBUG  Distro: wrong name: Linux Mint != Kubuntu Netbook
04-13 20:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro: wrong name: Linux Mint != Xubuntu
04-13 20:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro: wrong name: Linux Mint != Xubuntu
04-13 20:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro: wrong name: Linux Mint != Mythbuntu
04-13 20:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro: wrong name: Linux Mint != Mythbuntu
04-13 20:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu Netbook CD
04-13 20:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
04-13 20:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-13 20:44 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
04-13 20:44 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
04-13 20:44 INFO   root: Running the uninstaller...
04-13 20:44 INFO   CommonBackend: This is the uninstaller running
04-13 20:44 DEBUG  WindowsFrontend: __init__...
04-13 20:44 DEBUG  WindowsFrontend: on_init...
04-13 20:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\translations, languages=['en_CA', 'en']
04-13 20:44 INFO   root: Received settings
04-13 20:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\translations, languages=['en_CA', 'en']
04-13 20:44 DEBUG  TaskList: # Running tasklist...
04-13 20:44 DEBUG  TaskList: ## Running Backup ISO...
04-13 20:44 DEBUG  TaskList: ## Finished Backup ISO
04-13 20:44 DEBUG  TaskList: ## Running Remove bootloader entry...
04-13 20:44 DEBUG  WindowsBackend: Could not find bcd id
04-13 20:44 DEBUG  WindowsBackend: undo_bootini C:
04-13 20:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 578800.464844 mb free ntfs)
04-13 20:44 DEBUG  WindowsBackend: undo_bootini F:
04-13 20:44 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
04-13 20:44 DEBUG  WindowsBackend: undo_bootini G:
04-13 20:44 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
04-13 20:44 DEBUG  WindowsBackend: undo_bootini H:
04-13 20:44 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
04-13 20:44 DEBUG  WindowsBackend: undo_bootini I:
04-13 20:44 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
04-13 20:44 DEBUG  WindowsBackend: undo_bootini J:
04-13 20:44 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 0.0 mb free )
04-13 20:44 DEBUG  WindowsBackend: undo_bootini K:
04-13 20:44 DEBUG  WindowsBackend: undo_configsys Drive(K: removable 1002.921875 mb free fat32)
04-13 20:44 DEBUG  TaskList: ## Finished Remove bootloader entry
04-13 20:44 DEBUG  TaskList: ## Running Remove target dir...
04-13 20:44 DEBUG  CommonBackend: Deleting C:\ubuntu
04-13 20:44 DEBUG  TaskList: ## Finished Remove target dir
04-13 20:44 DEBUG  TaskList: ## Running Remove registry key...
04-13 20:44 DEBUG  TaskList: ## Finished Remove registry key
04-13 20:44 DEBUG  TaskList: # Finished tasklist
04-13 20:44 INFO   root: Almost finished uninstalling
04-13 20:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pyl7851.tmp\translations, languages=['en_CA', 'en']
04-13 20:44 INFO   root: Finished uninstallation
04-13 20:44 DEBUG  root: application.quit
04-13 20:44 DEBUG  WindowsFrontend: frontend.quit
04-13 20:44 DEBUG  WindowsFrontend: frontend.on_quit
04-13 20:44 DEBUG  root: application.on_quit
04-13 20:44 INFO   root: sys.exit
04-13 20:50 INFO   root: === wubi 10.10 rev197 ===
04-13 20:50 DEBUG  root: Logfile is c:\users\loren\appdata\local\temp\wubi-10.10-rev197.log
04-13 20:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
04-13 20:50 DEBUG  CommonBackend: data_dir=C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\data
04-13 20:50 DEBUG  WindowsBackend: 7z=C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\bin\7z.exe
04-13 20:50 DEBUG  CommonBackend: Fetching basic info...
04-13 20:50 DEBUG  CommonBackend: original_exe=E:\wubi.exe
04-13 20:50 DEBUG  CommonBackend: platform=win32
04-13 20:50 DEBUG  CommonBackend: osname=nt
04-13 20:50 DEBUG  CommonBackend: language=en_CA
04-13 20:50 DEBUG  CommonBackend: encoding=cp1252
04-13 20:50 DEBUG  WindowsBackend: arch=amd64
04-13 20:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\data\isolist.ini
04-13 20:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-13 20:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-13 20:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-13 20:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-13 20:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-13 20:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-13 20:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-13 20:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-13 20:50 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-13 20:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-13 20:50 DEBUG  WindowsBackend: Fetching host info...
04-13 20:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-13 20:50 DEBUG  WindowsBackend: windows version=vista
04-13 20:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-13 20:50 DEBUG  WindowsBackend: windows_sp=None
04-13 20:50 DEBUG  WindowsBackend: windows_build=7600
04-13 20:50 DEBUG  WindowsBackend: gmt=-8
04-13 20:50 DEBUG  WindowsBackend: country=CA
04-13 20:50 DEBUG  WindowsBackend: timezone=America/Vancouver
04-13 20:50 DEBUG  WindowsBackend: windows_username=Loren
04-13 20:50 DEBUG  WindowsBackend: user_full_name=Loren
04-13 20:50 DEBUG  WindowsBackend: user_directory=C:\Users\Loren
04-13 20:50 DEBUG  WindowsBackend: windows_language_code=1033
04-13 20:50 DEBUG  WindowsBackend: windows_language=English
04-13 20:50 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz
04-13 20:50 DEBUG  WindowsBackend: bootloader=vista
04-13 20:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 578874.757813 mb free ntfs)
04-13 20:50 DEBUG  WindowsBackend: drive=Drive(C: hd 578874.757813 mb free ntfs)
04-13 20:50 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-13 20:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-13 20:50 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
04-13 20:50 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
04-13 20:50 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
04-13 20:50 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
04-13 20:50 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
04-13 20:50 DEBUG  WindowsBackend: drive=Drive(K: removable 1002.921875 mb free fat32)
04-13 20:50 DEBUG  WindowsBackend: uninstaller_path=None
04-13 20:50 DEBUG  WindowsBackend: previous_target_dir=None
04-13 20:50 DEBUG  WindowsBackend: previous_distro_name=None
04-13 20:50 DEBUG  WindowsBackend: keyboard_id=67702793
04-13 20:50 DEBUG  WindowsBackend: keyboard_layout=us
04-13 20:50 DEBUG  WindowsBackend: keyboard_variant=
04-13 20:50 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
04-13 20:50 DEBUG  CommonBackend: locale=en_CA.UTF-8
04-13 20:50 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
04-13 20:50 DEBUG  CommonBackend: Searching ISOs on USB devices
04-13 20:50 DEBUG  CommonBackend: Searching for local CDs
04-13 20:50 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylF195.tmp is a valid Ubuntu CD
04-13 20:50 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylF195.tmp is a valid Ubuntu CD
04-13 20:50 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylF195.tmp is a valid Ubuntu Netbook CD
04-13 20:50 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylF195.tmp is a valid Kubuntu CD
04-13 20:50 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylF195.tmp is a valid Kubuntu CD
04-13 20:50 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylF195.tmp is a valid Kubuntu Netbook CD
04-13 20:50 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylF195.tmp is a valid Xubuntu CD
04-13 20:50 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylF195.tmp is a valid Xubuntu CD
04-13 20:50 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylF195.tmp is a valid Mythbuntu CD
04-13 20:50 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylF195.tmp is a valid Mythbuntu CD
04-13 20:50 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-13 20:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-13 20:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-13 20:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-13 20:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-13 20:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-13 20:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-13 20:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-13 20:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-13 20:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-13 20:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-13 20:50 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-13 20:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-13 20:50 INFO   Distro: Found a valid CD for Ubuntu: E:\
04-13 20:50 INFO   root: Running the CD menu...
04-13 20:50 DEBUG  WindowsFrontend: __init__...
04-13 20:50 DEBUG  WindowsFrontend: on_init...
04-13 20:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\translations, languages=['en_CA', 'en']
04-13 20:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\translations, languages=['en_CA', 'en']
04-13 20:50 INFO   root: CD menu finished
04-13 20:50 INFO   root: Running the installer...
04-13 20:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\translations, languages=['en_CA', 'en']
04-13 20:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\translations, languages=['en_CA', 'en']
04-13 20:50 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=loren
04-13 20:50 INFO   root: Received settings
04-13 20:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\translations, languages=['en_US', 'en']
04-13 20:50 DEBUG  TaskList: # Running tasklist...
04-13 20:50 DEBUG  TaskList: ## Running select_target_dir...
04-13 20:50 INFO   WindowsBackend: Installing into C:\ubuntu
04-13 20:50 DEBUG  TaskList: ## Finished select_target_dir
04-13 20:50 DEBUG  TaskList: ## Running create_dir_structure...
04-13 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-13 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-13 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-13 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-13 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-13 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-13 20:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-13 20:50 DEBUG  TaskList: ## Finished create_dir_structure
04-13 20:50 DEBUG  TaskList: ## Running uncompress_target_dir...
04-13 20:50 DEBUG  TaskList: ## Finished uncompress_target_dir
04-13 20:50 DEBUG  TaskList: ## Running create_uninstaller...
04-13 20:50 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-13 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-13 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-13 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-13 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-13 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-13 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-13 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-13 20:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-13 20:50 DEBUG  TaskList: ## Finished create_uninstaller
04-13 20:50 DEBUG  TaskList: ## Running copy_installation_files...
04-13 20:50 DEBUG  WindowsBackend: Copying C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-13 20:50 DEBUG  WindowsBackend: Copying C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\winboot -> C:\ubuntu\winboot
04-13 20:50 DEBUG  WindowsBackend: Copying C:\Users\Loren\AppData\Local\Temp\pylF195.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-13 20:50 DEBUG  TaskList: ## Finished copy_installation_files
04-13 20:50 DEBUG  TaskList: ## Running get_iso...
04-13 20:50 DEBUG  TaskList: New task copy_file
04-13 20:50 DEBUG  TaskList: ### Running copy_file...
04-13 20:50 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
04-13 20:50 DEBUG  TaskList: # Cancelling tasklist
04-13 20:50 DEBUG  TaskList: New task check_iso
04-13 20:50 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
04-13 20:50 DEBUG  CommonBackend: Searching for local ISO
04-13 20:50 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-13 20:50 DEBUG  TaskList: New task get_metalink
04-13 20:50 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-13 20:50 DEBUG  TaskList: # Cancelling tasklist
04-13 20:50 DEBUG  TaskList: # Finished tasklist
04-13 20:58 INFO   root: === wubi 10.10 rev197 ===
04-13 20:58 DEBUG  root: Logfile is c:\users\loren\appdata\local\temp\wubi-10.10-rev197.log
04-13 20:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
04-13 20:58 DEBUG  CommonBackend: data_dir=C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\data
04-13 20:58 DEBUG  WindowsBackend: 7z=C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\bin\7z.exe
04-13 20:58 DEBUG  CommonBackend: Fetching basic info...
04-13 20:58 DEBUG  CommonBackend: original_exe=E:\wubi.exe
04-13 20:58 DEBUG  CommonBackend: platform=win32
04-13 20:58 DEBUG  CommonBackend: osname=nt
04-13 20:58 DEBUG  CommonBackend: language=en_CA
04-13 20:58 DEBUG  CommonBackend: encoding=cp1252
04-13 20:58 DEBUG  WindowsBackend: arch=amd64
04-13 20:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\data\isolist.ini
04-13 20:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-13 20:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-13 20:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-13 20:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-13 20:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-13 20:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-13 20:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-13 20:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-13 20:58 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-13 20:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-13 20:58 DEBUG  WindowsBackend: Fetching host info...
04-13 20:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-13 20:58 DEBUG  WindowsBackend: windows version=vista
04-13 20:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-13 20:58 DEBUG  WindowsBackend: windows_sp=None
04-13 20:58 DEBUG  WindowsBackend: windows_build=7600
04-13 20:58 DEBUG  WindowsBackend: gmt=-8
04-13 20:58 DEBUG  WindowsBackend: country=CA
04-13 20:58 DEBUG  WindowsBackend: timezone=America/Vancouver
04-13 20:58 DEBUG  WindowsBackend: windows_username=Loren
04-13 20:58 DEBUG  WindowsBackend: user_full_name=Loren
04-13 20:58 DEBUG  WindowsBackend: user_directory=C:\Users\Loren
04-13 20:58 DEBUG  WindowsBackend: windows_language_code=1033
04-13 20:58 DEBUG  WindowsBackend: windows_language=English
04-13 20:58 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz
04-13 20:58 DEBUG  WindowsBackend: bootloader=vista
04-13 20:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 578649.890625 mb free ntfs)
04-13 20:58 DEBUG  WindowsBackend: drive=Drive(C: hd 578649.890625 mb free ntfs)
04-13 20:58 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-13 20:58 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-13 20:58 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
04-13 20:58 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
04-13 20:58 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
04-13 20:58 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
04-13 20:58 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
04-13 20:58 DEBUG  WindowsBackend: drive=Drive(K: removable 1002.921875 mb free fat32)
04-13 20:58 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-13 20:58 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-13 20:58 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-13 20:58 DEBUG  WindowsBackend: keyboard_id=67702793
04-13 20:58 DEBUG  WindowsBackend: keyboard_layout=us
04-13 20:58 DEBUG  WindowsBackend: keyboard_variant=
04-13 20:58 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
04-13 20:58 DEBUG  CommonBackend: locale=en_CA.UTF-8
04-13 20:58 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
04-13 20:58 DEBUG  CommonBackend: Searching ISOs on USB devices
04-13 20:58 DEBUG  CommonBackend: Searching for local CDs
04-13 20:58 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Ubuntu CD
04-13 20:58 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Ubuntu CD
04-13 20:58 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Ubuntu Netbook CD
04-13 20:58 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Kubuntu CD
04-13 20:58 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Kubuntu CD
04-13 20:58 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Kubuntu Netbook CD
04-13 20:58 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Xubuntu CD
04-13 20:58 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Xubuntu CD
04-13 20:58 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Mythbuntu CD
04-13 20:58 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Mythbuntu CD
04-13 20:58 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-13 20:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-13 20:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-13 20:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-13 20:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-13 20:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-13 20:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-13 20:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-13 20:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-13 20:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-13 20:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-13 20:58 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-13 20:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-13 20:58 INFO   Distro: Found a valid CD for Ubuntu: E:\
04-13 20:58 INFO   root: Running the CD menu...
04-13 20:58 DEBUG  WindowsFrontend: __init__...
04-13 20:58 DEBUG  WindowsFrontend: on_init...
04-13 20:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\translations, languages=['en_CA', 'en']
04-13 20:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\translations, languages=['en_CA', 'en']
04-13 20:59 INFO   root: CD menu finished
04-13 20:59 INFO   root: Already installed, running the uninstaller...
04-13 20:59 INFO   root: Running the uninstaller...
04-13 20:59 INFO   CommonBackend: This is the uninstaller running
04-13 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\translations, languages=['en_CA', 'en']
04-13 20:59 INFO   root: Received settings
04-13 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\translations, languages=['en_CA', 'en']
04-13 20:59 DEBUG  TaskList: # Running tasklist...
04-13 20:59 DEBUG  TaskList: ## Running Backup ISO...
04-13 20:59 DEBUG  TaskList: ## Finished Backup ISO
04-13 20:59 DEBUG  TaskList: ## Running Remove bootloader entry...
04-13 20:59 DEBUG  WindowsBackend: Could not find bcd id
04-13 20:59 DEBUG  WindowsBackend: undo_bootini C:
04-13 20:59 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 578649.890625 mb free ntfs)
04-13 20:59 DEBUG  WindowsBackend: undo_bootini F:
04-13 20:59 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
04-13 20:59 DEBUG  WindowsBackend: undo_bootini G:
04-13 20:59 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
04-13 20:59 DEBUG  WindowsBackend: undo_bootini H:
04-13 20:59 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
04-13 20:59 DEBUG  WindowsBackend: undo_bootini I:
04-13 20:59 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
04-13 20:59 DEBUG  WindowsBackend: undo_bootini J:
04-13 20:59 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 0.0 mb free )
04-13 20:59 DEBUG  WindowsBackend: undo_bootini K:
04-13 20:59 DEBUG  WindowsBackend: undo_configsys Drive(K: removable 1002.921875 mb free fat32)
04-13 20:59 DEBUG  TaskList: ## Finished Remove bootloader entry
04-13 20:59 DEBUG  TaskList: ## Running Remove target dir...
04-13 20:59 DEBUG  CommonBackend: Deleting C:\ubuntu
04-13 20:59 DEBUG  TaskList: ## Finished Remove target dir
04-13 20:59 DEBUG  TaskList: ## Running Remove registry key...
04-13 20:59 DEBUG  TaskList: ## Finished Remove registry key
04-13 20:59 DEBUG  TaskList: # Finished tasklist
04-13 20:59 INFO   root: Almost finished uninstalling
04-13 20:59 INFO   root: Finished uninstallation
04-13 20:59 DEBUG  CommonBackend: Fetching basic info...
04-13 20:59 DEBUG  CommonBackend: original_exe=E:\wubi.exe
04-13 20:59 DEBUG  CommonBackend: platform=win32
04-13 20:59 DEBUG  CommonBackend: osname=nt
04-13 20:59 DEBUG  WindowsBackend: arch=amd64
04-13 20:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\data\isolist.ini
04-13 20:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-13 20:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-13 20:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-13 20:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-13 20:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-13 20:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-13 20:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-13 20:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-13 20:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-13 20:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-13 20:59 DEBUG  WindowsBackend: Fetching host info...
04-13 20:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-13 20:59 DEBUG  WindowsBackend: windows version=vista
04-13 20:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-13 20:59 DEBUG  WindowsBackend: windows_sp=None
04-13 20:59 DEBUG  WindowsBackend: windows_build=7600
04-13 20:59 DEBUG  WindowsBackend: gmt=-8
04-13 20:59 DEBUG  WindowsBackend: country=CA
04-13 20:59 DEBUG  WindowsBackend: timezone=America/Vancouver
04-13 20:59 DEBUG  WindowsBackend: windows_username=Loren
04-13 20:59 DEBUG  WindowsBackend: user_full_name=Loren
04-13 20:59 DEBUG  WindowsBackend: user_directory=C:\Users\Loren
04-13 20:59 DEBUG  WindowsBackend: windows_language_code=1033
04-13 20:59 DEBUG  WindowsBackend: windows_language=English
04-13 20:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU         750  @ 2.67GHz
04-13 20:59 DEBUG  WindowsBackend: bootloader=vista
04-13 20:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 578874.421875 mb free ntfs)
04-13 20:59 DEBUG  WindowsBackend: drive=Drive(C: hd 578874.421875 mb free ntfs)
04-13 20:59 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-13 20:59 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-13 20:59 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
04-13 20:59 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
04-13 20:59 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
04-13 20:59 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
04-13 20:59 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
04-13 20:59 DEBUG  WindowsBackend: drive=Drive(K: removable 1002.921875 mb free fat32)
04-13 20:59 DEBUG  WindowsBackend: uninstaller_path=None
04-13 20:59 DEBUG  WindowsBackend: previous_target_dir=None
04-13 20:59 DEBUG  WindowsBackend: previous_distro_name=None
04-13 20:59 DEBUG  WindowsBackend: keyboard_id=67702793
04-13 20:59 DEBUG  WindowsBackend: keyboard_layout=us
04-13 20:59 DEBUG  WindowsBackend: keyboard_variant=
04-13 20:59 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
04-13 20:59 DEBUG  CommonBackend: Searching ISOs on USB devices
04-13 20:59 DEBUG  CommonBackend: Searching for local CDs
04-13 20:59 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Ubuntu CD
04-13 20:59 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Ubuntu CD
04-13 20:59 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Ubuntu Netbook CD
04-13 20:59 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Kubuntu CD
04-13 20:59 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Kubuntu CD
04-13 20:59 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Kubuntu Netbook CD
04-13 20:59 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Xubuntu CD
04-13 20:59 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Xubuntu CD
04-13 20:59 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Mythbuntu CD
04-13 20:59 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp is a valid Mythbuntu CD
04-13 20:59 DEBUG  Distro:     does not contain C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-13 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-13 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-13 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-13 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-13 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-13 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-13 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-13 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-13 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-13 20:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-13 20:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-13 20:59 INFO   Distro: Found a valid CD for Ubuntu: E:\
04-13 20:59 INFO   root: Running the installer...
04-13 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\translations, languages=['en_CA', 'en']
04-13 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\translations, languages=['en_CA', 'en']
04-13 20:59 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=loren
04-13 20:59 INFO   root: Received settings
04-13 20:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\translations, languages=['en_US', 'en']
04-13 20:59 DEBUG  TaskList: # Running tasklist...
04-13 20:59 DEBUG  TaskList: ## Running select_target_dir...
04-13 20:59 INFO   WindowsBackend: Installing into C:\ubuntu
04-13 20:59 DEBUG  TaskList: ## Finished select_target_dir
04-13 20:59 DEBUG  TaskList: ## Running create_dir_structure...
04-13 20:59 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-13 20:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-13 20:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-13 20:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-13 20:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-13 20:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-13 20:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-13 20:59 DEBUG  TaskList: ## Finished create_dir_structure
04-13 20:59 DEBUG  TaskList: ## Running uncompress_target_dir...
04-13 20:59 DEBUG  TaskList: ## Finished uncompress_target_dir
04-13 20:59 DEBUG  TaskList: ## Running create_uninstaller...
04-13 20:59 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-13 20:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-13 20:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-13 20:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-13 20:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-13 20:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-13 20:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-13 20:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-13 20:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-13 20:59 DEBUG  TaskList: ## Finished create_uninstaller
04-13 20:59 DEBUG  TaskList: ## Running copy_installation_files...
04-13 20:59 DEBUG  WindowsBackend: Copying C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-13 20:59 DEBUG  WindowsBackend: Copying C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\winboot -> C:\ubuntu\winboot
04-13 20:59 DEBUG  WindowsBackend: Copying C:\Users\Loren\AppData\Local\Temp\pylAAE5.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-13 20:59 DEBUG  TaskList: ## Finished copy_installation_files
04-13 20:59 DEBUG  TaskList: ## Running get_iso...
04-13 20:59 DEBUG  TaskList: New task copy_file
04-13 20:59 DEBUG  TaskList: ### Running copy_file...
04-13 20:59 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
04-13 20:59 DEBUG  TaskList: # Cancelling tasklist
04-13 20:59 DEBUG  TaskList: New task check_iso
04-13 20:59 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
04-13 20:59 DEBUG  CommonBackend: Searching for local ISO
04-13 20:59 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-13 20:59 DEBUG  TaskList: New task get_metalink
04-13 20:59 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-13 20:59 DEBUG  TaskList: # Cancelling tasklist
04-13 20:59 DEBUG  TaskList: # Finished tasklist

---

### Post by zvacet on 2011-04-14
I know this is not answer to your question,but install it in Virtual box or try dual boot.Vbox if you just want to see how it works and dual boot if you like it.

---

### Post by bcbc on 2011-04-14
Download wubi.exe from [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)
Place it in the same folder as the ISO (unmounted). 

Run Wubi from there.

---

