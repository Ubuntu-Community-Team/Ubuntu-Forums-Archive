---
title: "Wubi Problem"
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by Vikezor on 2012-01-17
When I try to install I get an error. Here is the log:```
01-17 16:04 INFO   root: === wubi 11.10 rev245 ===
01-17 16:04 DEBUG  root: Logfile is c:\users\viktor\appdata\local\temp\wubi-11.10-rev245.log
01-17 16:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Viktor\\wubi.exe"']
01-17 16:04 DEBUG  CommonBackend: data_dir=C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\data
01-17 16:04 DEBUG  WindowsBackend: 7z=C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\bin\7z.exe
01-17 16:04 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-17 16:04 DEBUG  CommonBackend: Fetching basic info...
01-17 16:04 DEBUG  CommonBackend: original_exe=C:\Users\Viktor\wubi.exe
01-17 16:04 DEBUG  CommonBackend: platform=win32
01-17 16:04 DEBUG  CommonBackend: osname=nt
01-17 16:04 DEBUG  CommonBackend: language=sv_FI
01-17 16:04 DEBUG  CommonBackend: encoding=cp1252
01-17 16:04 DEBUG  WindowsBackend: arch=amd64
01-17 16:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\data\isolist.ini
01-17 16:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-17 16:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-17 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-17 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-17 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-17 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-17 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-17 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-17 16:04 DEBUG  WindowsBackend: Fetching host info...
01-17 16:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-17 16:04 DEBUG  WindowsBackend: windows version=vista
01-17 16:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
01-17 16:04 DEBUG  WindowsBackend: windows_sp=None
01-17 16:04 DEBUG  WindowsBackend: windows_build=7601
01-17 16:04 DEBUG  WindowsBackend: gmt=2
01-17 16:04 DEBUG  WindowsBackend: country=FI
01-17 16:04 DEBUG  WindowsBackend: timezone=Europe/Helsinki
01-17 16:04 DEBUG  WindowsBackend: windows_username=Viktor
01-17 16:04 DEBUG  WindowsBackend: user_full_name=Viktor
01-17 16:04 DEBUG  WindowsBackend: user_directory=C:\Users\Viktor
01-17 16:04 DEBUG  WindowsBackend: windows_language_code=1053
01-17 16:04 DEBUG  WindowsBackend: windows_language=Swedish
01-17 16:04 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II N660 Dual-Core Processor
01-17 16:04 DEBUG  WindowsBackend: bootloader=vista
01-17 16:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 632693.304688 mb free ntfs)
01-17 16:04 DEBUG  WindowsBackend: drive=Drive(C: hd 632693.304688 mb free ntfs)
01-17 16:04 DEBUG  WindowsBackend: drive=Drive(D: hd 1801.0859375 mb free ntfs)
01-17 16:04 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-17 16:04 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
01-17 16:04 DEBUG  WindowsBackend: uninstaller_path=None
01-17 16:04 DEBUG  WindowsBackend: previous_target_dir=None
01-17 16:04 DEBUG  WindowsBackend: previous_distro_name=None
01-17 16:04 DEBUG  WindowsBackend: keyboard_id=69011485
01-17 16:04 DEBUG  WindowsBackend: keyboard_layout=se
01-17 16:04 DEBUG  WindowsBackend: keyboard_variant=
01-17 16:04 DEBUG  CommonBackend: python locale=('sv_FI', 'cp1252')
01-17 16:04 DEBUG  CommonBackend: locale=sv_FI.UTF-8
01-17 16:04 DEBUG  WindowsBackend: total_memory_mb=3834.90234375
01-17 16:04 DEBUG  CommonBackend: Searching ISOs on USB devices
01-17 16:04 DEBUG  CommonBackend: Searching for local CDs
01-17 16:04 DEBUG  Distro:   checking whether C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp is a valid Ubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp is a valid Ubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp is a valid Kubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp is a valid Kubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp is a valid Xubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp is a valid Xubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp is a valid Mythbuntu CD
01-17 16:04 DEBUG  Distro:     does not contain C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp is a valid Mythbuntu CD
01-17 16:04 DEBUG  Distro:     does not contain C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-17 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-17 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-17 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
01-17 16:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
01-17 16:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-17 16:04 INFO   root: Running the installer...
01-17 16:04 DEBUG  WindowsFrontend: __init__...
01-17 16:04 DEBUG  WindowsFrontend: on_init...
01-17 16:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\translations, languages=['sv_FI', 'sv']
01-17 16:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\translations, languages=['sv_FI', 'sv']
01-17 16:04 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=sv_SE, locale=sv_SE.UTF-8, username=viktor
01-17 16:04 INFO   root: Received settings
01-17 16:04 DEBUG  CommonBackend: Searching for local CD
01-17 16:04 DEBUG  Distro:   checking whether C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp is a valid Ubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-17 16:04 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
01-17 16:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-17 16:04 DEBUG  CommonBackend: Searching for local ISO
01-17 16:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\translations, languages=['sv_SE', 'sv']
01-17 16:04 DEBUG  TaskList: # Running tasklist...
01-17 16:04 DEBUG  TaskList: ## Running select_target_dir...
01-17 16:04 INFO   WindowsBackend: Installing into C:\ubuntu
01-17 16:04 DEBUG  TaskList: ## Finished select_target_dir
01-17 16:04 DEBUG  TaskList: ## Running create_dir_structure...
01-17 16:04 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-17 16:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-17 16:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-17 16:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-17 16:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-17 16:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-17 16:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-17 16:04 DEBUG  TaskList: ## Finished create_dir_structure
01-17 16:04 DEBUG  TaskList: ## Running create_uninstaller...
01-17 16:04 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Viktor\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-17 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-17 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-17 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-17 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-17 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
01-17 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-17 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
01-17 16:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
01-17 16:04 DEBUG  TaskList: ## Finished create_uninstaller
01-17 16:04 DEBUG  TaskList: ## Running create_preseed_diskimage...
01-17 16:04 DEBUG  TaskList: ## Finished create_preseed_diskimage
01-17 16:04 DEBUG  TaskList: ## Running get_diskimage...
01-17 16:04 DEBUG  TaskList: New task download
01-17 16:04 DEBUG  TaskList: ### Running download...
01-17 16:04 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
01-17 16:05 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
01-17 16:22 DEBUG  TaskList: ### Finished download
01-17 16:22 DEBUG  downloader: download finished (read 507143012 bytes)
01-17 16:22 DEBUG  TaskList: ## Finished get_diskimage
01-17 16:22 DEBUG  TaskList: ## Running extract_diskimage...
01-17 16:24 DEBUG  TaskList: ## Finished extract_diskimage
01-17 16:24 DEBUG  TaskList: ## Running choose_disk_sizes...
01-17 16:24 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
01-17 16:24 DEBUG  TaskList: ## Finished choose_disk_sizes
01-17 16:24 DEBUG  TaskList: ## Running expand_diskimage...
01-17 16:25 DEBUG  TaskList: ## Finished expand_diskimage
01-17 16:25 DEBUG  TaskList: ## Running create_swap_diskimage...
01-17 16:25 DEBUG  TaskList: ## Finished create_swap_diskimage
01-17 16:25 DEBUG  TaskList: ## Running modify_bootloader...
01-17 16:25 DEBUG  TaskList: New task modify_bcd
01-17 16:25 DEBUG  TaskList: ### Running modify_bcd...
01-17 16:25 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 632693.304688 mb free ntfs)
01-17 16:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {e3045290-b6a0-11e0-9a0d-a562099e6fe3}
01-17 16:25 DEBUG  TaskList: ### Finished modify_bcd
01-17 16:25 DEBUG  TaskList: New task modify_bcd
01-17 16:25 DEBUG  TaskList: ### Running modify_bcd...
01-17 16:25 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 1801.0859375 mb free ntfs)
01-17 16:25 DEBUG  WindowsBackend: BCD has already been modified
01-17 16:25 DEBUG  TaskList: ### Finished modify_bcd
01-17 16:25 DEBUG  TaskList: New task modify_bcd
01-17 16:25 DEBUG  TaskList: ### Running modify_bcd...
01-17 16:25 DEBUG  WindowsBackend: modify_bcd Drive(Q: hd 0.0 mb free )
01-17 16:25 DEBUG  WindowsBackend: BCD has already been modified
01-17 16:25 DEBUG  TaskList: ### Finished modify_bcd
01-17 16:25 DEBUG  TaskList: ## Finished modify_bootloader
01-17 16:25 DEBUG  TaskList: ## Running diskimage_bootloader...
01-17 16:25 DEBUG  WindowsBackend: Copying C:\Users\Viktor\AppData\Local\Temp\pylD365.tmp\winboot -> C:\ubuntu\winboot
01-17 16:25 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
01-17 16:25 DEBUG  TaskList: # Cancelling tasklist
01-17 16:25 DEBUG  TaskList: # Finished tasklist
01-17 16:25 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
```Also, what does this mean?
[IMG]http://img833.imageshack.us/img833/4140/skrmklippg.png[/IMG]

---

