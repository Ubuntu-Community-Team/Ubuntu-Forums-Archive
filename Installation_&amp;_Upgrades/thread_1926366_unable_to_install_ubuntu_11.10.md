---
title: "unable to install ubuntu 11.10"
date: 2012-02-16
forum: Installation &amp; Upgrades
---

### Post by GuruDevil on 2012-02-16
hey guys i am new to open source systems....i am trying to install ubuntu 11.10 on a system already installed with win 7......there is some error of permission that i keep getting and installation isnt completed.......the error is:

An Error occurred

Permission Denied

Please readfor more information the log file 
c:users\user\appdata\local\temp\wubi-11.10-rev245.log

please can any body help me with this...how do i properly install 11.10....thanx

---

### Post by Simple Name on 2012-02-16
What is inside ( copy/paste in [code] tags ) the specified log file ?

---

### Post by Gwaro on 2012-02-16
> **GuruDevil said:**
> hey guys i am new to open source systems....i am trying to install ubuntu 11.10 on a system already installed with win 7......there is some error of permission that i keep getting and installation isnt completed.......the error is:

An Error occurred

Permission Denied

Please readfor more information the log file 
c:users\user\appdata\local\temp\wubi-11.10-rev245.log

please can any body help me with this...how do i properly install 11.10....thanx


What kind of install are you carrying out/want? Install inside windows or Dual-booting each on its own partition or Ubuntu alone?

---

### Post by ranfan on 2012-02-19
Same problem here. I dont know where it came from and Ive been having problems reinstalling it after removing it the first time. I was installing it with windows via wubi

```
01-21 13:35 INFO   root: === wubi 11.10 rev245 ===
01-21 13:35 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-11.10-rev245.log
01-21 13:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Administrator\\Downloads\\wubi.exe"']
01-21 13:35 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\data
01-21 13:35 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\bin\7z.exe
01-21 13:35 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-21 13:35 DEBUG  CommonBackend: Fetching basic info...
01-21 13:35 DEBUG  CommonBackend: original_exe=C:\Users\Administrator\Downloads\wubi.exe
01-21 13:35 DEBUG  CommonBackend: platform=win32
01-21 13:35 DEBUG  CommonBackend: osname=nt
01-21 13:35 DEBUG  CommonBackend: language=en_US
01-21 13:35 DEBUG  CommonBackend: encoding=cp1252
01-21 13:35 DEBUG  WindowsBackend: arch=amd64
01-21 13:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\data\isolist.ini
01-21 13:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-21 13:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-21 13:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-21 13:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-21 13:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-21 13:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-21 13:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-21 13:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-21 13:35 DEBUG  WindowsBackend: Fetching host info...
01-21 13:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-21 13:35 DEBUG  WindowsBackend: windows version=vista
01-21 13:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-21 13:35 DEBUG  WindowsBackend: windows_sp=Service Pack 1
01-21 13:35 DEBUG  WindowsBackend: windows_build=7601
01-21 13:35 DEBUG  WindowsBackend: gmt=-5
01-21 13:35 DEBUG  WindowsBackend: country=US
01-21 13:35 DEBUG  WindowsBackend: timezone=America/New_York
01-21 13:35 DEBUG  WindowsBackend: windows_username=Administrator
01-21 13:35 DEBUG  WindowsBackend: user_full_name=Administrator
01-21 13:35 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
01-21 13:35 DEBUG  WindowsBackend: windows_language_code=1033
01-21 13:35 DEBUG  WindowsBackend: windows_language=English
01-21 13:35 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
01-21 13:35 DEBUG  WindowsBackend: bootloader=vista
01-21 13:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 86682.4375 mb free ntfs)
01-21 13:35 DEBUG  WindowsBackend: drive=Drive(C: hd 86682.4375 mb free ntfs)
01-21 13:35 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
01-21 13:35 DEBUG  WindowsBackend: uninstaller_path=None
01-21 13:35 DEBUG  WindowsBackend: previous_target_dir=None
01-21 13:35 DEBUG  WindowsBackend: previous_distro_name=None
01-21 13:35 DEBUG  WindowsBackend: keyboard_id=67699721
01-21 13:35 DEBUG  WindowsBackend: keyboard_layout=us
01-21 13:35 DEBUG  WindowsBackend: keyboard_variant=
01-21 13:35 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-21 13:35 DEBUG  CommonBackend: locale=en_US.UTF-8
01-21 13:35 DEBUG  WindowsBackend: total_memory_mb=1013.359375
01-21 13:35 DEBUG  CommonBackend: Searching ISOs on USB devices
01-21 13:35 DEBUG  CommonBackend: Searching for local CDs
01-21 13:35 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp is a valid Ubuntu CD
01-21 13:35 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\casper\filesystem.squashfs
01-21 13:35 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp is a valid Ubuntu CD
01-21 13:35 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\casper\filesystem.squashfs
01-21 13:35 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp is a valid Kubuntu CD
01-21 13:35 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\casper\filesystem.squashfs
01-21 13:35 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp is a valid Kubuntu CD
01-21 13:35 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\casper\filesystem.squashfs
01-21 13:35 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp is a valid Xubuntu CD
01-21 13:35 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\casper\filesystem.squashfs
01-21 13:35 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp is a valid Xubuntu CD
01-21 13:35 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\casper\filesystem.squashfs
01-21 13:35 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp is a valid Mythbuntu CD
01-21 13:35 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\casper\filesystem.squashfs
01-21 13:35 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp is a valid Mythbuntu CD
01-21 13:35 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\casper\filesystem.squashfs
01-21 13:35 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
01-21 13:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 13:35 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
01-21 13:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 13:35 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
01-21 13:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 13:35 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
01-21 13:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 13:35 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
01-21 13:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 13:35 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
01-21 13:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 13:35 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
01-21 13:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 13:35 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
01-21 13:35 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 13:35 INFO   root: Running the installer...
01-21 13:35 DEBUG  WindowsFrontend: __init__...
01-21 13:35 DEBUG  WindowsFrontend: on_init...
01-21 13:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\translations, languages=['en_US', 'en']
01-21 13:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\translations, languages=['en_US', 'en']
01-21 13:36 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=nta
01-21 13:36 INFO   root: Received settings
01-21 13:36 DEBUG  CommonBackend: Searching for local CD
01-21 13:36 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp is a valid Ubuntu CD
01-21 13:36 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\casper\filesystem.squashfs
01-21 13:36 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
01-21 13:36 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 13:36 DEBUG  CommonBackend: Searching for local ISO
01-21 13:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\translations, languages=['en_US', 'en']
01-21 13:36 DEBUG  TaskList: # Running tasklist...
01-21 13:36 DEBUG  TaskList: ## Running select_target_dir...
01-21 13:36 INFO   WindowsBackend: Installing into C:\ubuntu
01-21 13:36 DEBUG  TaskList: ## Finished select_target_dir
01-21 13:36 DEBUG  TaskList: ## Running create_dir_structure...
01-21 13:36 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-21 13:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-21 13:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-21 13:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-21 13:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-21 13:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-21 13:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-21 13:36 DEBUG  TaskList: ## Finished create_dir_structure
01-21 13:36 DEBUG  TaskList: ## Running create_uninstaller...
01-21 13:36 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Administrator\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-21 13:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-21 13:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-21 13:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-21 13:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-21 13:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
01-21 13:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-21 13:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
01-21 13:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
01-21 13:36 DEBUG  TaskList: ## Finished create_uninstaller
01-21 13:36 DEBUG  TaskList: ## Running create_preseed_diskimage...
01-21 13:36 DEBUG  TaskList: ## Finished create_preseed_diskimage
01-21 13:36 DEBUG  TaskList: ## Running get_diskimage...
01-21 13:36 DEBUG  TaskList: New task download
01-21 13:36 DEBUG  TaskList: ### Running download...
01-21 13:36 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
01-21 13:36 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
01-21 14:06 DEBUG  TaskList: ### Finished download
01-21 14:06 DEBUG  downloader: download finished (read 507143012 bytes)
01-21 14:06 DEBUG  TaskList: ## Finished get_diskimage
01-21 14:06 DEBUG  TaskList: ## Running extract_diskimage...
01-21 14:09 DEBUG  TaskList: ## Finished extract_diskimage
01-21 14:09 DEBUG  TaskList: ## Running choose_disk_sizes...
01-21 14:09 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
01-21 14:09 DEBUG  TaskList: ## Finished choose_disk_sizes
01-21 14:09 DEBUG  TaskList: ## Running expand_diskimage...
01-21 14:12 DEBUG  TaskList: ## Finished expand_diskimage
01-21 14:12 DEBUG  TaskList: ## Running create_swap_diskimage...
01-21 14:12 DEBUG  TaskList: ## Finished create_swap_diskimage
01-21 14:12 DEBUG  TaskList: ## Running modify_bootloader...
01-21 14:12 DEBUG  TaskList: New task modify_bcd
01-21 14:12 DEBUG  TaskList: ### Running modify_bcd...
01-21 14:12 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 86682.4375 mb free ntfs)
01-21 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {d390b265-4463-11e1-81ad-0026b9e2135e}
01-21 14:12 DEBUG  TaskList: ### Finished modify_bcd
01-21 14:12 DEBUG  TaskList: New task modify_bcd
01-21 14:12 DEBUG  TaskList: ### Running modify_bcd...
01-21 14:12 DEBUG  WindowsBackend: modify_bcd Drive(Q: hd 0.0 mb free )
01-21 14:12 DEBUG  WindowsBackend: BCD has already been modified
01-21 14:12 DEBUG  TaskList: ### Finished modify_bcd
01-21 14:12 DEBUG  TaskList: ## Finished modify_bootloader
01-21 14:12 DEBUG  TaskList: ## Running diskimage_bootloader...
01-21 14:12 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pylB34D.tmp\winboot -> C:\ubuntu\winboot
01-21 14:12 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
01-21 14:12 DEBUG  TaskList: # Cancelling tasklist
01-21 14:12 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
01-21 14:12 DEBUG  TaskList: # Finished tasklist
01-21 14:44 INFO   root: === wubi 11.10 rev245 ===
01-21 14:44 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-11.10-rev245.log
01-21 14:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Administrator\\Downloads\\wubi.exe"']
01-21 14:44 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp\data
01-21 14:44 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp\bin\7z.exe
01-21 14:44 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-21 14:44 DEBUG  CommonBackend: Fetching basic info...
01-21 14:44 DEBUG  CommonBackend: original_exe=C:\Users\Administrator\Downloads\wubi.exe
01-21 14:44 DEBUG  CommonBackend: platform=win32
01-21 14:44 DEBUG  CommonBackend: osname=nt
01-21 14:44 DEBUG  CommonBackend: language=en_US
01-21 14:44 DEBUG  CommonBackend: encoding=cp1252
01-21 14:44 DEBUG  WindowsBackend: arch=amd64
01-21 14:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp\data\isolist.ini
01-21 14:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-21 14:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-21 14:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-21 14:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-21 14:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-21 14:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-21 14:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-21 14:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-21 14:44 DEBUG  WindowsBackend: Fetching host info...
01-21 14:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-21 14:44 DEBUG  WindowsBackend: windows version=vista
01-21 14:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
01-21 14:44 DEBUG  WindowsBackend: windows_sp=Service Pack 1
01-21 14:44 DEBUG  WindowsBackend: windows_build=7601
01-21 14:44 DEBUG  WindowsBackend: gmt=-5
01-21 14:44 DEBUG  WindowsBackend: country=US
01-21 14:44 DEBUG  WindowsBackend: timezone=America/New_York
01-21 14:44 DEBUG  WindowsBackend: windows_username=Administrator
01-21 14:44 DEBUG  WindowsBackend: user_full_name=Administrator
01-21 14:44 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
01-21 14:44 DEBUG  WindowsBackend: windows_language_code=1033
01-21 14:44 DEBUG  WindowsBackend: windows_language=English
01-21 14:44 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
01-21 14:44 DEBUG  WindowsBackend: bootloader=vista
01-21 14:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 83588.4375 mb free ntfs)
01-21 14:44 DEBUG  WindowsBackend: drive=Drive(C: hd 83588.4375 mb free ntfs)
01-21 14:44 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
01-21 14:44 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-21 14:44 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-21 14:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-21 14:44 DEBUG  WindowsBackend: keyboard_id=67699721
01-21 14:44 DEBUG  WindowsBackend: keyboard_layout=us
01-21 14:44 DEBUG  WindowsBackend: keyboard_variant=
01-21 14:44 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-21 14:44 DEBUG  CommonBackend: locale=en_US.UTF-8
01-21 14:44 DEBUG  WindowsBackend: total_memory_mb=1013.359375
01-21 14:44 DEBUG  CommonBackend: Searching ISOs on USB devices
01-21 14:44 DEBUG  CommonBackend: Searching for local CDs
01-21 14:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp is a valid Ubuntu CD
01-21 14:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp\casper\filesystem.squashfs
01-21 14:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp is a valid Ubuntu CD
01-21 14:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp\casper\filesystem.squashfs
01-21 14:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp is a valid Kubuntu CD
01-21 14:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp\casper\filesystem.squashfs
01-21 14:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp is a valid Kubuntu CD
01-21 14:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp\casper\filesystem.squashfs
01-21 14:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp is a valid Xubuntu CD
01-21 14:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp\casper\filesystem.squashfs
01-21 14:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp is a valid Xubuntu CD
01-21 14:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp\casper\filesystem.squashfs
01-21 14:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp is a valid Mythbuntu CD
01-21 14:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp\casper\filesystem.squashfs
01-21 14:44 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp is a valid Mythbuntu CD
01-21 14:44 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp\casper\filesystem.squashfs
01-21 14:44 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
01-21 14:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 14:44 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
01-21 14:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 14:44 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
01-21 14:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 14:44 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
01-21 14:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 14:44 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
01-21 14:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 14:44 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
01-21 14:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 14:44 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
01-21 14:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 14:44 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
01-21 14:44 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
01-21 14:44 INFO   root: Already installed, running the uninstaller...
01-21 14:44 INFO   root: Running the uninstaller...
01-21 14:44 INFO   CommonBackend: This is the uninstaller running
01-21 14:44 DEBUG  WindowsFrontend: __init__...
01-21 14:44 DEBUG  WindowsFrontend: on_init...
01-21 14:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylFB46.tmp\translations, languages=['en_US', 'en']
01-21 14:49 INFO   WindowsFrontend: Operation cancelled
01-21 14:49 DEBUG  WindowsFrontend: frontend.quit
01-21 14:49 DEBUG  WindowsFrontend: frontend.on_quit
01-21 14:49 DEBUG  root: application.on_quit
01-21 14:49 INFO   root: sys.exit
02-03 18:50 INFO   root: === wubi 11.10 rev245 ===
02-03 18:50 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-11.10-rev245.log
02-03 18:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Administrator\\Desktop\\wubi.exe"']
02-03 18:50 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\data
02-03 18:50 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\bin\7z.exe
02-03 18:50 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-03 18:50 DEBUG  CommonBackend: Fetching basic info...
02-03 18:50 DEBUG  CommonBackend: original_exe=C:\Users\Administrator\Desktop\wubi.exe
02-03 18:50 DEBUG  CommonBackend: platform=win32
02-03 18:50 DEBUG  CommonBackend: osname=nt
02-03 18:50 DEBUG  CommonBackend: language=en_US
02-03 18:50 DEBUG  CommonBackend: encoding=cp1252
02-03 18:50 DEBUG  WindowsBackend: arch=amd64
02-03 18:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\data\isolist.ini
02-03 18:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-03 18:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-03 18:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-03 18:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-03 18:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-03 18:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-03 18:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-03 18:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-03 18:50 DEBUG  WindowsBackend: Fetching host info...
02-03 18:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-03 18:50 DEBUG  WindowsBackend: windows version=vista
02-03 18:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
02-03 18:50 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-03 18:50 DEBUG  WindowsBackend: windows_build=7601
02-03 18:50 DEBUG  WindowsBackend: gmt=-5
02-03 18:50 DEBUG  WindowsBackend: country=US
02-03 18:50 DEBUG  WindowsBackend: timezone=America/New_York
02-03 18:50 DEBUG  WindowsBackend: windows_username=Administrator
02-03 18:50 DEBUG  WindowsBackend: user_full_name=Administrator
02-03 18:50 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
02-03 18:50 DEBUG  WindowsBackend: windows_language_code=1033
02-03 18:50 DEBUG  WindowsBackend: windows_language=English
02-03 18:50 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
02-03 18:50 DEBUG  WindowsBackend: bootloader=vista
02-03 18:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 73200.6875 mb free ntfs)
02-03 18:50 DEBUG  WindowsBackend: drive=Drive(C: hd 73200.6875 mb free ntfs)
02-03 18:50 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-03 18:50 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-03 18:50 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-03 18:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-03 18:50 DEBUG  WindowsBackend: keyboard_id=67699721
02-03 18:50 DEBUG  WindowsBackend: keyboard_layout=us
02-03 18:50 DEBUG  WindowsBackend: keyboard_variant=
02-03 18:50 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-03 18:50 DEBUG  CommonBackend: locale=en_US.UTF-8
02-03 18:50 DEBUG  WindowsBackend: total_memory_mb=1013.359375
02-03 18:50 DEBUG  CommonBackend: Searching ISOs on USB devices
02-03 18:50 DEBUG  CommonBackend: Searching for local CDs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Ubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Ubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Kubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Kubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Xubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Xubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Mythbuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Mythbuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 INFO   root: Already installed, running the uninstaller...
02-03 18:50 INFO   root: Running the uninstaller...
02-03 18:50 INFO   CommonBackend: This is the uninstaller running
02-03 18:50 DEBUG  WindowsFrontend: __init__...
02-03 18:50 DEBUG  WindowsFrontend: on_init...
02-03 18:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\translations, languages=['en_US', 'en']
02-03 18:50 INFO   root: Received settings
02-03 18:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\translations, languages=['en_US', 'en']
02-03 18:50 DEBUG  TaskList: # Running tasklist...
02-03 18:50 DEBUG  TaskList: ## Running Remove bootloader entry...
02-03 18:50 DEBUG  WindowsBackend: Removing bcd entry {d390b265-4463-11e1-81ad-0026b9e2135e}
02-03 18:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
02-03 18:50 DEBUG  WindowsBackend: undo_bootini C:
02-03 18:50 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 73200.6875 mb free ntfs)
02-03 18:50 DEBUG  WindowsBackend: undo_bootini Q:
02-03 18:50 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
02-03 18:50 DEBUG  TaskList: ## Finished Remove bootloader entry
02-03 18:50 DEBUG  TaskList: ## Running Remove target dir...
02-03 18:50 DEBUG  CommonBackend: Deleting C:\ubuntu
02-03 18:50 DEBUG  TaskList: ## Finished Remove target dir
02-03 18:50 DEBUG  TaskList: ## Running Remove registry key...
02-03 18:50 DEBUG  TaskList: ## Finished Remove registry key
02-03 18:50 DEBUG  TaskList: # Finished tasklist
02-03 18:50 INFO   root: Almost finished uninstalling
02-03 18:50 INFO   root: Finished uninstallation
02-03 18:50 DEBUG  CommonBackend: Fetching basic info...
02-03 18:50 DEBUG  CommonBackend: original_exe=C:\Users\Administrator\Desktop\wubi.exe
02-03 18:50 DEBUG  CommonBackend: platform=win32
02-03 18:50 DEBUG  CommonBackend: osname=nt
02-03 18:50 DEBUG  WindowsBackend: arch=amd64
02-03 18:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\data\isolist.ini
02-03 18:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-03 18:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-03 18:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-03 18:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-03 18:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-03 18:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-03 18:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-03 18:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-03 18:50 DEBUG  WindowsBackend: Fetching host info...
02-03 18:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-03 18:50 DEBUG  WindowsBackend: windows version=vista
02-03 18:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
02-03 18:50 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-03 18:50 DEBUG  WindowsBackend: windows_build=7601
02-03 18:50 DEBUG  WindowsBackend: gmt=-5
02-03 18:50 DEBUG  WindowsBackend: country=US
02-03 18:50 DEBUG  WindowsBackend: timezone=America/New_York
02-03 18:50 DEBUG  WindowsBackend: windows_username=Administrator
02-03 18:50 DEBUG  WindowsBackend: user_full_name=Administrator
02-03 18:50 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
02-03 18:50 DEBUG  WindowsBackend: windows_language_code=1033
02-03 18:50 DEBUG  WindowsBackend: windows_language=English
02-03 18:50 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
02-03 18:50 DEBUG  WindowsBackend: bootloader=vista
02-03 18:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 76517.109375 mb free ntfs)
02-03 18:50 DEBUG  WindowsBackend: drive=Drive(C: hd 76517.109375 mb free ntfs)
02-03 18:50 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-03 18:50 DEBUG  WindowsBackend: uninstaller_path=None
02-03 18:50 DEBUG  WindowsBackend: previous_target_dir=None
02-03 18:50 DEBUG  WindowsBackend: previous_distro_name=None
02-03 18:50 DEBUG  WindowsBackend: keyboard_id=67699721
02-03 18:50 DEBUG  WindowsBackend: keyboard_layout=us
02-03 18:50 DEBUG  WindowsBackend: keyboard_variant=
02-03 18:50 DEBUG  WindowsBackend: total_memory_mb=1013.359375
02-03 18:50 DEBUG  CommonBackend: Searching ISOs on USB devices
02-03 18:50 DEBUG  CommonBackend: Searching for local CDs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Ubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Ubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Kubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Kubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Xubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Xubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Mythbuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp is a valid Mythbuntu CD
02-03 18:50 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-03 18:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 18:50 INFO   root: Running the installer...
02-03 18:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\translations, languages=['en_US', 'en']
02-03 18:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl27FC.tmp\translations, languages=['en_US', 'en']
02-03 18:50 INFO   WindowsFrontend: Operation cancelled
02-03 18:50 DEBUG  WindowsFrontend: frontend.quit
02-03 18:50 DEBUG  WindowsFrontend: frontend.on_quit
02-03 18:50 DEBUG  root: application.on_quit
02-03 18:50 INFO   root: sys.exit
02-03 19:04 INFO   root: === wubi 11.10 rev245 ===
02-03 19:04 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-11.10-rev245.log
02-03 19:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Administrator\\Desktop\\wubi.exe"']
02-03 19:04 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp\data
02-03 19:04 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp\bin\7z.exe
02-03 19:04 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-03 19:04 DEBUG  CommonBackend: Fetching basic info...
02-03 19:04 DEBUG  CommonBackend: original_exe=C:\Users\Administrator\Desktop\wubi.exe
02-03 19:04 DEBUG  CommonBackend: platform=win32
02-03 19:04 DEBUG  CommonBackend: osname=nt
02-03 19:04 DEBUG  CommonBackend: language=en_US
02-03 19:04 DEBUG  CommonBackend: encoding=cp1252
02-03 19:04 DEBUG  WindowsBackend: arch=amd64
02-03 19:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp\data\isolist.ini
02-03 19:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-03 19:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-03 19:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-03 19:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-03 19:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-03 19:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-03 19:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-03 19:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-03 19:04 DEBUG  WindowsBackend: Fetching host info...
02-03 19:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-03 19:04 DEBUG  WindowsBackend: windows version=vista
02-03 19:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
02-03 19:04 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-03 19:04 DEBUG  WindowsBackend: windows_build=7601
02-03 19:04 DEBUG  WindowsBackend: gmt=-5
02-03 19:04 DEBUG  WindowsBackend: country=US
02-03 19:04 DEBUG  WindowsBackend: timezone=America/New_York
02-03 19:04 DEBUG  WindowsBackend: windows_username=Administrator
02-03 19:04 DEBUG  WindowsBackend: user_full_name=Administrator
02-03 19:04 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
02-03 19:04 DEBUG  WindowsBackend: windows_language_code=1033
02-03 19:04 DEBUG  WindowsBackend: windows_language=English
02-03 19:04 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
02-03 19:04 DEBUG  WindowsBackend: bootloader=vista
02-03 19:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 78008.8164063 mb free ntfs)
02-03 19:04 DEBUG  WindowsBackend: drive=Drive(C: hd 78008.8164063 mb free ntfs)
02-03 19:04 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-03 19:04 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-03 19:04 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-03 19:04 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-03 19:04 DEBUG  WindowsBackend: keyboard_id=67699721
02-03 19:04 DEBUG  WindowsBackend: keyboard_layout=us
02-03 19:04 DEBUG  WindowsBackend: keyboard_variant=
02-03 19:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-03 19:04 DEBUG  CommonBackend: locale=en_US.UTF-8
02-03 19:04 DEBUG  WindowsBackend: total_memory_mb=1013.359375
02-03 19:04 DEBUG  CommonBackend: Searching ISOs on USB devices
02-03 19:04 DEBUG  CommonBackend: Searching for local CDs
02-03 19:04 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp is a valid Ubuntu CD
02-03 19:04 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
02-03 19:04 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp is a valid Ubuntu CD
02-03 19:04 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
02-03 19:04 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp is a valid Kubuntu CD
02-03 19:04 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
02-03 19:04 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp is a valid Kubuntu CD
02-03 19:04 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
02-03 19:04 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp is a valid Xubuntu CD
02-03 19:04 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
02-03 19:04 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp is a valid Xubuntu CD
02-03 19:04 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
02-03 19:04 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp is a valid Mythbuntu CD
02-03 19:04 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
02-03 19:04 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp is a valid Mythbuntu CD
02-03 19:04 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp\casper\filesystem.squashfs
02-03 19:04 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-03 19:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 19:04 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-03 19:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 19:04 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-03 19:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 19:04 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-03 19:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 19:04 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-03 19:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 19:04 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-03 19:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 19:04 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-03 19:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 19:04 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-03 19:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-03 19:04 INFO   root: Running the installer...
02-03 19:04 DEBUG  WindowsFrontend: __init__...
02-03 19:04 DEBUG  WindowsFrontend: on_init...
02-03 19:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp\translations, languages=['en_US', 'en']
02-03 19:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE1A7.tmp\translations, languages=['en_US', 'en']
02-03 19:05 INFO   WindowsFrontend: Operation cancelled
02-03 19:05 DEBUG  WindowsFrontend: frontend.quit
02-03 19:05 DEBUG  WindowsFrontend: frontend.on_quit
02-03 19:05 DEBUG  root: application.on_quit
02-03 19:05 INFO   root: sys.exit
02-16 08:57 INFO   root: === wubi 11.10 rev245 ===
02-16 08:57 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-11.10-rev245.log
02-16 08:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Administrator\\Desktop\\wubi.exe"']
02-16 08:57 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp\data
02-16 08:57 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp\bin\7z.exe
02-16 08:57 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-16 08:57 DEBUG  CommonBackend: Fetching basic info...
02-16 08:57 DEBUG  CommonBackend: original_exe=C:\Users\Administrator\Desktop\wubi.exe
02-16 08:57 DEBUG  CommonBackend: platform=win32
02-16 08:57 DEBUG  CommonBackend: osname=nt
02-16 08:57 DEBUG  CommonBackend: language=en_US
02-16 08:57 DEBUG  CommonBackend: encoding=cp1252
02-16 08:57 DEBUG  WindowsBackend: arch=amd64
02-16 08:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp\data\isolist.ini
02-16 08:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-16 08:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-16 08:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-16 08:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-16 08:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-16 08:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-16 08:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-16 08:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-16 08:57 DEBUG  WindowsBackend: Fetching host info...
02-16 08:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-16 08:57 DEBUG  WindowsBackend: windows version=vista
02-16 08:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
02-16 08:57 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-16 08:57 DEBUG  WindowsBackend: windows_build=7601
02-16 08:57 DEBUG  WindowsBackend: gmt=-5
02-16 08:57 DEBUG  WindowsBackend: country=US
02-16 08:57 DEBUG  WindowsBackend: timezone=America/New_York
02-16 08:57 DEBUG  WindowsBackend: windows_username=Administrator
02-16 08:57 DEBUG  WindowsBackend: user_full_name=Administrator
02-16 08:57 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
02-16 08:57 DEBUG  WindowsBackend: windows_language_code=1033
02-16 08:57 DEBUG  WindowsBackend: windows_language=English
02-16 08:57 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
02-16 08:57 DEBUG  WindowsBackend: bootloader=vista
02-16 08:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 38092.6367188 mb free ntfs)
02-16 08:57 DEBUG  WindowsBackend: drive=Drive(C: hd 38092.6367188 mb free ntfs)
02-16 08:57 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-16 08:57 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-16 08:57 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-16 08:57 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-16 08:57 DEBUG  WindowsBackend: keyboard_id=67699721
02-16 08:57 DEBUG  WindowsBackend: keyboard_layout=us
02-16 08:57 DEBUG  WindowsBackend: keyboard_variant=
02-16 08:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-16 08:57 DEBUG  CommonBackend: locale=en_US.UTF-8
02-16 08:57 DEBUG  WindowsBackend: total_memory_mb=1013.359375
02-16 08:57 DEBUG  CommonBackend: Searching ISOs on USB devices
02-16 08:57 DEBUG  CommonBackend: Searching for local CDs
02-16 08:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp is a valid Ubuntu CD
02-16 08:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp\casper\filesystem.squashfs
02-16 08:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp is a valid Ubuntu CD
02-16 08:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp\casper\filesystem.squashfs
02-16 08:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp is a valid Kubuntu CD
02-16 08:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp\casper\filesystem.squashfs
02-16 08:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp is a valid Kubuntu CD
02-16 08:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp\casper\filesystem.squashfs
02-16 08:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp is a valid Xubuntu CD
02-16 08:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp\casper\filesystem.squashfs
02-16 08:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp is a valid Xubuntu CD
02-16 08:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp\casper\filesystem.squashfs
02-16 08:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp is a valid Mythbuntu CD
02-16 08:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp\casper\filesystem.squashfs
02-16 08:57 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp is a valid Mythbuntu CD
02-16 08:57 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp\casper\filesystem.squashfs
02-16 08:57 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 08:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:57 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 08:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:57 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 08:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:57 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 08:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:57 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 08:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:57 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 08:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:57 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 08:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:57 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 08:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:57 INFO   root: Running the installer...
02-16 08:57 DEBUG  WindowsFrontend: __init__...
02-16 08:57 DEBUG  WindowsFrontend: on_init...
02-16 08:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp\translations, languages=['en_US', 'en']
02-16 08:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp\translations, languages=['en_US', 'en']
02-16 08:58 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=gerald
02-16 08:58 INFO   root: Received settings
02-16 08:58 DEBUG  CommonBackend: Searching for local CD
02-16 08:58 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp is a valid Ubuntu CD
02-16 08:58 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp\casper\filesystem.squashfs
02-16 08:58 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 08:58 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:58 DEBUG  CommonBackend: Searching for local ISO
02-16 08:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl820A.tmp\translations, languages=['en_US', 'en']
02-16 08:58 DEBUG  TaskList: # Running tasklist...
02-16 08:58 DEBUG  TaskList: ## Running select_target_dir...
02-16 08:58 INFO   WindowsBackend: Installing into C:\ubuntu
02-16 08:58 DEBUG  TaskList: ## Finished select_target_dir
02-16 08:58 DEBUG  TaskList: ## Running create_dir_structure...
02-16 08:58 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-16 08:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-16 08:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-16 08:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-16 08:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-16 08:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-16 08:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-16 08:58 DEBUG  TaskList: ## Finished create_dir_structure
02-16 08:58 DEBUG  TaskList: ## Running create_uninstaller...
02-16 08:58 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Administrator\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-16 08:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-16 08:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-16 08:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-16 08:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-16 08:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-16 08:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-16 08:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
02-16 08:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
02-16 08:58 DEBUG  TaskList: ## Finished create_uninstaller
02-16 08:58 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-16 08:58 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-16 08:58 DEBUG  TaskList: ## Running get_diskimage...
02-16 08:58 DEBUG  TaskList: New task download
02-16 08:58 DEBUG  TaskList: ### Running download...
02-16 08:58 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-16 08:58 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-16 08:59 INFO   WindowsFrontend: Operation cancelled
02-16 08:59 DEBUG  WindowsFrontend: frontend.quit
02-16 08:59 DEBUG  WindowsFrontend: frontend.on_quit
02-16 08:59 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
02-16 08:59 DEBUG  TaskList: # Cancelling tasklist
02-16 08:59 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
02-16 08:59 DEBUG  root: application.on_quit
02-16 08:59 DEBUG  root: Forceful exit
02-16 08:59 INFO   root: sys.exit
02-16 08:59 INFO   root: === wubi 11.10 rev245 ===
02-16 08:59 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-11.10-rev245.log
02-16 08:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Administrator\\Desktop\\wubi.exe"']
02-16 08:59 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\data
02-16 08:59 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\bin\7z.exe
02-16 08:59 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-16 08:59 DEBUG  CommonBackend: Fetching basic info...
02-16 08:59 DEBUG  CommonBackend: original_exe=C:\Users\Administrator\Desktop\wubi.exe
02-16 08:59 DEBUG  CommonBackend: platform=win32
02-16 08:59 DEBUG  CommonBackend: osname=nt
02-16 08:59 DEBUG  CommonBackend: language=en_US
02-16 08:59 DEBUG  CommonBackend: encoding=cp1252
02-16 08:59 DEBUG  WindowsBackend: arch=amd64
02-16 08:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\data\isolist.ini
02-16 08:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-16 08:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-16 08:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-16 08:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-16 08:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-16 08:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-16 08:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-16 08:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-16 08:59 DEBUG  WindowsBackend: Fetching host info...
02-16 08:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-16 08:59 DEBUG  WindowsBackend: windows version=vista
02-16 08:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
02-16 08:59 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-16 08:59 DEBUG  WindowsBackend: windows_build=7601
02-16 08:59 DEBUG  WindowsBackend: gmt=-5
02-16 08:59 DEBUG  WindowsBackend: country=US
02-16 08:59 DEBUG  WindowsBackend: timezone=America/New_York
02-16 08:59 DEBUG  WindowsBackend: windows_username=Administrator
02-16 08:59 DEBUG  WindowsBackend: user_full_name=Administrator
02-16 08:59 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
02-16 08:59 DEBUG  WindowsBackend: windows_language_code=1033
02-16 08:59 DEBUG  WindowsBackend: windows_language=English
02-16 08:59 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
02-16 08:59 DEBUG  WindowsBackend: bootloader=vista
02-16 08:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 38085.3046875 mb free ntfs)
02-16 08:59 DEBUG  WindowsBackend: drive=Drive(C: hd 38085.3046875 mb free ntfs)
02-16 08:59 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-16 08:59 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-16 08:59 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-16 08:59 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-16 08:59 DEBUG  WindowsBackend: keyboard_id=67699721
02-16 08:59 DEBUG  WindowsBackend: keyboard_layout=us
02-16 08:59 DEBUG  WindowsBackend: keyboard_variant=
02-16 08:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-16 08:59 DEBUG  CommonBackend: locale=en_US.UTF-8
02-16 08:59 DEBUG  WindowsBackend: total_memory_mb=1013.359375
02-16 08:59 DEBUG  CommonBackend: Searching ISOs on USB devices
02-16 08:59 DEBUG  CommonBackend: Searching for local CDs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Ubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Ubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Kubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Kubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Xubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Xubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Mythbuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Mythbuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 INFO   root: Already installed, running the uninstaller...
02-16 08:59 INFO   root: Running the uninstaller...
02-16 08:59 INFO   CommonBackend: This is the uninstaller running
02-16 08:59 DEBUG  WindowsFrontend: __init__...
02-16 08:59 DEBUG  WindowsFrontend: on_init...
02-16 08:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\translations, languages=['en_US', 'en']
02-16 08:59 INFO   root: Received settings
02-16 08:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\translations, languages=['en_US', 'en']
02-16 08:59 DEBUG  TaskList: # Running tasklist...
02-16 08:59 DEBUG  TaskList: ## Running Remove bootloader entry...
02-16 08:59 DEBUG  WindowsBackend: Removing bcd entry {d390b265-4463-11e1-81ad-0026b9e2135e}
02-16 08:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
02-16 08:59 DEBUG  WindowsBackend: undo_bootini C:
02-16 08:59 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 38085.3046875 mb free ntfs)
02-16 08:59 DEBUG  WindowsBackend: undo_bootini Q:
02-16 08:59 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
02-16 08:59 DEBUG  TaskList: ## Finished Remove bootloader entry
02-16 08:59 DEBUG  TaskList: ## Running Remove target dir...
02-16 08:59 DEBUG  CommonBackend: Deleting C:\ubuntu
02-16 08:59 DEBUG  TaskList: ## Finished Remove target dir
02-16 08:59 DEBUG  TaskList: ## Running Remove registry key...
02-16 08:59 DEBUG  TaskList: ## Finished Remove registry key
02-16 08:59 DEBUG  TaskList: # Finished tasklist
02-16 08:59 INFO   root: Almost finished uninstalling
02-16 08:59 INFO   root: Finished uninstallation
02-16 08:59 DEBUG  CommonBackend: Fetching basic info...
02-16 08:59 DEBUG  CommonBackend: original_exe=C:\Users\Administrator\Desktop\wubi.exe
02-16 08:59 DEBUG  CommonBackend: platform=win32
02-16 08:59 DEBUG  CommonBackend: osname=nt
02-16 08:59 DEBUG  WindowsBackend: arch=amd64
02-16 08:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\data\isolist.ini
02-16 08:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-16 08:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-16 08:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-16 08:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-16 08:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-16 08:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-16 08:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-16 08:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-16 08:59 DEBUG  WindowsBackend: Fetching host info...
02-16 08:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-16 08:59 DEBUG  WindowsBackend: windows version=vista
02-16 08:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
02-16 08:59 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-16 08:59 DEBUG  WindowsBackend: windows_build=7601
02-16 08:59 DEBUG  WindowsBackend: gmt=-5
02-16 08:59 DEBUG  WindowsBackend: country=US
02-16 08:59 DEBUG  WindowsBackend: timezone=America/New_York
02-16 08:59 DEBUG  WindowsBackend: windows_username=Administrator
02-16 08:59 DEBUG  WindowsBackend: user_full_name=Administrator
02-16 08:59 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
02-16 08:59 DEBUG  WindowsBackend: windows_language_code=1033
02-16 08:59 DEBUG  WindowsBackend: windows_language=English
02-16 08:59 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
02-16 08:59 DEBUG  WindowsBackend: bootloader=vista
02-16 08:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 38092.640625 mb free ntfs)
02-16 08:59 DEBUG  WindowsBackend: drive=Drive(C: hd 38092.640625 mb free ntfs)
02-16 08:59 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-16 08:59 DEBUG  WindowsBackend: uninstaller_path=None
02-16 08:59 DEBUG  WindowsBackend: previous_target_dir=None
02-16 08:59 DEBUG  WindowsBackend: previous_distro_name=None
02-16 08:59 DEBUG  WindowsBackend: keyboard_id=67699721
02-16 08:59 DEBUG  WindowsBackend: keyboard_layout=us
02-16 08:59 DEBUG  WindowsBackend: keyboard_variant=
02-16 08:59 DEBUG  WindowsBackend: total_memory_mb=1013.359375
02-16 08:59 DEBUG  CommonBackend: Searching ISOs on USB devices
02-16 08:59 DEBUG  CommonBackend: Searching for local CDs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Ubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Ubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Kubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Kubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Xubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Xubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Mythbuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Mythbuntu CD
02-16 08:59 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 08:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 08:59 INFO   root: Running the installer...
02-16 08:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\translations, languages=['en_US', 'en']
02-16 08:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\translations, languages=['en_US', 'en']
02-16 09:00 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=5000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=gerald
02-16 09:00 INFO   root: Received settings
02-16 09:00 DEBUG  CommonBackend: Searching for local CD
02-16 09:00 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp is a valid Ubuntu CD
02-16 09:00 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\casper\filesystem.squashfs
02-16 09:00 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 09:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:00 DEBUG  CommonBackend: Searching for local ISO
02-16 09:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\translations, languages=['en_US', 'en']
02-16 09:00 DEBUG  TaskList: # Running tasklist...
02-16 09:00 DEBUG  TaskList: ## Running select_target_dir...
02-16 09:00 INFO   WindowsBackend: Installing into C:\ubuntu
02-16 09:00 DEBUG  TaskList: ## Finished select_target_dir
02-16 09:00 DEBUG  TaskList: ## Running create_dir_structure...
02-16 09:00 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-16 09:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-16 09:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-16 09:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-16 09:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-16 09:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-16 09:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-16 09:00 DEBUG  TaskList: ## Finished create_dir_structure
02-16 09:00 DEBUG  TaskList: ## Running create_uninstaller...
02-16 09:00 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Administrator\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-16 09:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-16 09:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-16 09:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-16 09:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-16 09:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-16 09:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-16 09:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
02-16 09:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
02-16 09:00 DEBUG  TaskList: ## Finished create_uninstaller
02-16 09:00 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-16 09:00 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-16 09:00 DEBUG  TaskList: ## Running get_diskimage...
02-16 09:00 DEBUG  TaskList: New task download
02-16 09:00 DEBUG  TaskList: ### Running download...
02-16 09:00 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-16 09:00 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-16 09:36 DEBUG  TaskList: ### Finished download
02-16 09:36 DEBUG  downloader: download finished (read 507143012 bytes)
02-16 09:36 DEBUG  TaskList: ## Finished get_diskimage
02-16 09:36 DEBUG  TaskList: ## Running extract_diskimage...
02-16 09:40 DEBUG  TaskList: ## Finished extract_diskimage
02-16 09:40 DEBUG  TaskList: ## Running choose_disk_sizes...
02-16 09:40 DEBUG  WindowsBackend: total size=5000
  root=4744
  swap=256
  home=0
  usr=0
02-16 09:40 DEBUG  TaskList: ## Finished choose_disk_sizes
02-16 09:40 DEBUG  TaskList: ## Running expand_diskimage...
02-16 09:41 DEBUG  TaskList: ## Finished expand_diskimage
02-16 09:41 DEBUG  TaskList: ## Running create_swap_diskimage...
02-16 09:41 DEBUG  TaskList: ## Finished create_swap_diskimage
02-16 09:41 DEBUG  TaskList: ## Running modify_bootloader...
02-16 09:41 DEBUG  TaskList: New task modify_bcd
02-16 09:41 DEBUG  TaskList: ### Running modify_bcd...
02-16 09:41 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 38092.640625 mb free ntfs)
02-16 09:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {484de166-58ac-11e1-b4a0-001e101f79c9}
02-16 09:41 DEBUG  TaskList: ### Finished modify_bcd
02-16 09:41 DEBUG  TaskList: New task modify_bcd
02-16 09:41 DEBUG  TaskList: ### Running modify_bcd...
02-16 09:41 DEBUG  WindowsBackend: modify_bcd Drive(Q: hd 0.0 mb free )
02-16 09:41 DEBUG  WindowsBackend: BCD has already been modified
02-16 09:41 DEBUG  TaskList: ### Finished modify_bcd
02-16 09:41 DEBUG  TaskList: ## Finished modify_bootloader
02-16 09:41 DEBUG  TaskList: ## Running diskimage_bootloader...
02-16 09:41 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl71F4.tmp\winboot -> C:\ubuntu\winboot
02-16 09:41 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-16 09:41 DEBUG  TaskList: # Cancelling tasklist
02-16 09:41 DEBUG  TaskList: # Finished tasklist
02-16 09:41 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-16 09:41 INFO   root: === wubi 11.10 rev245 ===
02-16 09:41 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-11.10-rev245.log
02-16 09:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Administrator\\Desktop\\wubi.exe"']
02-16 09:41 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\data
02-16 09:41 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\bin\7z.exe
02-16 09:41 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-16 09:41 DEBUG  CommonBackend: Fetching basic info...
02-16 09:41 DEBUG  CommonBackend: original_exe=C:\Users\Administrator\Desktop\wubi.exe
02-16 09:41 DEBUG  CommonBackend: platform=win32
02-16 09:41 DEBUG  CommonBackend: osname=nt
02-16 09:41 DEBUG  CommonBackend: language=en_US
02-16 09:41 DEBUG  CommonBackend: encoding=cp1252
02-16 09:41 DEBUG  WindowsBackend: arch=amd64
02-16 09:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\data\isolist.ini
02-16 09:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-16 09:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-16 09:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-16 09:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-16 09:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-16 09:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-16 09:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-16 09:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-16 09:41 DEBUG  WindowsBackend: Fetching host info...
02-16 09:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-16 09:41 DEBUG  WindowsBackend: windows version=vista
02-16 09:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
02-16 09:41 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-16 09:41 DEBUG  WindowsBackend: windows_build=7601
02-16 09:41 DEBUG  WindowsBackend: gmt=-5
02-16 09:41 DEBUG  WindowsBackend: country=US
02-16 09:41 DEBUG  WindowsBackend: timezone=America/New_York
02-16 09:41 DEBUG  WindowsBackend: windows_username=Administrator
02-16 09:41 DEBUG  WindowsBackend: user_full_name=Administrator
02-16 09:41 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
02-16 09:41 DEBUG  WindowsBackend: windows_language_code=1033
02-16 09:41 DEBUG  WindowsBackend: windows_language=English
02-16 09:41 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
02-16 09:41 DEBUG  WindowsBackend: bootloader=vista
02-16 09:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 34955.1445313 mb free ntfs)
02-16 09:41 DEBUG  WindowsBackend: drive=Drive(C: hd 34955.1445313 mb free ntfs)
02-16 09:41 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-16 09:41 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-16 09:41 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-16 09:41 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-16 09:41 DEBUG  WindowsBackend: keyboard_id=67699721
02-16 09:41 DEBUG  WindowsBackend: keyboard_layout=us
02-16 09:41 DEBUG  WindowsBackend: keyboard_variant=
02-16 09:41 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-16 09:41 DEBUG  CommonBackend: locale=en_US.UTF-8
02-16 09:41 DEBUG  WindowsBackend: total_memory_mb=1013.359375
02-16 09:41 DEBUG  CommonBackend: Searching ISOs on USB devices
02-16 09:41 DEBUG  CommonBackend: Searching for local CDs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Ubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Ubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Kubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Kubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Xubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Xubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Mythbuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Mythbuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 INFO   root: Already installed, running the uninstaller...
02-16 09:41 INFO   root: Running the uninstaller...
02-16 09:41 INFO   CommonBackend: This is the uninstaller running
02-16 09:41 DEBUG  WindowsFrontend: __init__...
02-16 09:41 DEBUG  WindowsFrontend: on_init...
02-16 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\translations, languages=['en_US', 'en']
02-16 09:41 INFO   root: Received settings
02-16 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\translations, languages=['en_US', 'en']
02-16 09:41 DEBUG  TaskList: # Running tasklist...
02-16 09:41 DEBUG  TaskList: ## Running Remove bootloader entry...
02-16 09:41 DEBUG  WindowsBackend: Removing bcd entry {484de166-58ac-11e1-b4a0-001e101f79c9}
02-16 09:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
02-16 09:41 DEBUG  WindowsBackend: undo_bootini C:
02-16 09:41 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 34955.1445313 mb free ntfs)
02-16 09:41 DEBUG  WindowsBackend: undo_bootini Q:
02-16 09:41 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
02-16 09:41 DEBUG  TaskList: ## Finished Remove bootloader entry
02-16 09:41 DEBUG  TaskList: ## Running Remove target dir...
02-16 09:41 DEBUG  CommonBackend: Deleting C:\ubuntu
02-16 09:41 DEBUG  TaskList: ## Finished Remove target dir
02-16 09:41 DEBUG  TaskList: ## Running Remove registry key...
02-16 09:41 DEBUG  TaskList: ## Finished Remove registry key
02-16 09:41 DEBUG  TaskList: # Finished tasklist
02-16 09:41 INFO   root: Almost finished uninstalling
02-16 09:41 INFO   root: Finished uninstallation
02-16 09:41 DEBUG  CommonBackend: Fetching basic info...
02-16 09:41 DEBUG  CommonBackend: original_exe=C:\Users\Administrator\Desktop\wubi.exe
02-16 09:41 DEBUG  CommonBackend: platform=win32
02-16 09:41 DEBUG  CommonBackend: osname=nt
02-16 09:41 DEBUG  WindowsBackend: arch=amd64
02-16 09:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\data\isolist.ini
02-16 09:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-16 09:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-16 09:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-16 09:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-16 09:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-16 09:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-16 09:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-16 09:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-16 09:41 DEBUG  WindowsBackend: Fetching host info...
02-16 09:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-16 09:41 DEBUG  WindowsBackend: windows version=vista
02-16 09:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
02-16 09:41 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-16 09:41 DEBUG  WindowsBackend: windows_build=7601
02-16 09:41 DEBUG  WindowsBackend: gmt=-5
02-16 09:41 DEBUG  WindowsBackend: country=US
02-16 09:41 DEBUG  WindowsBackend: timezone=America/New_York
02-16 09:41 DEBUG  WindowsBackend: windows_username=Administrator
02-16 09:41 DEBUG  WindowsBackend: user_full_name=Administrator
02-16 09:41 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
02-16 09:41 DEBUG  WindowsBackend: windows_language_code=1033
02-16 09:41 DEBUG  WindowsBackend: windows_language=English
02-16 09:41 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
02-16 09:41 DEBUG  WindowsBackend: bootloader=vista
02-16 09:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 37534.4960938 mb free ntfs)
02-16 09:41 DEBUG  WindowsBackend: drive=Drive(C: hd 37534.4960938 mb free ntfs)
02-16 09:41 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-16 09:41 DEBUG  WindowsBackend: uninstaller_path=None
02-16 09:41 DEBUG  WindowsBackend: previous_target_dir=None
02-16 09:41 DEBUG  WindowsBackend: previous_distro_name=None
02-16 09:41 DEBUG  WindowsBackend: keyboard_id=67699721
02-16 09:41 DEBUG  WindowsBackend: keyboard_layout=us
02-16 09:41 DEBUG  WindowsBackend: keyboard_variant=
02-16 09:41 DEBUG  WindowsBackend: total_memory_mb=1013.359375
02-16 09:41 DEBUG  CommonBackend: Searching ISOs on USB devices
02-16 09:41 DEBUG  CommonBackend: Searching for local CDs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Ubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Ubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Kubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Kubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Xubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Xubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Mythbuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Mythbuntu CD
02-16 09:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 09:41 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:41 INFO   root: Running the installer...
02-16 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\translations, languages=['en_US', 'en']
02-16 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\translations, languages=['en_US', 'en']
02-16 09:42 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=5000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=gerald
02-16 09:42 INFO   root: Received settings
02-16 09:42 DEBUG  CommonBackend: Searching for local CD
02-16 09:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp is a valid Ubuntu CD
02-16 09:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\casper\filesystem.squashfs
02-16 09:42 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 09:42 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 09:42 DEBUG  CommonBackend: Searching for local ISO
02-16 09:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\translations, languages=['en_US', 'en']
02-16 09:42 DEBUG  TaskList: # Running tasklist...
02-16 09:42 DEBUG  TaskList: ## Running select_target_dir...
02-16 09:42 INFO   WindowsBackend: Installing into C:\ubuntu
02-16 09:42 DEBUG  TaskList: ## Finished select_target_dir
02-16 09:42 DEBUG  TaskList: ## Running create_dir_structure...
02-16 09:42 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-16 09:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-16 09:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-16 09:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-16 09:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-16 09:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-16 09:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-16 09:42 DEBUG  TaskList: ## Finished create_dir_structure
02-16 09:42 DEBUG  TaskList: ## Running create_uninstaller...
02-16 09:42 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Administrator\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-16 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-16 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-16 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-16 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-16 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-16 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-16 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
02-16 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
02-16 09:42 DEBUG  TaskList: ## Finished create_uninstaller
02-16 09:42 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-16 09:42 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-16 09:42 DEBUG  TaskList: ## Running get_diskimage...
02-16 09:42 DEBUG  TaskList: New task download
02-16 09:42 DEBUG  TaskList: ### Running download...
02-16 09:42 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-16 09:42 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-16 10:25 DEBUG  TaskList: ### Finished download
02-16 10:25 DEBUG  downloader: download finished (read 507143012 bytes)
02-16 10:25 DEBUG  TaskList: ## Finished get_diskimage
02-16 10:25 DEBUG  TaskList: ## Running extract_diskimage...
02-16 10:28 DEBUG  TaskList: ## Finished extract_diskimage
02-16 10:28 DEBUG  TaskList: ## Running choose_disk_sizes...
02-16 10:28 DEBUG  WindowsBackend: total size=5000
  root=4744
  swap=256
  home=0
  usr=0
02-16 10:28 DEBUG  TaskList: ## Finished choose_disk_sizes
02-16 10:28 DEBUG  TaskList: ## Running expand_diskimage...
02-16 10:29 DEBUG  TaskList: ## Finished expand_diskimage
02-16 10:29 DEBUG  TaskList: ## Running create_swap_diskimage...
02-16 10:29 DEBUG  TaskList: ## Finished create_swap_diskimage
02-16 10:29 DEBUG  TaskList: ## Running modify_bootloader...
02-16 10:29 DEBUG  TaskList: New task modify_bcd
02-16 10:29 DEBUG  TaskList: ### Running modify_bcd...
02-16 10:29 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 37534.4960938 mb free ntfs)
02-16 10:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {484de167-58ac-11e1-b4a0-001e101f79c9}
02-16 10:29 DEBUG  TaskList: ### Finished modify_bcd
02-16 10:29 DEBUG  TaskList: New task modify_bcd
02-16 10:29 DEBUG  TaskList: ### Running modify_bcd...
02-16 10:29 DEBUG  WindowsBackend: modify_bcd Drive(Q: hd 0.0 mb free )
02-16 10:29 DEBUG  WindowsBackend: BCD has already been modified
02-16 10:29 DEBUG  TaskList: ### Finished modify_bcd
02-16 10:29 DEBUG  TaskList: ## Finished modify_bootloader
02-16 10:29 DEBUG  TaskList: ## Running diskimage_bootloader...
02-16 10:29 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl7011.tmp\winboot -> C:\ubuntu\winboot
02-16 10:29 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-16 10:29 DEBUG  TaskList: # Cancelling tasklist
02-16 10:29 DEBUG  TaskList: # Finished tasklist
02-16 10:29 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-16 10:30 INFO   root: === wubi 11.10 rev245 ===
02-16 10:30 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-11.10-rev245.log
02-16 10:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
02-16 10:30 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp\data
02-16 10:30 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp\bin\7z.exe
02-16 10:30 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-16 10:30 DEBUG  CommonBackend: Fetching basic info...
02-16 10:30 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-16 10:30 DEBUG  CommonBackend: platform=win32
02-16 10:30 DEBUG  CommonBackend: osname=nt
02-16 10:30 DEBUG  CommonBackend: language=en_US
02-16 10:30 DEBUG  CommonBackend: encoding=cp1252
02-16 10:30 DEBUG  WindowsBackend: arch=amd64
02-16 10:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp\data\isolist.ini
02-16 10:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-16 10:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-16 10:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-16 10:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-16 10:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-16 10:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-16 10:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-16 10:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-16 10:30 DEBUG  WindowsBackend: Fetching host info...
02-16 10:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-16 10:30 DEBUG  WindowsBackend: windows version=vista
02-16 10:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
02-16 10:30 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-16 10:30 DEBUG  WindowsBackend: windows_build=7601
02-16 10:30 DEBUG  WindowsBackend: gmt=-5
02-16 10:30 DEBUG  WindowsBackend: country=US
02-16 10:30 DEBUG  WindowsBackend: timezone=America/New_York
02-16 10:30 DEBUG  WindowsBackend: windows_username=Administrator
02-16 10:30 DEBUG  WindowsBackend: user_full_name=Administrator
02-16 10:30 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
02-16 10:30 DEBUG  WindowsBackend: windows_language_code=1033
02-16 10:30 DEBUG  WindowsBackend: windows_language=English
02-16 10:30 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
02-16 10:30 DEBUG  WindowsBackend: bootloader=vista
02-16 10:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 34944.328125 mb free ntfs)
02-16 10:30 DEBUG  WindowsBackend: drive=Drive(C: hd 34944.328125 mb free ntfs)
02-16 10:30 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-16 10:30 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-16 10:30 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-16 10:30 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-16 10:30 DEBUG  WindowsBackend: keyboard_id=67699721
02-16 10:30 DEBUG  WindowsBackend: keyboard_layout=us
02-16 10:30 DEBUG  WindowsBackend: keyboard_variant=
02-16 10:30 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-16 10:30 DEBUG  CommonBackend: locale=en_US.UTF-8
02-16 10:30 DEBUG  WindowsBackend: total_memory_mb=1013.359375
02-16 10:30 DEBUG  CommonBackend: Searching ISOs on USB devices
02-16 10:30 DEBUG  CommonBackend: Searching for local CDs
02-16 10:30 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp is a valid Ubuntu CD
02-16 10:30 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp\casper\filesystem.squashfs
02-16 10:30 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp is a valid Ubuntu CD
02-16 10:30 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp\casper\filesystem.squashfs
02-16 10:30 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp is a valid Kubuntu CD
02-16 10:30 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp\casper\filesystem.squashfs
02-16 10:30 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp is a valid Kubuntu CD
02-16 10:30 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp\casper\filesystem.squashfs
02-16 10:30 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp is a valid Xubuntu CD
02-16 10:30 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp\casper\filesystem.squashfs
02-16 10:30 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp is a valid Xubuntu CD
02-16 10:30 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp\casper\filesystem.squashfs
02-16 10:30 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp is a valid Mythbuntu CD
02-16 10:30 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp\casper\filesystem.squashfs
02-16 10:30 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp is a valid Mythbuntu CD
02-16 10:30 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp\casper\filesystem.squashfs
02-16 10:30 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 10:30 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:30 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 10:30 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:30 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 10:30 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:30 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 10:30 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:30 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 10:30 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:30 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 10:30 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:30 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 10:30 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:30 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 10:30 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:30 INFO   root: Running the uninstaller...
02-16 10:30 INFO   CommonBackend: This is the uninstaller running
02-16 10:30 DEBUG  WindowsFrontend: __init__...
02-16 10:30 DEBUG  WindowsFrontend: on_init...
02-16 10:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp\translations, languages=['en_US', 'en']
02-16 10:31 INFO   root: Received settings
02-16 10:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp\translations, languages=['en_US', 'en']
02-16 10:31 DEBUG  TaskList: # Running tasklist...
02-16 10:31 DEBUG  TaskList: ## Running Remove bootloader entry...
02-16 10:31 DEBUG  WindowsBackend: Removing bcd entry {484de167-58ac-11e1-b4a0-001e101f79c9}
02-16 10:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
02-16 10:31 DEBUG  WindowsBackend: undo_bootini C:
02-16 10:31 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 34944.328125 mb free ntfs)
02-16 10:31 DEBUG  WindowsBackend: undo_bootini Q:
02-16 10:31 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
02-16 10:31 DEBUG  TaskList: ## Finished Remove bootloader entry
02-16 10:31 DEBUG  TaskList: ## Running Remove target dir...
02-16 10:31 DEBUG  CommonBackend: Deleting C:\ubuntu
02-16 10:31 DEBUG  TaskList: ## Finished Remove target dir
02-16 10:31 DEBUG  TaskList: ## Running Remove registry key...
02-16 10:31 DEBUG  TaskList: ## Finished Remove registry key
02-16 10:31 DEBUG  TaskList: # Finished tasklist
02-16 10:31 INFO   root: Almost finished uninstalling
02-16 10:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylD337.tmp\translations, languages=['en_US', 'en']
02-16 10:31 INFO   root: Finished uninstallation
02-16 10:31 DEBUG  root: application.quit
02-16 10:31 DEBUG  WindowsFrontend: frontend.quit
02-16 10:31 DEBUG  WindowsFrontend: frontend.on_quit
02-16 10:31 DEBUG  root: application.on_quit
02-16 10:31 INFO   root: sys.exit
02-16 10:34 INFO   root: === wubi 11.10 rev245 ===
02-16 10:34 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-11.10-rev245.log
02-16 10:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Administrator\\Desktop\\wubi.exe"']
02-16 10:34 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\data
02-16 10:34 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\bin\7z.exe
02-16 10:34 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-16 10:34 DEBUG  CommonBackend: Fetching basic info...
02-16 10:34 DEBUG  CommonBackend: original_exe=C:\Users\Administrator\Desktop\wubi.exe
02-16 10:34 DEBUG  CommonBackend: platform=win32
02-16 10:34 DEBUG  CommonBackend: osname=nt
02-16 10:34 DEBUG  CommonBackend: language=en_US
02-16 10:34 DEBUG  CommonBackend: encoding=cp1252
02-16 10:34 DEBUG  WindowsBackend: arch=amd64
02-16 10:34 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\data\isolist.ini
02-16 10:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-16 10:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-16 10:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-16 10:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-16 10:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-16 10:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-16 10:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-16 10:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-16 10:34 DEBUG  WindowsBackend: Fetching host info...
02-16 10:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-16 10:34 DEBUG  WindowsBackend: windows version=vista
02-16 10:34 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
02-16 10:34 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-16 10:34 DEBUG  WindowsBackend: windows_build=7601
02-16 10:34 DEBUG  WindowsBackend: gmt=-5
02-16 10:34 DEBUG  WindowsBackend: country=US
02-16 10:34 DEBUG  WindowsBackend: timezone=America/New_York
02-16 10:34 DEBUG  WindowsBackend: windows_username=Administrator
02-16 10:34 DEBUG  WindowsBackend: user_full_name=Administrator
02-16 10:34 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
02-16 10:34 DEBUG  WindowsBackend: windows_language_code=1033
02-16 10:34 DEBUG  WindowsBackend: windows_language=English
02-16 10:34 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
02-16 10:34 DEBUG  WindowsBackend: bootloader=vista
02-16 10:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 37533.7929688 mb free ntfs)
02-16 10:34 DEBUG  WindowsBackend: drive=Drive(C: hd 37533.7929688 mb free ntfs)
02-16 10:34 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-16 10:34 DEBUG  WindowsBackend: uninstaller_path=None
02-16 10:34 DEBUG  WindowsBackend: previous_target_dir=None
02-16 10:34 DEBUG  WindowsBackend: previous_distro_name=None
02-16 10:34 DEBUG  WindowsBackend: keyboard_id=67699721
02-16 10:34 DEBUG  WindowsBackend: keyboard_layout=us
02-16 10:34 DEBUG  WindowsBackend: keyboard_variant=
02-16 10:34 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-16 10:34 DEBUG  CommonBackend: locale=en_US.UTF-8
02-16 10:34 DEBUG  WindowsBackend: total_memory_mb=1013.359375
02-16 10:34 DEBUG  CommonBackend: Searching ISOs on USB devices
02-16 10:34 DEBUG  CommonBackend: Searching for local CDs
02-16 10:34 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp is a valid Ubuntu CD
02-16 10:34 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\casper\filesystem.squashfs
02-16 10:34 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp is a valid Ubuntu CD
02-16 10:34 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\casper\filesystem.squashfs
02-16 10:34 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp is a valid Kubuntu CD
02-16 10:34 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\casper\filesystem.squashfs
02-16 10:34 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp is a valid Kubuntu CD
02-16 10:34 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\casper\filesystem.squashfs
02-16 10:34 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp is a valid Xubuntu CD
02-16 10:34 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\casper\filesystem.squashfs
02-16 10:34 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp is a valid Xubuntu CD
02-16 10:34 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\casper\filesystem.squashfs
02-16 10:34 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp is a valid Mythbuntu CD
02-16 10:34 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\casper\filesystem.squashfs
02-16 10:34 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp is a valid Mythbuntu CD
02-16 10:34 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\casper\filesystem.squashfs
02-16 10:34 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 10:34 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:34 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 10:34 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:34 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 10:34 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:34 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 10:34 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:34 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 10:34 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:34 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 10:34 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:34 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 10:34 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:34 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 10:34 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:34 INFO   root: Running the installer...
02-16 10:34 DEBUG  WindowsFrontend: __init__...
02-16 10:34 DEBUG  WindowsFrontend: on_init...
02-16 10:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\translations, languages=['en_US', 'en']
02-16 10:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\translations, languages=['en_US', 'en']
02-16 10:36 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=5000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=gerald
02-16 10:36 INFO   root: Received settings
02-16 10:36 DEBUG  CommonBackend: Searching for local CD
02-16 10:36 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp is a valid Ubuntu CD
02-16 10:36 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\casper\filesystem.squashfs
02-16 10:36 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 10:36 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 10:36 DEBUG  CommonBackend: Searching for local ISO
02-16 10:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\translations, languages=['en_US', 'en']
02-16 10:36 DEBUG  TaskList: # Running tasklist...
02-16 10:36 DEBUG  TaskList: ## Running select_target_dir...
02-16 10:36 INFO   WindowsBackend: Installing into C:\ubuntu
02-16 10:36 DEBUG  TaskList: ## Finished select_target_dir
02-16 10:36 DEBUG  TaskList: ## Running create_dir_structure...
02-16 10:36 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-16 10:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-16 10:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-16 10:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-16 10:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-16 10:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-16 10:36 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-16 10:36 DEBUG  TaskList: ## Finished create_dir_structure
02-16 10:36 DEBUG  TaskList: ## Running create_uninstaller...
02-16 10:36 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Administrator\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-16 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-16 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-16 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-16 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-16 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-16 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-16 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
02-16 10:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
02-16 10:36 DEBUG  TaskList: ## Finished create_uninstaller
02-16 10:36 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-16 10:36 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-16 10:36 DEBUG  TaskList: ## Running get_diskimage...
02-16 10:36 DEBUG  TaskList: New task download
02-16 10:36 DEBUG  TaskList: ### Running download...
02-16 10:36 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-16 10:36 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-16 11:21 DEBUG  TaskList: ### Finished download
02-16 11:21 DEBUG  downloader: download finished (read 507143012 bytes)
02-16 11:21 DEBUG  TaskList: ## Finished get_diskimage
02-16 11:21 DEBUG  TaskList: ## Running extract_diskimage...
02-16 11:25 DEBUG  TaskList: ## Finished extract_diskimage
02-16 11:25 DEBUG  TaskList: ## Running choose_disk_sizes...
02-16 11:25 DEBUG  WindowsBackend: total size=5000
  root=4744
  swap=256
  home=0
  usr=0
02-16 11:25 DEBUG  TaskList: ## Finished choose_disk_sizes
02-16 11:25 DEBUG  TaskList: ## Running expand_diskimage...
02-16 11:26 DEBUG  TaskList: ## Finished expand_diskimage
02-16 11:26 DEBUG  TaskList: ## Running create_swap_diskimage...
02-16 11:26 DEBUG  TaskList: ## Finished create_swap_diskimage
02-16 11:26 DEBUG  TaskList: ## Running modify_bootloader...
02-16 11:26 DEBUG  TaskList: New task modify_bcd
02-16 11:26 DEBUG  TaskList: ### Running modify_bcd...
02-16 11:26 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 37533.7929688 mb free ntfs)
02-16 11:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {484de168-58ac-11e1-b4a0-001e101f79c9}
02-16 11:26 DEBUG  TaskList: ### Finished modify_bcd
02-16 11:26 DEBUG  TaskList: New task modify_bcd
02-16 11:26 DEBUG  TaskList: ### Running modify_bcd...
02-16 11:26 DEBUG  WindowsBackend: modify_bcd Drive(Q: hd 0.0 mb free )
02-16 11:26 DEBUG  WindowsBackend: BCD has already been modified
02-16 11:26 DEBUG  TaskList: ### Finished modify_bcd
02-16 11:26 DEBUG  TaskList: ## Finished modify_bootloader
02-16 11:26 DEBUG  TaskList: ## Running diskimage_bootloader...
02-16 11:26 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl3775.tmp\winboot -> C:\ubuntu\winboot
02-16 11:26 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-16 11:26 DEBUG  TaskList: # Cancelling tasklist
02-16 11:26 DEBUG  TaskList: # Finished tasklist
02-16 11:26 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-16 11:27 INFO   root: === wubi 11.10 rev245 ===
02-16 11:27 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-11.10-rev245.log
02-16 11:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
02-16 11:27 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp\data
02-16 11:27 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp\bin\7z.exe
02-16 11:27 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-16 11:27 DEBUG  CommonBackend: Fetching basic info...
02-16 11:27 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-16 11:27 DEBUG  CommonBackend: platform=win32
02-16 11:27 DEBUG  CommonBackend: osname=nt
02-16 11:27 DEBUG  CommonBackend: language=en_US
02-16 11:27 DEBUG  CommonBackend: encoding=cp1252
02-16 11:27 DEBUG  WindowsBackend: arch=amd64
02-16 11:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp\data\isolist.ini
02-16 11:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-16 11:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-16 11:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-16 11:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-16 11:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-16 11:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-16 11:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-16 11:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-16 11:27 DEBUG  WindowsBackend: Fetching host info...
02-16 11:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-16 11:27 DEBUG  WindowsBackend: windows version=vista
02-16 11:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
02-16 11:27 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-16 11:27 DEBUG  WindowsBackend: windows_build=7601
02-16 11:27 DEBUG  WindowsBackend: gmt=-5
02-16 11:27 DEBUG  WindowsBackend: country=US
02-16 11:27 DEBUG  WindowsBackend: timezone=America/New_York
02-16 11:27 DEBUG  WindowsBackend: windows_username=Administrator
02-16 11:27 DEBUG  WindowsBackend: user_full_name=Administrator
02-16 11:27 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
02-16 11:27 DEBUG  WindowsBackend: windows_language_code=1033
02-16 11:27 DEBUG  WindowsBackend: windows_language=English
02-16 11:27 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
02-16 11:27 DEBUG  WindowsBackend: bootloader=vista
02-16 11:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 34729.4296875 mb free ntfs)
02-16 11:27 DEBUG  WindowsBackend: drive=Drive(C: hd 34729.4257813 mb free ntfs)
02-16 11:27 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-16 11:27 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-16 11:27 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-16 11:27 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-16 11:27 DEBUG  WindowsBackend: keyboard_id=67699721
02-16 11:27 DEBUG  WindowsBackend: keyboard_layout=us
02-16 11:27 DEBUG  WindowsBackend: keyboard_variant=
02-16 11:27 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-16 11:27 DEBUG  CommonBackend: locale=en_US.UTF-8
02-16 11:27 DEBUG  WindowsBackend: total_memory_mb=1013.359375
02-16 11:27 DEBUG  CommonBackend: Searching ISOs on USB devices
02-16 11:27 DEBUG  CommonBackend: Searching for local CDs
02-16 11:27 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp is a valid Ubuntu CD
02-16 11:27 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp\casper\filesystem.squashfs
02-16 11:27 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp is a valid Ubuntu CD
02-16 11:27 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp\casper\filesystem.squashfs
02-16 11:27 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp is a valid Kubuntu CD
02-16 11:27 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp\casper\filesystem.squashfs
02-16 11:27 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp is a valid Kubuntu CD
02-16 11:27 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp\casper\filesystem.squashfs
02-16 11:27 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp is a valid Xubuntu CD
02-16 11:27 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp\casper\filesystem.squashfs
02-16 11:27 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp is a valid Xubuntu CD
02-16 11:27 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp\casper\filesystem.squashfs
02-16 11:27 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp is a valid Mythbuntu CD
02-16 11:27 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp\casper\filesystem.squashfs
02-16 11:27 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp is a valid Mythbuntu CD
02-16 11:27 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp\casper\filesystem.squashfs
02-16 11:27 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 11:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 11:27 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-16 11:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 11:27 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 11:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 11:27 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-16 11:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 11:27 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 11:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 11:27 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-16 11:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 11:27 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 11:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 11:27 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-16 11:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-16 11:27 INFO   root: Running the uninstaller...
02-16 11:27 INFO   CommonBackend: This is the uninstaller running
02-16 11:27 DEBUG  WindowsFrontend: __init__...
02-16 11:27 DEBUG  WindowsFrontend: on_init...
02-16 11:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp\translations, languages=['en_US', 'en']
02-16 11:27 INFO   root: Received settings
02-16 11:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp\translations, languages=['en_US', 'en']
02-16 11:27 DEBUG  TaskList: # Running tasklist...
02-16 11:27 DEBUG  TaskList: ## Running Remove bootloader entry...
02-16 11:27 DEBUG  WindowsBackend: Removing bcd entry {484de168-58ac-11e1-b4a0-001e101f79c9}
02-16 11:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
02-16 11:27 DEBUG  WindowsBackend: undo_bootini C:
02-16 11:27 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 34729.4257813 mb free ntfs)
02-16 11:27 DEBUG  WindowsBackend: undo_bootini Q:
02-16 11:27 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
02-16 11:27 DEBUG  TaskList: ## Finished Remove bootloader entry
02-16 11:27 DEBUG  TaskList: ## Running Remove target dir...
02-16 11:27 DEBUG  CommonBackend: Deleting C:\ubuntu
02-16 11:27 DEBUG  TaskList: ## Finished Remove target dir
02-16 11:27 DEBUG  TaskList: ## Running Remove registry key...
02-16 11:27 DEBUG  TaskList: ## Finished Remove registry key
02-16 11:27 DEBUG  TaskList: # Finished tasklist
02-16 11:27 INFO   root: Almost finished uninstalling
02-16 11:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylDC6C.tmp\translations, languages=['en_US', 'en']
02-16 11:27 INFO   root: Finished uninstallation
02-16 11:27 DEBUG  root: application.quit
02-16 11:27 DEBUG  WindowsFrontend: frontend.quit
02-16 11:27 DEBUG  WindowsFrontend: frontend.on_quit
02-16 11:27 DEBUG  root: application.on_quit
02-16 11:27 INFO   root: sys.exit
02-19 18:23 INFO   root: === wubi 11.10 rev245 ===
02-19 18:23 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-11.10-rev245.log
02-19 18:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Administrator\\Desktop\\wubi.exe"']
02-19 18:23 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\data
02-19 18:23 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\bin\7z.exe
02-19 18:23 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-19 18:23 DEBUG  CommonBackend: Fetching basic info...
02-19 18:23 DEBUG  CommonBackend: original_exe=C:\Users\Administrator\Desktop\wubi.exe
02-19 18:23 DEBUG  CommonBackend: platform=win32
02-19 18:23 DEBUG  CommonBackend: osname=nt
02-19 18:23 DEBUG  CommonBackend: language=en_US
02-19 18:23 DEBUG  CommonBackend: encoding=cp1252
02-19 18:23 DEBUG  WindowsBackend: arch=amd64
02-19 18:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\data\isolist.ini
02-19 18:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-19 18:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-19 18:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-19 18:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-19 18:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-19 18:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-19 18:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-19 18:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-19 18:23 DEBUG  WindowsBackend: Fetching host info...
02-19 18:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-19 18:23 DEBUG  WindowsBackend: windows version=vista
02-19 18:23 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
02-19 18:23 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-19 18:23 DEBUG  WindowsBackend: windows_build=7601
02-19 18:23 DEBUG  WindowsBackend: gmt=-5
02-19 18:23 DEBUG  WindowsBackend: country=US
02-19 18:23 DEBUG  WindowsBackend: timezone=America/New_York
02-19 18:23 DEBUG  WindowsBackend: windows_username=Administrator
02-19 18:23 DEBUG  WindowsBackend: user_full_name=Administrator
02-19 18:23 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
02-19 18:23 DEBUG  WindowsBackend: windows_language_code=1033
02-19 18:23 DEBUG  WindowsBackend: windows_language=English
02-19 18:23 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N450   @ 1.66GHz
02-19 18:23 DEBUG  WindowsBackend: bootloader=vista
02-19 18:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 34499.3085938 mb free ntfs)
02-19 18:23 DEBUG  WindowsBackend: drive=Drive(C: hd 34499.3085938 mb free ntfs)
02-19 18:23 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
02-19 18:23 DEBUG  WindowsBackend: uninstaller_path=None
02-19 18:23 DEBUG  WindowsBackend: previous_target_dir=None
02-19 18:23 DEBUG  WindowsBackend: previous_distro_name=None
02-19 18:23 DEBUG  WindowsBackend: keyboard_id=67699721
02-19 18:23 DEBUG  WindowsBackend: keyboard_layout=us
02-19 18:23 DEBUG  WindowsBackend: keyboard_variant=
02-19 18:23 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-19 18:23 DEBUG  CommonBackend: locale=en_US.UTF-8
02-19 18:23 DEBUG  WindowsBackend: total_memory_mb=1013.359375
02-19 18:23 DEBUG  CommonBackend: Searching ISOs on USB devices
02-19 18:23 DEBUG  CommonBackend: Searching for local CDs
02-19 18:23 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp is a valid Ubuntu CD
02-19 18:23 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\casper\filesystem.squashfs
02-19 18:23 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp is a valid Ubuntu CD
02-19 18:23 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\casper\filesystem.squashfs
02-19 18:23 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp is a valid Kubuntu CD
02-19 18:23 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\casper\filesystem.squashfs
02-19 18:23 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp is a valid Kubuntu CD
02-19 18:23 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\casper\filesystem.squashfs
02-19 18:23 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp is a valid Xubuntu CD
02-19 18:23 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\casper\filesystem.squashfs
02-19 18:23 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp is a valid Xubuntu CD
02-19 18:23 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\casper\filesystem.squashfs
02-19 18:23 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp is a valid Mythbuntu CD
02-19 18:23 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\casper\filesystem.squashfs
02-19 18:23 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp is a valid Mythbuntu CD
02-19 18:23 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\casper\filesystem.squashfs
02-19 18:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-19 18:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-19 18:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-19 18:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-19 18:23 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-19 18:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-19 18:23 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-19 18:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-19 18:23 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-19 18:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-19 18:23 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-19 18:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-19 18:23 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-19 18:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-19 18:23 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-19 18:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-19 18:23 INFO   root: Running the installer...
02-19 18:23 DEBUG  WindowsFrontend: __init__...
02-19 18:23 DEBUG  WindowsFrontend: on_init...
02-19 18:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\translations, languages=['en_US', 'en']
02-19 18:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\translations, languages=['en_US', 'en']
02-19 18:43 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=5000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=gerald
02-19 18:43 INFO   root: Received settings
02-19 18:43 DEBUG  CommonBackend: Searching for local CD
02-19 18:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp is a valid Ubuntu CD
02-19 18:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\casper\filesystem.squashfs
02-19 18:43 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-19 18:43 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-19 18:43 DEBUG  CommonBackend: Searching for local ISO
02-19 18:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\translations, languages=['en_US', 'en']
02-19 18:43 DEBUG  TaskList: # Running tasklist...
02-19 18:43 DEBUG  TaskList: ## Running select_target_dir...
02-19 18:43 INFO   WindowsBackend: Installing into C:\ubuntu
02-19 18:43 DEBUG  TaskList: ## Finished select_target_dir
02-19 18:43 DEBUG  TaskList: ## Running create_dir_structure...
02-19 18:43 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-19 18:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-19 18:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-19 18:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-19 18:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-19 18:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-19 18:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-19 18:43 DEBUG  TaskList: ## Finished create_dir_structure
02-19 18:43 DEBUG  TaskList: ## Running create_uninstaller...
02-19 18:43 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Administrator\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-19 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-19 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-19 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-19 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-19 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-19 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-19 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
02-19 18:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
02-19 18:43 DEBUG  TaskList: ## Finished create_uninstaller
02-19 18:43 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-19 18:43 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-19 18:43 DEBUG  TaskList: ## Running get_diskimage...
02-19 18:43 DEBUG  TaskList: New task download
02-19 18:43 DEBUG  TaskList: ### Running download...
02-19 18:43 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-19 18:43 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-19 19:20 DEBUG  TaskList: ### Finished download
02-19 19:20 DEBUG  downloader: download finished (read 507143012 bytes)
02-19 19:20 DEBUG  TaskList: ## Finished get_diskimage
02-19 19:20 DEBUG  TaskList: ## Running extract_diskimage...
02-19 19:30 DEBUG  TaskList: ## Finished extract_diskimage
02-19 19:30 DEBUG  TaskList: ## Running choose_disk_sizes...
02-19 19:30 DEBUG  WindowsBackend: total size=5000
  root=4744
  swap=256
  home=0
  usr=0
02-19 19:30 DEBUG  TaskList: ## Finished choose_disk_sizes
02-19 19:30 DEBUG  TaskList: ## Running expand_diskimage...
02-19 19:31 DEBUG  TaskList: ## Finished expand_diskimage
02-19 19:31 DEBUG  TaskList: ## Running create_swap_diskimage...
02-19 19:31 DEBUG  TaskList: ## Finished create_swap_diskimage
02-19 19:31 DEBUG  TaskList: ## Running modify_bootloader...
02-19 19:31 DEBUG  TaskList: New task modify_bcd
02-19 19:31 DEBUG  TaskList: ### Running modify_bcd...
02-19 19:31 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 34499.3085938 mb free ntfs)
02-19 19:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {3db3a3bc-5b5a-11e1-ac3f-001e101fb45e}
02-19 19:31 DEBUG  TaskList: ### Finished modify_bcd
02-19 19:31 DEBUG  TaskList: New task modify_bcd
02-19 19:31 DEBUG  TaskList: ### Running modify_bcd...
02-19 19:31 DEBUG  WindowsBackend: modify_bcd Drive(Q: hd 0.0 mb free )
02-19 19:31 DEBUG  WindowsBackend: BCD has already been modified
02-19 19:31 DEBUG  TaskList: ### Finished modify_bcd
02-19 19:31 DEBUG  TaskList: ## Finished modify_bootloader
02-19 19:31 DEBUG  TaskList: ## Running diskimage_bootloader...
02-19 19:31 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl9AD7.tmp\winboot -> C:\ubuntu\winboot
02-19 19:31 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-19 19:31 DEBUG  TaskList: # Cancelling tasklist
02-19 19:31 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
02-19 19:31 DEBUG  TaskList: # Finished tasklist

```

---

