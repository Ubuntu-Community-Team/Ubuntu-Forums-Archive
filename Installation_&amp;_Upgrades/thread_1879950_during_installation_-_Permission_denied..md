---
title: "during installation - Permission denied."
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by socalheel on 2011-11-12
hi.

when i'm doing a windows installation for ubuntu, i get the attached error.

here is the log file as well.



```
11-12 14:07 INFO   root: === wubi 11.10 rev245 ===
11-12 14:07 DEBUG  root: Logfile is c:\users\mom\appdata\local\temp\wubi-11.10-rev245.log
11-12 14:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Thomas\\Downloads\\wubi.exe"']
11-12 14:07 DEBUG  CommonBackend: data_dir=C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\data
11-12 14:07 DEBUG  WindowsBackend: 7z=C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\bin\7z.exe
11-12 14:07 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-12 14:07 DEBUG  CommonBackend: Fetching basic info...
11-12 14:07 DEBUG  CommonBackend: original_exe=C:\Users\Thomas\Downloads\wubi.exe
11-12 14:07 DEBUG  CommonBackend: platform=win32
11-12 14:07 DEBUG  CommonBackend: osname=nt
11-12 14:07 DEBUG  CommonBackend: language=en_US
11-12 14:07 DEBUG  CommonBackend: encoding=cp1252
11-12 14:07 DEBUG  WindowsBackend: arch=amd64
11-12 14:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\data\isolist.ini
11-12 14:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-12 14:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-12 14:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-12 14:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-12 14:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-12 14:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-12 14:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-12 14:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-12 14:07 DEBUG  WindowsBackend: Fetching host info...
11-12 14:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-12 14:07 DEBUG  WindowsBackend: windows version=vista
11-12 14:07 DEBUG  WindowsBackend: windows_version2=Windows (TM) Vista Home Premium
11-12 14:07 DEBUG  WindowsBackend: windows_sp=None
11-12 14:07 DEBUG  WindowsBackend: windows_build=6002
11-12 14:07 DEBUG  WindowsBackend: gmt=-5
11-12 14:07 DEBUG  WindowsBackend: country=US
11-12 14:07 DEBUG  WindowsBackend: timezone=America/New_York
11-12 14:07 DEBUG  WindowsBackend: windows_username=Mom
11-12 14:07 DEBUG  WindowsBackend: user_full_name=Mom
11-12 14:07 DEBUG  WindowsBackend: user_directory=
11-12 14:07 DEBUG  WindowsBackend: windows_language_code=1033
11-12 14:07 DEBUG  WindowsBackend: windows_language=English
11-12 14:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
11-12 14:07 DEBUG  WindowsBackend: bootloader=vista
11-12 14:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 136558.867188 mb free ntfs)
11-12 14:07 DEBUG  WindowsBackend: drive=Drive(C: hd 136558.867188 mb free ntfs)
11-12 14:07 DEBUG  WindowsBackend: drive=Drive(D: hd 193677.300781 mb free ntfs)
11-12 14:07 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
11-12 14:07 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-12 14:07 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-12 14:07 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
11-12 14:07 DEBUG  WindowsBackend: uninstaller_path=None
11-12 14:07 DEBUG  WindowsBackend: previous_target_dir=None
11-12 14:07 DEBUG  WindowsBackend: previous_distro_name=None
11-12 14:07 DEBUG  WindowsBackend: keyboard_id=67699721
11-12 14:07 DEBUG  WindowsBackend: keyboard_layout=us
11-12 14:07 DEBUG  WindowsBackend: keyboard_variant=
11-12 14:07 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-12 14:07 DEBUG  CommonBackend: locale=en_US.UTF-8
11-12 14:07 DEBUG  WindowsBackend: total_memory_mb=4062.14453125
11-12 14:07 DEBUG  CommonBackend: Searching ISOs on USB devices
11-12 14:07 DEBUG  CommonBackend: Searching for local CDs
11-12 14:07 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp is a valid Ubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp is a valid Ubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp is a valid Kubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp is a valid Kubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp is a valid Xubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp is a valid Xubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp is a valid Mythbuntu CD
11-12 14:07 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp is a valid Mythbuntu CD
11-12 14:07 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 14:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 14:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-12 14:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-12 14:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 14:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 14:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 14:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 14:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-12 14:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-12 14:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:07 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-12 14:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:07 INFO   root: Running the installer...
11-12 14:07 DEBUG  WindowsFrontend: __init__...
11-12 14:07 DEBUG  WindowsFrontend: on_init...
11-12 14:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\translations, languages=['en_US', 'en']
11-12 14:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\translations, languages=['en_US', 'en']
11-12 14:10 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tom
11-12 14:10 INFO   root: Received settings
11-12 14:10 DEBUG  CommonBackend: Searching for local CD
11-12 14:10 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp is a valid Ubuntu CD
11-12 14:10 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\casper\filesystem.squashfs
11-12 14:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:10 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:10 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:10 DEBUG  CommonBackend: Searching for local ISO
11-12 14:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\translations, languages=['en_US', 'en']
11-12 14:10 DEBUG  TaskList: # Running tasklist...
11-12 14:10 DEBUG  TaskList: ## Running select_target_dir...
11-12 14:10 INFO   WindowsBackend: Installing into D:\ubuntu
11-12 14:10 DEBUG  TaskList: ## Finished select_target_dir
11-12 14:10 DEBUG  TaskList: ## Running create_dir_structure...
11-12 14:10 DEBUG  CommonBackend: Creating dir D:\ubuntu
11-12 14:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
11-12 14:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
11-12 14:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
11-12 14:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
11-12 14:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
11-12 14:10 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
11-12 14:10 DEBUG  TaskList: ## Finished create_dir_structure
11-12 14:10 DEBUG  TaskList: ## Running create_uninstaller...
11-12 14:10 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Thomas\Downloads\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
11-12 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
11-12 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
11-12 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-12 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
11-12 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-12 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-12 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-12 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-12 14:10 DEBUG  TaskList: ## Finished create_uninstaller
11-12 14:10 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-12 14:10 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-12 14:10 DEBUG  TaskList: ## Running get_diskimage...
11-12 14:10 DEBUG  TaskList: New task download
11-12 14:10 DEBUG  TaskList: ### Running download...
11-12 14:10 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > D:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
11-12 14:10 DEBUG  downloader: Download start filename=D:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
11-12 14:14 DEBUG  TaskList: ### Finished download
11-12 14:14 DEBUG  downloader: download finished (read 507143012 bytes)
11-12 14:14 DEBUG  TaskList: ## Finished get_diskimage
11-12 14:14 DEBUG  TaskList: ## Running extract_diskimage...
11-12 14:15 DEBUG  TaskList: ## Finished extract_diskimage
11-12 14:15 DEBUG  TaskList: ## Running choose_disk_sizes...
11-12 14:15 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
11-12 14:15 DEBUG  TaskList: ## Finished choose_disk_sizes
11-12 14:15 DEBUG  TaskList: ## Running expand_diskimage...
11-12 14:16 DEBUG  TaskList: ## Finished expand_diskimage
11-12 14:16 DEBUG  TaskList: ## Running create_swap_diskimage...
11-12 14:16 DEBUG  TaskList: ## Finished create_swap_diskimage
11-12 14:16 DEBUG  TaskList: ## Running modify_bootloader...
11-12 14:16 DEBUG  TaskList: New task modify_bcd
11-12 14:16 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:16 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 136558.867188 mb free ntfs)
11-12 14:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {da19424b-0d62-11e1-9ab5-00214ff73e3d}
11-12 14:16 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:16 DEBUG  TaskList: New task modify_bcd
11-12 14:16 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:16 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 193677.300781 mb free ntfs)
11-12 14:16 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:16 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:16 DEBUG  TaskList: New task modify_bcd
11-12 14:16 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:16 DEBUG  WindowsBackend: modify_bcd Drive(E: removable 0.0 mb free )
11-12 14:16 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:16 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:16 DEBUG  TaskList: New task modify_bcd
11-12 14:16 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:16 DEBUG  WindowsBackend: modify_bcd Drive(F: removable 0.0 mb free )
11-12 14:16 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:16 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:16 DEBUG  TaskList: New task modify_bcd
11-12 14:16 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:16 DEBUG  WindowsBackend: modify_bcd Drive(G: removable 0.0 mb free )
11-12 14:16 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:16 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:16 DEBUG  TaskList: ## Finished modify_bootloader
11-12 14:16 DEBUG  TaskList: ## Running diskimage_bootloader...
11-12 14:16 DEBUG  WindowsBackend: Copying C:\Users\Mom\AppData\Local\Temp\pyl43A4.tmp\winboot -> D:\ubuntu\winboot
11-12 14:16 ERROR  TaskList: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'E:\\wubildr'
11-12 14:16 DEBUG  TaskList: # Cancelling tasklist
11-12 14:16 DEBUG  TaskList: # Finished tasklist
11-12 14:16 ERROR  root: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'E:\\wubildr'
11-12 14:23 INFO   root: === wubi 11.10 rev245 ===
11-12 14:23 DEBUG  root: Logfile is c:\users\mom\appdata\local\temp\wubi-11.10-rev245.log
11-12 14:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Thomas\\Downloads\\wubi.exe"']
11-12 14:23 DEBUG  CommonBackend: data_dir=C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\data
11-12 14:23 DEBUG  WindowsBackend: 7z=C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\bin\7z.exe
11-12 14:23 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-12 14:23 DEBUG  CommonBackend: Fetching basic info...
11-12 14:23 DEBUG  CommonBackend: original_exe=C:\Users\Thomas\Downloads\wubi.exe
11-12 14:23 DEBUG  CommonBackend: platform=win32
11-12 14:23 DEBUG  CommonBackend: osname=nt
11-12 14:23 DEBUG  CommonBackend: language=en_US
11-12 14:23 DEBUG  CommonBackend: encoding=cp1252
11-12 14:23 DEBUG  WindowsBackend: arch=amd64
11-12 14:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\data\isolist.ini
11-12 14:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-12 14:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-12 14:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-12 14:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-12 14:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-12 14:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-12 14:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-12 14:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-12 14:23 DEBUG  WindowsBackend: Fetching host info...
11-12 14:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-12 14:23 DEBUG  WindowsBackend: windows version=vista
11-12 14:23 DEBUG  WindowsBackend: windows_version2=Windows (TM) Vista Home Premium
11-12 14:23 DEBUG  WindowsBackend: windows_sp=None
11-12 14:23 DEBUG  WindowsBackend: windows_build=6002
11-12 14:23 DEBUG  WindowsBackend: gmt=-5
11-12 14:23 DEBUG  WindowsBackend: country=US
11-12 14:23 DEBUG  WindowsBackend: timezone=America/New_York
11-12 14:23 DEBUG  WindowsBackend: windows_username=Mom
11-12 14:23 DEBUG  WindowsBackend: user_full_name=Mom
11-12 14:23 DEBUG  WindowsBackend: user_directory=C:\Users\Mom
11-12 14:23 DEBUG  WindowsBackend: windows_language_code=1033
11-12 14:23 DEBUG  WindowsBackend: windows_language=English
11-12 14:23 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
11-12 14:23 DEBUG  WindowsBackend: bootloader=vista
11-12 14:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 136555.039063 mb free ntfs)
11-12 14:23 DEBUG  WindowsBackend: drive=Drive(C: hd 136555.039063 mb free ntfs)
11-12 14:23 DEBUG  WindowsBackend: drive=Drive(D: hd 190121.632813 mb free ntfs)
11-12 14:23 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
11-12 14:23 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-12 14:23 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-12 14:23 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
11-12 14:23 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
11-12 14:23 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
11-12 14:23 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-12 14:23 DEBUG  WindowsBackend: keyboard_id=67699721
11-12 14:23 DEBUG  WindowsBackend: keyboard_layout=us
11-12 14:23 DEBUG  WindowsBackend: keyboard_variant=
11-12 14:23 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-12 14:23 DEBUG  CommonBackend: locale=en_US.UTF-8
11-12 14:23 DEBUG  WindowsBackend: total_memory_mb=4062.14453125
11-12 14:23 DEBUG  CommonBackend: Searching ISOs on USB devices
11-12 14:23 DEBUG  CommonBackend: Searching for local CDs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 INFO   root: Already installed, running the uninstaller...
11-12 14:23 INFO   root: Running the uninstaller...
11-12 14:23 INFO   CommonBackend: This is the uninstaller running
11-12 14:23 DEBUG  WindowsFrontend: __init__...
11-12 14:23 DEBUG  WindowsFrontend: on_init...
11-12 14:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\translations, languages=['en_US', 'en']
11-12 14:23 INFO   root: Received settings
11-12 14:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\translations, languages=['en_US', 'en']
11-12 14:23 DEBUG  TaskList: # Running tasklist...
11-12 14:23 DEBUG  TaskList: ## Running Remove bootloader entry...
11-12 14:23 DEBUG  WindowsBackend: Removing bcd entry {da19424b-0d62-11e1-9ab5-00214ff73e3d}
11-12 14:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
11-12 14:23 DEBUG  WindowsBackend: undo_bootini C:
11-12 14:23 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 136555.039063 mb free ntfs)
11-12 14:23 DEBUG  WindowsBackend: undo_bootini D:
11-12 14:23 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 190121.632813 mb free ntfs)
11-12 14:23 DEBUG  WindowsBackend: undo_bootini E:
11-12 14:23 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 0.0 mb free )
11-12 14:23 DEBUG  WindowsBackend: undo_bootini F:
11-12 14:23 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
11-12 14:23 DEBUG  WindowsBackend: undo_bootini G:
11-12 14:23 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
11-12 14:23 DEBUG  TaskList: ## Finished Remove bootloader entry
11-12 14:23 DEBUG  TaskList: ## Running Remove target dir...
11-12 14:23 DEBUG  CommonBackend: Deleting D:\ubuntu
11-12 14:23 DEBUG  TaskList: ## Finished Remove target dir
11-12 14:23 DEBUG  TaskList: ## Running Remove registry key...
11-12 14:23 DEBUG  TaskList: ## Finished Remove registry key
11-12 14:23 DEBUG  TaskList: # Finished tasklist
11-12 14:23 INFO   root: Almost finished uninstalling
11-12 14:23 INFO   root: Finished uninstallation
11-12 14:23 DEBUG  CommonBackend: Fetching basic info...
11-12 14:23 DEBUG  CommonBackend: original_exe=C:\Users\Thomas\Downloads\wubi.exe
11-12 14:23 DEBUG  CommonBackend: platform=win32
11-12 14:23 DEBUG  CommonBackend: osname=nt
11-12 14:23 DEBUG  WindowsBackend: arch=amd64
11-12 14:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\data\isolist.ini
11-12 14:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-12 14:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-12 14:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-12 14:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-12 14:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-12 14:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-12 14:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-12 14:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-12 14:23 DEBUG  WindowsBackend: Fetching host info...
11-12 14:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-12 14:23 DEBUG  WindowsBackend: windows version=vista
11-12 14:23 DEBUG  WindowsBackend: windows_version2=Windows (TM) Vista Home Premium
11-12 14:23 DEBUG  WindowsBackend: windows_sp=None
11-12 14:23 DEBUG  WindowsBackend: windows_build=6002
11-12 14:23 DEBUG  WindowsBackend: gmt=-5
11-12 14:23 DEBUG  WindowsBackend: country=US
11-12 14:23 DEBUG  WindowsBackend: timezone=America/New_York
11-12 14:23 DEBUG  WindowsBackend: windows_username=Mom
11-12 14:23 DEBUG  WindowsBackend: user_full_name=Mom
11-12 14:23 DEBUG  WindowsBackend: user_directory=C:\Users\Mom
11-12 14:23 DEBUG  WindowsBackend: windows_language_code=1033
11-12 14:23 DEBUG  WindowsBackend: windows_language=English
11-12 14:23 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
11-12 14:23 DEBUG  WindowsBackend: bootloader=vista
11-12 14:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 136554.933594 mb free ntfs)
11-12 14:23 DEBUG  WindowsBackend: drive=Drive(C: hd 136554.933594 mb free ntfs)
11-12 14:23 DEBUG  WindowsBackend: drive=Drive(D: hd 193677.238281 mb free ntfs)
11-12 14:23 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
11-12 14:23 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-12 14:23 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-12 14:23 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
11-12 14:23 DEBUG  WindowsBackend: uninstaller_path=None
11-12 14:23 DEBUG  WindowsBackend: previous_target_dir=None
11-12 14:23 DEBUG  WindowsBackend: previous_distro_name=None
11-12 14:23 DEBUG  WindowsBackend: keyboard_id=67699721
11-12 14:23 DEBUG  WindowsBackend: keyboard_layout=us
11-12 14:23 DEBUG  WindowsBackend: keyboard_variant=
11-12 14:23 DEBUG  WindowsBackend: total_memory_mb=4062.14453125
11-12 14:23 DEBUG  CommonBackend: Searching ISOs on USB devices
11-12 14:23 DEBUG  CommonBackend: Searching for local CDs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-12 14:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:23 INFO   root: Running the installer...
11-12 14:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\translations, languages=['en_US', 'en']
11-12 14:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\translations, languages=['en_US', 'en']
11-12 14:24 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=mom
11-12 14:24 INFO   root: Received settings
11-12 14:24 DEBUG  CommonBackend: Searching for local CD
11-12 14:24 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylA534.tmp is a valid Ubuntu CD
11-12 14:24 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\casper\filesystem.squashfs
11-12 14:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:24 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:24 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:24 DEBUG  CommonBackend: Searching for local ISO
11-12 14:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\translations, languages=['en_US', 'en']
11-12 14:24 DEBUG  TaskList: # Running tasklist...
11-12 14:24 DEBUG  TaskList: ## Running select_target_dir...
11-12 14:24 INFO   WindowsBackend: Installing into D:\ubuntu
11-12 14:24 DEBUG  TaskList: ## Finished select_target_dir
11-12 14:24 DEBUG  TaskList: ## Running create_dir_structure...
11-12 14:24 DEBUG  CommonBackend: Creating dir D:\ubuntu
11-12 14:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
11-12 14:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
11-12 14:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
11-12 14:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
11-12 14:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
11-12 14:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
11-12 14:24 DEBUG  TaskList: ## Finished create_dir_structure
11-12 14:24 DEBUG  TaskList: ## Running create_uninstaller...
11-12 14:24 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Thomas\Downloads\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
11-12 14:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
11-12 14:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
11-12 14:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-12 14:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
11-12 14:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-12 14:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-12 14:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-12 14:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-12 14:24 DEBUG  TaskList: ## Finished create_uninstaller
11-12 14:24 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-12 14:24 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-12 14:24 DEBUG  TaskList: ## Running get_diskimage...
11-12 14:24 DEBUG  TaskList: New task download
11-12 14:24 DEBUG  TaskList: ### Running download...
11-12 14:24 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > D:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
11-12 14:24 DEBUG  downloader: Download start filename=D:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
11-12 14:28 DEBUG  TaskList: ### Finished download
11-12 14:28 DEBUG  downloader: download finished (read 507143012 bytes)
11-12 14:28 DEBUG  TaskList: ## Finished get_diskimage
11-12 14:28 DEBUG  TaskList: ## Running extract_diskimage...
11-12 14:29 DEBUG  TaskList: ## Finished extract_diskimage
11-12 14:29 DEBUG  TaskList: ## Running choose_disk_sizes...
11-12 14:29 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
11-12 14:29 DEBUG  TaskList: ## Finished choose_disk_sizes
11-12 14:29 DEBUG  TaskList: ## Running expand_diskimage...
11-12 14:30 DEBUG  TaskList: ## Finished expand_diskimage
11-12 14:30 DEBUG  TaskList: ## Running create_swap_diskimage...
11-12 14:30 DEBUG  TaskList: ## Finished create_swap_diskimage
11-12 14:30 DEBUG  TaskList: ## Running modify_bootloader...
11-12 14:30 DEBUG  TaskList: New task modify_bcd
11-12 14:30 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:30 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 136554.933594 mb free ntfs)
11-12 14:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {da19424c-0d62-11e1-9ab5-00214ff73e3d}
11-12 14:30 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:30 DEBUG  TaskList: New task modify_bcd
11-12 14:30 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:30 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 193677.238281 mb free ntfs)
11-12 14:30 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:30 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:30 DEBUG  TaskList: New task modify_bcd
11-12 14:30 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:30 DEBUG  WindowsBackend: modify_bcd Drive(E: removable 0.0 mb free )
11-12 14:30 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:30 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:30 DEBUG  TaskList: New task modify_bcd
11-12 14:30 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:30 DEBUG  WindowsBackend: modify_bcd Drive(F: removable 0.0 mb free )
11-12 14:30 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:30 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:30 DEBUG  TaskList: New task modify_bcd
11-12 14:30 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:30 DEBUG  WindowsBackend: modify_bcd Drive(G: removable 0.0 mb free )
11-12 14:30 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:30 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:30 DEBUG  TaskList: ## Finished modify_bootloader
11-12 14:30 DEBUG  TaskList: ## Running diskimage_bootloader...
11-12 14:30 DEBUG  WindowsBackend: Copying C:\Users\Mom\AppData\Local\Temp\pylA534.tmp\winboot -> D:\ubuntu\winboot
11-12 14:30 ERROR  TaskList: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'E:\\wubildr'
11-12 14:30 DEBUG  TaskList: # Cancelling tasklist
11-12 14:30 DEBUG  TaskList: # Finished tasklist
11-12 14:30 ERROR  root: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'E:\\wubildr'
11-12 14:33 INFO   root: === wubi 11.10 rev245 ===
11-12 14:33 DEBUG  root: Logfile is c:\users\mom\appdata\local\temp\wubi-11.10-rev245.log
11-12 14:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\wubi.exe"']
11-12 14:33 DEBUG  CommonBackend: data_dir=C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\data
11-12 14:33 DEBUG  WindowsBackend: 7z=C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\bin\7z.exe
11-12 14:33 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-12 14:33 DEBUG  CommonBackend: Fetching basic info...
11-12 14:33 DEBUG  CommonBackend: original_exe=C:\wubi.exe
11-12 14:33 DEBUG  CommonBackend: platform=win32
11-12 14:33 DEBUG  CommonBackend: osname=nt
11-12 14:33 DEBUG  CommonBackend: language=en_US
11-12 14:33 DEBUG  CommonBackend: encoding=cp1252
11-12 14:33 DEBUG  WindowsBackend: arch=amd64
11-12 14:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\data\isolist.ini
11-12 14:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-12 14:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-12 14:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-12 14:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-12 14:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-12 14:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-12 14:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-12 14:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-12 14:33 DEBUG  WindowsBackend: Fetching host info...
11-12 14:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-12 14:33 DEBUG  WindowsBackend: windows version=vista
11-12 14:33 DEBUG  WindowsBackend: windows_version2=Windows (TM) Vista Home Premium
11-12 14:33 DEBUG  WindowsBackend: windows_sp=None
11-12 14:33 DEBUG  WindowsBackend: windows_build=6002
11-12 14:33 DEBUG  WindowsBackend: gmt=-5
11-12 14:33 DEBUG  WindowsBackend: country=US
11-12 14:33 DEBUG  WindowsBackend: timezone=America/New_York
11-12 14:33 DEBUG  WindowsBackend: windows_username=Mom
11-12 14:33 DEBUG  WindowsBackend: user_full_name=Mom
11-12 14:33 DEBUG  WindowsBackend: user_directory=C:\Users\Mom
11-12 14:33 DEBUG  WindowsBackend: windows_language_code=1033
11-12 14:33 DEBUG  WindowsBackend: windows_language=English
11-12 14:33 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
11-12 14:33 DEBUG  WindowsBackend: bootloader=vista
11-12 14:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 136554.089844 mb free ntfs)
11-12 14:33 DEBUG  WindowsBackend: drive=Drive(C: hd 136554.089844 mb free ntfs)
11-12 14:33 DEBUG  WindowsBackend: drive=Drive(D: hd 190121.632813 mb free ntfs)
11-12 14:33 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
11-12 14:33 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-12 14:33 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-12 14:33 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
11-12 14:33 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
11-12 14:33 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
11-12 14:33 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-12 14:33 DEBUG  WindowsBackend: keyboard_id=67699721
11-12 14:33 DEBUG  WindowsBackend: keyboard_layout=us
11-12 14:33 DEBUG  WindowsBackend: keyboard_variant=
11-12 14:33 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-12 14:33 DEBUG  CommonBackend: locale=en_US.UTF-8
11-12 14:33 DEBUG  WindowsBackend: total_memory_mb=4062.14453125
11-12 14:33 DEBUG  CommonBackend: Searching ISOs on USB devices
11-12 14:33 DEBUG  CommonBackend: Searching for local CDs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 INFO   root: Already installed, running the uninstaller...
11-12 14:33 INFO   root: Running the uninstaller...
11-12 14:33 INFO   CommonBackend: This is the uninstaller running
11-12 14:33 DEBUG  WindowsFrontend: __init__...
11-12 14:33 DEBUG  WindowsFrontend: on_init...
11-12 14:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\translations, languages=['en_US', 'en']
11-12 14:33 INFO   root: Received settings
11-12 14:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\translations, languages=['en_US', 'en']
11-12 14:33 DEBUG  TaskList: # Running tasklist...
11-12 14:33 DEBUG  TaskList: ## Running Remove bootloader entry...
11-12 14:33 DEBUG  WindowsBackend: Removing bcd entry {da19424c-0d62-11e1-9ab5-00214ff73e3d}
11-12 14:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
11-12 14:33 DEBUG  WindowsBackend: undo_bootini C:
11-12 14:33 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 136554.089844 mb free ntfs)
11-12 14:33 DEBUG  WindowsBackend: undo_bootini D:
11-12 14:33 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 190121.632813 mb free ntfs)
11-12 14:33 DEBUG  WindowsBackend: undo_bootini E:
11-12 14:33 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 0.0 mb free )
11-12 14:33 DEBUG  WindowsBackend: undo_bootini F:
11-12 14:33 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
11-12 14:33 DEBUG  WindowsBackend: undo_bootini G:
11-12 14:33 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
11-12 14:33 DEBUG  TaskList: ## Finished Remove bootloader entry
11-12 14:33 DEBUG  TaskList: ## Running Remove target dir...
11-12 14:33 DEBUG  CommonBackend: Deleting D:\ubuntu
11-12 14:33 DEBUG  TaskList: ## Finished Remove target dir
11-12 14:33 DEBUG  TaskList: ## Running Remove registry key...
11-12 14:33 DEBUG  TaskList: ## Finished Remove registry key
11-12 14:33 DEBUG  TaskList: # Finished tasklist
11-12 14:33 INFO   root: Almost finished uninstalling
11-12 14:33 INFO   root: Finished uninstallation
11-12 14:33 DEBUG  CommonBackend: Fetching basic info...
11-12 14:33 DEBUG  CommonBackend: original_exe=C:\wubi.exe
11-12 14:33 DEBUG  CommonBackend: platform=win32
11-12 14:33 DEBUG  CommonBackend: osname=nt
11-12 14:33 DEBUG  WindowsBackend: arch=amd64
11-12 14:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\data\isolist.ini
11-12 14:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-12 14:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-12 14:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-12 14:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-12 14:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-12 14:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-12 14:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-12 14:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-12 14:33 DEBUG  WindowsBackend: Fetching host info...
11-12 14:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-12 14:33 DEBUG  WindowsBackend: windows version=vista
11-12 14:33 DEBUG  WindowsBackend: windows_version2=Windows (TM) Vista Home Premium
11-12 14:33 DEBUG  WindowsBackend: windows_sp=None
11-12 14:33 DEBUG  WindowsBackend: windows_build=6002
11-12 14:33 DEBUG  WindowsBackend: gmt=-5
11-12 14:33 DEBUG  WindowsBackend: country=US
11-12 14:33 DEBUG  WindowsBackend: timezone=America/New_York
11-12 14:33 DEBUG  WindowsBackend: windows_username=Mom
11-12 14:33 DEBUG  WindowsBackend: user_full_name=Mom
11-12 14:33 DEBUG  WindowsBackend: user_directory=C:\Users\Mom
11-12 14:33 DEBUG  WindowsBackend: windows_language_code=1033
11-12 14:33 DEBUG  WindowsBackend: windows_language=English
11-12 14:33 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
11-12 14:33 DEBUG  WindowsBackend: bootloader=vista
11-12 14:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 136554.207031 mb free ntfs)
11-12 14:33 DEBUG  WindowsBackend: drive=Drive(C: hd 136554.207031 mb free ntfs)
11-12 14:33 DEBUG  WindowsBackend: drive=Drive(D: hd 193677.238281 mb free ntfs)
11-12 14:33 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
11-12 14:33 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-12 14:33 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-12 14:33 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
11-12 14:33 DEBUG  WindowsBackend: uninstaller_path=None
11-12 14:33 DEBUG  WindowsBackend: previous_target_dir=None
11-12 14:33 DEBUG  WindowsBackend: previous_distro_name=None
11-12 14:33 DEBUG  WindowsBackend: keyboard_id=67699721
11-12 14:33 DEBUG  WindowsBackend: keyboard_layout=us
11-12 14:33 DEBUG  WindowsBackend: keyboard_variant=
11-12 14:33 DEBUG  WindowsBackend: total_memory_mb=4062.14453125
11-12 14:33 DEBUG  CommonBackend: Searching ISOs on USB devices
11-12 14:33 DEBUG  CommonBackend: Searching for local CDs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 INFO   root: Running the installer...
11-12 14:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\translations, languages=['en_US', 'en']
11-12 14:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\translations, languages=['en_US', 'en']
11-12 14:33 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=mom
11-12 14:33 INFO   root: Received settings
11-12 14:33 DEBUG  CommonBackend: Searching for local CD
11-12 14:33 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:33 DEBUG  CommonBackend: Searching for local ISO
11-12 14:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\translations, languages=['en_US', 'en']
11-12 14:33 DEBUG  TaskList: # Running tasklist...
11-12 14:33 DEBUG  TaskList: ## Running select_target_dir...
11-12 14:33 INFO   WindowsBackend: Installing into C:\ubuntu
11-12 14:33 DEBUG  TaskList: ## Finished select_target_dir
11-12 14:33 DEBUG  TaskList: ## Running create_dir_structure...
11-12 14:33 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-12 14:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-12 14:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-12 14:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-12 14:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-12 14:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-12 14:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-12 14:33 DEBUG  TaskList: ## Finished create_dir_structure
11-12 14:33 DEBUG  TaskList: ## Running create_uninstaller...
11-12 14:33 DEBUG  WindowsBackend: Copying uninstaller C:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-12 14:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-12 14:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-12 14:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-12 14:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-12 14:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-12 14:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-12 14:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-12 14:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-12 14:33 DEBUG  TaskList: ## Finished create_uninstaller
11-12 14:33 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-12 14:33 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-12 14:33 DEBUG  TaskList: ## Running get_diskimage...
11-12 14:33 DEBUG  TaskList: New task download
11-12 14:33 DEBUG  TaskList: ### Running download...
11-12 14:33 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
11-12 14:33 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
11-12 14:37 DEBUG  TaskList: ### Finished download
11-12 14:37 DEBUG  downloader: download finished (read 507143012 bytes)
11-12 14:37 DEBUG  TaskList: ## Finished get_diskimage
11-12 14:37 DEBUG  TaskList: ## Running extract_diskimage...
11-12 14:38 DEBUG  TaskList: ## Finished extract_diskimage
11-12 14:38 DEBUG  TaskList: ## Running choose_disk_sizes...
11-12 14:38 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
11-12 14:38 DEBUG  TaskList: ## Finished choose_disk_sizes
11-12 14:38 DEBUG  TaskList: ## Running expand_diskimage...
11-12 14:40 DEBUG  TaskList: ## Finished expand_diskimage
11-12 14:40 DEBUG  TaskList: ## Running create_swap_diskimage...
11-12 14:40 DEBUG  TaskList: ## Finished create_swap_diskimage
11-12 14:40 DEBUG  TaskList: ## Running modify_bootloader...
11-12 14:40 DEBUG  TaskList: New task modify_bcd
11-12 14:40 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:40 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 136554.207031 mb free ntfs)
11-12 14:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {da19424d-0d62-11e1-9ab5-00214ff73e3d}
11-12 14:40 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:40 DEBUG  TaskList: New task modify_bcd
11-12 14:40 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:40 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 193677.238281 mb free ntfs)
11-12 14:40 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:40 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:40 DEBUG  TaskList: New task modify_bcd
11-12 14:40 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:40 DEBUG  WindowsBackend: modify_bcd Drive(E: removable 0.0 mb free )
11-12 14:40 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:40 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:40 DEBUG  TaskList: New task modify_bcd
11-12 14:40 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:40 DEBUG  WindowsBackend: modify_bcd Drive(F: removable 0.0 mb free )
11-12 14:40 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:40 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:40 DEBUG  TaskList: New task modify_bcd
11-12 14:40 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:40 DEBUG  WindowsBackend: modify_bcd Drive(G: removable 0.0 mb free )
11-12 14:40 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:40 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:40 DEBUG  TaskList: ## Finished modify_bootloader
11-12 14:40 DEBUG  TaskList: ## Running diskimage_bootloader...
11-12 14:40 DEBUG  WindowsBackend: Copying C:\Users\Mom\AppData\Local\Temp\pyl531E.tmp\winboot -> C:\ubuntu\winboot
11-12 14:40 ERROR  TaskList: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'E:\\wubildr'
11-12 14:40 DEBUG  TaskList: # Cancelling tasklist
11-12 14:40 DEBUG  TaskList: # Finished tasklist
11-12 14:40 ERROR  root: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'E:\\wubildr'
11-12 14:41 INFO   root: === wubi 11.10 rev245 ===
11-12 14:41 DEBUG  root: Logfile is c:\users\mom\appdata\local\temp\wubi-11.10-rev245.log
11-12 14:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\wubi.exe"']
11-12 14:41 DEBUG  CommonBackend: data_dir=C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\data
11-12 14:41 DEBUG  WindowsBackend: 7z=C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\bin\7z.exe
11-12 14:41 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-12 14:41 DEBUG  CommonBackend: Fetching basic info...
11-12 14:41 DEBUG  CommonBackend: original_exe=C:\wubi.exe
11-12 14:41 DEBUG  CommonBackend: platform=win32
11-12 14:41 DEBUG  CommonBackend: osname=nt
11-12 14:41 DEBUG  CommonBackend: language=en_US
11-12 14:41 DEBUG  CommonBackend: encoding=cp1252
11-12 14:41 DEBUG  WindowsBackend: arch=amd64
11-12 14:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\data\isolist.ini
11-12 14:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-12 14:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-12 14:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-12 14:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-12 14:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-12 14:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-12 14:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-12 14:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-12 14:41 DEBUG  WindowsBackend: Fetching host info...
11-12 14:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-12 14:41 DEBUG  WindowsBackend: windows version=vista
11-12 14:41 DEBUG  WindowsBackend: windows_version2=Windows (TM) Vista Home Premium
11-12 14:41 DEBUG  WindowsBackend: windows_sp=None
11-12 14:41 DEBUG  WindowsBackend: windows_build=6002
11-12 14:41 DEBUG  WindowsBackend: gmt=-5
11-12 14:41 DEBUG  WindowsBackend: country=US
11-12 14:41 DEBUG  WindowsBackend: timezone=America/New_York
11-12 14:41 DEBUG  WindowsBackend: windows_username=Mom
11-12 14:41 DEBUG  WindowsBackend: user_full_name=Mom
11-12 14:41 DEBUG  WindowsBackend: user_directory=C:\Users\Mom
11-12 14:41 DEBUG  WindowsBackend: windows_language_code=1033
11-12 14:41 DEBUG  WindowsBackend: windows_language=English
11-12 14:41 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
11-12 14:41 DEBUG  WindowsBackend: bootloader=vista
11-12 14:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 132998.023438 mb free ntfs)
11-12 14:41 DEBUG  WindowsBackend: drive=Drive(C: hd 132998.023438 mb free ntfs)
11-12 14:41 DEBUG  WindowsBackend: drive=Drive(D: hd 193677.109375 mb free ntfs)
11-12 14:41 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
11-12 14:41 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-12 14:41 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-12 14:41 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
11-12 14:41 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-12 14:41 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-12 14:41 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-12 14:41 DEBUG  WindowsBackend: keyboard_id=67699721
11-12 14:41 DEBUG  WindowsBackend: keyboard_layout=us
11-12 14:41 DEBUG  WindowsBackend: keyboard_variant=
11-12 14:41 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-12 14:41 DEBUG  CommonBackend: locale=en_US.UTF-8
11-12 14:41 DEBUG  WindowsBackend: total_memory_mb=4062.14453125
11-12 14:41 DEBUG  CommonBackend: Searching ISOs on USB devices
11-12 14:41 DEBUG  CommonBackend: Searching for local CDs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 INFO   root: Already installed, running the uninstaller...
11-12 14:41 INFO   root: Running the uninstaller...
11-12 14:41 INFO   CommonBackend: This is the uninstaller running
11-12 14:41 DEBUG  WindowsFrontend: __init__...
11-12 14:41 DEBUG  WindowsFrontend: on_init...
11-12 14:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\translations, languages=['en_US', 'en']
11-12 14:41 INFO   root: Received settings
11-12 14:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\translations, languages=['en_US', 'en']
11-12 14:41 DEBUG  TaskList: # Running tasklist...
11-12 14:41 DEBUG  TaskList: ## Running Remove bootloader entry...
11-12 14:41 DEBUG  WindowsBackend: Removing bcd entry {da19424d-0d62-11e1-9ab5-00214ff73e3d}
11-12 14:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
11-12 14:41 DEBUG  WindowsBackend: undo_bootini C:
11-12 14:41 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 132998.023438 mb free ntfs)
11-12 14:41 DEBUG  WindowsBackend: undo_bootini D:
11-12 14:41 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 193677.109375 mb free ntfs)
11-12 14:41 DEBUG  WindowsBackend: undo_bootini E:
11-12 14:41 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 0.0 mb free )
11-12 14:41 DEBUG  WindowsBackend: undo_bootini F:
11-12 14:41 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
11-12 14:41 DEBUG  WindowsBackend: undo_bootini G:
11-12 14:41 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
11-12 14:41 DEBUG  TaskList: ## Finished Remove bootloader entry
11-12 14:41 DEBUG  TaskList: ## Running Remove target dir...
11-12 14:41 DEBUG  CommonBackend: Deleting C:\ubuntu
11-12 14:41 DEBUG  TaskList: ## Finished Remove target dir
11-12 14:41 DEBUG  TaskList: ## Running Remove registry key...
11-12 14:41 DEBUG  TaskList: ## Finished Remove registry key
11-12 14:41 DEBUG  TaskList: # Finished tasklist
11-12 14:41 INFO   root: Almost finished uninstalling
11-12 14:41 INFO   root: Finished uninstallation
11-12 14:41 DEBUG  CommonBackend: Fetching basic info...
11-12 14:41 DEBUG  CommonBackend: original_exe=C:\wubi.exe
11-12 14:41 DEBUG  CommonBackend: platform=win32
11-12 14:41 DEBUG  CommonBackend: osname=nt
11-12 14:41 DEBUG  WindowsBackend: arch=amd64
11-12 14:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\data\isolist.ini
11-12 14:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-12 14:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-12 14:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-12 14:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-12 14:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-12 14:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-12 14:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-12 14:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-12 14:41 DEBUG  WindowsBackend: Fetching host info...
11-12 14:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-12 14:41 DEBUG  WindowsBackend: windows version=vista
11-12 14:41 DEBUG  WindowsBackend: windows_version2=Windows (TM) Vista Home Premium
11-12 14:41 DEBUG  WindowsBackend: windows_sp=None
11-12 14:41 DEBUG  WindowsBackend: windows_build=6002
11-12 14:41 DEBUG  WindowsBackend: gmt=-5
11-12 14:41 DEBUG  WindowsBackend: country=US
11-12 14:41 DEBUG  WindowsBackend: timezone=America/New_York
11-12 14:41 DEBUG  WindowsBackend: windows_username=Mom
11-12 14:41 DEBUG  WindowsBackend: user_full_name=Mom
11-12 14:41 DEBUG  WindowsBackend: user_directory=C:\Users\Mom
11-12 14:41 DEBUG  WindowsBackend: windows_language_code=1033
11-12 14:41 DEBUG  WindowsBackend: windows_language=English
11-12 14:41 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz
11-12 14:41 DEBUG  WindowsBackend: bootloader=vista
11-12 14:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 136553.617188 mb free ntfs)
11-12 14:41 DEBUG  WindowsBackend: drive=Drive(C: hd 136553.617188 mb free ntfs)
11-12 14:41 DEBUG  WindowsBackend: drive=Drive(D: hd 193677.238281 mb free ntfs)
11-12 14:41 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
11-12 14:41 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
11-12 14:41 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
11-12 14:41 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
11-12 14:41 DEBUG  WindowsBackend: uninstaller_path=None
11-12 14:41 DEBUG  WindowsBackend: previous_target_dir=None
11-12 14:41 DEBUG  WindowsBackend: previous_distro_name=None
11-12 14:41 DEBUG  WindowsBackend: keyboard_id=67699721
11-12 14:41 DEBUG  WindowsBackend: keyboard_layout=us
11-12 14:41 DEBUG  WindowsBackend: keyboard_variant=
11-12 14:41 DEBUG  WindowsBackend: total_memory_mb=4062.14453125
11-12 14:41 DEBUG  CommonBackend: Searching ISOs on USB devices
11-12 14:41 DEBUG  CommonBackend: Searching for local CDs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
11-12 14:41 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:41 INFO   root: Running the installer...
11-12 14:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\translations, languages=['en_US', 'en']
11-12 14:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\translations, languages=['en_US', 'en']
11-12 14:45 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=mom
11-12 14:45 INFO   root: Received settings
11-12 14:45 DEBUG  CommonBackend: Searching for local CD
11-12 14:45 DEBUG  Distro:   checking whether C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp is a valid Ubuntu CD
11-12 14:45 DEBUG  Distro:     does not contain C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\casper\filesystem.squashfs
11-12 14:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-12 14:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-12 14:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-12 14:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-12 14:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-12 14:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-12 14:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-12 14:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-12 14:45 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
11-12 14:45 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
11-12 14:45 DEBUG  CommonBackend: Searching for local ISO
11-12 14:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\translations, languages=['en_US', 'en']
11-12 14:45 DEBUG  TaskList: # Running tasklist...
11-12 14:45 DEBUG  TaskList: ## Running select_target_dir...
11-12 14:45 INFO   WindowsBackend: Installing into C:\ubuntu
11-12 14:45 DEBUG  TaskList: ## Finished select_target_dir
11-12 14:45 DEBUG  TaskList: ## Running create_dir_structure...
11-12 14:45 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-12 14:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-12 14:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-12 14:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-12 14:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-12 14:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-12 14:45 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-12 14:45 DEBUG  TaskList: ## Finished create_dir_structure
11-12 14:45 DEBUG  TaskList: ## Running create_uninstaller...
11-12 14:45 DEBUG  WindowsBackend: Copying uninstaller C:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-12 14:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-12 14:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-12 14:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-12 14:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-12 14:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-12 14:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-12 14:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-12 14:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-12 14:45 DEBUG  TaskList: ## Finished create_uninstaller
11-12 14:45 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-12 14:45 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-12 14:45 DEBUG  TaskList: ## Running get_diskimage...
11-12 14:45 DEBUG  TaskList: New task download
11-12 14:45 DEBUG  TaskList: ### Running download...
11-12 14:45 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
11-12 14:45 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
11-12 14:49 DEBUG  TaskList: ### Finished download
11-12 14:49 DEBUG  downloader: download finished (read 507143012 bytes)
11-12 14:49 DEBUG  TaskList: ## Finished get_diskimage
11-12 14:49 DEBUG  TaskList: ## Running extract_diskimage...
11-12 14:51 DEBUG  TaskList: ## Finished extract_diskimage
11-12 14:51 DEBUG  TaskList: ## Running choose_disk_sizes...
11-12 14:51 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
11-12 14:51 DEBUG  TaskList: ## Finished choose_disk_sizes
11-12 14:51 DEBUG  TaskList: ## Running expand_diskimage...
11-12 14:52 DEBUG  TaskList: ## Finished expand_diskimage
11-12 14:52 DEBUG  TaskList: ## Running create_swap_diskimage...
11-12 14:52 DEBUG  TaskList: ## Finished create_swap_diskimage
11-12 14:52 DEBUG  TaskList: ## Running modify_bootloader...
11-12 14:52 DEBUG  TaskList: New task modify_bcd
11-12 14:52 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:52 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 136553.617188 mb free ntfs)
11-12 14:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {da19424e-0d62-11e1-9ab5-00214ff73e3d}
11-12 14:52 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:52 DEBUG  TaskList: New task modify_bcd
11-12 14:52 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:52 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 193677.238281 mb free ntfs)
11-12 14:52 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:52 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:52 DEBUG  TaskList: New task modify_bcd
11-12 14:52 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:52 DEBUG  WindowsBackend: modify_bcd Drive(E: removable 0.0 mb free )
11-12 14:52 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:52 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:52 DEBUG  TaskList: New task modify_bcd
11-12 14:52 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:52 DEBUG  WindowsBackend: modify_bcd Drive(F: removable 0.0 mb free )
11-12 14:52 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:52 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:52 DEBUG  TaskList: New task modify_bcd
11-12 14:52 DEBUG  TaskList: ### Running modify_bcd...
11-12 14:52 DEBUG  WindowsBackend: modify_bcd Drive(G: removable 0.0 mb free )
11-12 14:52 DEBUG  WindowsBackend: BCD has already been modified
11-12 14:52 DEBUG  TaskList: ### Finished modify_bcd
11-12 14:52 DEBUG  TaskList: ## Finished modify_bootloader
11-12 14:52 DEBUG  TaskList: ## Running diskimage_bootloader...
11-12 14:52 DEBUG  WindowsBackend: Copying C:\Users\Mom\AppData\Local\Temp\pylAAC0.tmp\winboot -> C:\ubuntu\winboot
11-12 14:52 ERROR  TaskList: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'E:\\wubildr'
11-12 14:52 DEBUG  TaskList: # Cancelling tasklist
11-12 14:52 DEBUG  TaskList: # Finished tasklist
11-12 14:52 ERROR  root: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'E:\\wubildr'
```

---

### Post by marinara on 2011-11-12
this is tagged lubuntu.  A mistake on your part?

What version of the installer are you using?
What drive are you installing to?

Are you trying to install to a cd-rom drive?
That wouldn't work... cd-roms are read-only always

---

### Post by socalheel on 2011-11-12
quite possibly a mistake on my part for the tag error.  i'll have a mod correct for me.

trying to install ubuntu 11.10

trying to install to C: drive.

---

### Post by bcbc on 2011-11-12
This is probably the reason: [lpbug]862003[/lpbug] - likely the install is actually successful. Try booting it...

---

### Post by socalheel on 2011-11-13
> **bcbc said:**
> This is probably the reason: [lpbug]862003[/lpbug] - likely the install is actually successful. Try booting it...

you are correct.  after a restart, it went right into ubuntu and then after another restart, i got the dual-boot option.

thanks so much.

---

### Post by mörgæs on 2011-11-13
Good, please mark the thread 'solved'.

---

