---
title: "Install error?"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by zKoolz on 2011-04-20
I was in the middle of installing Ubuntu when the the installation program crashed and gave me this log. Apparently it couldn't find the .iso o_O 



04-20 18:25 INFO   root: === wubi 10.10 rev197 ===
04-20 18:25 DEBUG  root: Logfile is c:\users\owner\appdata\local\temp\wubi-10.10-rev197.log
04-20 18:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
04-20 18:25 DEBUG  CommonBackend: data_dir=C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\data
04-20 18:25 DEBUG  WindowsBackend: 7z=C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\bin\7z.exe
04-20 18:25 DEBUG  CommonBackend: Fetching basic info...
04-20 18:25 DEBUG  CommonBackend: original_exe=G:\wubi.exe
04-20 18:25 DEBUG  CommonBackend: platform=win32
04-20 18:25 DEBUG  CommonBackend: osname=nt
04-20 18:25 DEBUG  CommonBackend: language=en_US
04-20 18:25 DEBUG  CommonBackend: encoding=cp1252
04-20 18:25 DEBUG  WindowsBackend: arch=amd64
04-20 18:25 DEBUG  CommonBackend: Parsing isolist=C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\data\isolist.ini
04-20 18:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-20 18:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-20 18:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-20 18:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-20 18:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-20 18:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-20 18:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-20 18:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-20 18:25 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-20 18:25 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-20 18:25 DEBUG  WindowsBackend: Fetching host info...
04-20 18:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-20 18:25 DEBUG  WindowsBackend: windows version=vista
04-20 18:25 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-20 18:25 DEBUG  WindowsBackend: windows_sp=None
04-20 18:25 DEBUG  WindowsBackend: windows_build=7600
04-20 18:25 DEBUG  WindowsBackend: gmt=-8
04-20 18:25 DEBUG  WindowsBackend: country=US
04-20 18:25 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-20 18:25 DEBUG  WindowsBackend: windows_username=Owner
04-20 18:25 DEBUG  WindowsBackend: user_full_name=Owner
04-20 18:25 DEBUG  WindowsBackend: user_directory=C:\Users\Owner
04-20 18:25 DEBUG  WindowsBackend: windows_language_code=1033
04-20 18:25 DEBUG  WindowsBackend: windows_language=English
04-20 18:25 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) CPU        P6100  @ 2.00GHz
04-20 18:25 DEBUG  WindowsBackend: bootloader=vista
04-20 18:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 78982.0742188 mb free ntfs)
04-20 18:25 DEBUG  WindowsBackend: drive=Drive(C: hd 78982.0742188 mb free ntfs)
04-20 18:25 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-20 18:25 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-20 18:25 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-20 18:25 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
04-20 18:25 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
04-20 18:25 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
04-20 18:25 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-20 18:25 DEBUG  WindowsBackend: uninstaller_path=None
04-20 18:25 DEBUG  WindowsBackend: previous_target_dir=None
04-20 18:25 DEBUG  WindowsBackend: previous_distro_name=None
04-20 18:25 DEBUG  WindowsBackend: keyboard_id=67699721
04-20 18:25 DEBUG  WindowsBackend: keyboard_layout=us
04-20 18:25 DEBUG  WindowsBackend: keyboard_variant=
04-20 18:25 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-20 18:25 DEBUG  CommonBackend: locale=en_US.UTF-8
04-20 18:25 DEBUG  WindowsBackend: total_memory_mb=3766.7109375
04-20 18:25 DEBUG  CommonBackend: Searching ISOs on USB devices
04-20 18:25 DEBUG  CommonBackend: Searching for local CDs
04-20 18:25 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp is a valid Ubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp is a valid Ubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp is a valid Ubuntu Netbook CD
04-20 18:25 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp is a valid Kubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp is a valid Kubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp is a valid Kubuntu Netbook CD
04-20 18:25 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp is a valid Xubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp is a valid Xubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp is a valid Mythbuntu CD
04-20 18:25 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp is a valid Mythbuntu CD
04-20 18:25 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-20 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-20 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-20 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-20 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-20 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-20 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-20 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-20 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-20 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-20 18:25 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-20 18:25 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-20 18:25 INFO   Distro: Found a valid CD for Ubuntu: G:\
04-20 18:25 INFO   root: Running the CD menu...
04-20 18:25 DEBUG  WindowsFrontend: __init__...
04-20 18:25 DEBUG  WindowsFrontend: on_init...
04-20 18:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\translations, languages=['en_US', 'en']
04-20 18:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\translations, languages=['en_US', 'en']
04-20 18:26 INFO   root: CD menu finished
04-20 18:26 INFO   root: Running the installer...
04-20 18:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\translations, languages=['en_US', 'en']
04-20 18:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\translations, languages=['en_US', 'en']
04-20 18:26 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=quan
04-20 18:26 INFO   root: Received settings
04-20 18:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\translations, languages=['en_US', 'en']
04-20 18:26 DEBUG  TaskList: # Running tasklist...
04-20 18:26 DEBUG  TaskList: ## Running select_target_dir...
04-20 18:26 INFO   WindowsBackend: Installing into C:\ubuntu
04-20 18:26 DEBUG  TaskList: ## Finished select_target_dir
04-20 18:26 DEBUG  TaskList: ## Running create_dir_structure...
04-20 18:26 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-20 18:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-20 18:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-20 18:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-20 18:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-20 18:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-20 18:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-20 18:26 DEBUG  TaskList: ## Finished create_dir_structure
04-20 18:26 DEBUG  TaskList: ## Running uncompress_target_dir...
04-20 18:26 DEBUG  TaskList: ## Finished uncompress_target_dir
04-20 18:26 DEBUG  TaskList: ## Running create_uninstaller...
04-20 18:26 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-20 18:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-20 18:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-20 18:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-20 18:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-20 18:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-20 18:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-20 18:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-20 18:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-20 18:26 DEBUG  TaskList: ## Finished create_uninstaller
04-20 18:26 DEBUG  TaskList: ## Running copy_installation_files...
04-20 18:26 DEBUG  WindowsBackend: Copying C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-20 18:26 DEBUG  WindowsBackend: Copying C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\winboot -> C:\ubuntu\winboot
04-20 18:26 DEBUG  WindowsBackend: Copying C:\Users\Owner\AppData\Local\Temp\pyl6C32.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-20 18:26 DEBUG  TaskList: ## Finished copy_installation_files
04-20 18:26 DEBUG  TaskList: ## Running get_iso...
04-20 18:26 DEBUG  TaskList: New task copy_file
04-20 18:26 DEBUG  TaskList: ### Running copy_file...
04-20 18:26 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
04-20 18:26 DEBUG  TaskList: # Cancelling tasklist
04-20 18:26 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
04-20 18:26 DEBUG  TaskList: New task check_iso
04-20 18:26 DEBUG  CommonBackend: Searching for local ISO
04-20 18:26 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-20 18:26 DEBUG  TaskList: New task get_metalink
04-20 18:26 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-20 18:26 DEBUG  TaskList: # Cancelling tasklist
04-20 18:26 DEBUG  TaskList: # Finished tasklist
04-20 18:28 INFO   root: === wubi 10.10 rev197 ===
04-20 18:28 DEBUG  root: Logfile is c:\users\owner\appdata\local\temp\wubi-10.10-rev197.log
04-20 18:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
04-20 18:28 DEBUG  CommonBackend: data_dir=C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp\data
04-20 18:28 DEBUG  WindowsBackend: 7z=C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp\bin\7z.exe
04-20 18:28 DEBUG  CommonBackend: Fetching basic info...
04-20 18:28 DEBUG  CommonBackend: original_exe=G:\wubi.exe
04-20 18:28 DEBUG  CommonBackend: platform=win32
04-20 18:28 DEBUG  CommonBackend: osname=nt
04-20 18:28 DEBUG  CommonBackend: language=en_US
04-20 18:28 DEBUG  CommonBackend: encoding=cp1252
04-20 18:28 DEBUG  WindowsBackend: arch=amd64
04-20 18:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp\data\isolist.ini
04-20 18:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-20 18:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-20 18:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-20 18:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-20 18:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-20 18:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-20 18:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-20 18:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-20 18:28 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-20 18:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-20 18:28 DEBUG  WindowsBackend: Fetching host info...
04-20 18:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-20 18:28 DEBUG  WindowsBackend: windows version=vista
04-20 18:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-20 18:28 DEBUG  WindowsBackend: windows_sp=None
04-20 18:28 DEBUG  WindowsBackend: windows_build=7600
04-20 18:28 DEBUG  WindowsBackend: gmt=-8
04-20 18:28 DEBUG  WindowsBackend: country=US
04-20 18:28 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-20 18:28 DEBUG  WindowsBackend: windows_username=Owner
04-20 18:28 DEBUG  WindowsBackend: user_full_name=Owner
04-20 18:28 DEBUG  WindowsBackend: user_directory=C:\Users\Owner
04-20 18:28 DEBUG  WindowsBackend: windows_language_code=1033
04-20 18:28 DEBUG  WindowsBackend: windows_language=English
04-20 18:28 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) CPU        P6100  @ 2.00GHz
04-20 18:28 DEBUG  WindowsBackend: bootloader=vista
04-20 18:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 78712.9492188 mb free ntfs)
04-20 18:28 DEBUG  WindowsBackend: drive=Drive(C: hd 78712.9492188 mb free ntfs)
04-20 18:28 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-20 18:28 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-20 18:28 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-20 18:28 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
04-20 18:28 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
04-20 18:28 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
04-20 18:28 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-20 18:28 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-20 18:28 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-20 18:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-20 18:28 DEBUG  WindowsBackend: keyboard_id=67699721
04-20 18:28 DEBUG  WindowsBackend: keyboard_layout=us
04-20 18:28 DEBUG  WindowsBackend: keyboard_variant=
04-20 18:28 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-20 18:28 DEBUG  CommonBackend: locale=en_US.UTF-8
04-20 18:28 DEBUG  WindowsBackend: total_memory_mb=3766.7109375
04-20 18:28 DEBUG  CommonBackend: Searching ISOs on USB devices
04-20 18:28 DEBUG  CommonBackend: Searching for local CDs
04-20 18:28 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp is a valid Ubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp is a valid Ubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp is a valid Ubuntu Netbook CD
04-20 18:28 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp is a valid Kubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp is a valid Kubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp is a valid Kubuntu Netbook CD
04-20 18:28 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp is a valid Xubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp is a valid Xubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp is a valid Mythbuntu CD
04-20 18:28 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp is a valid Mythbuntu CD
04-20 18:28 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-20 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-20 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 18:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-20 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-20 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 18:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-20 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-20 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-20 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-20 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-20 18:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:28 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-20 18:28 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-20 18:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-20 18:28 INFO   Distro: Found a valid CD for Ubuntu: G:\
04-20 18:28 INFO   root: Running the CD menu...
04-20 18:28 DEBUG  WindowsFrontend: __init__...
04-20 18:28 DEBUG  WindowsFrontend: on_init...
04-20 18:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp\translations, languages=['en_US', 'en']
04-20 18:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pyl8AAA.tmp\translations, languages=['en_US', 'en']
04-20 18:28 INFO   root: CD menu finished
04-20 18:28 INFO   root: Rebooting
04-20 18:28 DEBUG  TaskList: # Running tasklist...
04-20 18:28 DEBUG  TaskList: ## Running reboot...
04-20 18:28 DEBUG  TaskList: ## Finished reboot
04-20 18:28 DEBUG  TaskList: # Finished tasklist
04-20 18:28 DEBUG  root: application.quit
04-20 18:28 DEBUG  WindowsFrontend: frontend.quit
04-20 18:28 DEBUG  WindowsFrontend: frontend.on_quit
04-20 18:28 DEBUG  root: application.on_quit
04-20 18:28 INFO   root: sys.exit
04-20 18:35 INFO   root: === wubi 10.10 rev197 ===
04-20 18:35 DEBUG  root: Logfile is c:\users\owner\appdata\local\temp\wubi-10.10-rev197.log
04-20 18:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
04-20 18:35 DEBUG  CommonBackend: data_dir=C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\data
04-20 18:35 DEBUG  WindowsBackend: 7z=C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\bin\7z.exe
04-20 18:35 DEBUG  CommonBackend: Fetching basic info...
04-20 18:35 DEBUG  CommonBackend: original_exe=G:\wubi.exe
04-20 18:35 DEBUG  CommonBackend: platform=win32
04-20 18:35 DEBUG  CommonBackend: osname=nt
04-20 18:35 DEBUG  CommonBackend: language=en_US
04-20 18:35 DEBUG  CommonBackend: encoding=cp1252
04-20 18:35 DEBUG  WindowsBackend: arch=amd64
04-20 18:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\data\isolist.ini
04-20 18:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-20 18:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-20 18:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-20 18:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-20 18:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-20 18:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-20 18:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-20 18:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-20 18:35 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-20 18:35 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-20 18:35 DEBUG  WindowsBackend: Fetching host info...
04-20 18:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-20 18:35 DEBUG  WindowsBackend: windows version=vista
04-20 18:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-20 18:35 DEBUG  WindowsBackend: windows_sp=None
04-20 18:35 DEBUG  WindowsBackend: windows_build=7600
04-20 18:35 DEBUG  WindowsBackend: gmt=-8
04-20 18:35 DEBUG  WindowsBackend: country=US
04-20 18:35 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-20 18:35 DEBUG  WindowsBackend: windows_username=Owner
04-20 18:35 DEBUG  WindowsBackend: user_full_name=Owner
04-20 18:35 DEBUG  WindowsBackend: user_directory=C:\Users\Owner
04-20 18:35 DEBUG  WindowsBackend: windows_language_code=1033
04-20 18:35 DEBUG  WindowsBackend: windows_language=English
04-20 18:35 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) CPU        P6100  @ 2.00GHz
04-20 18:35 DEBUG  WindowsBackend: bootloader=vista
04-20 18:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 78718.7539063 mb free ntfs)
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(C: hd 78718.7539063 mb free ntfs)
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-20 18:35 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-20 18:35 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-20 18:35 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-20 18:35 DEBUG  WindowsBackend: keyboard_id=67699721
04-20 18:35 DEBUG  WindowsBackend: keyboard_layout=us
04-20 18:35 DEBUG  WindowsBackend: keyboard_variant=
04-20 18:35 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-20 18:35 DEBUG  CommonBackend: locale=en_US.UTF-8
04-20 18:35 DEBUG  WindowsBackend: total_memory_mb=3766.7109375
04-20 18:35 DEBUG  CommonBackend: Searching ISOs on USB devices
04-20 18:35 DEBUG  CommonBackend: Searching for local CDs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Ubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Kubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
04-20 18:35 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
04-20 18:35 INFO   Distro: Found a valid CD for Ubuntu: G:\
04-20 18:35 INFO   root: Running the CD menu...
04-20 18:35 DEBUG  WindowsFrontend: __init__...
04-20 18:35 DEBUG  WindowsFrontend: on_init...
04-20 18:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\translations, languages=['en_US', 'en']
04-20 18:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\translations, languages=['en_US', 'en']
04-20 18:35 INFO   root: CD menu finished
04-20 18:35 INFO   root: Already installed, running the uninstaller...
04-20 18:35 INFO   root: Running the uninstaller...
04-20 18:35 INFO   CommonBackend: This is the uninstaller running
04-20 18:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\translations, languages=['en_US', 'en']
04-20 18:35 INFO   root: Received settings
04-20 18:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\translations, languages=['en_US', 'en']
04-20 18:35 DEBUG  TaskList: # Running tasklist...
04-20 18:35 DEBUG  TaskList: ## Running Backup ISO...
04-20 18:35 DEBUG  TaskList: ## Finished Backup ISO
04-20 18:35 DEBUG  TaskList: ## Running Remove bootloader entry...
04-20 18:35 DEBUG  WindowsBackend: Could not find bcd id
04-20 18:35 DEBUG  WindowsBackend: undo_bootini C:
04-20 18:35 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 78718.7539063 mb free ntfs)
04-20 18:35 DEBUG  WindowsBackend: undo_bootini Q:
04-20 18:35 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
04-20 18:35 DEBUG  TaskList: ## Finished Remove bootloader entry
04-20 18:35 DEBUG  TaskList: ## Running Remove target dir...
04-20 18:35 DEBUG  CommonBackend: Deleting C:\ubuntu
04-20 18:35 DEBUG  TaskList: ## Finished Remove target dir
04-20 18:35 DEBUG  TaskList: ## Running Remove registry key...
04-20 18:35 DEBUG  TaskList: ## Finished Remove registry key
04-20 18:35 DEBUG  TaskList: # Finished tasklist
04-20 18:35 INFO   root: Almost finished uninstalling
04-20 18:35 INFO   root: Finished uninstallation
04-20 18:35 DEBUG  CommonBackend: Fetching basic info...
04-20 18:35 DEBUG  CommonBackend: original_exe=G:\wubi.exe
04-20 18:35 DEBUG  CommonBackend: platform=win32
04-20 18:35 DEBUG  CommonBackend: osname=nt
04-20 18:35 DEBUG  WindowsBackend: arch=amd64
04-20 18:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\data\isolist.ini
04-20 18:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-20 18:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-20 18:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-20 18:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-20 18:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-20 18:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-20 18:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-20 18:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-20 18:35 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-20 18:35 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-20 18:35 DEBUG  WindowsBackend: Fetching host info...
04-20 18:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-20 18:35 DEBUG  WindowsBackend: windows version=vista
04-20 18:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-20 18:35 DEBUG  WindowsBackend: windows_sp=None
04-20 18:35 DEBUG  WindowsBackend: windows_build=7600
04-20 18:35 DEBUG  WindowsBackend: gmt=-8
04-20 18:35 DEBUG  WindowsBackend: country=US
04-20 18:35 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-20 18:35 DEBUG  WindowsBackend: windows_username=Owner
04-20 18:35 DEBUG  WindowsBackend: user_full_name=Owner
04-20 18:35 DEBUG  WindowsBackend: user_directory=C:\Users\Owner
04-20 18:35 DEBUG  WindowsBackend: windows_language_code=1033
04-20 18:35 DEBUG  WindowsBackend: windows_language=English
04-20 18:35 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) CPU        P6100  @ 2.00GHz
04-20 18:35 DEBUG  WindowsBackend: bootloader=vista
04-20 18:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 78985.265625 mb free ntfs)
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(C: hd 78985.265625 mb free ntfs)
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
04-20 18:35 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
04-20 18:35 DEBUG  WindowsBackend: uninstaller_path=None
04-20 18:35 DEBUG  WindowsBackend: previous_target_dir=None
04-20 18:35 DEBUG  WindowsBackend: previous_distro_name=None
04-20 18:35 DEBUG  WindowsBackend: keyboard_id=67699721
04-20 18:35 DEBUG  WindowsBackend: keyboard_layout=us
04-20 18:35 DEBUG  WindowsBackend: keyboard_variant=
04-20 18:35 DEBUG  WindowsBackend: total_memory_mb=3766.7109375
04-20 18:35 DEBUG  CommonBackend: Searching ISOs on USB devices
04-20 18:35 DEBUG  CommonBackend: Searching for local CDs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Ubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Kubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether C:\Users\Owner\AppData\Local\Temp\pylECED.tmp is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-20 18:35 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-20 18:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-20 18:35 INFO   Distro: Found a valid CD for Ubuntu: G:\
04-20 18:35 INFO   root: Running the installer...
04-20 18:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\translations, languages=['en_US', 'en']
04-20 18:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\translations, languages=['en_US', 'en']
04-20 18:35 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=quan
04-20 18:35 INFO   root: Received settings
04-20 18:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\translations, languages=['en_US', 'en']
04-20 18:35 DEBUG  TaskList: # Running tasklist...
04-20 18:35 DEBUG  TaskList: ## Running select_target_dir...
04-20 18:35 INFO   WindowsBackend: Installing into C:\ubuntu
04-20 18:35 DEBUG  TaskList: ## Finished select_target_dir
04-20 18:35 DEBUG  TaskList: ## Running create_dir_structure...
04-20 18:35 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-20 18:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-20 18:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-20 18:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-20 18:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-20 18:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-20 18:35 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-20 18:35 DEBUG  TaskList: ## Finished create_dir_structure
04-20 18:35 DEBUG  TaskList: ## Running uncompress_target_dir...
04-20 18:35 DEBUG  TaskList: ## Finished uncompress_target_dir
04-20 18:35 DEBUG  TaskList: ## Running create_uninstaller...
04-20 18:35 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-20 18:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-20 18:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-20 18:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-20 18:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-20 18:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
04-20 18:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-20 18:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-20 18:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-20 18:35 DEBUG  TaskList: ## Finished create_uninstaller
04-20 18:35 DEBUG  TaskList: ## Running copy_installation_files...
04-20 18:35 DEBUG  WindowsBackend: Copying C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-20 18:35 DEBUG  WindowsBackend: Copying C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\winboot -> C:\ubuntu\winboot
04-20 18:35 DEBUG  WindowsBackend: Copying C:\Users\Owner\AppData\Local\Temp\pylECED.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-20 18:35 DEBUG  TaskList: ## Finished copy_installation_files
04-20 18:35 DEBUG  TaskList: ## Running get_iso...
04-20 18:35 DEBUG  TaskList: New task copy_file
04-20 18:35 DEBUG  TaskList: ### Running copy_file...
04-20 18:36 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
04-20 18:36 DEBUG  TaskList: # Cancelling tasklist
04-20 18:36 DEBUG  TaskList: New task check_iso
04-20 18:36 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
04-20 18:36 DEBUG  CommonBackend: Searching for local ISO
04-20 18:36 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
04-20 18:36 DEBUG  TaskList: New task get_metalink
04-20 18:36 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
04-20 18:36 DEBUG  TaskList: # Cancelling tasklist
04-20 18:36 DEBUG  TaskList: # Finished tasklist

---

### Post by bcbc on 2011-04-21
The problem is: Errno 22 on copying the .iso from the CD (G:[SIZE="1"] [/SIZE])

This can be caused by incompatibilities with the CD/DVD hardware, or perhaps the disk - but it can occur when the disk is known to be good (works on different machine, or even different CD/DVD drive on same machine). It may also be a bad burn on the CD. 

Best way to install wubi is to place wubi.exe and the 10.10 .iso in the same folder, and run wubi.exe from there. Make sure you use the correct version of wubi.exe (you can copy the one from the CD). Also make sure you remove the CD from the drive or it will find it and fail again.

---

